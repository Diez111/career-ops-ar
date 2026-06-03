# Modos en Español Argentino

Esta carpeta contiene los modos de career-ops completamente traducidos y adaptados al español argentino, optimizados para el mercado laboral de Argentina.

## Modos disponibles

| Modo | Archivo | Comando | Descripción |
|------|---------|---------|-------------|
| Contexto compartido | `_shared.md` | — | Sistema de puntuación, reglas globales, vocabulario argentino |
| Evaluación de oferta | `oferta.md` | `/career-ops oferta` | Evaluación completa A-G con puntuación |
| Auto-pipeline | `auto-pipeline.md` | (pegar JD/URL) | Pipeline automático completo |
| Escáner de portales | `scan.md` | `/career-ops scan` | Descubrimiento de ofertas en portales |
| Generación PDF | `pdf.md` | `/career-ops pdf` | CV ATS-optimizado en PDF |
| Pipeline de URLs | `pipeline.md` | `/career-ops pipeline` | Procesar URLs pendientes |
| Procesamiento masivo | `lote.md` | `/career-ops lote` | Procesar ofertas en batch |
| Comparación de ofertas | `comparar.md` | `/career-ops comparar` | Comparar múltiples ofertas |
| Tracker | `tracker.md` | `/career-ops tracker` | Seguimiento de postulaciones |
| Asistente de postulación | `postular.md` | `/career-ops postular` | Completar formularios |
| Contacto LinkedIn | `contactar.md` | `/career-ops contactar` | Mensajes de outreach |
| Investigación de empresa | `investigar.md` | `/career-ops investigar` | Investigación profunda |
| Preparación entrevista | `entrevista.md` | `/career-ops entrevista` | Preparación por empresa |
| Evaluación de curso | `entrenar.md` | `/career-ops entrenar` | Evaluar curso/cert |
| Evaluación de proyecto | `proyecto.md` | `/career-ops proyecto` | Evaluar proyecto portfolio |
| Análisis de patrones | `patrones.md` | `/career-ops patrones` | Detectar patrones de rechazo |
| Seguimiento de postulaciones | `seguimiento.md` | `/career-ops seguimiento` | Seguimiento y cadencia |
| Exportar LaTeX | `latex.md` | `/career-ops latex` | Exportar CV a LaTeX/Overleaf |

## Uso

Para usar los modos en español argentino, configurar en `config/profile.yml`:

```yaml
language:
  modes_dir: "modes/es"
```

O simplemente decirle al agente: "usá los modos en español" o "cambiá a modos argentinos".

## Adaptaciones para Argentina

- Arquetipos adaptados al mercado tech argentino (Backend, Frontend, Data/ML, DevOps, Producto, Liderazgo)
- Vocabulario específico argentino (postularse, búsqueda laboral, aguinaldo, monotributo, etc.)
- Soportes para tipos de contratación local (relación de dependencia, monotributo, contractor USD)
- Portales de empleo argentinos pre-configurados
- Rangos salariales en ARS y USD
- Filtros geográficos para Argentina y LATAM
