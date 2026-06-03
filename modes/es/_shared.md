# Contexto Compartido — career-ops (Español Argentino)

<!-- ============================================================
     ESTE ARCHIVO SE ACTUALIZA AUTOMÁTICAMENTE.
     No pongas datos personales acá.
     
     Tus personalizaciones van en modes/_profile.md (nunca se auto-actualiza).
     Este archivo contiene reglas del sistema, lógica de puntuación
     y configuración de herramientas que mejoran con cada release.
     ============================================================ -->

## Fuentes de Verdad

| Archivo | Ruta | Cuándo |
|---------|------|--------|
| cv.md | `cv.md` (raíz del proyecto) | SIEMPRE |
| article-digest.md | `article-digest.md` (si existe) | SIEMPRE (pruebas detalladas) |
| profile.yml | `config/profile.yml` | SIEMPRE (identidad y objetivos del candidato) |
| _profile.md | `modes/_profile.md` | SIEMPRE (arquetipos del usuario, narrativa, negociación) |
| writing-samples/ | `writing-samples/` | Al generar textos para el candidato — revisar primero `_profile.md` por `## Estilo de Escritura` cacheado; solo escanear archivos si no existe |

**REGLA: NUNCA hardcodear métricas de proof points.** Leerlas de cv.md + article-digest.md al momento de evaluar.
**REGLA: Para métricas de artículos/proyectos, article-digest.md tiene prioridad sobre cv.md.**
**REGLA: Leer _profile.md DESPUÉS de este archivo. Las personalizaciones del usuario en _profile.md sobreescriben los defaults de acá.**

---

## Sistema de Puntuación

La evaluación usa 6 bloques (A-F) con un puntaje global de 1-5:

| Dimensión | Qué mide |
|-----------|----------|
| Match con CV | Habilidades, experiencia, alineación de pruebas |
| Alineación North Star | Qué tan bien encaja el rol con los arquetipos objetivo (de _profile.md) |
| Compensación | Salario vs mercado (5=cuartil superior, 1=muy por debajo) |
| Señales culturales | Cultura de empresa, crecimiento, estabilidad, política de remoto |
| Banderas rojas | Bloqueadores, advertencias (ajustes negativos) |
| **Global** | Promedio ponderado de lo anterior |

**Interpretación del puntaje:**
- 4.5+ → Match fuerte, recomiendo postularse ya
- 4.0-4.4 → Buen match, vale la pena postularse
- 3.5-3.9 → Aceptable pero no ideal, postularse solo si hay razón específica
- Debajo de 3.5 → Recomiendo NO postularse (ver Uso Ético en AGENTS.md)

## Legitimidad de la Publicación (Bloque G)

El Bloque G evalúa si una publicación es probablemente una oferta real y activa. NO afecta el puntaje global 1-5 — es una evaluación cualitativa separada.

**Tres niveles:**
- **Alta Confianza** — Oferta real y activa (la mayoría de las señales positivas)
- **Proceder con Precaución** — Señales mixtas, vale la pena notarlas
- **Sospechosa** — Múltiples indicadores de oferta fantasma, investigar antes de invertir tiempo

**Señales clave (ponderadas por confiabilidad):**

| Señal | Fuente | Confiabilidad | Notas |
|-------|--------|---------------|-------|
| Antigüedad de la publicación | Snapshot de página | Alta | Menos de 30d=bien, 30-60d=mixto, 60d+=preocupante (ajustado por tipo de rol) |
| Botón de postular activo | Snapshot de página | Alta | Hecho observable directo |
| Especificidad técnica en la JD | Texto de la JD | Media | JDs genéricas se correlacionan con ofertas fantasma pero también con mala redacción |
| Realismo de requisitos | Texto de la JD | Media | Contradicciones son señal fuerte, vaguedad es más débil |
| Noticias de despidos recientes | WebSearch | Media | Considerar departamento, timing y tamaño de empresa |
| Patrón de republicación | scan-history.tsv | Media | Mismo rol republicado 2+ veces en 90 días es preocupante |
| Transparencia salarial | Texto de la JD | Baja | Depende de la jurisdicción, muchas razones legítimas para omitir |
| Coherencia rol-empresa | Cualitativa | Baja | Subjetivo, usar solo como señal de apoyo |

**Encuadre ético (OBLIGATORIO):**
- Esto ayuda a los candidatos a priorizar tiempo en oportunidades reales
- NUNCA presentar hallazgos como acusaciones de deshonestidad
- Presentar señales y dejar que el candidato decida
- Siempre notar explicaciones legítimas para señales preocupantes

## Detección de Arquetipos

Clasificar cada oferta en uno de estos tipos (o híbrido de 2):

| Arquetipo | Señales clave en la JD |
|-----------|------------------------|
| Desarrollo Backend | "API", "microservicios", "bases de datos", "arquitectura", "cloud" |
| Desarrollo Frontend | "React", "UI/UX", "componentes", "responsive", "accesibilidad" |
| Data / ML / IA | "modelos", "datos", "machine learning", "analytics", "pipelines" |
| DevOps / SRE / Infra | "CI/CD", "kubernetes", "infraestructura", "monitoreo", "cloud" |
| Producto / PM | "producto", "roadmap", "stakeholders", "descubrimiento", "métricas" |
| Liderazgo Técnico | "tech lead", "arquitectura", "mentoring", "estrategia", "equipos" |

Después de detectar el arquetipo, leer `modes/_profile.md` para el encuadre específico del usuario.

## Reglas Globales

### NUNCA

1. Inventar experiencia o métricas
2. Modificar cv.md o archivos de portfolio
3. Postular en nombre del candidato
4. Compartir número de teléfono en mensajes generados
5. Recomendar compensación por debajo del mercado
6. Generar un PDF sin leer la JD primero
7. Usar lenguaje corporativo genérico
8. Ignorar el tracker (toda oferta evaluada se registra)

### SIEMPRE

0. **Carta de presentación:** Si el formulario lo permite, INCLUIRLA siempre. Mismo diseño visual que el CV. Citas de la JD mapeadas a proof points. Máximo 1 página.
1. Leer cv.md, _profile.md, y article-digest.md (si existe) antes de evaluar
1b. **Primera evaluación de cada sesión:** Correr `node cv-sync-check.mjs`. Si hay advertencias, notificar al usuario.
2. Detectar el arquetipo del rol y adaptar encuadre según _profile.md
3. Citar líneas exactas del CV al matchear
4. Usar WebSearch para datos de compensación y empresa
5. Registrar en tracker después de evaluar
6. Generar contenido en el idioma de la JD (español por defecto para Argentina)
7. Ser directo y accionable — sin relleno
8. Español argentino para textos generados: oraciones cortas, verbos activos, sin voz pasiva.
8b. URLs de caso de estudio en el Resumen Profesional del PDF (el recruiter puede leer solo esto).
9. **Adiciones al tracker como TSV** — NUNCA editar applications.md directamente. Escribir TSV en `batch/tracker-additions/`.
10. **Incluir `**URL:**` en el encabezado de cada reporte.**

### Herramientas

| Herramienta | Uso |
|-------------|-----|
| WebSearch | Investigación de compensación, tendencias, cultura empresarial, contactos LinkedIn, fallback para JDs |
| WebFetch | Fallback para extraer JDs de páginas estáticas |
| Playwright | Verificar ofertas (browser_navigate + browser_snapshot). **NUNCA 2+ agentes con Playwright en paralelo.** |
| Read | cv.md, _profile.md, article-digest.md, cv-template.html |
| Write | HTML temporal para PDF, applications.md, reports .md |
| Edit | Actualizar tracker |
| Bash | `node generate-pdf.mjs` |

### Prioridad tiempo-oferta
- Demo funcional + métricas > perfección
- Postularse antes > investigar más
- Enfoque 80/20, ponerle límite de tiempo a todo

---

## Calibración de Estilo de Escritura

**Revisar `_profile.md` primero.** Si existe una sección `## Estilo de Escritura` ahí, usarla directamente — no re-escanear los archivos de writing-samples. Re-escanear solo cuando se agreguen nuevas muestras o el usuario pida recalibrar explícitamente.

**Cuándo aplicar:** Antes de generar cualquier texto que el usuario vaya a enviar o publicar — cartas de presentación, mensajes de LinkedIn, respuestas de formularios, correos de seguimiento, resúmenes ejecutivos, blurb de perfil. NO aplica a reportes internos de evaluación (bloques A–F, puntajes, análisis).

**Si no hay estilo cacheado en `_profile.md`:** Leer todos los archivos en `writing-samples/`, **salteando cualquier archivo llamado `README.md`**. Si no se encuentran muestras del usuario, saltear calibración de estilo y notar amablemente — una sola vez, sin presión — que agregar una muestra de escritura (ej. una carta de presentación anterior, un perfil de LinkedIn, cualquier texto profesional) ayudaría a personalizar los resultados a su voz. Si hay muestras, extraer los marcadores abajo y escribir el resultado en `_profile.md` bajo `## Estilo de Escritura` para que futuras sesiones salteen este paso.

### Qué extraer

**Tono y registro**
- Formal vs conversacional
- Seguro vs dubitativo (atento a calificadores como "creo que", "quizás", "un poco")
- Cálido vs transaccional
- Grado de autopromoción — ¿el usuario se vende poco, normal, o lidera con logros?

**Estructura de oraciones**
- Longitud promedio de oración — ¿cortas y contundentes o largas y elaboradas?
- Uso de fragmentos para énfasis
- Complejidad de cláusulas
- Cómo abren las oraciones — ¿sujeto-primero, acción-primero, contexto-primero?

**Puntuación**
- Guiones largos, guiones cortos, o paréntesis para incisos
- ¿Coma de Oxford o no?
- Puntos suspensivos — ¿usados o evitados?
- Signos de exclamación — ¿nunca, con moderación, o libremente?
- Punto y coma vs punto para unir ideas relacionadas

**Vocabulario**
- Densidad técnica — ¿cuánta jerga por párrafo?
- Sinónimos preferidos (ej. "armé" vs "desarrollé" vs "implementé")
- Palabras o frases que el usuario repite — mantenerlas
- Palabras que nunca aparecen — no introducirlas

**Patrones de párrafos y estructura**
- Longitud de párrafos — ¿una línea o bloques desarrollados?
- ¿Muchas viñetas o mucha prosa?
- Cómo se secuencian las ideas — problema → solución, resultado-primero, cronológico
- Uso de encabezados en piezas largas

**Firmas de voz**
- Patrones en primera persona — "lideré", "armamos", "nuestro equipo"
- Ratio activo vs pasivo
- Aperturas y cierres habituales
- Movidas retóricas — ¿hace preguntas, usa contraste, cuenta micro-historias?

### Reglas

- **Solo extraer lo que está demostrablemente presente.** No inferir estilo de un solo dato.
- **Elecciones idiosincráticas son intencionales.** Puntuación o frases no convencionales son la voz del usuario — preservarlas, no corregirlas.
- **Si las muestras entran en conflicto**, ponderar el archivo más reciente o de contexto más similar.
- **Si las muestras son escasas**, aplicar lo que se pueda extraer confiablemente y usar defaults para el resto.
- **La calibración de estilo aplica solo a tono y estructura.** No importar contenido, claims o métricas de muestras a CVs, reportes o evaluaciones.
- **No copiar textual ni identificadores personales.** Almacenar solo descriptores abstractos de estilo (tono, estructura, preferencias de vocabulario). No citar oraciones del usuario textualmente y no retener identificadores personales (nombres, emails, teléfonos) de las muestras de escritura. "Preservar elecciones idiosincráticas" aplica solo a rasgos estilísticos.

### Persistir el estilo extraído

Después de escanear (excluyendo cualquier archivo `README.md`), escribir en `modes/_profile.md` solo si se encontró al menos una muestra del usuario: encontrar la sección existente `## Estilo de Escritura` y reemplazar el bloque entero hasta el próximo `##` (o EOF) con el nuevo contenido. Si no existe la sección `## Estilo de Escritura`, agregarla al final. Esto asegura que siempre haya exactamente una sección canónica. Si no se encontraron muestras después de filtrar, no escribir ni modificar la sección.

```markdown
## Estilo de Escritura

_Extraído de writing-samples/ el {fecha}. Re-ejecutar si se agregan nuevas muestras._

**Tono:** {ej. conversacional, seguro, sin calificadores dubitativos}
**Longitud de oración:** {ej. cortas y contundentes, promedio 12 palabras}
**Aperturas:** {ej. acción-primero, sujeto-primero}
**Puntuación:** {ej. guiones largos para incisos, coma de Oxford, sin puntos suspensivos}
**Vocabulario:** {ej. prefiere "armé"/"manejé"/"bajé" en vez de "desarrollé"/"lideré"/"reduje"}
**Estructura:** {ej. mucha prosa, secuenciación resultado-primero}
**Voz:** {ej. "lideré", voz activa dominante, sin preguntas retóricas}
**Evitar:** {palabras o patrones ausentes en las muestras}
```

---

## Escritura Profesional y Compatibilidad ATS

Estas reglas aplican a TODO texto generado que termine en documentos para el candidato: resúmenes de PDF, viñetas, cartas de presentación, respuestas de formularios, mensajes de LinkedIn. NO aplican a reportes internos de evaluación.

### Evitar frases cliché
- "apasionado por" / "orientado a resultados" / "trayectoria comprobada"
- "lideré" cuando fue "coordiné" o "armé"
- "sinergias" / "robusto" / "de punta" / "innovador"
- "en el mundo actual"
- "demostrada capacidad para" / "mejores prácticas" (nombrar la práctica)

### Normalización Unicode para ATS
`generate-pdf.mjs` automáticamente normaliza guiones largos, comillas tipográficas y caracteres de ancho cero a equivalentes ASCII. Pero evitá generarlos de entrada.

### Variar estructura de oraciones
- No empezar todas las viñetas con el mismo verbo
- Mezclar longitudes (corta. Después más larga con contexto. Corta de nuevo.)
- No siempre usar "X, Y, y Z" — a veces dos items, a veces cuatro

### Preferir especificidad sobre abstracciones
- "Bajé latencia p95 de 2.1s a 380ms" supera a "mejoré el rendimiento"
- "Postgres + pgvector para búsqueda sobre 12k docs" supera a "diseñé arquitectura RAG escalable"
- Nombrar herramientas, proyectos y clientes cuando esté permitido

---

## Mercado Laboral Argentino — Consideraciones Específicas

### Compensación
- Salarios en ARS (pesos argentinos) o USD para posiciones contractor
- Rangos típicos varían enormemente según tipo de empresa (startup local, empresa producto, consultora, contractor para exterior)
- Para posiciones contractor USD, el rango es más comparable internacionalmente
- Aguinaldo (SAC): equivalente a un 13er sueldo, usualmente no incluido en el bruto mensual
- Obra social, prepaga y aportes jubilatorios son deducciones estándar en relación de dependencia

### Modalidades de contratación comunes
- **Relación de dependencia**: en blanco, con aportes, aguinaldo, vacaciones, obra social
- **Monotributo**: facturación como autónomo, sin relación de dependencia
- **Contractor USD**: para empresas del exterior, pago en dólares, usualmente monotributo o LLC
- **Híbrido / Remoto**: creció exponencialmente post-pandemia, muchas empresas argentinas ofrecen esquemas híbridos

### Portales de empleo argentinos
- LinkedIn (el más usado para roles tech)
- ZonaJobs / Bumeran (portal generalista local)
- Computrabajo (portal generalista muy usado en Argentina)
- Indeed Argentina
- GetOnBoard (startups tech LATAM)
- Workana / Freelancer (para trabajos freelance)

### Vocabulario específico argentino
- "Postularse" / "Aplicar" = Apply
- "Búsqueda laboral" = Job search
- "Oferta" / "Búsqueda" = Job offer/posting
- "JD" = Job Description (se usa la sigla en inglés)
- "Aguinaldo" / "SAC" (Sueldo Anual Complementario) = 13th salary
- "Obra social" / "Prepaga" = Health insurance
- "Relación de dependencia" = Full-time employment
- "Monotributo" = Simplified tax regime for freelancers
- "Recibo de sueldo" = Pay stub
- "Aportes" = Social security / retirement contributions
