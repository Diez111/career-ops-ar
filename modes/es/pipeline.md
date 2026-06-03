# Modo: pipeline — Bandeja de URLs (Segundo Cerebro)

Procesar URLs de ofertas almacenadas en `data/pipeline.md`. El usuario agrega URLs en cualquier momento y después ejecuta `/career-ops pipeline` para procesarlas todas.

## Workflow

1. **Leer** `data/pipeline.md` → buscar items `- [ ]` en la sección "Pendientes"
2. **Para cada URL pendiente**:
   a. Calcular el próximo `REPORT_NUM` secuencial
   b. **Extraer JD** usando Playwright → WebFetch → WebSearch
   c. Si la URL no es accesible → marcar como `- [!]` con nota y continuar
   d. **Ejecutar auto-pipeline completo**: Evaluación A-F → Reporte .md → PDF (si puntaje >= `auto_pdf_score_threshold`) → Tracker
   e. **Mover de "Pendientes" a "Procesadas"**: `- [x] #NNN | URL | Empresa | Rol | Puntaje/5 | PDF ✅/❌`

   **Sobre el filtro de PDF (configurable):** Leer `config/profile.yml` → `auto_pdf_score_threshold`. Si no existe la clave, usar 3.0 por defecto. Si el puntaje es menor al umbral, saltear generación de PDF: escribir el reporte normalmente, mostrar en el encabezado `**PDF:** no generado — ejecutar /career-ops pdf {empresa-slug} para crear a demanda`, y marcar PDF ❌ en el tracker.

3. **Si hay 3+ URLs pendientes**, lanzar agentes en paralelo (Agent tool con `run_in_background`) para maximizar velocidad.
4. **Al final**, mostrar tabla resumen:

```
| # | Empresa | Rol | Puntaje | PDF | Acción recomendada |
```

## Formato de pipeline.md

```markdown
## Pendientes
- [ ] https://empleos.ejemplo.com/posting/123
- [ ] https://boards.greenhouse.io/empresa/jobs/456 | Empresa SA | Senior Dev
- [!] https://url.privada/trabajo — Error: requiere login

## Procesadas
- [x] #143 | https://empleos.ejemplo.com/posting/789 | Acme Corp | Desarrollador | 4.2/5 | PDF ✅
- [x] #144 | https://boards.greenhouse.io/xyz/jobs/012 | BigCo | Arquitecto | 2.1/5 | PDF ❌
```

## Detección inteligente de JD desde URL

1. **Playwright (preferido):** `browser_navigate` + `browser_snapshot`. Funciona con todas las SPAs.
2. **WebFetch (fallback):** Para páginas estáticas o cuando Playwright no está disponible.
3. **WebSearch (último recurso):** Buscar en portales secundarios que indexen la JD.

**Casos especiales:**
- **LinkedIn**: Puede requerir login → marcar `[!]` y pedir al usuario que pegue el texto
- **PDF**: Si la URL apunta a un PDF, leerlo directamente con Read
- **`local:`**: Leer archivo local. Ej: `local:jds/puesto.md` → leer `jds/puesto.md`

## Numeración automática

1. Listar todos los archivos en `reports/`
2. Extraer el número del prefijo (ej. `142-empresa...` → 142)
3. Nuevo número = máximo encontrado + 1

## Sincronización de fuentes

Antes de procesar cualquier URL, verificar sync:
```bash
node cv-sync-check.mjs
```
Si hay desincronización, advertir al usuario antes de continuar.
