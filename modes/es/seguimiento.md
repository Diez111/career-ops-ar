# Modo: seguimiento — Seguimiento de Postulaciones Activas

## Propósito

Hacer seguimiento de postulaciones activas. Marcar seguimientos vencidos, extraer contactos de notas y generar borradores de email/LinkedIn personalizados usando el contexto del reporte.

## Inputs

- `data/applications.md` — Tracker de postulaciones
- `data/follow-ups.md` — Historial de seguimientos (creado en primer uso)
- `reports/` — Reportes de evaluación (contexto para borradores)
- `config/profile.yml` — Perfil del usuario
- `cv.md` — CV para proof points en borradores

## Paso 1 — Ejecutar Script de Cadencia

```bash
node followup-cadence.mjs
```

Si no hay entradas accionables:
> "No hay postulaciones activas para hacer seguimiento. Postulate a algunos roles primero con `/career-ops` y volvé cuando estén madurando."

## Paso 2 — Mostrar Dashboard

```
Panel de Seguimiento — {fecha}
{N} postulaciones en seguimiento, {N} accionables

| # | Empresa | Rol | Estado | Días | Seguimientos | Próximo | Urgencia | Contacto |
```

Indicadores visuales:
- **URGENTE** — responder dentro de 24hs (la empresa respondió)
- **VENCIDO** — seguimiento atrasado
- **esperando (X días)** — en fecha, seguimiento programado
- **FRÍO** — 2+ seguimientos enviados, sugerir cerrar

## Paso 3 — Generar Borradores

Para cada entrada **vencida** o **urgente**:

1. Leer reporte vinculado
2. Leer `cv.md` para proof points
3. Leer `config/profile.yml` para identidad del candidato

### Framework de Email (primer seguimiento)

Generar email de 3-4 oraciones:

1. **Oración 1:** Referenciar el rol específico + cuándo postulaste
2. **Oración 2:** Un valor agregado concreto del match del reporte o proof point
3. **Oración 3:** Pedido suave + disponibilidad
4. **Oración 4 (opcional):** Mención breve de proyecto o logro reciente

**Reglas:**
- Profesional pero cálido, NADA desesperado
- **NUNCA** usar "solo consultaba", "solo haciendo seguimiento", "tocando base"
- Liderar con valor, no con el pedido
- Referenciar algo específico de ESA empresa
- Menos de 150 palabras
- Incluir asunto
- Usar el nombre del candidato de `config/profile.yml`

### LinkedIn (si no hay email)

Reusar framework de contacto: 3 oraciones, máximo 300 caracteres.

### Segundo seguimiento

Más corto (2-3 oraciones). Tomar un **ángulo nuevo**:
- Compartir un insight, artículo o actualización de proyecto relevante
- No repetir el contenido del primer seguimiento

### Postulación Fría (2+ seguimientos)

NO generar otro seguimiento. En su lugar sugerir:
> "Esta postulación tuvo {N} seguimientos sin respuesta. Considerá:
> - Actualizar estado a `Descartada` si el rol parece cubierto
> - Intentar otro contacto vía `/career-ops contactar`
> - Mantener en `Postulada` pero bajar prioridad"

## Paso 4 — Registrar Seguimientos

Después de que el usuario revise y confirme que envió un seguimiento:

1. Si `data/follow-ups.md` no existe, crearlo
2. Agregar fila con número secuencial, App#, fecha, empresa, rol, canal, contacto, notas
3. Opcionalmente actualizar columna Notas en `data/applications.md`

**IMPORTANTE:** Solo registrar seguimientos que el usuario confirma que efectivamente envió.

## Reglas de Cadencia

| Estado | Primer seguimiento | Siguientes | Máx intentos |
|--------|-------------------|------------|-------------|
| Postulada | 7 días después de postular | Cada 7 días | 2 (después marcar frío) |
| Respondida | 1 día (respuesta urgente) | Cada 3 días | Sin límite |
| Entrevista | 1 día después (agradecimiento) | Cada 3 días | Sin límite |

Estos defaults se pueden sobreescribir vía `node followup-cadence.mjs --applied-days N`.
