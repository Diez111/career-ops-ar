# Modo: lote — Procesamiento Masivo de Ofertas

Dos modos de uso: **conductor --chrome** (navega portales en tiempo real) o **standalone** (script para URLs ya recolectadas).

## Arquitectura

```text
Conductor (navegador headed)
  │
  │  Chrome: navega portales (sesiones logueadas)
  │  Lee DOM directamente — el usuario ve todo en tiempo real
  │
  ├─ Oferta 1: lee JD del DOM + URL
  │    └─► worker headless → reporte .md + PDF + línea tracker
  │
  ├─ Oferta 2: click siguiente, leer JD + URL
  │    └─► worker headless → reporte .md + PDF + línea tracker
  │
  └─ Fin: merge tracker-additions → applications.md + resumen
```

## Archivos

```text
batch/
  batch-input.tsv               # URLs (del conductor o manual)
  batch-state.tsv               # Progreso (auto-generado, gitignored)
  batch-runner.sh               # Script orquestador standalone
  batch-prompt.md               # Template de prompt para workers
  logs/                         # Un log por oferta (gitignored)
  tracker-additions/            # Líneas de tracker (gitignored)
```

## Modo A: Conductor --chrome

1. **Leer estado**: `batch/batch-state.tsv` → identificar lo ya procesado
2. **Navegar portal**: Chrome → URL de búsqueda
3. **Extraer URLs**: Leer DOM de resultados → extraer lista de URLs → agregar a `batch-input.tsv`
4. **Para cada URL pendiente**:
   a. Chrome: click en la oferta → leer texto JD del DOM
   b. Guardar JD en `/tmp/batch-jd-{id}.txt`
   c. Calcular próximo REPORT_NUM secuencial
   d. Ejecutar vía Bash
   e. Actualizar `batch-state.tsv`
   f. Loguear en `logs/{report_num}-{id}.log`
   g. Chrome: volver → siguiente oferta
5. **Paginación**: Si no hay más ofertas → click "Siguiente" → repetir
6. **Fin**: Merge `tracker-additions/` → `applications.md` + resumen

## Modo B: Script standalone

```bash
batch/batch-runner.sh [OPCIONES]
```

Opciones:
- `--dry-run` — listar ofertas pendientes sin ejecutar
- `--retry-failed` — reintentar solo ofertas fallidas
- `--start-from N` — empezar desde ID N
- `--parallel N` — N workers en paralelo
- `--max-retries N` — intentos por oferta (default: 2)

## Manejo de errores

| Error | Recuperación |
|-------|-------------|
| URL inaccesible | Worker falla → conductor marca `failed`, continúa |
| JD detrás de login | Conductor intenta leer DOM. Si falla → `failed` |
| Portal cambió layout | Conductor razona sobre HTML, adapta |
| Worker crashea | Conductor marca `failed`, continúa. Reintentar con `--retry-failed` |
| Conductor crashea | Re-ejecutar → lee estado → saltea ofertas completadas |
| PDF falla | Reporte .md se guarda. PDF queda pendiente |
