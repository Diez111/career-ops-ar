# Modo: auto-pipeline — Pipeline Automático Completo

Cuando el usuario pegue una JD (texto o URL) sin un subcomando explícito, ejecutar el pipeline ENTERO en secuencia:

## Paso 0 — Extraer JD

Si lo ingresado es una **URL** (no texto de JD pegado), seguir esta estrategia para extraer el contenido:

**Orden de prioridad:**

1. **Playwright (preferido):** La mayoría de los portales de empleo (Lever, Ashby, Greenhouse, Workday) son SPAs. Usar `browser_navigate` + `browser_snapshot` para renderizar y leer la JD.
2. **WebFetch (fallback):** Para páginas estáticas (ZonaJobs, Computrabajo, páginas de carrera de empresas).
3. **WebSearch (último recurso):** Buscar el título del rol + empresa en portales secundarios que indexen la JD en HTML estático.

**Si ningún método funciona:** Pedir al candidato que pegue la JD manualmente o comparta una captura.

**Si lo ingresado es texto de JD** (no URL): usar directamente, sin necesidad de fetch.

## Paso 1 — Evaluación A-G

Ejecutar igual que el modo `oferta` (leer `modes/oferta.md` para todos los bloques A-F + Bloque G Legitimidad).

## Paso 2 — Guardar Reporte .md

Guardar la evaluación completa en `reports/{###}-{empresa-slug}-{YYYY-MM-DD}.md` (ver formato en `modes/oferta.md`).
Incluir Bloque G en el reporte guardado. Agregar **URL:** {url} y **Legitimidad:** {nivel} en el encabezado.

## Paso 3 — Generar PDF

Leer `config/profile.yml`. Verificar `cv.output_format`:

- Si `"latex"`, ejecutar el pipeline completo de `modes/latex.md`
- Sino (default), ejecutar el pipeline completo de `modes/pdf.md`

## Paso 4 — Borrador de Respuestas (solo si puntaje >= 4.5)

Si el puntaje final es >= 4.5, generar un borrador de respuestas para el formulario de postulación:

1. **Extraer preguntas del formulario**: Usar Playwright para navegar al formulario y tomar snapshot. Si no se pueden extraer, usar las preguntas genéricas.
2. **Generar respuestas** siguiendo el tono (ver abajo).
3. **Guardar en el reporte** como sección `## H) Borrador de Respuestas`.

### Preguntas genéricas (usar si no se pueden extraer del formulario)

- ¿Por qué te interesa este rol?
- ¿Por qué querés trabajar en [Empresa]?
- Contanos sobre un proyecto o logro relevante
- ¿Qué te hace un buen fit para esta posición?
- ¿Cómo te enteraste de este rol?

### Tono para Respuestas del Formulario

**Posicionamiento: "Te estoy eligiendo."** El candidato tiene opciones y está eligiendo esta empresa por razones específicas.

**Reglas de tono:**
- **Seguro sin arrogancia**: "Pasé el último año armando sistemas de IA en producción — tu rol es donde quiero aplicar esa experiencia"
- **Selectivo sin arrogancia**: "Vengo buscando intencionalmente un equipo donde pueda contribuir de manera significativa desde el día uno"
- **Específico y concreto**: Siempre referenciar algo REAL de la JD o de la empresa, y algo REAL de la experiencia del candidato
- **Directo, sin relleno**: 2-4 oraciones por respuesta. Nada de "Me apasiona..." o "Me encantaría la oportunidad de..."
- **El gancho es la prueba, no la declaración**: En vez de "Soy buenísimo en X", decir "Armé X que logra Y"

**Framework por pregunta:**
- **¿Por qué este rol?** → "Tu [cosa específica] mapea directo a [cosa específica que armé]."
- **¿Por qué esta empresa?** → Mencionar algo específico sobre la empresa. "Vengo usando [producto] para [tiempo/propósito]."
- **¿Experiencia relevante?** → Un proof point cuantificado. "Armé [X] que [métrica]."
- **¿Buen fit?** → "Estoy en la intersección de [A] y [B], que es justo donde vive este rol."
- **¿Cómo te enteraste?** → Honesto: "Lo encontré por [portal/scan], lo evalué contra mis criterios y fue el que más puntuó."

**Idioma**: Siempre en el idioma de la JD (español por defecto para Argentina).

## Paso 5 — Actualizar Tracker

Registrar en `data/applications.md` con todas las columnas incluyendo Reporte y PDF como ✅.

**Si algún paso falla**, continuar con los siguientes y marcar el paso fallido como pendiente en el tracker.
