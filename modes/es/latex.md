# Modo: latex — Exportar CV a LaTeX/Overleaf

Exportar un CV personalizado y optimizado para ATS como archivo `.tex` y compilarlo a PDF vía `tectonic` o `pdflatex`.

## Pipeline

1. Leer `cv.md` como fuente de verdad
2. Leer `config/profile.yml` para identidad y contacto del candidato
3. Preguntar al usuario por la JD si no está en contexto (texto o URL)
4. Extraer 15-20 keywords de la JD
5. Detectar idioma de la JD → idioma del CV (español por defecto)
6. Detectar arquetipo del rol → adaptar encuadre
7. Reescribir Resumen Profesional inyectando keywords de la JD (mismas reglas que modo `pdf` — NUNCA inventar skills)
8. Seleccionar top 3-4 proyectos más relevantes para la oferta
9. Reordenar bullets de experiencia por relevancia a la JD
10. Inyectar keywords naturalmente en logros existentes
11. Generar el archivo `.tex` usando `templates/cv-template.tex`
12. Escribir en `output/cv-{candidato}-{empresa}-{YYYY-MM-DD}.tex`
13. Ejecutar: `node generate-latex.mjs output/cv-{candidato}-{empresa}-{YYYY-MM-DD}.tex output/cv-{candidato}-{empresa}-{YYYY-MM-DD}.pdf`
14. Reportar: ruta .tex, ruta .pdf, tamaño de archivos, cantidad de secciones, % de cobertura de keywords

**Requiere:** `tectonic` (preferido) o `pdflatex` (MiKTeX / TeX Live) en el PATH.

## Placeholders del Template

El template en `templates/cv-template.tex` usa sintaxis `{{PLACEHOLDER}}`.

## Generación de Contenido LaTeX

Cada entrada de Educación, Experiencia, Proyectos y Habilidades se convierte en los comandos LaTeX correspondientes siguiendo las mismas reglas de contenido que el modo PDF.

## Escape de LaTeX (CRÍTICO)

Todo contenido de texto DEBE ser escapado para LaTeX antes de insertar:

| Carácter | Escape |
|----------|--------|
| `&` | `\&` |
| `%` | `\%` |
| `$` | `\$` |
| `#` | `\#` |
| `_` | `\_` |
| `{` | `\{` |
| `}` | `\}` |
| `~` | `\textasciitilde{}` |
| `^` | `\textasciicircum{}` |
| `\` | `\textbackslash{}` |

**Excepción:** NO escapar los comandos LaTeX en sí — solo texto suministrado por el usuario.
**Excepción para URLs:** NO escapar texto dentro del primer argumento de `\href{URL}{...}`.

## Compatibilidad con Overleaf

El `.tex` generado usa solo paquetes CTAN estándar. Subir el archivo directamente a Overleaf — compila sin configuración extra.
