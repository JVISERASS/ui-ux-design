# Accesibilidad: WCAG 2.2 AA como checklist de desarrollo

Leer al auditar accesibilidad, al construir componentes interactivos (modales, menús, formularios, arrastre, login) o cuando haya dudas legales (EAA, EN 301 549, Ley 11/2023). §10 es la checklist corta para revisar código. Investigado el 03/10/2026; todo parafraseado; lo no comprobado contra fuente primaria va marcado **UNVERIFIED**.

## 0. Estado de la norma (verificado)

- WCAG 2.2 es Recomendación W3C desde el 5/10/2023; la versión vigente publicada en /TR es la del 12/12/2024 (actualización editorial). Fuente: https://www.w3.org/TR/WCAG22/ y https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/
- 2.2 añade 9 criterios (6 en A/AA, 3 en AAA) y **elimina 4.1.1 Parsing** (obsoleto). Quien esté obligado por política a 2.0/2.1 puede seguir teniendo que informar de 4.1.1. Fuente: https://www.w3.org/TR/WCAG22/
- Recuento A+AA en 2.2 (contado a mano sobre la lista de /TR/WCAG22): **31 de nivel A + 24 de nivel AA = 55 criterios**.
- Objetivo práctico: "conforme AA" = cumplir todos los A y todos los AA. Los AAA no se exigen en bloque.

Leyenda: 🆕 = nuevo en 2.2. Cada línea: número, nombre corto, nivel y comprobación de desarrollador (redacción propia).

## 1. Perceptible

- 1.1.1 Contenido no textual (A): toda `<img>` informativa con `alt` que diga lo que aporta; decorativas con `alt=""`; iconos-botón con nombre accesible; SVG con `<title>` o `aria-label`, o `aria-hidden` si son decoración.
- 1.2.1 Solo audio y solo vídeo grabados (A): transcripción para audio; transcripción o pista de audio para vídeo mudo.
- 1.2.2 Subtítulos grabados (A): vídeo con audio lleva subtítulos sincronizados.
- 1.2.3 Audiodescripción o alternativa (A): vídeo grabado con información visual relevante tiene audiodescripción o alternativa textual completa.
- 1.2.4 Subtítulos en directo (AA): emisiones en vivo con subtítulos.
- 1.2.5 Audiodescripción grabada (AA): audiodescripción (no basta la alternativa textual).
- 1.3.1 Información y relaciones (A): la estructura visual existe en el marcado: encabezados `h1…h6`, listas reales, `<table>` con `<th scope>`, `<label for>`, `<fieldset>/<legend>` en grupos de radios/checkbox, landmarks.
- 1.3.2 Secuencia significativa (A): el orden del DOM produce un orden de lectura con sentido (cuidado con `order`, `flex-direction: row-reverse`, grid reordenado).
- 1.3.3 Características sensoriales (A): instrucciones que no dependan solo de forma, posición, tamaño o sonido ("pulsa el botón verde de la derecha").
- 1.3.4 Orientación (AA): no bloquear la vista a vertical u horizontal salvo que sea esencial.
- 1.3.5 Identificar el propósito de la entrada (AA): campos sobre el propio usuario con `autocomplete` correcto (`name`, `email`, `tel`, `street-address`, `postal-code`…).
- 1.4.1 Uso del color (A): el color nunca es el único indicador (errores con icono/texto, enlaces en texto distinguibles por algo más que el color o con 3:1 respecto al texto y señal extra al foco/hover).
- 1.4.2 Control del audio (A): audio automático de más de 3 s se puede parar o bajar.
- 1.4.3 Contraste mínimo (AA): texto normal ≥ 4.5:1; texto grande (≥ 24 px, o ≥ 18.66 px en negrita) ≥ 3:1. Incluye placeholders y texto de botones; logos y texto inactivo exentos.
- 1.4.4 Redimensionar texto (AA): zoom al 200 % sin pérdida de contenido ni funciones; no bloquear el zoom (`user-scalable=no`, `maximum-scale=1`).
- 1.4.5 Imágenes de texto (AA): texto real, no imágenes de texto (salvo logos o personalización).
- 1.4.10 Reflow (AA): a 320 px CSS de ancho (equivale a 1280 px al 400 %) no hay scroll en dos dimensiones; excepciones para tablas de datos, mapas, diagramas y barras de herramientas.
- 1.4.11 Contraste no textual (AA): bordes de inputs, iconos que comunican, indicadores de foco y estados de componentes ≥ 3:1 contra lo adyacente.
- 1.4.12 Espaciado del texto (AA): nada se corta ni se solapa si el usuario fuerza interlineado 1.5, párrafos 2×, letras 0.12em, palabras 0.16em (evitar alturas fijas en contenedores de texto).
- 1.4.13 Contenido al pasar el ratón o al enfocar (AA): tooltips/popovers descartables (Esc), que se puedan recorrer con el puntero sin desaparecer y persistentes hasta que se quiten.

## 2. Operable

- 2.1.1 Teclado (A): todo lo que hace el ratón se hace con teclado (sin depender de tiempos por pulsación). `div onclick` sin `tabindex`/teclas = fallo.
- 2.1.2 Sin trampas de teclado (A): siempre se puede salir con Tab/Shift+Tab/Esc (ojo con editores embebidos y modales).
- 2.1.4 Atajos de una sola tecla (A): atajos de un carácter se pueden desactivar, reasignar o solo actúan con el foco en el componente.
- 2.2.1 Tiempo ajustable (A): límites de tiempo (sesión, formulario) avisables y ampliables (mínimo 20 s para pedir más, hasta 10× el tiempo) salvo excepciones (tiempo real, > 20 h, esencial).
- 2.2.2 Poner en pausa, detener, ocultar (A): carruseles, animaciones o contenido que se mueve > 5 s y en paralelo a otro contenido se pueden pausar; contenido que se autoactualiza, también.
- 2.3.1 Tres destellos o por debajo del umbral (A): nada parpadea más de 3 veces por segundo.
- 2.4.1 Saltar bloques (A): enlace "Saltar al contenido" o landmarks/encabezados que permitan saltarse la navegación repetida.
- 2.4.2 Página titulada (A): `<title>` único y descriptivo por vista (también en SPA al cambiar de ruta).
- 2.4.3 Orden del foco (A): Tab recorre en un orden que preserva el significado; nada de `tabindex` positivo.
- 2.4.4 Propósito de los enlaces (en contexto) (A): el texto del enlace (más su frase/celda) dice adónde va; evitar "pulsa aquí" sueltos.
- 2.4.5 Múltiples vías (AA): más de una forma de llegar a una página (menú + búsqueda, mapa del sitio…), salvo pasos de un proceso.
- 2.4.6 Encabezados y etiquetas (AA): encabezados y labels describen tema o propósito.
- 2.4.7 Foco visible (AA): siempre hay indicador de foco visible; nunca `outline: none` sin sustituto (usar `:focus-visible`).
- 2.4.11 🆕 Foco no oculto (mínimo) (AA): el elemento con foco no queda **completamente** tapado por contenido del autor (cabeceras/pies sticky, banners de cookies, barras inferiores). Solución típica: `scroll-padding-top/bottom` igual a la altura de lo fijo.
- 2.5.1 Gestos de puntero (A): lo que exige gesto multipunto o con trayectoria (pellizco, swipe) tiene alternativa de un solo puntero sin trayectoria (botones).
- 2.5.2 Cancelación del puntero (A): las acciones se disparan al soltar (`click`/`pointerup`), no al pulsar, o se pueden abortar/deshacer.
- 2.5.3 Etiqueta en el nombre (A): el nombre accesible contiene el texto visible (idealmente al principio): si el botón dice "Enviar", su `aria-label` no puede ser "Submit form".
- 2.5.4 Activación por movimiento (A): agitar/inclinar tiene alternativa en la UI y se puede desactivar.
- 2.5.7 🆕 Movimientos de arrastre (AA): todo lo que se hace arrastrando (kanban, ordenar filas, sliders, mapas) tiene alternativa con un solo puntero sin arrastrar (botones subir/bajar, menú "Mover a…", clic en destino).
- 2.5.8 🆕 Tamaño del objetivo (mínimo) (AA): objetivos de puntero ≥ 24×24 px CSS, o con espaciado suficiente (un círculo de 24 px centrado en cada objetivo no toca otro objetivo ni su círculo). Excepciones: control equivalente que sí cumple, enlaces en línea dentro de texto, control nativo no modificado del navegador, esencial (p. ej. pines de mapa). Fuente: https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html

## 3. Comprensible

- 3.1.1 Idioma de la página (A): `<html lang="es">`.
- 3.1.2 Idioma de las partes (AA): fragmentos en otro idioma con `lang` propio.
- 3.2.1 Al recibir el foco (A): enfocar no cambia de contexto (no abrir ventanas, no enviar).
- 3.2.2 Al introducir datos (A): cambiar un select/checkbox no navega ni envía por sí solo sin avisar antes.
- 3.2.3 Navegación coherente (AA): la navegación repetida aparece en el mismo orden relativo en todas las páginas.
- 3.2.4 Identificación coherente (AA): mismos iconos/etiquetas para la misma función en todo el producto.
- 3.2.6 🆕 Ayuda coherente (A): si hay mecanismos de ayuda (contacto, teléfono, chat, FAQ) repetidos en varias páginas, aparecen en el mismo orden relativo. No obliga a tener ayuda.
- 3.3.1 Identificación de errores (A): el error detectado automáticamente se identifica y se describe en texto (no solo borde rojo); vincular con `aria-describedby` y marcar `aria-invalid="true"`.
- 3.3.2 Etiquetas o instrucciones (A): todo campo tiene label visible e instrucciones de formato cuando hagan falta (el placeholder no cuenta como label).
- 3.3.3 Sugerencia ante errores (AA): si se sabe cómo corregir, el mensaje lo dice ("Escribe la fecha como 25/12/2026").
- 3.3.4 Prevención de errores (legales, financieros, datos) (AA): en compromisos legales/económicos o borrado de datos: reversible, o verificado, o con paso de revisión y confirmación.
- 3.3.7 🆕 Entrada redundante (A): no pedir de nuevo en el mismo proceso lo ya introducido: autorrellenar o dejarlo seleccionable ("misma dirección que la de facturación"). Excepciones: esencial, seguridad (repetir contraseña), dato caducado.
- 3.3.8 🆕 Autenticación accesible (mínimo) (AA): ningún paso de login exige una prueba cognitiva (recordar, transcribir, resolver) sin alternativa o ayuda. En la práctica: **no bloquear pegar** en contraseña ni en código OTP, `autocomplete="username"`/`current-password"`/`one-time-code"`, no partir el OTP en casillas que impidan pegar, CAPTCHA de transcripción solo con alternativa; se permite reconocer objetos o contenido propio. Fuente: https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html

## 4. Robusto

- ~~4.1.1 Procesamiento~~: eliminado en 2.2 (los navegadores y AT ya reparan el HTML mal formado; los problemas reales se cubren con 1.3.1 y 4.1.2). IDs duplicados siguen siendo un bug si rompen `for`/`aria-labelledby`.
- 4.1.2 Nombre, función, valor (A): todo componente de UI expone nombre, rol, estado y valor a la API de accesibilidad (`aria-expanded`, `aria-pressed`, `aria-checked`, `aria-selected`, `aria-current`) y se actualiza al cambiar.
- 4.1.3 Mensajes de estado (AA): los avisos que no mueven el foco (guardado, "5 resultados", error de envío, "cargando") se anuncian por tecnología de apoyo: `role="status"` (cortesía), `role="alert"` (urgente), `role="log"`, `aria-live`. Fuente: https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html

## 5. Los 9 nuevos de 2.2 de un vistazo

| SC | Nivel | Qué exige (resumen propio) |
|---|---|---|
| 2.4.11 Foco no oculto (mínimo) | AA | El foco no queda tapado del todo por contenido del autor |
| 2.4.12 Foco no oculto (mejorado) | AAA | Ninguna parte del foco queda tapada |
| 2.4.13 Apariencia del foco | AAA | Indicador ≥ área de un perímetro de 2 px CSS y 3:1 entre estado con y sin foco |
| 2.5.7 Movimientos de arrastre | AA | Alternativa de un solo puntero sin arrastrar |
| 2.5.8 Tamaño del objetivo (mínimo) | AA | 24×24 px CSS o espaciado equivalente |
| 3.2.6 Ayuda coherente | A | Ayuda repetida en el mismo orden relativo |
| 3.3.7 Entrada redundante | A | No volver a pedir lo ya dado en el proceso |
| 3.3.8 Autenticación accesible (mínimo) | AA | Sin prueba cognitiva sin alternativa; permitir pegar y gestores |
| 3.3.9 Autenticación accesible (mejorado) | AAA | Ni siquiera reconocimiento de objetos o contenido propio |

Fuente: https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/

## 6. WCAG 3.0 y APCA: no usar para cumplimiento

- WCAG 3.0 sigue siendo **Working Draft** (último borrador publicado el 3/03/2026: https://www.w3.org/TR/2026/WD-wcag-3.0-20260303/). Modelo de resultados con niveles Bronce/Plata/Oro en vez de checklist A/AA/AAA. Calendario citado por terceros: Candidate Recommendation hacia finales de 2027 y Recomendación no antes de 2028 (https://abilitynet.org.uk/resources/digital-accessibility/what-expect-wcag-30-web-content-accessibility-guidelines) — fechas **UNVERIFIED** contra el W3C.
- **APCA no está en el borrador de WCAG 3**: el grupo de trabajo lo retiró en julio de 2023 y el borrador actual dice que el algoritmo de contraste está por decidir (https://adrianroselli.com/2026/04/wcag3-contrast-as-of-april-2026.html).
- Regla para el agente: el contraste se mide con la fórmula de WCAG 2.x (4.5:1 / 3:1). APCA, como mucho, como segunda opinión documentada; nunca como justificación de un color que no pase 2.x.

## 7. Marco legal UE y España

- **Acta Europea de Accesibilidad (Directiva (UE) 2019/882, EAA)**: aplicable desde el **28/06/2025**. Hasta el 28/06/2030 pueden seguir usándose productos ya en uso para prestar servicios, y hay periodos transitorios para contratos previos. Fuente: https://www.cuatrecasas.com/es/global/propiedad-intelectual/art/claves-proxima-entrada-vigor-ley-accesibilidad-espana
- Ámbito: productos (ordenadores, SO, terminales de pago, cajeros, e-readers…) y **servicios a consumidores** (comunicaciones electrónicas, banca para consumidores, comercio electrónico, transporte, libros electrónicos…). Un SaaS puramente B2B queda en principio fuera; si hay una parte que ve el consumidor final (p. ej. una página pública que firma un particular) conviene diseñarla AA igualmente — esto último es criterio propio, no conclusión jurídica.
- **Exención de microempresas que prestan servicios** (< 10 personas y volumen de negocio o balance ≤ 2 M€): exentas de los requisitos para servicios (art. 4.5 de la Directiva), no para productos. Fuente secundaria: https://www.taylorwessing.com/en/interface/2025/accessibility/key-eu-accessibility-act-exemptions-and-the-challenges-they-pose — texto literal del artículo **UNVERIFIED** (EUR-Lex no cargó).
- **Norma armonizada EN 301 549**: la versión que estaba en vigor, **V3.2.1, remite a WCAG 2.1 A+AA**. La **V4.1.1** se adoptó el 24/08/2026 y se publicó el **2/09/2026**; incorpora **WCAG 2.2 A+AA**. Solo da presunción de conformidad con la EAA cuando se cite en el DOUE; se esperaba hacia el 30/11/2026. Fuentes: https://www.deque.com/blog/en-301-549-v4-1-1-is-final-what-changed-what-it-means-and-what-you-should-do/ y https://www.dwt.com/insights/2026/09/european-accessibility-act-ict-standards-update. La fecha de cita en el DOUE es una previsión: **UNVERIFIED**.
- Conclusión práctica: diseñar contra **WCAG 2.2 AA**. Cubre 2.1 AA (2.2 es compatible hacia atrás salvo 4.1.1) y es lo que pedirá la EN 301 549 V4.1.1.
- **España — Ley 11/2023, de 8 de mayo** (BOE-A-2023-11022, BOE del 9/05/2023): su Título I traspone la Directiva 2019/882; las obligaciones de accesibilidad de productos y servicios se aplican desde el 28/06/2025, con adaptación hasta 2030 para lo ya comercializado. Fuentes: https://www.boe.es/buscar/act.php?id=BOE-A-2023-11022 y https://www.icab.es/es/actualidad/noticias/noticia/Ley-11-2023-de-8-de-mayo-de-trasposicion-de-Directivas-de-la-Union-Europea-en-materia-de-accesibilidad-de-determinados-productos-y-servicios-migracion-de-personas-altamente-cualificadas-tributaria-y-digitalizacion-de-actuaciones-notariales-y-registra/. Cómo recoge la ley española la exención de microempresas y quién vigila y sanciona: **UNVERIFIED** (la lectura automática del BOE no fue fiable; consultar el texto consolidado).
- Para el sector público español sigue aplicando el RD 1112/2018 (webs y apps públicas) — **UNVERIFIED** en esta pasada; no afecta a un SaaS privado.

## 8. Reglas prácticas de ARIA

Fuente principal: "Using ARIA" (W3C), hoy **Discontinued Draft** (24/02/2026), que se conserva por motivos históricos y remite a la APG: https://www.w3.org/TR/using-aria/ · APG: https://www.w3.org/WAI/ARIA/apg/

1. **Primera regla**: si existe un elemento o atributo HTML nativo con la semántica y el comportamiento que necesitas, úsalo en vez de reconvertir otro elemento y añadirle ARIA. `<button>`, `<a href>`, `<input type=checkbox>`, `<select>`, `<details>`, `<dialog>`.
2. No cambies la semántica nativa salvo que no haya más remedio (no `<h2 role="tab">`; envuelve).
3. Todo control ARIA interactivo debe funcionar con teclado (Enter/Espacio, flechas en compuestos según la APG).
4. Nunca `role="presentation"` ni `aria-hidden="true"` sobre algo enfocable.
5. (Regla histórica) Todo elemento interactivo necesita **nombre accesible**. La versión actual del documento enumera cuatro reglas; que la quinta siga en el texto: **UNVERIFIED**. El requisito en sí lo impone 4.1.2.
- Corolario de la APG: "no ARIA is better than bad ARIA". ARIA solo cambia lo que se anuncia, no añade comportamiento.

**Nombres accesibles** (orden de preferencia, criterio propio basado en APG): texto visible del propio elemento → `<label for>` o `aria-labelledby` apuntando a texto visible → `aria-label` solo si no hay texto visible (botón-icono). Respeta 2.5.3: el nombre empieza por el texto visible. `title` y `placeholder` no sirven como nombre.

**Diálogos modales** (APG, https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/):
- Contenedor `role="dialog"` + `aria-modal="true"` + `aria-labelledby` al título visible; `aria-describedby` solo si la descripción es corta.
- Al abrir, el foco entra en el diálogo: primer control en diálogos simples; el título o un elemento estático con `tabindex="-1"` si el contenido es largo; **el botón menos destructivo** si la acción es peligrosa.
- Tab/Shift+Tab giran dentro del diálogo; **Esc** cierra.
- Al cerrar, el foco **vuelve al elemento que lo abrió** (o al sitio lógico si ya no existe, p. ej. la fila recién creada).
- `<dialog>` nativo con `showModal()` da trampa de foco, Esc e `inert` en el fondo; la página de la APG no lo trata (**UNVERIFIED** que cubra todo en todos los lectores). Con Radix/shadcn ya viene resuelto: no reimplementar.

**Regiones vivas para estados asíncronos** (4.1.3):
- `role="status"` (equivale a `aria-live="polite"`) para "Guardado", "3 resultados", "Cargando…". `role="alert"` (assertive) solo para errores que interrumpen.
- La región tiene que **existir en el DOM antes** de que cambie su texto (montarla vacía y rellenarla); si se inserta ya con texto, muchos lectores no la anuncian — práctica conocida, **UNVERIFIED** contra fuente normativa en esta pasada.
- No mover el foco a un toast; los toasts que desaparecen solos deben durar lo bastante o poder pausarse (2.2.1).
- Spinners: `aria-busy="true"` en la región que se recarga + texto de estado.

**Formularios**: `aria-invalid="true"` en el campo con error, `aria-describedby` al mensaje y a la pista, `required` nativo (anuncia "obligatorio"), resumen de errores con enlaces a cada campo y foco al resumen al enviar (patrón GOV.UK).

## 9. Receta de pruebas

1. **Pasada solo con teclado** (desenchufar el ratón): Tab por toda la vista; ¿el foco se ve siempre (2.4.7) y no queda tapado por lo sticky (2.4.11)?; ¿orden lógico (2.4.3)?; ¿todo se activa con Enter/Espacio?; ¿menús y modales se cierran con Esc y devuelven el foco?; ¿alternativa al arrastre (2.5.7)?; ¿enlace para saltar al contenido?
2. **Zoom y reflow**: 200 % de texto y ventana de 320 px CSS; espaciado de texto forzado con un bookmarklet (1.4.12).
3. **Lector de pantalla, prueba rápida**: NVDA + Firefox/Chrome (Windows), VoiceOver + Safari (macOS/iOS), TalkBack (Android). Recorrer encabezados (H), landmarks y formularios; comprobar que cada control dice nombre + rol + estado y que "Guardado" o los errores se anuncian sin mover el foco.
4. **Automático**: axe-core (extensión, `@axe-core/playwright`, `jest-axe`) y Lighthouse en CI. Detectan sobre todo contraste, alt ausente, labels, nombres vacíos, `lang`, ARIA inválido.
5. **Límites de lo automático** (cifras con fuente):
   - GDS (GOV.UK), 2017: 10 herramientas contra una página con 142–143 barreras deliberadas; la mejor encontró ~41 % y todas juntas ~71 %; el 29 % no lo vio ninguna. https://accessibility.blog.gov.uk/2017/02/24/what-we-found-when-we-tested-tools-on-the-worlds-least-accessible-webpage/
   - Deque, 2021: sobre más de 2.000 auditorías reales (~300.000 incidencias), axe detectó el **57 % del volumen** de incidencias. Lo midió el propio fabricante y cuenta incidencias, no criterios. https://www.deque.com/blog/automated-testing-study-identifies-57-percent-of-digital-accessibility-issues/
   - La cifra "solo 20–30 %", muy repetida, se refiere a **criterios** WCAG comprobables de forma automática, no a incidencias. Regla: un axe en verde **no** significa accesible.
6. **Lo que más falla en la web real** (WebAIM Million 2026, páginas de inicio): 95,9 % con fallos detectables; media de 56,1 errores; top: contraste bajo 83,9 %, alt ausente 53,1 %, inputs sin label 51 %, enlaces vacíos 46,3 %, botones vacíos 30,6 %, sin `lang` 13,5 %. Estos seis tipos suman ~96 % de los errores detectados. https://webaim.org/projects/million/

## 10. Checklist corta para revisión de código (resumen propio)

- [ ] HTML nativo primero; cero `div`/`span` clicables.
- [ ] Cada input con `<label>` visible; `autocomplete` en datos personales; `type`/`inputmode` adecuados.
- [ ] Errores en texto junto al campo + `aria-invalid` + `aria-describedby`; nada solo por color.
- [ ] Contraste: texto 4.5:1, texto grande y UI 3:1 (bordes de input, iconos, foco).
- [ ] `:focus-visible` con indicador claro; `scroll-padding` bajo cabeceras/barras fijas.
- [ ] Objetivos ≥ 24×24 px (y 44–48 px en táctil por criterio de diseño, ver `patrones.md` §4.4).
- [ ] Arrastrar siempre con alternativa sin arrastre.
- [ ] Modales: foco dentro, Esc, devolver el foco, `aria-labelledby`.
- [ ] Estados asíncronos en `role="status"`/`alert` montado de antemano.
- [ ] Login: se puede pegar, gestores de contraseñas funcionan, OTP con `one-time-code`.
- [ ] No volver a pedir datos ya dados en el mismo flujo.
- [ ] `<html lang="es">`, `<title>` por ruta, un `h1`, encabezados sin saltos.
- [ ] Reflow a 320 px sin scroll horizontal (salvo tablas de datos).
- [ ] axe sin errores **y** pasada de teclado **y** prueba rápida con lector.
