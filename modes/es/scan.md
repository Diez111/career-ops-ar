# Modo: scan — Escáner de Portales (Descubrimiento de Ofertas)

Escanea portales de empleo configurados, filtra por relevancia de título, y agrega nuevas ofertas al pipeline para evaluación posterior.

## Configuración

Leer `portals.yml` que contiene:
- `search_queries`: Lista de queries WebSearch con filtros `site:` por portal (descubrimiento amplio)
- `tracked_companies`: Empresas específicas con `careers_url` para navegación directa
- `title_filter`: Keywords positive/negative/seniority_boost para filtrado de títulos

## Estrategia de descubrimiento (4 niveles)

### Nivel 0 — Parser local (MÁS BARATO)
Para empresas en `tracked_companies` con `parser:` configurado: ejecutar el parser local. Zero-token.

### Nivel 1 — Playwright directo (PRINCIPAL)
Para cada empresa en `tracked_companies`: navegar a su `careers_url` con Playwright, leer listings visibles, extraer título + URL.

### Nivel 2 — ATS APIs / Feeds (COMPLEMENTARIO)
Para empresas con API pública (Greenhouse, Ashby, Lever, etc.): usar respuesta JSON/XML como complemento.

### Nivel 3 — WebSearch (DESCUBRIMIENTO AMPLIO)
Queries con filtros `site:` para descubrir empresas NUEVAS que no están en `tracked_companies`.

## Portales argentinos específicos

Para el mercado argentino, el escáner prioriza:

**Portales locales (Level 3 WebSearch preferido):**
- `site:linkedin.com/jobs` — búsquedas con ubicación "Argentina"
- `site:zonajobs.com.ar` — portal generalista argentino
- `site:bumeran.com.ar` — portal generalista (del grupo Navent, mismo que ZonaJobs)
- `site:computrabajo.com.ar` — portal muy usado en Argentina
- `site:ar.indeed.com` — Indeed Argentina
- `site:getonbrd.com` — startups tech LATAM (Chile/Argentina/México)
- `site:workana.com` — freelance LATAM

**Empresas argentinas pre-configuradas (tracked_companies):**
- Mercado Libre (más grande empleador tech de LATAM)
- Globant (consultora de software argentina)
- Despegar (travel tech)
- Ualá (fintech)
- Naranja X (fintech)
- PedidosYa (delivery tech, parte de Delivery Hero)
- Auth0 (hoy parte de Okta, fundada en Argentina)
- OLX (classifieds)
- Navent (empleos, parte de QuintoAndar)

## Workflow

1. **Leer configuración**: `portals.yml`
2. **Leer historial**: `data/scan-history.tsv`
3. **Leer dedup**: `data/applications.md` + `data/pipeline.md`
4. **Ejecutar niveles 0-3**
5. **Filtrar por título** usando `title_filter`
6. **Filtrar por ubicación** usando `location_filter` (si existe)
7. **Deduplicar** contra historial y tracker
8. **Agregar a pipeline.md** ofertas nuevas
9. **Registrar en scan-history.tsv**

## Filtro de ubicación para Argentina

Configuración recomendada en `portals.yml`:

```yaml
location_filter:
  always_allow:
    - "Argentina"
    - "Buenos Aires"
    - "CABA"
    - "GBA"
    - "Córdoba"
    - "Rosario"
    - "Mendoza"
  allow:
    - "Remoto"
    - "Argentina"
    - "Buenos Aires"
    - "CABA"
    - "Híbrido"
    - "Latinoamérica"
    - "LATAM"
  block:
    - "Estados Unidos"
    - "United States"
    - "España"
    - "Uruguay"
    - "Chile"
    - "Colombia"
    - "México"
    - "Brasil"
```

## Resumen de salida

```
Portal Scan — {YYYY-MM-DD}
━━━━━━━━━━━━━━━━━━━━━━━━━━
Queries ejecutados: N
Ofertas encontradas: N total
Filtradas por título: N relevantes
Duplicadas: N (ya evaluadas o en pipeline)
Nuevas agregadas a pipeline.md: N

  + {empresa} | {título} | {query_name}
  ...

→ Ejecutá /career-ops pipeline para evaluar las nuevas ofertas.
```
