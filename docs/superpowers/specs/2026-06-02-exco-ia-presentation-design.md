# Diseño: Presentación exCo IA — Studio Connect, WAM Global

**Fecha:** 2026-06-02  
**Audiencia:** Comité ejecutivo WAM Global  
**Duración:** 25 min (≈20 discurso + 5 demo en vivo)  
**Equipo:** Gonzalo · Enric · Borja — Studio Connect  

---

## Objetivo

Demostrar (no pedir) que el Studio de Connect ha rediseñado el proceso de delivery de proyectos Salesforce con IA. El comité debe salir con la sensación de que esto ya está en producción y bajo control. Tono: resumen ejecutivo, no técnico. Solidez y liderazgo, no entusiasmo de laboratorio.

---

## Fichero de salida

`index.html` en la raíz del proyecto. Sin dependencias de servidor — abre directamente con `file://`. Fuentes desde `fonts/` (ya existentes). GSAP desde CDN.

---

## Sistema visual

Herencia exacta del design system de `templates/sample-presentation.html` y `templates/sample-presentation-2.html`:

- **Fondo:** `#080808`
- **Texto:** `#ffffff` / muted `#555555` / dim `#333333`
- **Acento principal:** `#FF7EFF`
- **Superficies:** `rgba(255,255,255,0.03)` con borde `rgba(255,255,255,0.07)`
- **Tipografía:** TiemposFine (títulos, 54px, weight 400) + Inter (cuerpo)
- **Slide padding:** 72px horizontal, 52px vertical
- **Transiciones:** GSAP `xPercent` horizontal, 0.5s `power2.inOut`
- **Animación entrada:** `[data-a]` stagger opacity 0→1, 0.12s, `power2.out`
- **Progress dots:** bottom center, acento en activo

**Extensión de color para agentes** (misma saturación/brillo que el acento):
- Consultor: `#FF7EFF` (acento existente)
- Arquitecto: `#64B4FF`
- Desarrollador: `#50F0A0`

---

## Estructura de slides

### Slide 1 — Portada
- Componente: cover con glow radial top-right + breathing animation en título
- Título grande TiemposFine: *"IA con criterio"*
- Subtítulo: "Cómo el Studio de Connect ha rediseñado el delivery de proyectos Salesforce con IA."
- Crédito: "Gonzalo · Enric · Borja — Studio Connect, WAM Global"
- Logo WAM top-left

### Slide 2 — ¿Para qué hacemos esto?
- Section tag + slide title
- cards-3: (1) Reglas del juego, (2) El mercado se mueve, (3) Ventaja de velocidad
- accent-line: tono de liderazgo implícito
- Sin métricas de ROI/coste

### Slide 3 — ¿Qué objetivos nos marcamos?
- Section tag + slide title
- setup-steps numerados (3 pasos): todo el proceso / con criterio / humano en el juego

### Slide 4 — Filosofía
- Section tag + slide title
- cards-3: Conversacional no automático / El humano es el criterio / Calidad no solo velocidad

### Slide 5 — El cómo: de prompters a método
- Section tag + slide title
- recipe-flow visual (4 pasos): Skill=receta / MCPs=instrumentos / Ingredientes=materia prima / Agente=cocinero
- accent-line: portabilidad y estándares

### Slide 6 — Los tres asistentes
- Section tag + slide title
- cards-3: Consultor / Arquitecto / Desarrollador
- Pie de slide: entidades vivas + Confluence compartido + skills en lenguaje natural

### Slide 7 — El proceso de delivery ⭐ SLIDE ESTRELLA
Ver sección detallada abajo.

### Slide 8 — Demo UATs `[PLACEHOLDER]`
- Solo título + zona reservada visual grande (dashed border, texto placeholder)
- Mensaje: "Demo en vivo — ≈5 min"

### Slide 9 — Visión a futuro
- Section tag + slide title
- 3 col-blocks: Nuevas líneas (SMC + auditorías) / Gobernanza / Mantenernos AI-Ready

### Slide 10 — Gracias
- Cierre centrado con glow inferior
- Texto: "Gracias." + créditos equipo
- Logo WAM bottom center

---

## Slide 7 — Diseño detallado

### Layout
La slide se divide verticalmente en dos zonas:
- **Zona superior (≈55% altura):** el timeline con las 12 paradas, a full width (de padding a padding de la slide).
- **Zona inferior (≈35% altura):** el cajón de detalle, que cambia con cada parada al hacer hover.

### Timeline
Las paradas se agrupan en bloques por agente, con fondo de color suave y borde del color del agente:
- Parada 1 (inicio): nodo neutral sin zona de color
- Paradas 2–5: zona Consultor `#FF7EFF`
- Paradas 6–9: zona Arquitecto `#64B4FF`
- Parada 10: zona Desarrollador `#50F0A0`
- Paradas 11–12: zona Consultor `#FF7EFF`

Cada parada: círculo numerado + label debajo. Hover sobre la parada: highlight del círculo (glow ring) + actualización del cajón inferior.

Herramientas de apoyo (Gemini transcripción, NotebookLM) mencionadas como pequeñas etiquetas en las paradas 3 y donde aplique.

### Cajón inferior
Estado por defecto: mensaje neutral *"Pasa el cursor sobre una parada para ver el detalle"*.

Al hacer hover sobre una parada, transición suave (fade + translateY) mostrando:
- Número de parada (grande, en dim)
- Eyebrow con color del agente responsable
- Título de la parada
- Descripción `[PENDIENTE: descripción]`
- Enlace opcional `[PENDIENTE: enlace vídeo]`

### Estructura de datos (objeto JS)
```js
const STOPS = [
  {
    id: 1,
    label: "Traspaso comercial",
    agent: null,  // "consultor" | "arquitecto" | "desarrollador" | null
    description: "[PENDIENTE: descripción]",
    videoUrl: null,
    tools: []
  },
  // … 11 más
];
```

Señalizado con `/* ===== DATOS PARADAS — EDITAR AQUÍ ===== */` al inicio del script.

---

## Implementación

- **Enfoque:** HTML monolítico (Enfoque C) — un único `index.html`, sin dependencias de servidor
- **Datos editables:** objeto `STOPS` al inicio del script, separado del resto del código
- **Placeholders:** literales `[PENDIENTE: descripción]` y `[PENDIENTE: enlace vídeo]`, visibles y buscables
- **Navegación:** misma que las plantillas — teclado (←→ espacio), click (mitad izq/der), swipe táctil, dots
- **Slide 8:** estructura completa pero marcada visualmente como placeholder

---

## Decisiones de diseño tomadas

- Journey layout: **Timeline con zonas de color** (opción C del brainstorming)
- Hover behavior: **Cajón inferior** (opción C del brainstorming)
- Path: **full width** de la slide
- Idioma: español
- Sin métricas ni cifras de ROI/coste
- Título portada: "IA con criterio"
- Analogía cocina: solo en slide 5 (no como motivo visual recurrente — el design system minimalista no invita a iconografía decorativa)
