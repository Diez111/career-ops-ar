# Career-Ops AR 🇦🇷

<p align="center">
  <em>Meses mandando CVs al vacío. Así que me armé el sistema que necesitaba.</em><br>
  Las empresas usan IA para filtrarte. <strong>Yo le di a los candidatos IA para <em>elegir empresas</em>.</strong><br>
  <em>Ahora es open source — y 100% en español argentino.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-000?style=flat&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white" alt="Go">
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white" alt="Playwright">
  <img src="https://img.shields.io/badge/Licencia-MIT-blue.svg" alt="MIT">
  <img src="https://img.shields.io/badge/Argentina-75AADB?style=flat&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAwIDU2MDAiPjxnIGZpbGw9IiNmZmYiPjxyZWN0IHdpZHRoPSI5MDAwIiBoZWlnaHQ9IjE2MDAiLz48cmVjdCB5PSIyMDAwIiB3aWR0aD0iOTAwMCIgaGVpZ2h0PSIxNjAwIi8+PC9nPjxyZWN0IHdpZHRoPSI5MDAwIiBoZWlnaHQ9IjU2MDAiIGZpbGw9IiM3NUFBREIiLz48ZyBmaWxsPSIjRkZEMjA1Ij48Y2lyY2xlIGN4PSIyMjUwIiBjeT0iMjgwMCIgcj0iNjAwIi8+PC9nPjwvc3ZnPg==" alt="Argentina">
  <br>
  <img src="https://img.shields.io/badge/ES_AR-red?style=flat" alt="Español AR">
  <img src="https://img.shields.io/badge/EN-blue?style=flat" alt="English">
</p>

<p align="center">
  <em>Fork argentino de <a href="https://github.com/santifer/career-ops">career-ops</a> por <a href="https://github.com/santifer">Santiago Fernández</a></em>
</p>

---

## ¿Qué es esto?

Career-Ops AR convierte cualquier CLI de IA (Claude Code, Codex, Gemini CLI) en un centro de comando de búsqueda laboral 100% en español, optimizado para el mercado argentino. En vez de trackear postulaciones en un Excel, tenés un pipeline con IA que:

- **Evalúa ofertas** con puntuación estructurada A-F (10 dimensiones ponderadas)
- **Genera PDFs personalizados** — CVs optimizados para ATS por cada búsqueda
- **Escanea portales** automáticamente (LinkedIn, ZonaJobs, Bumeran, Computrabajo, Greenhouse, Lever, Ashby)
- **Procesa en lote** — evaluá 10+ ofertas en paralelo con sub-agentes
- **Trackea todo** en un solo lugar con chequeos de integridad

> **Importante: Esto NO es una herramienta de disparo masivo.** Career-Ops AR es un filtro — te ayuda a encontrar las pocas ofertas que valen tu tiempo entre cientos. El sistema recomienda fuertemente NO postularse a nada que puntúe debajo de 4.0/5. Tu tiempo vale, y el del recruiter también.

## Novedades de la versión AR

Esta versión argentina incluye adaptaciones específicas para el mercado laboral local:

- **100% en español argentino** — todos los modos, mensajes e interfaces
- **Arquetipos adaptados** — Backend, Frontend, Data/ML, DevOps, Producto, Liderazgo Técnico
- **Soporte para tipos de contratación local** — Relación de dependencia, Monotributo, Contractor USD
- **Portales argentinos pre-configurados** — ZonaJobs, Bumeran, Computrabajo, LinkedIn AR, GetOnBoard
- **Empresas argentinas pre-cargadas** — Mercado Libre, Globant, Despegar, Ualá, Naranja X, y más
- **Vocabulario laboral argentino** — Aguinaldo/SAC, obra social, prepaga, monotributo, recibo de sueldo
- **Rangos salariales en ARS y USD** — con datos de OpenQube, Glassdoor, Sysarmy
- **Filtros geográficos** — CABA, GBA, Córdoba, Rosario, Mendoza, remoto LATAM
- **Modos de entrevista** — adaptados a procesos de selección locales

## Arranque rápido

```bash

# 1. Clonar e instalar
git clone https://github.com/Diez111/career-ops-ar.git
cd career-ops-ar && npm install
npx playwright install chromium   # Necesario para generar PDFs

# 2. Verificar instalación
npm run doctor                     # Valida todos los prerequisitos

# 3. Configurar
cp config/profile.example.yml config/profile.yml  # Editar con tus datos
cp templates/portals.example.yml portals.yml       # Personalizar empresas y portales

# 4. Agregar tu CV
# Creá cv.md en la raíz del proyecto con tu CV en markdown

# 5. Personalizar con Claude
claude   # Abrí Claude Code en este directorio

# Después pedile a Claude que adapte el sistema a vos:
# "Cambiá los arquetipos a roles de data engineering"
# "Agregá estas 5 empresas a portals.yml"
# "Actualizá mi perfil con este CV que te pego"

# 6. Empezá a usar
# Pegá una URL de oferta o ejecutá /career-ops
```

> **El sistema está diseñado para ser personalizado por Claude mismo.** Modos, arquetipos, pesos de puntuación, scripts de negociación — solo pedile a Claude que los cambie.

## Funcionalidades

| Funcionalidad | Descripción |
|---------------|-------------|
| **Auto-Pipeline** | Pegá una URL y obtené evaluación completa + PDF + entrada en tracker |
| **Evaluación 7-Bloques** | Resumen del rol, match con CV, estrategia de nivel, compensación, personalización, plan de entrevista (STAR+R) |
| **Banco de Historias** | Acumula historias STAR+Reflexión entre evaluaciones — 5-10 historias maestras que responden cualquier pregunta |
| **Scripts de Negociación** | Frameworks para pretensión salarial, negociación contractor vs relación de dependencia |
| **PDF ATS** | CVs con keywords inyectadas y diseño Space Grotesk + DM Sans |
| **Escáner de Portales** | +45 empresas pre-configuradas + queries en Ashby, Greenhouse, Lever, ZonaJobs, Bumeran, Computrabajo |
| **Procesamiento en Lote** | Evaluación paralela con workers Claude Code |
| **Dashboard TUI** | Interfaz de terminal para navegar, filtrar y ordenar tu pipeline |
| **Humano en el Loop** | La IA evalúa y recomienda, vos decidís y actuás |
| **Integridad del Pipeline** | Merge, dedup, normalización de estados, chequeos de salud automatizados |

## Uso

Career-Ops AR es un solo comando slash con múltiples modos:

```
/career-ops                  → Mostrar todos los comandos disponibles
/career-ops {pegá una JD}    → Auto-pipeline completo (evaluar + PDF + tracker)
/career-ops scan             → Escanear portales por ofertas nuevas
/career-ops pdf              → Generar CV optimizado para ATS
/career-ops lote             → Procesar ofertas en lote
/career-ops tracker          → Ver estado de postulaciones
/career-ops postular         → Completar formularios con IA
/career-ops pipeline         → Procesar URLs pendientes
/career-ops contactar        → Mensaje de outreach en LinkedIn
/career-ops investigar       → Investigación profunda de empresa
/career-ops entrenar         → Evaluar un curso o certificación
/career-ops proyecto         → Evaluar una idea de proyecto para portfolio
/career-ops comparar         → Comparar múltiples ofertas entre sí
/career-ops patrones         → Analizar patrones de rechazo
/career-ops seguimiento      → Seguimiento de postulaciones activas
/career-ops latex            → Exportar CV a LaTeX/Overleaf
```

O simplemente pegá una URL o descripción de oferta — career-ops la auto-detecta y ejecuta el pipeline completo.

## ¿Cómo funciona?

```
Pegás una URL o descripción de oferta
        │
        ▼
┌──────────────────┐
│  Detección de    │  Clasifica: Backend / Frontend / Data-ML /
│  Arquetipo       │  DevOps / Producto / Liderazgo
└────────┬─────────┘
         │
┌────────▼─────────┐
│  Evaluación A-F  │  Match, brechas, compensación, historias STAR
│  (lee cv.md)     │
└────────┬─────────┘
         │
    ┌────┼────┐
    ▼    ▼    ▼
 Reporte  PDF  Tracker
  .md   .pdf   .tsv
```

## Portales Pre-configurados

### Portales argentinos

| Portal | Tipo | Cobertura |
|--------|------|-----------|
| LinkedIn Argentina | Red profesional | Roles tech y corporativos |
| ZonaJobs | Generalista | Todos los rubros |
| Bumeran | Generalista | Similar a ZonaJobs (mismo grupo) |
| Computrabajo | Generalista | Muy amplio, incluye ofertas informales |
| Indeed Argentina | Generalista | Agregador internacional |
| GetOnBoard | Startups tech LATAM | Roles tech en startups |
| Workana | Freelance LATAM | Trabajos freelance y remotos |

### Empresas argentinas pre-cargadas

**Tecnología y Producto:** Mercado Libre, Globant, Despegar, Auth0/Okta, OLX
**Fintech:** Ualá, Naranja X, Mercado Pago, Lemon, Ripio
**Delivery y Logística:** PedidosYa, Rappi Argentina, Moova
**Consultoras:** Accenture, Globant, Flux IT, Baufest, intive
**Startups:** Pomelo, Pomelo, Satellogic, Aivo, Mudafy, Ualá

### Portales internacionales (para contractor USD)

El escáner también cubre portales ATS internacionales: Greenhouse, Ashby, Lever, Workable, Wellfound, RemoteOK, WeWorkRemotely.

## Stack Tecnológico

![Claude Code](https://img.shields.io/badge/Claude_Code-000?style=flat&logo=anthropic&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Bubble Tea](https://img.shields.io/badge/Bubble_Tea-FF75B5?style=flat&logo=go&logoColor=white)

- **Agente**: Claude Code con modos y skills personalizados
- **PDF**: Playwright + template HTML
- **Escáner**: Playwright + Greenhouse/Ashby/Lever APIs + WebSearch
- **Dashboard**: Go + Bubble Tea + Lipgloss
- **Datos**: Tablas Markdown + YAML config + TSV para lote

## Estructura del Proyecto

```
career-ops-ar/
├── AGENTS.md                    # Instrucciones canónicas del agente
├── CLAUDE.md                    # Wrapper Claude Code (importa AGENTS.md)
├── cv.md                        # Tu CV (crealo)
├── article-digest.md            # Tus proof points (opcional)
├── config/
│   └── profile.example.yml      # Template para tu perfil (adaptado a AR)
├── modes/
│   ├── es/                      # ⭐ MODOS EN ESPAÑOL ARGENTINO
│   │   ├── _shared.md           # Contexto compartido (personalizá esto)
│   │   ├── oferta.md            # Evaluación individual
│   │   ├── pdf.md               # Generación de PDF
│   │   ├── scan.md              # Escáner de portales
│   │   ├── lote.md              # Procesamiento masivo
│   │   └── ... (15 modos más)
│   ├── _profile.template.md     # Template de perfil en español
│   └── _shared.md               # Contexto sistema (inglés original)
├── templates/
│   ├── cv-template.html         # Template CV ATS-optimizado
│   ├── portals.example.yml      # Config de escáner (empresas AR)
│   └── states.yml               # Estados canónicos
├── batch/
│   ├── batch-prompt.md          # Prompt auto-contenido para workers
│   └── batch-runner.sh          # Script orquestador
├── dashboard/                   # Go TUI visualizador de pipeline
├── data/                        # Tus datos de seguimiento (gitignored)
├── reports/                     # Reportes de evaluación (gitignored)
├── output/                      # PDFs generados (gitignored)
├── fonts/                       # Space Grotesk + DM Sans
├── docs/                        # Documentación
└── examples/                    # CV, reporte y proof points de ejemplo
```

## Créditos

Este es un fork argentino del proyecto original **[career-ops](https://github.com/santifer/career-ops)** creado por **[Santiago Fernández de Valderrama](https://santifer.io)**.

Santiago usó el sistema original para evaluar 740+ ofertas, generar 100+ CVs personalizados y conseguir un rol de Head of Applied AI. [Leer el caso de estudio completo](https://santifer.io/career-ops-system).

### ¿Qué cambia en esta versión?

- Traducción completa al español argentino
- Arquetipos adaptados al mercado tech local
- Portales, empresas y filtros geográficos argentinos
- Soporte para tipos de contratación AR (rel. dependencia, monotributo, contractor USD)
- Vocabulario y contexto del mercado laboral argentino
- Rangos salariales y datos de compensación locales

## Disclaimer

**Career-Ops AR es una herramienta local y open-source — NO un servicio hosteado.** Al usar este software, reconocés que:

1. **Vos controlás tus datos.** Tu CV, información de contacto y datos personales quedan en tu máquina y se envían directo al proveedor de IA que elijas. No recolectamos, almacenamos ni tenemos acceso a ninguno de tus datos.
2. **Vos controlás la IA.** Los prompts por defecto instruyen a la IA que NO auto-envíe postulaciones, pero los modelos de IA pueden comportarse de forma impredecible. Si modificás los prompts o usás modelos diferentes, lo hacés bajo tu propio riesgo.
3. **Cumplís con los Términos de Servicio de terceros.** Usá esta herramienta de acuerdo con los Términos de Servicio de los portales de empleo con los que interactúes.
4. **Sin garantías.** Las evaluaciones son recomendaciones, no verdades absolutas. Los modelos de IA pueden alucinar skills o experiencia.

## Licencia

El código está licenciado bajo [MIT](LICENSE). El proyecto original es de [santifer/career-ops](https://github.com/santifer/career-ops).

---

<p align="center">
  <strong>🇦🇷 Hecho con mate y pasión argentina 🇦🇷</strong><br>
  <em>Forkeado de <a href="https://github.com/santifer/career-ops">santifer/career-ops</a></em>
</p>
