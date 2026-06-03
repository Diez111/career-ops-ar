# Modo: postular — Asistente de Postulación en Vivo

Modo interactivo para cuando el candidato está completando un formulario de postulación. Lee lo que está en pantalla, carga el contexto previo de la oferta y genera respuestas personalizadas para cada pregunta del formulario.

## Requisitos

- **Ideal con Playwright en modo visible**
- **Sin Playwright**: el candidato comparte captura o pega las preguntas manualmente

## Workflow

```text
1. DETECTAR    → Leer pestaña activa del navegador (screenshot/URL/título)
2. IDENTIFICAR  → Extraer empresa + rol de la página
3. BUSCAR       → Buscar contra reportes existentes en reports/
4. CARGAR       → Leer reporte completo + Sección H (si existe)
5. COMPARAR     → ¿El rol en pantalla coincide con el evaluado? Si cambió → notificar
6. ANALIZAR     → Identificar TODAS las preguntas visibles del formulario
7. GENERAR      → Para cada pregunta, generar respuesta personalizada
8. PRESENTAR    → Mostrar respuestas formateadas para copiar y pegar
```

## Paso 1 — Detectar la oferta

**Con Playwright:** Tomar snapshot de la página activa. Leer título, URL y contenido visible.

**Sin Playwright:** Pedir al candidato que:
- Comparta captura del formulario
- O pegue las preguntas como texto
- O diga empresa + rol para buscarlo

## Paso 2 — Identificar y buscar contexto

1. Extraer nombre de empresa y título del rol de la página
2. Buscar en `reports/` por nombre de empresa (grep case-insensitive)
3. Si hay match → cargar el reporte completo
4. Si hay Sección H → cargar respuestas previas como base
5. Si NO hay match → notificar y ofrecer ejecutar auto-pipeline rápido

## Paso 3 — Detectar cambios en el rol

Si el rol en pantalla difiere del evaluado:
- **Notificar al candidato**: "El rol cambió de [X] a [Y]. ¿Querés que re-evalúe o adapto las respuestas al nuevo título?"
- **Si adaptar**: Ajustar respuestas al nuevo rol sin re-evaluar
- **Si re-evaluar**: Ejecutar evaluación A-F completa, actualizar reporte, regenerar Sección H
- **Actualizar tracker**: Cambiar título del rol en applications.md si corresponde

## Paso 4 — Analizar preguntas del formulario

Identificar TODAS las preguntas visibles:
- Campos de texto libre (carta de presentación, por qué este rol, etc.)
- Dropdowns (cómo te enteraste, autorización de trabajo, etc.)
- Sí/No (relocación, visa, etc.)
- Campos de salario (rango, pretensión)
- Campos de upload (CV, carta de presentación PDF)

Clasificar cada pregunta:
- **Ya respondida en Sección H** → adaptar la respuesta existente
- **Nueva pregunta** → generar respuesta del reporte + cv.md

## Paso 5 — Generar respuestas

Para cada pregunta, generar la respuesta siguiendo:

1. **Contexto del reporte**: Usar proof points del bloque B, historias STAR del bloque F
2. **Sección H previa**: Si existe borrador, usarlo como base y refinar
3. **Tono "te estoy eligiendo"**: Mismo framework del auto-pipeline
4. **Especificidad**: Referenciar algo específico de la JD visible en pantalla
5. **Idioma**: En español argentino natural

**Formato de salida:**

```text
## Respuestas para [Empresa] — [Rol]

Basado en: Reporte #NNN | Puntaje: X.X/5 | Arquetipo: [tipo]

---

### 1. [Pregunta exacta del formulario]
> [Respuesta lista para copiar y pegar]

### 2. [Próxima pregunta]
> [Respuesta]

...

---

Notas:
- [Observaciones sobre el rol, cambios, etc.]
- [Sugerencias de personalización que el candidato debería revisar]
```

## Paso 6 — Post-postulación (opcional)

Si el candidato confirma que envió la postulación:
1. Actualizar estado en `applications.md` de "Evaluada" a "Postulada"
2. Actualizar Sección H del reporte con las respuestas finales
3. Sugerir próximo paso: `/career-ops contactar` para contacto LinkedIn

## Manejo de scroll

Si el formulario tiene más preguntas que las visibles:
- Pedir al candidato que scrollee y comparta otra captura
- O que pegue las preguntas restantes
- Procesar en iteraciones hasta cubrir todo el formulario

## Preguntas frecuentes en formularios argentinos

- **Remuneración pretendida** → Responder con rango basado en investigación del Bloque D. Para posiciones locales en ARS, dar rango bruto mensual. Para contractor USD, dar rango mensual en dólares.
- **Disponibilidad** → Inmediata, 2 semanas, o la real del candidato
- **Tipo de contratación** → Relación de dependencia / Monotributo / Contractor
- **Lugar de residencia** → Ciudad, Provincia
- **LinkedIn / Portfolio / GitHub** → URLs del perfil
