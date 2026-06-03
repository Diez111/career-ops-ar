# Modo: tracker — Seguimiento de Postulaciones

Leer y mostrar `data/applications.md`.

**Formato del tracker:**
```markdown
| # | Fecha | Empresa | Rol | Estado | Puntaje | PDF | Reporte |
```

Estados posibles: `Evaluada` → `Postulada` → `Respondida` → `Contactada` → `Entrevista` → `Oferta` / `Rechazada` / `Descartada` / `NO APLICAR`

- `Postulada` = el candidato envió su postulación
- `Respondida` = Un recruiter/empresa contactó y el candidato respondió (inbound)
- `Contactada` = El candidato contactó proactivamente a alguien de la empresa (outbound, ej: LinkedIn power move)

Si el usuario pide actualizar un estado, editar la fila correspondiente.

Mostrar también estadísticas:
- Total de postulaciones
- Por estado
- Puntaje promedio
- % con PDF generado
- % con reporte generado

## Métricas de Pipeline

Al mostrar el tracker, incluir un resumen con:
- **Pipeline activo**: cuántas ofertas en Evaluada + Postulada + Respondida + Contactada
- **Tasa de conversión**: Postulada → Respondida → Entrevista → Oferta
- **Tiempo promedio** entre Postulada y Respondida
- **Puntaje promedio** de ofertas que llegaron a Entrevista vs las que no

## Acciones rápidas

Ofrecer al usuario:
- "¿Querés que evalúe las pendientes en pipeline.md? → `/career-ops pipeline`"
- "¿Querés hacer seguimiento de postulaciones activas? → `/career-ops followup`"
- "¿Querés analizar patrones de rechazo? → `/career-ops patterns`"
