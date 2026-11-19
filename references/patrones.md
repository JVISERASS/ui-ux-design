# Patrones de interacción con evidencia

Leer al diseñar o revisar formularios, estados (carga, vacío, error, confirmación), tablas y dashboards, navegación móvil, microcopy o cualquier cosa que roce un patrón engañoso. §7 es el resumen de reglas. Investigado el 03/10/2026; todo parafraseado; lo no comprobado va marcado **UNVERIFIED**; donde las fuentes chocan, se dice.

## 1. Formularios

### 1.1 Posición de la etiqueta: arriba
- Penzo (UXmatters, 12/07/2006), eye-tracking: con etiqueta **encima** del campo, el salto ocular etiqueta→campo fue de ~50 ms, frente a ~170–240 ms con etiqueta a la izquierda alineada a la derecha y ~500 ms con etiqueta a la izquierda alineada a la izquierda. Poner la etiqueta en negrita encima la empeoró (~80 ms). Recomendación: arriba; si va a la izquierda, alineada a la derecha. https://www.uxmatters.com/mt/archives/2006/07/label-placement-in-forms.php
- NN/g (Whitenton, 2016): etiqueta pegada a su campo, encima en móvil y en formularios cortos; al lado solo en formularios de escritorio muy largos. https://www.nngroup.com/articles/web-form-design/
- **Nunca el placeholder como etiqueta**: desaparece al escribir, algunos lectores de pantalla no lo leen y suele no pasar el contraste (GOV.UK, NN/g). https://design-system.service.gov.uk/components/text-input/

### 1.2 Una sola columna
- NN/g: un campo por fila para mantener el flujo vertical; excepción: campos cortos y lógicamente unidos (CP + ciudad). https://www.nngroup.com/articles/web-form-design/
- Baymard también desaconseja los formularios a varias columnas: https://baymard.com/blog/avoid-multi-column-forms (titular comprobado; cifras internas **UNVERIFIED**).

### 1.3 Cuándo validar en línea
- **Consenso**: no validar mientras se escribe; validar al salir del campo (blur) o al enviar; **quitar el error en cuanto el valor ya es válido** (por pulsación).
  - NN/g (Krause, 2019, revisado 12/2024): no mostrar el error hasta que el usuario ha terminado el campo y ha pasado al siguiente; el mensaje junto al campo, no escondido en un tooltip; el resumen arriba no puede ser el único aviso; si un error se repite 3+ veces, el problema es el diseño. https://www.nngroup.com/articles/errors-forms-design-guidelines/
  - Baymard (09/01/2024): el 31 % de los sitios no tiene validación en línea; la validación prematura frustra ("¡todavía no he terminado de escribir el email!"); validar en blur o al llegar a la longitud correcta (p. ej. CP); retirar el error al instante al corregir; marca de "correcto" en campos propensos a erratas. https://baymard.com/blog/inline-form-validation
  - Friedman, Smart Interface Design Patterns (8/02/2022): **"reward early, punish late"**: si el campo estaba en error, se valida en cada pulsación para quitarlo en cuanto esté bien; si estaba bien, solo se vuelve a validar en blur. Los campos vacíos, solo al enviar. En formularios cortos, validar solo al enviar es válido (pulsar "Enviar" es la señal más clara de "he terminado"). Ojo a los saltos de layout al aparecer los mensajes (reservar el hueco). Dar salida si el validador rechaza un valor correcto. https://smart-interface-design-patterns.com/articles/inline-validation-ux/
- GOV.UK valida al enviar y conserva todos los datos, también los correctos. https://design-system.service.gov.uk/components/error-message/

### 1.4 Mensajes de error
- NN/g (14/05/2023) — **visibilidad**: junto al campo, con alto contraste, texto e icono (no solo color), gravedad proporcional. **Comunicación**: lenguaje llano, sin códigos, decir exactamente qué pasó y cómo arreglarlo, tono sin culpa (evitar "inválido" o "ilegal"). **Eficiencia**: conservar lo que escribió el usuario, sugerir la corrección, enlazar a la explicación larga. https://www.nngroup.com/articles/error-message-guidelines/
- GOV.UK — redacción: decir qué pasó y cómo arreglarlo, con las mismas palabras que la etiqueta; prohibidos "inválido", "prohibido", "por favor", "lo sentimos", "ups", la jerga y los genéricos ("Ha ocurrido un error", "Campo obligatorio"). Patrones: vacío → "Escribe tu [campo]"; longitud → "[Campo] debe tener [X] caracteres o menos"; formato → "Escribe [campo] con el formato correcto" (mejor aún, di cuál). Mismo texto en el campo y en el resumen; prefijo oculto "Error:" para lectores de pantalla. https://design-system.service.gov.uk/components/error-message/

### 1.5 Obligatorio y opcional — las fuentes chocan
- GOV.UK: pedir solo lo necesario, marcar lo **opcional** con "(opcional)" y **no usar asteriscos**. https://design-system.service.gov.uk/patterns/question-pages/
- NN/g (Budiu, 2019): marcar **todos** los obligatorios con asterisco (al principio de la etiqueta, con contraste suficiente); marcar también los opcionales ayuda; las instrucciones de cabecera ("* obligatorio") no se leen. https://www.nngroup.com/articles/required-fields/
- Baymard (2021): marcar **ambos** (asterisco en obligatorios y "(opcional)" en opcionales); solo el 14 % de los sitios lo hacía; marcar solo los opcionales llevó a que el 32 % de los usuarios se topara con errores de validación. https://baymard.com/blog/required-optional-form-fields
- Síntesis para el agente: minimizar los opcionales; si casi todo es obligatorio, marcar solo "(opcional)"; si hay mezcla, marcar los dos; poner siempre `required` en el HTML.

### 1.6 Tipos de input, `autocomplete` y no partir campos
- `autocomplete` con el token correcto: `name`, `given-name`, `family-name`, `email`, `tel`, `street-address`, `postal-code`, `address-level2` (ciudad), `country`, `organization`, `username`, `current-password`, `new-password`, `one-time-code`, `bday`. Los gestores de contraseñas ignoran `autocomplete="off"` en el login. https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/autocomplete — además lo exige WCAG 1.3.5.
- Números: GOV.UK desaconseja `type="number"` (incrementos accidentales con la rueda o las flechas, mal feedback); usar `inputmode="numeric"` para enteros e `inputmode="decimal"` para decimales, con `spellcheck="false"`. Ancho del campo proporcional a lo que se espera (un CP no ocupa todo el ancho). https://design-system.service.gov.uk/components/text-input/
- **No partir entidades únicas** (teléfono, fecha, IBAN, nombre) en varios campos: más toques, ambigüedad sobre qué parte es obligatoria y choque con cómo lo piensa el usuario. Baymard (2013, móvil) https://baymard.com/blog/mobile-form-usability-single-input-fields. Nombre: el 42 % escribió el nombre completo en "Nombre" al menos una vez; con un único campo "Nombre completo" solo el 4 % dudó (cifras del resumen de búsqueda de baymard.com, artículo concreto **UNVERIFIED**).
- Para 2–3 opciones, radios mejor que un desplegable (NN/g 2016).
- Sin botones de "Borrar" o "Restablecer" (NN/g 2016).

### 1.7 Botones
- Un verbo, o verbo + objeto, que diga lo que pasará: "Borrar carpeta" mejor que "Borrar"; un verbo concreto mejor que "Siguiente" o "Aceptar"; el texto refleja el estado al que se pasa, no el actual. NN/g, UI Copy: https://www.nngroup.com/articles/ui-copy/
- GOV.UK: mayúscula solo inicial ("Guardar y continuar"), **un solo botón principal por página**, evitar botones deshabilitados (poco contraste y no explican el porqué: mejor dejar pulsar y mostrar el error), evitar el doble envío (cliente y servidor), botón de aviso o destructivo solo para lo grave e irreversible. https://design-system.service.gov.uk/components/button/

### 1.8 "Una cosa por página" (GOV.UK)
- Una pregunta por página en procesos largos o poco frecuentes; la etiqueta o `legend` hace de `h1`; enlace "Atrás" siempre (y que el botón Atrás del navegador funcione); botón "Continuar" alineado a la izquierda; agrupar preguntas solo si la investigación lo respalda. https://design-system.service.gov.uk/patterns/question-pages/
- Aplicación a B2B (criterio propio): en herramientas de uso diario los usuarios expertos prefieren densidad; "una cosa por página" sirve para flujos esporádicos (alta, configuración inicial, primer documento), no para la edición de todos los días.

## 2. Estados: carga, vacío, error, confirmación

### 2.1 Tiempos de respuesta (Nielsen, 1993/2014; Miller 1968, Card et al. 1991)
- **0,1 s**: se percibe instantáneo; basta con mostrar el resultado.
- **1 s**: el pensamiento no se corta aunque se note el retraso; por encima conviene una señal de que algo pasa.
- **10 s**: límite de la atención; más allá, indicador de progreso con porcentaje y forma de cancelar. https://www.nngroup.com/articles/response-times-3-important-limits/

### 2.2 Esqueleto, spinner o barra de progreso
- NN/g (Sherwin, 2014): < 1 s sin indicador (un spinner que parpadea molesta); 2–10 s animación en bucle; > 10 s porcentaje completado o tiempo estimado + cancelar; texto explicativo ("Cargando comentarios…"); no decir "no pulses dos veces". https://www.nngroup.com/articles/progress-indicators/
- NN/g (Tankala, 2023, revisado 09/2026): **esqueleto** para cargas de página o vista completa de 2–10 s (prepara el modelo mental del layout y parece más rápido); **spinner** para un solo módulo; **barra de progreso** para procesos largos (subidas, importaciones). Evitar el esqueleto que solo pinta cabecera y pie. https://www.nngroup.com/articles/skeleton-screens/
- Corolarios (criterio propio): el esqueleto debe coincidir con el layout real (sin saltos, CLS); para guardar, feedback optimista o en el propio botón ("Guardando…"); anunciarlo con `role="status"` (`accesibilidad.md` §8).

### 2.3 Estados vacíos (NN/g, Kaplan, 2021)
1. Comunicar el estado: que no se confunda "vacío" con "cargando" o "error" ("No hay registros para este rango de fechas"); no decir "sin resultados" antes de que termine la carga.
2. Enseñar: qué aparecerá aquí y cómo llenarlo.
3. Dar el camino directo: botón "Crear…", importar o datos de ejemplo.
https://www.nngroup.com/articles/empty-state-interface-design/
- Distinguir (criterio propio): vacío de primera vez (enseñar + CTA), vacío por filtros (decir qué filtro y "Quitar filtros"), vacío por permisos (quién puede darlos) y error (qué pasó + reintentar).

### 2.4 Confirmar o deshacer
- NN/g: confirmar solo lo grave o irreversible; si se pide confirmación para todo, la gente la acepta sin leer. Ser específico (qué se borra, cuántos, nombres) y nada de "¿Seguro?"; botones con la acción ("Borrar factura" / "Conservar") en vez de Sí/No; **mejor deshacer que confirmar** cuando se pueda; para lo muy peligroso, una acción no rutinaria (escribir el nombre). https://www.nngroup.com/articles/confirmation-dialog/
- En el modal destructivo, el foco inicial va al botón menos destructivo (APG, `accesibilidad.md` §8).
- WCAG 3.3.4: en operaciones legales o financieras, hacerlas reversibles, verificables o con revisión antes de confirmar.

## 3. Tablas y aplicaciones B2B con muchos datos

### 3.1 Alineación y cifras
- Números alineados a la derecha cuando se comparan columnas (GOV.UK, clases `--numeric`); texto a la izquierda; cabecera con la misma alineación que su columna; `<caption>` como título; `scope` en los `<th>`. https://design-system.service.gov.uk/components/table/
- **Cifras tabulares**: `font-variant-numeric: tabular-nums` (todas las cifras del mismo ancho, así se alinean por columnas); `lining-nums` en cifras de tabla. https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/font-variant-numeric
- Mismo número de decimales en toda la columna y unidad en la cabecera, no en cada celda (criterio propio, habitual en tipografía de datos; **UNVERIFIED** como recomendación de NN/g).

### 3.2 Estructura y tareas (NN/g, Laubheimer, 2022)
- Primera columna con un identificador legible (nombre o código humano, no un UUID).
- Columnas por importancia y las relacionadas juntas.
- **Cabecera fija** y primera columna fija en tablas grandes.
- Ayudas para seguir la fila: bordes, cebreado o resaltado al pasar el ratón.
- Ocultar y reordenar columnas, con indicación de qué hay oculto.
- Ordenar y filtrar visibles y claros, y que se vea qué filtros están activos.
- Editar un registro en un panel lateral no modal mejor que en un modal que tapa el contexto.
- Acciones en lote con casillas y "Seleccionar todo".
- No depender del arrastre para reordenar (alternativa de menú; WCAG 2.5.7).
https://www.nngroup.com/articles/data-tables/
- Acciones de fila (criterio propio + WCAG): 1–2 visibles como botones con texto o icono con nombre accesible, el resto en un menú "⋯" con `aria-label` que incluya la fila ("Acciones de Pedido 1042"); que no aparezcan solo al pasar el ratón (en táctil no existe el hover).
- Densidad: ofrecer compacta/cómoda en herramientas expertas — **UNVERIFIED** como recomendación explícita de NN/g en este artículo; aparece en Smart Interface Design Patterns (curso de pago, no comprobado).

### 3.3 Tablas en móvil (NN/g, Schade, 2017)
- Legible sin zoom; con contenido complejo, quizá solo 2 columnas.
- Cabeceras fijas; si hay scroll horizontal, **congelar la primera columna** y señalar que hay más (corte visible o flechas).
- No obligar a girar el móvil.
- Dejar elegir columnas y filas, acordeones por grupos, priorizar el contenido.
https://www.nngroup.com/articles/mobile-tables/
- Tabla → tarjetas (criterio propio, coherente con lo anterior): cuando la tarea es revisar registros de uno en uno, cada fila pasa a ser una tarjeta (identificador como título, 2–4 campos clave, importe alineado y acción principal); cuando la tarea es **comparar** valores entre filas, mejor tabla con scroll horizontal y primera columna fija. WCAG 1.4.10 exime a las tablas de datos del reflow.

### 3.4 Dashboards (NN/g, Laubheimer, 2017)
- Un dashboard da información de un vistazo para actuar rápido sobre **una** tarea; no es un portal.
- Codificar con atributos preatentivos: **posición y longitud** para cantidades (barras, líneas, dispersión); el color solo para categorías o alertas, nunca como única pista (daltonismo).
- Evitar tartas, donuts, treemaps, velocímetros y 3D: el ojo compara mal áreas y ángulos.
https://www.nngroup.com/articles/dashboards-preattentive/
- "Pocos KPI y con contexto" (criterio propio, en línea con lo anterior): cada cifra con su comparación (contra el periodo anterior, el objetivo o el presupuesto), la unidad y el periodo; sin un muro de tarjetas con números sueltos. Que el número exacto de KPI sea 5–7: **UNVERIFIED**, no hay fuente sólida.

## 4. Navegación y móvil

### 4.1 Hamburguesa (NN/g, Pernice y Budiu, 2016)
- La navegación oculta redujo el descubrimiento de contenido más de un 20 %; en escritorio la tarea fue ≥ 39 % más lenta y en móvil un 15 % más lenta; dificultad percibida mayor (2,6 frente a 2,1). En escritorio se usó el menú oculto en el 27 % de los casos, frente al 48–50 % de la navegación visible.
- Recomendación: en escritorio **no** esconder la navegación principal; en móvil, si hay 4 destinos o menos, enseñarlos (barra inferior o pestañas); esconder solo lo que no cabe, con enlaces en la propia página a lo importante. https://www.nngroup.com/articles/hamburger-menus/

### 4.2 Barra inferior
- Material: entre 3 y 5 destinos de importancia parecida; con menos de 3, pestañas; con 3, icono + texto en todos; con 4–5, texto como mínimo en el activo y recomendado en todos; presente en todas las pantallas de primer nivel. https://material.io/components/bottom-navigation (resumen vía búsqueda; ficha de M3 no comprobada directamente: **UNVERIFIED** en detalle).
- Criterio propio: siempre icono + texto (un icono suelto es ambiguo), estado activo con `aria-current="page"` y espacio seguro inferior (`env(safe-area-inset-bottom)`).

### 4.3 Zona del pulgar — matizar el mito
- Hoober (UXmatters, 18/02/2013): 1.333 observaciones en la calle; de las 780 en las que se tocaba la pantalla: 49 % a una mano, 36 % sujetando con una y tocando con la otra, 15 % con los dos pulgares; a una mano, el 67 % con el pulgar derecho. Los mapas de alcance (verde/amarillo/rojo) salen de ahí. https://www.uxmatters.com/mt/archives/2013/02/how-do-users-really-hold-mobile-devices.php
- El propio Hoober corrigió después ("Design for Fingers, Touch, and People", UXmatters, 2017; libro *Touch Design for Mobile Interfaces*, Smashing, 2021): la gente cambia de agarre según la tarea y prefiere tocar y mirar el **centro** de la pantalla; la precisión es peor en los bordes y las esquinas. Recomendación: contenido y acciones principales en el centro, secundarias en los bordes (pestañas y barras), terciarias en menús. https://www.smashingmagazine.com/printed-books/touch-design-for-mobile-interfaces y https://addyosmani.com/blog/touch-friendly-design/ (resúmenes secundarios; la cifra "75 % toca solo con el pulgar" es **UNVERIFIED**).
- Para el agente: no justificar decisiones con "la zona del pulgar" de 2013; sí con "las acciones frecuentes en zonas alcanzables y grandes, y nada crítico en las esquinas superiores".

### 4.4 Tamaño de los objetivos táctiles
| Fuente | Mínimo | Nota |
|---|---|---|
| WCAG 2.2 · 2.5.8 (AA) | 24×24 px CSS o espaciado equivalente | requisito legal mínimo — https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html |
| WCAG 2.5.5 (AAA) | 44×44 px CSS | nivel mejorado (2.1/2.2) |
| Apple HIG | 44×44 pt (iOS/iPadOS) | https://developer.apple.com/design/human-interface-guidelines/accessibility |
| Material / Android | 48×48 dp (≈ 9 mm), separados ≥ 8 dp | el área táctil puede ser mayor que el icono (icono de 24 dp con relleno hasta 48) — https://support.google.com/accessibility/android/answer/7101858 |
- Regla para el agente: 24 px es el suelo de cumplimiento; **diseñar a 44–48 px** en táctil y ampliar el área con relleno o pseudo-elemento, no con el tamaño visual.

## 5. Microcopy y escaneo

- **Krug, *Don't Make Me Think***, cap. 5 "Omit needless words" (tomado de Strunk y White): tercera ley, quitar la mitad de las palabras de cada página y luego la mitad de lo que queda; los objetivos son la "happy talk" (texto de bienvenida que no dice nada) y las instrucciones que nadie lee: lo mejor es que la interfaz se explique sola. https://www.oreilly.com/library/view/dont-make-me/0789723107/ch06.html y https://cscie12.dce.harvard.edu/lecture_notes/2024-fall/20241016/slide101.html (resúmenes secundarios; la idea central de Krug es "no me hagas pensar": cada pantalla obvia o, como mínimo, autoexplicativa).
- **Lo importante al principio** (Nielsen, 2009): en listas, enlaces y titulares se leen ~2 palabras (~11 caracteres) antes de decidir; empezar por el término que importa al usuario y la acción, con nombres convencionales; nada de "Introducción a…" ni palabras inventadas. https://www.nngroup.com/articles/first-2-words-a-signal-for-scanning/
- **Patrón en F** (Pernice, 2006, revisado 2017): sobre texto sin formato, se lee la parte de arriba, otra franja más corta y luego se baja por el margen izquierdo; lo de la derecha se pierde. Se combate con lo clave en el primer párrafo, subtítulos que empiezan por palabras con información, listas y negritas puntuales. https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content/
- **Patrón de tarta de capas** (Pernice, 2019): se leen sobre todo los encabezados y se baja al cuerpo solo donde interesa; es el escaneo eficaz y se provoca con subtítulos descriptivos, visualmente distintos y coherentes, que empiecen por lo importante, y con el contenido troceado. Otros patrones: a saltos (buscar algo concreto) y de compromiso (leer entero cuando interesa). https://www.nngroup.com/articles/layer-cake-pattern-scanning/
- **Lenguaje llano** (GOV.UK + NN/g): palabras del usuario, no de la base de datos; frases cortas; voz activa; segunda persona; sin jerga interna ni códigos. Botones con verbos (sección 1.7). Errores con las mismas palabras que la etiqueta (sección 1.4).
- Microcopy en español (criterio propio para la skill): tuteo coherente con el producto; mayúscula solo inicial; sin "Por favor" en los botones; cifras con el formato de España (1.234,56 €).

## 6. Patrones engañosos (dark patterns)

- Catálogo de deceptive.design (creado por Harry Brignull, que acuñó "dark patterns" en 2010 — autoría **UNVERIFIED** en esta pasada; la página solo atribuía el diseño web a Alastair Driver): https://www.deceptive.design/types
  - Colar cosas (*sneaking*), acción forzada, difícil de cancelar, preselección, obstrucción, suscripción oculta, costes ocultos, redacción con trampa, interferencia visual, prueba social falsa, urgencia falsa, insistencia (*nagging*), escasez falsa, anuncios disfrazados, *confirmshaming* (culpabilizar al que dice que no), impedir la comparación, diseño adictivo y confusión de moneda.
- Reglas para el agente: la opción de rechazar o cancelar con el mismo peso visual que la de aceptar; nada premarcado que beneficie solo al negocio; darse de baja tan fácil como darse de alta; precios completos desde el principio; sin cuentas atrás falsas; el "No, gracias" en tono neutro.
- **DSA, Reglamento (UE) 2022/2065, art. 25**: prohíbe a los **proveedores de plataformas en línea** diseñar u organizar su interfaz de forma que engañe o manipule a los usuarios o les impida decidir con libertad e información. Excluye las prácticas ya cubiertas por la Directiva 2005/29/CE (prácticas comerciales desleales) y por el RGPD. La Comisión puede publicar directrices sobre: dar más protagonismo a una opción, pedir varias veces que se elija algo ya elegido y hacer la baja más difícil que el alta. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32022R2065
  - Alcance: solo plataformas en línea (marketplaces, redes…); un SaaS B2B normalmente no lo es, pero la Directiva 2005/29/CE (en España, la Ley de Competencia Desleal) sí aplica a las prácticas con consumidores — aplicación española concreta **UNVERIFIED**.
- **Digital Fairness Act**: propuesta de la Comisión todavía no presentada a septiembre de 2026; se apuntaba al 11/11/2026 para el Colegio de Comisarios; incluiría patrones engañosos, diseño adictivo y personalización desleal (B2C). https://newsletter.digitalfairnessact.com/p/digital-fairness-act-targeted-for y https://www.europarl.europa.eu/legislative-train/theme-protecting-our-democracy-upholding-our-values/file-digital-fairness-act — fecha **UNVERIFIED** (fuente no oficial).

## 7. Resumen de reglas para la skill (criterio propio)

1. Etiqueta encima, una columna, sin placeholder como etiqueta, `autocomplete` y `inputmode` correctos, sin partir entidades.
2. Validar en blur o al enviar; quitar el error al corregir ("reward early, punish late"); mensaje junto al campo que diga qué pasó y cómo arreglarlo; conservar lo escrito.
3. Marcar "(opcional)"; si se mezclan, marcar los dos tipos; `required` en el HTML.
4. Botones con verbo + objeto; un solo botón principal; evitar los deshabilitados; evitar el doble envío.
5. < 1 s nada; 1–10 s esqueleto (página) o spinner (módulo); > 10 s progreso con porcentaje y cancelar.
6. Vacío = estado + explicación + acción; distinguir vacío, filtrado, sin permisos y error.
7. Deshacer mejor que confirmar; confirmar solo lo irreversible, con botones específicos.
8. Tablas: números a la derecha con `tabular-nums`, cabecera fija, identificador legible primero, filtros visibles, acciones en lote y edición en panel lateral; en móvil, tarjetas para revisar y tabla con columna fija para comparar.
9. Dashboard: una tarea, barras y líneas, color con significado, cada KPI con su comparación.
10. Navegación visible en escritorio; barra inferior de 3–5 destinos con texto en móvil; objetivos de 44–48 px (suelo legal 24 px); acciones clave lejos de las esquinas superiores.
11. Textos: lo importante al principio, la mitad de palabras, subtítulos que se puedan escanear y lenguaje del usuario.
12. Ningún patrón del catálogo de deceptive.design; rechazar tan fácil como aceptar.
