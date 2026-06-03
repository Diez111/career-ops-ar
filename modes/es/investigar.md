# Modo: investigar — Investigación Profunda de Empresa

Generar un prompt estructurado para Perplexity/Claude/ChatGPT con 6 ejes:

```text
## Investigación Profunda: [Empresa] — [Rol]

Contexto: Estoy evaluando una postulación para [rol] en [empresa]. Necesito información accionable para la entrevista.

### 1. Estrategia Tecnológica
- ¿Qué productos/features usan IA/ML o tecnologías modernas?
- ¿Cuál es su stack tecnológico? (modelos, infraestructura, herramientas)
- ¿Tienen blog de ingeniería? ¿Qué publican?
- ¿Qué charlas o papers presentaron?

### 2. Movimientos recientes (últimos 6 meses)
- Contrataciones relevantes en tecnología/producto?
- Adquisiciones o partnerships?
- Lanzamientos de productos o pivots?
- Rondas de financiamiento o cambios de liderazgo?

### 3. Cultura de ingeniería
- ¿Cómo shippean? (cadencia de deploys, CI/CD)
- ¿Monorepo o multirepo?
- ¿Qué lenguajes/frameworks usan?
- ¿Remoto-first u office-first?
- Reseñas en OpenQube/Glassdoor sobre cultura de ingeniería

### 4. Desafíos probables
- ¿Qué problemas de escalado tienen?
- ¿Desafíos de confiabilidad, costo, latencia?
- ¿Están migrando algo? (infraestructura, plataformas)
- ¿Qué puntos de dolor mencionan en reseñas?

### 5. Competidores y diferenciación
- ¿Quiénes son sus principales competidores?
- ¿Cuál es su foso/diferenciador?
- ¿Cómo están posicionados vs competidores?

### 6. Ángulo del candidato
Dado mi perfil (leer de cv.md y profile.yml):
- ¿Qué valor único aporto a este equipo?
- ¿Cuáles de mis proyectos son más relevantes?
- ¿Qué historia debería contar en la entrevista?
```

Personalizar cada sección con el contexto específico de la oferta evaluada.

**Para Argentina específicamente:**
- Buscar en OpenQube y Glassdoor para reseñas de empleados argentinos
- Revisar el perfil de LinkedIn de la empresa para ver equipo local
- Considerar estabilidad de la operatoria argentina (fusiones, adquisiciones, cierres de oficina local)
- Para startups: verificar si tienen entidad legal en Argentina o contratan vía Deel/Remote.com
