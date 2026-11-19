# Fuentes: qué aporta cada una y cuánto fiarse

Para lectura y para citar con enlace; nunca copiar texto. Si una regla de la skill va a decidir algo caro (rediseño, argumento legal), abrir la fuente primaria antes.

## Libros (de pago: aquí solo hay paráfrasis de índices, avances oficiales y reseñas)

| Libro | Para qué sirve | Qué se pudo verificar |
|---|---|---|
| **Travis Lowdermilk, *User-Centered Design: A Developer's Guide to Building User-Friendly Applications*** (O'Reilly, 2013, ~154 págs.) | Introductorio y pensado para programadores. Convertir peticiones en necesidades, plan de proyecto con requisitos de usuario antes que funcionales, contención con las funcionalidades, personas y escenarios, guion de un test de usabilidad (cap. 9). | Índice completo (Helion). El interior, solo por reseñas. Lo más útil y concreto (entrevistas, nº de usuarios, SUS, severidad) se completó con NN/g y MeasuringU → `centrado-en-usuario.md`. |
| **Jon Yablonski, *Laws of UX*** (O'Reilly; 1.ª ed. 2020, **2.ª ed. 2024**, ~186 págs.) | 10 leyes desarrolladas con ejemplos, un capítulo para convertirlas en principios de equipo y otro de ética (dark patterns, fricción deliberada). La 2.ª ed. añade paradoja de la elección, sesgo de complejidad, flow, accesibilidad, personalización y técnicas de investigación. | Índices de las dos ediciones; las 30 entradas de lawsofux.com; orígenes contrastados (Doherty 1982 leído en el escaneo; Miller frente a Cowan; meta-análisis de choice overload y Zeigarnik) → `leyes-ux.md`. |
| **Adam Wathan y Steve Schoger, *Refactoring UI*** (2018, PDF, 218 págs.) | El más práctico para escribir UI: jerarquía, espaciado, texto, color, profundidad, imágenes y toques finales, con reglas tácticas. | Índice oficial, dos avances oficiales («Building your color palette», «Labels are a last resort»), «7 practical tips for cheating at design», notas de la charla de CSS Day 2019 y resúmenes. Algunos valores exactos (escala de espaciado completa, escala tipográfica) coinciden con Tailwind pero no están confirmados como cita del libro → `diseno-visual.md`. |
| Steve Krug, *Don't Make Me Think* (3.ª ed. 2014) | Escaneo, «quitar la mitad de las palabras», tests de usabilidad baratos. | Solo resúmenes secundarios → `patrones.md` §5. |

## Webs y normas (gratis, primarias)

- NN/g — heurísticas: https://www.nngroup.com/articles/ten-usability-heuristics/ · severidad: https://www.nngroup.com/articles/how-to-rate-the-severity-of-usability-problems/ · tiempos de respuesta: https://www.nngroup.com/articles/response-times-3-important-limits/ · qué método usar: https://www.nngroup.com/articles/which-ux-research-methods/
- Laws of UX: https://lawsofux.com (CC BY-NC-ND 4.0)
- Refactoring UI, avances: https://www.refactoringui.com/previews/building-your-color-palette · https://www.refactoringui.com/previews/labels-are-a-last-resort
- WCAG 2.2: https://www.w3.org/TR/WCAG22/ · novedades: https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/ · referencia rápida: https://www.w3.org/WAI/WCAG22/quickref/
- ARIA Authoring Practices Guide: https://www.w3.org/WAI/ARIA/apg/
- GOV.UK Design System (formularios, errores, botones, tablas; muy basado en evidencia): https://design-system.service.gov.uk/
- Baymard (formularios y checkout, con estudios): https://baymard.com/blog
- Smart Interface Design Patterns (Vitaly Friedman): https://smart-interface-design-patterns.com/
- Apple HIG: https://developer.apple.com/design/human-interface-guidelines/ · Material 3: https://m3.material.io
- OKLCH: https://evilmartians.com/chronicles/oklch-in-css-why-quit-rgb-hsl · https://oklch.com/
- Patrones engañosos: https://www.deceptive.design/types
- ISO 9241-11:2018 (usabilidad) e ISO 9241-210:2019 (diseño centrado en las personas): de pago; vistas previas citadas en `centrado-en-usuario.md` §4.
- WebAIM Million (qué falla más en accesibilidad): https://webaim.org/projects/million/

## Estado legal (a 03/10/2026; revisar si pasa tiempo)

- WCAG 2.2 es la versión a cumplir; WCAG 3.0 sigue en borrador y APCA no forma parte de él.
- EAA (Directiva 2019/882) aplicable desde el 28/06/2025; en España, Ley 11/2023. Exención para microempresas que prestan servicios (texto literal no verificado).
- EN 301 549 V4.1.1 (con WCAG 2.2) publicada el 02/09/2026; la presunción de conformidad llega cuando se cite en el DOUE (previsto hacia finales de 2026, sin confirmar).
- DSA art. 25 (interfaces engañosas) solo obliga a plataformas en línea; la Digital Fairness Act aún no se había propuesto en septiembre de 2026.

## Bases históricas, solo como contexto

- Research-Based Web Design & Usability Guidelines (HHS, 2004).
- Nielsen y Landauer (1993) sobre el nº de usuarios en tests; Faulkner (2003) lo matiza (ver `centrado-en-usuario.md` §3.6).
