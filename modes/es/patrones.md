# Modo: patrones — Detector de Patrones de Rechazo

## Propósito

Analizar todas las postulaciones registradas para encontrar patrones en los resultados y generar insights accionables. Identifica qué funciona (arquetipos, políticas de remoto, rangos de puntaje) y qué hace perder tiempo (roles con restricción geográfica, mismatches de stack, postulaciones de bajo puntaje).

## Inputs

- `data/applications.md` — Tracker de postulaciones
- `reports/` — Reportes de evaluación individuales
- `config/profile.yml` — Perfil del usuario
- `modes/_profile.md` — Arquetipos y encuadre del usuario
- `portals.yml` — Configuración de portales

## Umbral mínimo

Antes de ejecutar el análisis, verificar: ¿`data/applications.md` tiene al menos 5 entradas con estado más allá de "Evaluada"?

Si no, decir al usuario:
> "Todavía no hay suficientes datos — {N}/5 postulaciones avanzaron más allá de la evaluación. Seguí postulándote y volvé cuando tengas más resultados para analizar."

## Paso 1 — Ejecutar Script de Análisis

```bash
node analyze-patterns.mjs
```

## Paso 2 — Generar Reporte

Escribir el reporte en `reports/analisis-patrones-{YYYY-MM-DD}.md`.

### Estructura del Reporte

```markdown
# Análisis de Patrones — {YYYY-MM-DD}

**Postulaciones analizadas:** {total}
**Rango de fechas:** {desde} a {hasta}
**Resultados:** {positivos} positivos, {negativos} negativos, {auto-filtradas} auto-filtradas, {pendientes} pendientes

---

## Embudo de Conversión
(cada etapa con conteo y porcentaje)

## Puntaje vs Resultado
(puntaje promedio por grupo de resultado)

## Rendimiento por Arquetipo
(arquetipo, total, positivos, tasa de conversión)

## Principales Bloqueadores
(tabla de frecuencia de bloqueadores recurrentes)

## Patrones de Política Remota
(tasa de conversión por política de ubicación)

## Brechas de Stack Tecnológico
(habilidades faltantes más comunes en resultados negativos)

## Umbral de Puntaje Recomendado
(umbral mínimo basado en datos y justificación)

## Recomendaciones
(top recomendaciones accionables)
```

## Paso 3 — Presentar Resumen

Mostrar al usuario versión condensada:
1. Resumen de una línea
2. Top 3 hallazgos
3. Link al reporte completo

## Paso 4 — Ofrecer Aplicar Recomendaciones

> "¿Querés que aplique alguna de estas recomendaciones? Puedo:
> - Actualizar `portals.yml` para filtrar roles con restricción geográfica
> - Configurar umbral de puntaje en `_profile.md`
> - Ajustar arquetipos objetivo según lo que está convirtiendo
>
> Decime cuáles, o 'todas' para aplicar todo."

## Clasificación de Resultados

| Estado | Resultado |
|--------|-----------|
| Entrevista, Oferta, Respondida, Postulada | **Positivo** |
| Rechazada, Descartada | **Negativo** |
| NO APLICAR | **Auto-filtrada** |
| Evaluada | **Pendiente** |
