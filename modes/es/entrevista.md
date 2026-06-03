# Modo: entrevista — Preparación de Entrevista por Empresa

Cuando el usuario pide prepararse para una entrevista en una empresa+rol específicos, o cuando una evaluación puntúa 4.0+ y el usuario actualiza el estado a `Entrevista`, ejecutar este modo.

## Inputs

1. **Nombre de empresa** y **título del rol** (requerido)
2. **Reporte de evaluación** en `reports/` (si existe)
3. **Banco de historias** en `interview-prep/story-bank.md`
4. **CV** en `cv.md` + `article-digest.md`
5. **Perfil** en `config/profile.yml` + `modes/_profile.md`

## Paso 1 — Investigación

Ejecutar estas búsquedas WebSearch. Extraer datos estructurados, no resúmenes. Citar fuentes.

**Para recruiter / HR screen** (filtro inicial: fit, compensación, logística):

| Query | Qué extraer |
|-------|-------------|
| `"{empresa} {rol} salario" site:openqube.io` y `"{empresa} {rol} sueldo"` | Rangos de compensación por nivel |
| `"{empresa} entrevistas site:glassdoor.com"` | Proceso, timeline, preguntas comunes |
| `"{empresa} cultura site:openqube.io"` | Cultura, beneficios, work-life balance |

**Para hiring manager / liderazgo** (motivación, scope, team fit):

| Query | Qué extraer |
|-------|-------------|
| `"{empresa} blog ingeniería"` y `"{empresa} tech"` | Trabajo reciente del equipo, prioridades técnicas |
| `"{empresa}" noticias OR lanzamiento OR ronda` (últimos 12 meses) | Hitos recientes, apuestas públicas, motores de contratación |

**Para pares / panel técnico** (profundidad, colaboración):

| Query | Qué extraer |
|-------|-------------|
| `"{empresa} {rol} preguntas entrevista"` | Preguntas reales, dificultad, experiencia |
| `"{empresa} entrevista técnica site:glassdoor.com"` | Problemas de código, system design, estructura de rounds |

## Paso 2 — Vista General del Proceso

```markdown
## Vista General del Proceso
- **Rounds:** {N} rounds, ~{X} días total
- **Formato:** {ej: recruiter screen → técnica → entrevista con manager}
- **Dificultad:** {X}/5 (promedio Glassdoor)
- **Tasa de experiencia positiva:** {X}%
- **Particularidades conocidas:** {ej: "nada de LeetCode, todo práctico"}
- **Fuentes:** {links}
```

## Paso 3 — Preguntas Probables

Agrupar todas las preguntas descubiertas e inferidas por audiencia. Dentro de cada audiencia, redactar respuestas específicas para el candidato usando `cv.md`, `article-digest.md`, `config/profile.yml` y `modes/_profile.md`.

### Audiencia: `recruiter-screen`

- **"Contame de vos / por qué estás buscando"** — narrativa de 60-90 segundos anclada en `modes/_profile.md`
- **Expectativa salarial** — rango concreto basado en investigación del Paso 1
- **Por qué esta empresa** — 2-3 oraciones referenciando señales públicas
- **Ubicación / remoto / relocación** — respuesta basada en `config/profile.yml`
- **Disponibilidad / preaviso** — números, no sensaciones
- **Otros procesos en curso** — encuadre recomendado solamente

### Audiencia: `hiring-manager`

- **"Por qué este rol, por qué ahora"** — conectar últimos 1-2 roles con desafío del equipo
- **"¿Cómo serían tus primeros 90 días?"** — basado en scope de la JD
- **Preguntas para hacerles** — 2-3 atadas a algo específico que el equipo haya hecho o escrito

### Audiencia: `peer-tech`

- Preguntas técnicas (system design, código, arquitectura, dominio)
- Preguntas específicas del rol atadas al arquetipo de la JD
- Preguntas para hacerles — sobre guardias, code review, deploys, qué les sorprendió al entrar

## Paso 4 — Banco de Historias

Mapear historias existentes del story-bank a las preguntas probables:

| # | Audiencia | Pregunta probable | Mejor historia | Fit | ¿Falta? |
|---|----------|-------------------|----------------|-----|---------|
| 1 | recruiter-screen | ... | [Título] | fuerte/parcial/ninguno | |
| 2 | hiring-manager | ... | [Título] | fuerte/parcial/ninguno | |

Para cada brecha: "Necesitás una historia sobre {tema}. Considerá: {experiencia específica de cv.md}."

## Paso 5 — Checklist de Preparación Técnica

Basado en lo que la empresa realmente evalúa:
- [ ] {tema} — por qué: "{evidencia de la investigación}"
- Priorizar por frecuencia y relevancia. Máx 10 items.

## Paso 6 — Señales de Empresa

Cosas que decir, hacer y evitar — segmentadas por quién escucha.

## Salida

Guardar el reporte completo en `interview-prep/{empresa-slug}-{rol-slug}.md`.

**Reglas:**
- NUNCA inventar preguntas de entrevista y atribuirlas a fuentes
- NUNCA fabricar estadísticas de Glassdoor
- Citar todo — cada pregunta, cada stat, cada afirmación
- Ser directo — esto es un documento de trabajo, no una charla motivacional
- Generar en español argentino
