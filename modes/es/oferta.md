# Modo: oferta — Evaluación Completa A-G

Cuando el candidato pegue una oferta laboral (texto o URL), ENTREGAR SIEMPRE los 7 bloques (evaluación A-F + legitimidad G):

## Paso 0 — Detección de Arquetipo

Clasificar la oferta en uno de los 6 arquetipos (ver `_shared.md`). Si es híbrido, indicar los 2 más cercanos. Esto determina:
- Qué proof points priorizar en el bloque B
- Cómo reescribir el resumen en el bloque E
- Qué historias STAR preparar en el bloque F

## Bloque A — Resumen del Rol

Tabla con:
- Arquetipo detectado
- Dominio (backend/frontend/datos/ML/infra/producto)
- Función (construir/consultar/gestionar/desplegar)
- Seniority
- Remoto (full/híbrido/presencial)
- Tamaño de equipo (si se menciona)
- TL;DR en 1 oración

## Bloque B — Match con CV

Leer `cv.md`. Crear una tabla con cada requisito de la JD mapeado a líneas exactas del CV.

**Adaptado al arquetipo:**
- Si Backend → priorizar APIs, bases de datos, arquitectura, escalabilidad
- Si Frontend → priorizar frameworks, UI/UX, accesibilidad, performance
- Si Data/ML → priorizar pipelines, modelos, métricas, experimentación
- Si DevOps → priorizar CI/CD, infraestructura como código, monitoreo
- Si Producto → priorizar descubrimiento, métricas, roadmap, stakeholders
- Si Liderazgo Técnico → priorizar mentoring, diseño de sistemas, estrategia

**Sección de brechas** con estrategia de mitigación para cada una. Para cada brecha:
1. ¿Es bloqueante o deseable?
2. ¿Puede el candidato demostrar experiencia adyacente?
3. ¿Hay un proyecto del portfolio que cubra esta brecha?
4. Plan concreto de mitigación (frase para cover letter, proyecto rápido, etc.)

## Bloque C — Nivel y Estrategia

1. **Nivel detectado** en la JD vs **nivel natural del candidato para ese arquetipo**
2. **Plan "vender seniority sin mentir"**: frases específicas adaptadas al arquetipo, logros concretos a destacar, cómo posicionar experiencia emprendedora como ventaja
3. **Plan "si me bajan el seniority"**: aceptar si la compensación es justa, negociar revisión a 6 meses, criterios claros de promoción

## Bloque D — Compensación y Demanda

Usar WebSearch para:
- Salarios actuales para el rol (Glassdoor, OpenQube, Love Mondays para Argentina)
- Reputación de compensación de la empresa
- Tendencia de demanda para el rol

Tabla con datos y fuentes citadas. Si no hay datos, declararlo en vez de inventar.

**Para Argentina específicamente:**
- Distinguir entre posiciones en ARS (relación de dependencia) y USD (contractor)
- Considerar aguinaldo/SAC como parte del paquete total
- Buscar datos en OpenQube, Glassdoor, r/empleos_AR, y encuestas de Sysarmy
- Notar bandas salariales por seniority y si son bruto o neto

## Bloque E — Plan de Personalización

| # | Sección | Estado actual | Cambio propuesto | Por qué |
|---|---------|---------------|------------------|---------|
| 1 | Resumen | ... | ... | ... |
| ... | ... | ... | ... | ... |

Top 5 cambios al CV + Top 5 cambios al LinkedIn para maximizar el match.

## Bloque F — Plan de Entrevista

6-10 historias STAR+R mapeadas a requisitos de la JD (STAR + **Reflexión**):

| # | Requisito JD | Historia STAR+R | S | T | A | R | Reflexión |
|---|-------------|-----------------|---|---|---|---|------------|

La columna **Reflexión** captura qué se aprendió o qué se haría diferente. Esto demuestra seniority — los juniors describen lo que pasó, los seniors extraen lecciones.

**Banco de Historias:** Si existe `interview-prep/story-bank.md`, verificar si alguna de estas historias ya está ahí. Si no, agregar las nuevas. Con el tiempo esto construye un banco reutilizable de 5-10 historias maestras que pueden adaptarse a cualquier pregunta de entrevista.

**Seleccionadas y encuadradas según el arquetipo:**
- Backend → enfatizar escalabilidad, decisiones de arquitectura
- Frontend → enfatizar experiencia de usuario, performance
- Data/ML → enfatizar métricas, experimentación, producción
- DevOps → enfatizar automatización, confiabilidad, respuesta a incidentes
- Producto → enfatizar descubrimiento, trade-offs, impacto en negocio
- Liderazgo → enfatizar mentoring, estrategia técnica, gestión de equipos

Incluir también:
- 1 caso de estudio recomendado (cuál de sus proyectos presentar y cómo)
- Preguntas bandera-roja y cómo responderlas (ej: "¿por qué dejaste tu empresa anterior?", "¿tenés experiencia liderando equipos?")

## Bloque G — Legitimidad de la Publicación

Analizar la oferta laboral buscando señales que indiquen si es una oportunidad real y activa. Esto ayuda al candidato a priorizar esfuerzo en oportunidades con más chances de avanzar.

**Encuadre ético:** Presentar observaciones, no acusaciones. Toda señal tiene explicaciones legítimas. El candidato decide cómo ponderarlas.

### Señales a analizar (en orden):

**1. Frescura de la publicación** (del snapshot de Playwright):
- Fecha de publicación o "hace X días" — extraer de la página
- Estado del botón de postular (activo / cerrado / no está / redirige a página genérica)
- Si la URL redirigió a página genérica de carreras, notarlo

**2. Calidad de la descripción** (del texto de la JD):
- ¿Nombra tecnologías, frameworks, herramientas específicas?
- ¿Menciona tamaño del equipo, estructura de reporte o contexto organizacional?
- ¿Los requisitos son realistas? (años de experiencia vs edad de la tecnología)
- ¿Hay un alcance claro para los primeros 6-12 meses?
- ¿Se menciona salario/compensación?
- ¿Qué proporción de la JD es específica del rol vs genérica?
- ¿Hay contradicciones internas? (título junior + requisitos de staff, etc.)

**3. Señales de contratación de la empresa** (2-3 búsquedas WebSearch, combinar con investigación del Bloque D):
- Buscar: `"{empresa}" despidos {año}` — notar fecha, escala, departamentos
- Buscar: `"{empresa}" hiring freeze {año}` — notar anuncios
- Si hay despidos: ¿son en el mismo departamento que este rol?

**4. Detección de republicaciones** (de scan-history.tsv):
- Verificar si empresa + rol similar apareció antes con URL diferente
- Notar cuántas veces y en qué período

**5. Contexto de mercado del rol** (cualitativo, sin consultas adicionales):
- ¿Es un rol común que típicamente se llena en 4-6 semanas?
- ¿Tiene sentido el rol para el negocio de esta empresa?
- ¿El nivel de seniority es uno que legítimamente toma más tiempo en llenarse?

### Formato de salida:

**Evaluación:** Uno de tres niveles:
- **Alta Confianza** — Múltiples señales sugieren una oferta real y activa
- **Proceder con Precaución** — Señales mixtas que vale la pena notar
- **Sospechosa** — Múltiples indicadores de oferta fantasma, investigar antes de invertir tiempo

**Tabla de señales:** Cada señal observada con su hallazgo y peso (Positivo / Neutral / Preocupante).

**Notas de contexto:** Cualquier salvedad (rol de nicho, puesto gubernamental, posición evergreen, etc.) que explique señales potencialmente preocupantes.

### Manejo de casos borde:
- **Publicaciones gubernamentales/académicas:** Plazos más largos son estándar. Ajustar umbrales (60-90 días es normal).
- **Publicaciones evergreen/contratación continua:** Si la JD dice explícitamente "búsqueda permanente" o "rolling", notarlo como contexto — no es oferta fantasma, es rol pipeline.
- **Roles de nicho/ejecutivos:** Staff+, VP, Director o roles altamente especializados legítimamente quedan abiertos por meses. Ajustar umbrales de antigüedad.
- **Startup / pre-revenue:** Empresas en etapa temprana pueden tener JDs vagas porque el rol está genuinamente poco definido. Ponderar menos la vaguedad de descripción.
- **Sin fecha disponible:** Si no se puede determinar la antigüedad y no hay otras señales preocupantes, usar por defecto "Proceder con Precaución" con nota de que hay datos limitados. NUNCA usar "Sospechosa" sin evidencia.
- **Búsqueda por recruiter (sin publicación pública):** Señales de frescura no disponibles. Notar que el contacto activo de un recruiter es en sí mismo una señal positiva de legitimidad.

---

## Post-evaluación

**SIEMPRE** después de generar los bloques A-G:

### 1. Guardar reporte .md

Guardar evaluación completa en `reports/{###}-{empresa-slug}-{YYYY-MM-DD}.md`.

- `{###}` = próximo número secuencial (3 dígitos, con cero a la izquierda)
- `{empresa-slug}` = nombre de empresa en minúsculas, sin espacios (usar guiones)
- `{YYYY-MM-DD}` = fecha actual

**Formato del reporte:**

```markdown
# Evaluación: {Empresa} — {Rol}

**Fecha:** {YYYY-MM-DD}
**URL:**
**Arquetipo:** {detectado}
**Puntaje:** {X/5}
**Legitimidad:** {Alta Confianza | Proceder con Precaución | Sospechosa}
**PDF:** {ruta o pendiente}

---

## A) Resumen del Rol
(contenido completo del bloque A)

## B) Match con CV
(contenido completo del bloque B)

## C) Nivel y Estrategia
(contenido completo del bloque C)

## D) Compensación y Demanda
(contenido completo del bloque D)

## E) Plan de Personalización
(contenido completo del bloque E)

## F) Plan de Entrevista
(contenido completo del bloque F)

## G) Legitimidad de la Publicación
(contenido completo del bloque G)

## H) Borrador de Respuestas
(solo si puntaje >= 4.5 — borrador de respuestas para el formulario de postulación)

---

## Palabras clave extraídas
(lista de 15-20 keywords de la JD para optimización ATS)
```

### 2. Registrar en tracker

**SIEMPRE** registrar en `data/applications.md`:
- Número secuencial
- Fecha actual
- Empresa
- Rol
- Puntaje (1-5)
- Estado: `Evaluada`
- PDF: ❌ (o ✅ si auto-pipeline generó PDF)
- Reporte: link relativo a la raíz `[001](reports/001-empresa-2026-01-01.md)`

**Formato del tracker:**

```markdown
| # | Fecha | Empresa | Rol | Estado | Puntaje | PDF | Reporte |
```
