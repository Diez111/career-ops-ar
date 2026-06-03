# Modo: pdf — Generación de PDF Optimizado para ATS

## Pipeline completo

1. Leer `cv.md` como fuente de verdad
2. Preguntar al usuario por la JD si no está en contexto (texto o URL)
3. Extraer 15-20 keywords de la JD
4. Detectar idioma de la JD → idioma del CV (español por defecto)
5. Detectar ubicación de la empresa → formato de papel:
   - Argentina/LATAM → `a4`
6. Detectar arquetipo del rol → adaptar encuadre
7. Reescribir Resumen Profesional inyectando keywords de la JD + puente narrativo ("Armé y escalé sistemas en producción. Ahora aplico pensamiento de sistemas a [dominio JD].")
8. Seleccionar top 3-4 proyectos más relevantes para la oferta
9. Reordenar bullets de experiencia por relevancia a la JD
10. Construir grilla de competencias desde requisitos de la JD (6-8 frases clave)
11. Inyectar keywords naturalmente en logros existentes (NUNCA inventar)
12. Generar HTML completo desde template + contenido personalizado
13. Leer `name` de `config/profile.yml` → normalizar a kebab-case minúsculas (ej. "Juan Perez" → "juan-perez") → `{candidato}`
14. Escribir HTML a `/tmp/cv-{candidato}-{empresa}.html`
15. Ejecutar: `node generate-pdf.mjs /tmp/cv-{candidato}-{empresa}.html output/cv-{candidato}-{empresa}-{YYYY-MM-DD}.pdf --format=a4`
16. Reportar: ruta del PDF, cantidad de páginas, % de cobertura de keywords

## Reglas ATS (parseo limpio)

- Layout de una sola columna (sin sidebars, sin columnas paralelas)
- Encabezados estándar: "Resumen Profesional", "Experiencia Laboral", "Educación", "Habilidades", "Certificaciones", "Proyectos"
- Sin texto en imágenes/SVGs
- Sin información crítica en headers/footers del PDF (ATS los ignora)
- UTF-8, texto seleccionable (no rasterizado)
- Sin tablas anidadas
- Keywords de JD distribuidas: Resumen (top 5), primer bullet de cada rol, sección de Habilidades

## Diseño del PDF

- **Tipografías**: Space Grotesk (títulos, 600-700) + DM Sans (cuerpo, 400-500)
- **Tipografías self-hosted**: `fonts/`
- **Encabezado**: nombre en Space Grotesk 24px bold + línea con gradiente `linear-gradient(to right, hsl(187,74%,32%), hsl(270,70%,45%))` 2px + fila de contacto
- **Títulos de sección**: Space Grotesk 13px, mayúsculas, letter-spacing 0.05em, color cyan primario
- **Cuerpo**: DM Sans 11px, line-height 1.5
- **Nombres de empresa**: color acento violeta `hsl(270,70%,45%)`
- **Márgenes**: 0.6in
- **Fondo**: blanco puro

## Orden de secciones (optimizado para "escaneo de 6 segundos del recruiter")

1. Encabezado (nombre grande, gradiente, contacto, link portfolio)
2. Resumen Profesional (3-4 líneas, denso en keywords)
3. Competencias Principales (6-8 frases clave en flex-grid)
4. Experiencia Laboral (orden cronológico inverso)
5. Proyectos (top 3-4 más relevantes)
6. Educación y Certificaciones
7. Habilidades (lenguajes + técnico)

## Estrategia de inyección de keywords (ética, basada en verdad)

Ejemplos de reformulación legítima:
- JD dice "microservicios" y CV dice "APIs REST con arquitectura distribuida" → cambiar a "Microservicios y APIs REST con arquitectura distribuida"
- JD dice "CI/CD" y CV dice "automatización de deploys" → cambiar a "CI/CD y automatización de despliegues"
- JD dice "manejo de stakeholders" y CV dice "coordinación con equipos" → cambiar a "Manejo de stakeholders entre ingeniería, operaciones y negocio"

**NUNCA agregar habilidades que el candidato no tiene. Solo reformular experiencia real usando el vocabulario exacto de la JD.**

## Template HTML

Usar el template en `cv-template.html`. Reemplazar los placeholders `{{...}}` con contenido personalizado.

## Post-generación

Actualizar tracker si la oferta ya está registrada: cambiar PDF de ❌ a ✅.
