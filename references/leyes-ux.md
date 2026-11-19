# Leyes de UX (Jon Yablonski): las 30 del sitio, el libro y sus malos usos

Leer cuando haya que justificar una decisión con una ley, revisar un flujo (formularios, onboarding, checkout, carga) o detectar una ley mal aplicada. §3 es el mapa por situación y §5 la lista de exageraciones.

Fecha: 03/10/2026. Todo parafraseado. Marcas: **[VERIFICADO]** = contrastado con fuente primaria o con dos fuentes; **[SITIO]** = lo dice lawsofux.com y no lo he contrastado más; **UNVERIFIED** = no comprobado, no citar como hecho.

## 0. Fuentes principales

- Sitio: https://lawsofux.com (cada ley en `https://lawsofux.com/<slug>/`, con versión `index.md`). Licencia CC BY-NC-ND 4.0.
- Libro 2.ª ed.: https://oreilly.com/library/view/laws-of-ux/9781098146955 · página del autor: https://jonyablonski.com/articles/2024/laws-of-ux-the-2nd-edition/ · https://lawsofux.com/book/
- Índice detallado 2.ª ed.: https://www.managementboek.nl/boek/9781098146962/laws-of-ux-jon-yablonski · Google Books 1.ª ed. (id BuneDwAAQBAJ) y 2.ª ed. (id 3xHwEAAAQBAJ).
- NN/g: tiempos de respuesta https://www.nngroup.com/articles/response-times-3-important-limits/ · Fitts https://www.nngroup.com/articles/fitts-law/ · Peak-End https://www.nngroup.com/articles/peak-end-rule/ · estética-usabilidad https://www.nngroup.com/articles/aesthetic-usability-effect/ · Hick (vídeo) https://www.nngroup.com/videos/hicks-law-long-menus/ · Jakob https://nngroup.com/videos/jakobs-law-internet-ux/ y https://jakobnielsenphd.substack.com/p/jakobs-law
- Doherty & Thadhani 1982 (escaneo): https://archive.computerhistory.org/resources/access/text/2024/03/102751398-05-01-acc.pdf

## 1. El libro

**Ediciones [VERIFICADO]**
- 1.ª: O'Reilly, 21/04/2020, ~152 págs. Subtítulo «Using Psychology to Design Better Products & Services».
- 2.ª: O'Reilly, enero de 2024 (Google Books: 23/01/2024; el post del autor la anuncia en marzo de 2024 — probablemente el papel), ~186 págs. ISBN 9781098146962.

**Índice (10 leyes + 2 capítulos aplicados)**
- 1.ª ed.: 1 Jakob · 2 Fitts · 3 Hick · 4 Miller · 5 Postel · 6 Peak-End · 7 Estética-usabilidad · 8 Von Restorff · 9 Tesler · 10 Doherty · 11 *With Power Comes Responsibility* · 12 *Applying Psychological Principles in Design*.
- 2.ª ed.: igual pero **Miller pasa al 3 y Hick al 4**, y los aplicados se invierten: **11 Applying Psychological Principles in Design · 12 With Power Comes Responsibility** (la ética cierra el libro).
- Prefacio 2.ª ed. con «A Brief History of Psychology and Design»: Gestalt → factores humanos → HCI → diseño UX.
- Cada capítulo de ley: Overview → Origins → Examples → Conclusion. En la 2.ª ed. añade conceptos psicológicos de fondo, «consideraciones» y técnicas de investigación asociadas.
- **Novedades 2.ª ed. [VERIFICADO, web del autor]**: conceptos *Paradox of Choice*, *Complexity Bias*, *Flow*; consideraciones *The Human Factor*, *Accessibility*, *Paradox of the Active User*, *Personalization*; técnicas *Contextual Inquiry*, *User Interviews*, *Eye-tracking*. Ejemplos actualizados (menciona LLM, imagen generativa, computación espacial). En qué capítulo cae cada uno: UNVERIFIED (plausible: Choice/Paradox → Hick; Flow → Doherty; Complexity bias → Tesler; Active user → Tesler/Jakob).

**El sitio frente al libro.** El sitio tiene 30 entradas cortas (resumen, takeaways, origen, lecturas); el libro desarrolla solo 10 leyes a fondo, con ejemplos deconstruidos de apps, y los dos capítulos aplicados que el sitio no tiene. Las otras ~20 entradas del sitio (Gestalt, sesgos, Pareto, Parkinson…) en el libro aparecen como conceptos relacionados o no aparecen.

**Cap. «Applying Psychological Principles in Design» (paráfrasis de su estructura)** — secciones: Building Awareness · Visibility · Show-and-Tell · Design Principles · Defining Your Principles · Best Practices · Connecting Principles to Laws.
- Idea: conocer las leyes no basta; hay que convertirlas en conocimiento compartido del equipo. Hacerlas *visibles* (pósteres, tarjetas, wiki) y explicarlas en revisiones con ejemplos (show-and-tell).
- Escribir **principios de diseño propios** del producto (pocos, memorables, accionables, que sirvan para decidir entre dos opciones y no sean obviedades) y **enlazar cada principio con las leyes** que lo fundamentan, para que las decisiones tengan un porqué común. Esto es el «playbook» de equipo.
- La lista de «buenas prácticas» concreta del capítulo: UNVERIFIED (no pude leer el texto).

**Cap. «With Power Comes Responsibility» (ética)** — secciones: How Technology Shapes Behavior (recompensas variables intermitentes, bucles infinitos, afirmación social, personalización, valores por defecto, (falta de) fricción, reciprocidad, dark patterns) · Why Ethics Matter (buenas intenciones con consecuencias imprevistas; el imperativo ético) · Slow Down and Be Intentional (pensar más allá del camino feliz; diversificar equipos y pensamiento; mirar más allá de los datos; abrazar la fricción).
- Tesis: las mismas leyes que hacen un producto fácil sirven para manipular (scroll infinito, notificaciones tipo tragaperras, defaults que favorecen al negocio, falsa urgencia). El diseñador responde de los efectos, no solo de la intención.
- Prácticas: diseñar también los caminos de error, abuso y salida; equipos diversos para ver daños que uno no ve; no optimizar solo métricas de engagement; añadir fricción deliberada donde protege al usuario (borrar, pagar, compartir datos).

## 2. Las 30 entradas de lawsofux.com (lista completa a 03/10/2026)

Orden y categoría del sitio: «Theory» (heurísticas y modelos) o «Psychology» (conceptos de apoyo). Agrupo para el uso.

### 2.1 Modelos predictivos y heurísticas

**Jakob (Teoría)** — La gente pasa casi todo su tiempo en otros productos y espera que el tuyo funcione igual.
- Acciones: usar convenciones (carrito arriba a la derecha, logo → inicio, controles nativos); innovar en el valor, no en los patrones; en rediseños, dejar volver a la versión vieja un tiempo (caso YouTube 2017).
- Origen: Jakob Nielsen, 2000 [VERIFICADO]. Relacionado: *Mental Model* (Craik 1943).
- Aviso: no es «copia a la competencia»; las convenciones del sector (ERP, CAD) pesan más que las de la web general.

**Fitts (Teoría)** — El tiempo para alcanzar un objetivo crece con la distancia y decrece con su tamaño.
- Acciones: objetivos táctiles grandes y separados; la acción cerca de donde está la atención (Enviar junto al último campo); etiqueta + icono clicables juntos; menús que se abren junto a su disparador.
- Origen: Paul Fitts, 1954. Fórmula NN/g: T = a + b·log₂(2D/W) (variante de Shannon/MacKenzie: log₂(D/W+1)) [VERIFICADO].
- Bordes y esquinas son «infinitos» con ratón (menú de macOS), **pero no en táctil**: ahí no ayudan y pueden empeorar (NN/g) [VERIFICADO].
- Tamaños: WCAG 2.2 AA 24×24 CSS px mínimo (2.5.8); AAA/Apple 44×44 pt; Material 48×48 dp. (Fuente WCAG/HIG, no del sitio.)

**Hick / Hick-Hyman (Teoría)** — El tiempo de decisión crece con el número y la complejidad de las opciones.
- Acciones: menos opciones donde el tiempo importa; dividir tareas largas en pasos; destacar la opción recomendada; onboarding progresivo; sin simplificar hasta la abstracción.
- Origen: W. E. Hick y R. Hyman, 1952-53. RT = a + b·log₂(n+1) [VERIFICADO].
- **Sobreuso**: vale para elegir 1 de n estímulos conocidos y equiprobables. Si el usuario tiene que *buscar* en una lista que no conoce, el tiempo es casi lineal (escaneo), no logarítmico. Una lista ordenada (alfabética, numérica) o agrupada permite búsqueda por subdivisión. No justifica por sí sola «menús de máximo N» ni «un menú grande es mejor que submenús» (Wikipedia, NN/g vídeo 2018 de Katie Sherwin).

**Miller (Teoría)** — Se dice que retenemos ~7±2 elementos en memoria de trabajo.
- Acciones: agrupar (chunking) números, datos y contenido; **no usar el 7 para limitar menús o pestañas**; recordar que varía según conocimiento previo y contexto.
- Origen: George A. Miller, 1956, «The Magical Number Seven, Plus or Minus Two».
- **Visión moderna [VERIFICADO]**: Cowan (2001, *Behavioral and Brain Sciences*): el límite central es **~4 fragmentos (3-5)**; el «siete» de Miller era en parte recurso retórico y su aporte central era el chunking.
- **Mal uso típico**: «la navegación debe tener 7 elementos». Un menú está *a la vista*: es reconocimiento, no recuerdo; el límite de memoria aplica a lo que el usuario debe *retener* entre pantallas (códigos, comparaciones, instrucciones), no a lo que ve. El propio sitio advierte contra ese uso.

**Postel / principio de robustez (Teoría)** — Sé liberal con lo que aceptas y conservador con lo que envías.
- Acciones: aceptar formatos variados (teléfono con o sin espacios, fechas, «1.500,00»), normalizar por dentro, mostrar el valor interpretado y dar feedback claro; límites explícitos de entrada.
- Origen: Jon Postel, especificación de TCP (RFC 760/793, 1980-81).
- **Aviso**: en protocolos la idea está cuestionada (RFC 9413, 2023, borrador titulado «postel-was-wrong»): tolerar entradas malformadas en silencio fosiliza errores. En UX: aceptar con flexibilidad **sí**, adivinar en silencio **no** — si la interpretación es ambigua, mostrarla o preguntar.

**Peak-End (Teoría)** — Juzgamos una experiencia por su pico emocional y su final, no por la media.
- Acciones: cuidar el momento de más valor y el cierre (confirmación de envío/pago con carácter, Mailchimp); vigilar los picos negativos (errores, esperas: Uber); acabar sin pop-ups que bloqueen la salida.
- Origen: Kahneman, Fredrickson, Schreiber, Redelmeier 1993 (agua fría: 60 s a 14 °C frente a 60 s + 30 s a 15 °C; se prefería repetir la larga) [VERIFICADO]. También colonoscopia, Redelmeier & Kahneman 1996.
- Los negativos se recuerdan con más viveza (sesgo de negatividad). NN/g (Lexie Kane, 2018) lo confirma.

**Estética-usabilidad (Teoría)** — Lo bonito se percibe como más usable.
- Acciones: invertir en acabado visual porque compra tolerancia ante fallos menores; **en tests, no fiarse de lo que se dice: mirar lo que se hace** (la estética tapa problemas).
- Origen: Kurosu & Kashimura, Hitachi, 1995: 26 variantes de cajero, 252 participantes; la estética correlaciona más con la facilidad *percibida* que con la real [VERIFICADO]. Tractinsky (1997/2000, «What is beautiful is usable») lo replicó en Israel [UNVERIFIED detalle].
- NN/g (Kate Moran, 2024): solo perdona fallos menores, no graves.

**Von Restorff / efecto de aislamiento (Teoría)** — Lo que difiere del resto se recuerda y se ve.
- Acciones: una sola acción principal destacada por pantalla; contención en el énfasis (si todo destaca, nada destaca, y lo destacado puede parecer anuncio); no depender solo del color (daltonismo); cuidado con movimiento (vestibular, `prefers-reduced-motion`).
- Origen: Hedwig von Restorff, 1933.

**Tesler / conservación de la complejidad (Teoría)** — Toda tarea tiene una complejidad irreducible: o la absorbe el sistema o el usuario.
- Acciones: que la absorba el sistema (valores por defecto inteligentes, autocompletar, cálculo automático); no diseñar para un usuario idealmente racional; ayuda contextual.
- Origen: Larry Tesler, Xerox PARC, mediados de los 80 (entrevista en *Designing for Interaction*, Saffer). Matiz de Tognazzini: al simplificar, la gente aborda tareas más complejas.
- Aviso: simplificar ocultando no elimina complejidad, la desplaza.

**Doherty (Teoría)** — La productividad se dispara cuando sistema y persona no se esperan; el sitio fija el umbral en <400 ms.
- Acciones: feedback inmediato; rendimiento percibido (UI optimista, skeletons, carga progresiva); animación durante procesos; barras de progreso; un retardo deliberado puede aumentar la confianza en procesos «serios» (cálculo, búsqueda).
- **Verificación del origen [VERIFICADO en el escaneo]**: Doherty & Thadhani, *The Economic Value of Rapid Response Time*, folleto/informe IBM GE20-0752-0, nov. 1982 (12 págs.; **no** un artículo del *IBM Systems Journal* como dice el sitio). Argumenta pasar de los 2 s de R. B. Miller (1968) a tiempo **subsegundo**; datos de Thadhani (1981): ~180 transacciones/hora con 3 s de respuesta frente a ~371 con 0,3 s (+106 %); otro caso: +35 % al bajar de 0,6 a 0,25 s. **En el texto no encontré una cifra de 400 ms como umbral ni la palabra «addicting»** (búsqueda en OCR; los «400» son ejes y número de usuarios). El «400 ms» es una cifra de la tradición posterior: tratarlo como orientativo.
- Era de mainframes y programadores; los datos son de IBM sobre sus propios sistemas (interés comercial).
- Referencia más sólida para web: **0,1 s / 1 s / 10 s** de Nielsen (1993, basada en Miller 1968 y Card et al. 1991) [VERIFICADO]: 0,1 s = instantáneo, sin feedback; 1 s = el flujo de pensamiento se mantiene; 2-10 s = indicador discreto (spinner); >10 s = indicador de porcentaje, estimación y opción de cancelar.

### 2.2 Gestalt (agrupación perceptiva)

Origen común: psicología de la Gestalt (Wertheimer, Köhler, Koffka, 1910-1920s). El sitio cuenta la anécdota de Wertheimer y las luces del paso a nivel (1910), que en realidad es el origen del **fenómeno phi** (movimiento aparente, 1912), no de la Prägnanz como tal (Wertheimer 1923) — [aviso propio, verificar si se cita].

**Proximidad** — Lo cercano se percibe como grupo. Acciones: más espacio *entre* grupos que *dentro* (etiqueta pegada a su campo, no equidistante); resultados de búsqueda separados por aire. Es la herramienta de agrupación más barata.

**Región común** — Lo que comparte un área delimitada se agrupa. Acciones: tarjetas, fondo o borde (o un filete fino si el sistema no usa sombras) para agrupar. Origen específico: Palmer 1992 [UNVERIFIED, conocimiento previo].

**Semejanza** — Lo parecido (color, forma, tamaño, orientación, movimiento) se percibe relacionado. Acciones: un estilo por función (todos los enlaces iguales y distintos del texto); no dar el mismo aspecto a cosas que hacen cosas distintas.

**Conexión uniforme** — Lo unido visualmente (líneas, marcos, flechas) se percibe más relacionado que lo cercano o parecido. Acciones: steppers con línea, relaciones en diagramas, grupos destacados con borde. Origen específico: Palmer & Rock 1994 [UNVERIFIED, conocimiento previo].

**Prägnanz (buena forma)** — Interpretamos lo ambiguo de la forma más simple posible. Acciones: iconos y formas simples; composiciones que se lean de un golpe; evitar siluetas ambiguas.

### 2.3 Conceptos psicológicos de apoyo

**Elección excesiva / choice overload (Teoría)** — Demasiadas opciones abruman y empeoran la decisión y la satisfacción.
- Acciones: comparación lado a lado (planes de precio); destacar un producto/plan recomendado; filtros y búsqueda antes de mostrar el catálogo.
- Origen: Alvin Toffler, *Future Shock*, 1970 («overchoice»); el popular estudio de las mermeladas es Iyengar & Lepper 2000 (24 frente a 6 variedades; compraban mucho más con 6). Schwartz, *The Paradox of Choice*, 2004.
- **Evidencia [VERIFICADO]**: meta-análisis Scheibehenne, Greifeneder & Todd 2010 (50 experimentos, N≈5.000): efecto medio ≈ 0 con mucha variación. Chernev, Böckenholt & Goodman 2015: aparece cuando la tarea es difícil, las opciones complejas/no alineadas, la preferencia incierta y el usuario quiere minimizar esfuerzo. → No es ley universal: reducir opciones cuando se dan esas condiciones; con expertos que saben lo que buscan, más surtido puede ayudar.

**Chunking (Psicología)** — Agrupar piezas en unidades con sentido. Acciones: IBAN/teléfono en bloques; contenido en módulos con jerarquía; formularios en secciones. Origen: Miller 1956.

**Sesgo cognitivo (Psicología)** — Errores sistemáticos de juicio por atajos mentales. Acciones: reconocer los propios (confirmación) en investigación y decisiones de equipo; no explotar los del usuario (ver ética). Origen: Tversky & Kahneman, 1972-1974.

**Carga cognitiva (Psicología)** — Recursos mentales que exige la interfaz. Intrínseca (la de la tarea) frente a extrínseca (la que añade el diseño: ruido, decoración, inconsistencias). Acciones: eliminar la extrínseca; no la intrínseca, solo repartirla. Origen: John Sweller, finales de los 80. Aviso: el sitio fecha en 1988 un artículo cuyo título («Cognitive Load Theory, Learning Difficulty, and Instructional Design») creo que es de 1994; el de 1988 es «Cognitive load during problem solving» — UNVERIFIED, comprobar antes de citar.

**Flow (Psicología)** — Inmersión con foco y disfrute cuando el reto encaja con la habilidad. Acciones: feedback constante de lo hecho; quitar fricción innecesaria; respuesta rápida; dificultad adaptada (ni aburrido ni frustrante). Origen: Mihály Csíkszentmihályi, 1975.

**Efecto gradiente de meta (Teoría)** — Se acelera el esfuerzo al acercarse a la meta.
- Acciones: barra de progreso visible; mostrar «te falta 1 paso»; **progreso dotado** (empezar con algo hecho).
- Origen: Clark Hull, 1932/1934 (ratas más rápidas cerca de la comida). Humanos: Kivetz, Urminsky & Zheng 2006, *JMR* (tarjeta de café: compran más seguido cerca del premio; el progreso ilusorio acelera) [VERIFICADO]. Progreso dotado: Nunes & Drèze 2006, *JCR* (lavado de coches: 8 casillas vacías frente a 10 con 2 sellos regalados → 19 % frente a 34 % de canje) [VERIFICADO].
- Aviso ético: el «progreso artificial» que recomienda el sitio se convierte en dark pattern si el progreso es falso.

**Modelo mental (Psicología)** — Representación comprimida de cómo creemos que funciona algo. Acciones: investigar el modelo del usuario (entrevistas, journey maps) y diseñar según él; usar sus palabras. Origen: Kenneth Craik, 1943.

**Navaja de Ockham (Teoría)** — Entre explicaciones equivalentes, la de menos supuestos. Acciones: quitar elementos hasta que quitar uno más rompa la función; mejor evitar la complejidad que gestionarla. Origen: Guillermo de Ockham (s. XIV).

**Paradoja del usuario activo (Teoría)** — Nadie lee el manual: se empieza a usar ya, aunque aprender antes ahorraría tiempo. Acciones: ayuda en contexto (tooltips, estados vacíos que enseñan, valores de ejemplo); diseñar para aprender usando; tolerar errores y permitir deshacer. Origen: Carroll & Rosson, 1987.

**Pareto 80/20 (Teoría)** — Pocas causas producen la mayoría de efectos. Acciones: priorizar los flujos que más usuarios usan; analítica para encontrar el 20 %. Origen: Vilfredo Pareto (tierra en Italia, ~1896); el nombre se lo dio Juran después. Aviso: 80/20 es metáfora, no proporción medida.

**Parkinson (Teoría)** — La tarea se expande hasta llenar el tiempo disponible. Acciones: que la tarea dure menos de lo que el usuario espera; autocompletar (direcciones, pagos); tiempo estimado visible. Origen: C. N. Parkinson, ensayo humorístico, *The Economist*, 1955 (no es un hallazgo empírico).

**Atención selectiva (Psicología)** — Atendemos solo a lo relevante para nuestro objetivo. Acciones: no dar aspecto de anuncio a contenido importante (ceguera a banners); evitar cambios simultáneos que compitan (ceguera al cambio): un aviso a la vez, junto a donde está la atención. Origen: Cherry 1953, Broadbent 1958, Treisman 1960, Kahneman 1973.

**Efecto de posición serial (Teoría)** — Se recuerdan mejor el primero y el último de una serie (primacía y recencia).
- Acciones: lo clave al principio y al final de listas y barras de navegación; lo menos importante en medio.
- Origen: Ebbinghaus (1885); curva clásica Murdock 1962.
- **Aviso**: es un efecto de *recuerdo* de listas presentadas en secuencia; en navegación visible su efecto sobre clics es indirecto. La recomendación de «extremos izquierdo y derecho» del sitio es extrapolación razonable, no medida en nav.

**Memoria de trabajo (Psicología)** — Sistema que mantiene y manipula información temporalmente. El sitio da 4-7 fragmentos que se desvanecen en 20-30 s (el desvanecimiento remite a Brown 1958 / Peterson & Peterson 1959, ~18 s sin repaso — UNVERIFIED la cifra exacta del sitio). Acciones: reconocer mejor que recordar (enlaces visitados, migas); que el sistema cargue la memoria (arrastrar datos entre pantallas, tablas comparativas, resúmenes antes de confirmar). Origen: Miller, Galanter & Pribram 1960; Atkinson & Shiffrin 1968; Baddeley & Hitch 1974 (no citado en el sitio).

**Efecto Zeigarnik (Teoría)** — Se recordarían mejor las tareas interrumpidas que las terminadas.
- Acciones del sitio: señales de que hay más contenido; progreso visible para incitar a completar.
- Origen: Bluma Zeigarnik, 1927.
- **Evidencia [VERIFICADO]**: meta-análisis Ghibellini & Meier 2025 (*Humanities and Social Sciences Communications*; 59 publicaciones): **no hay ventaja de memoria** general para lo inacabado; sí una tendencia general a **reanudar** tareas interrumpidas (efecto Ovsiankina). → Usarlo como «la gente tiende a querer terminar lo empezado», no como «lo recordará mejor».

### 2.4 Lista de comprobación del orden del sitio

Aesthetic-Usability · Choice Overload · Chunking · Cognitive Bias · Cognitive Load · Doherty · Fitts · Flow · Goal-Gradient · Hick · Jakob · Common Region · Proximity · Prägnanz · Similarity · Uniform Connectedness · Mental Model · Miller · Occam · Paradox of the Active User · Pareto · Parkinson · Peak-End · Postel · Selective Attention · Serial Position · Tesler · Von Restorff · Working Memory · Zeigarnik = **30**. (Ni Gestalt de continuidad/cierre/figura-fondo ni «thumb zone» son entradas del sitio.)

## 3. Mapa por situación de interfaz

| Situación | Leyes que mandan | Qué hacer |
|---|---|---|
| **Formularios** | Proximidad, Chunking, Postel, Tesler, Carga cognitiva, Memoria de trabajo, Parkinson, Fitts | Etiqueta pegada a su campo; secciones con título; aceptar formatos variados y mostrar la interpretación; autocompletar y valores por defecto; no pedir lo que el sistema ya sabe; error junto al campo; botón Enviar cerca del último campo |
| **Navegación** | Jakob, Posición serial, Hick, Semejanza, Von Restorff, Memoria de trabajo | Patrones convencionales; lo clave en los extremos; agrupar y ordenar listas largas en vez de recortar a 7; estado actual visible; migas y enlaces visitados distinguibles |
| **Onboarding** | Paradoja del usuario activo, Hick, Tesler, Goal-gradient, Flow, Peak-End | Aprender haciendo (no carrusel de diapositivas); revelar funciones progresivamente (Slack); checklist con progreso dotado; primer éxito pronto y celebrado |
| **Dashboards** | Pareto, Carga cognitiva, Von Restorff, Región común, Atención selectiva, Prägnanz | Pocas cifras clave arriba; un solo acento; tarjetas/regiones por tema; nada con aspecto de anuncio; no cambiar varias cosas a la vez |
| **Checkout / pago** | Tesler, Parkinson, Goal-gradient, Peak-End, Hick, Fitts, Jakob | Pasos numerados con progreso; autocompletar dirección/tarjeta; sin opciones distractoras; confirmación final cuidada; nada de pop-ups de salida; ética: sin cargos ocultos ni casillas premarcadas |
| **Tablas** | Proximidad, Semejanza, Conexión uniforme, Memoria de trabajo, Chunking | Alineación y agrupación por espacio; cabecera fija (no obligar a recordar columnas); filas con relación por línea/fondo; cifras alineadas a la derecha y en mono; en móvil → tarjetas |
| **Móvil / zona del pulgar** | Fitts, Jakob | Objetivos ≥44-48 px y separados; acción principal abajo, al alcance; nada crítico en esquinas superiores. Dato de Hoober 2013 (>1.300 observaciones): 49 % agarre a una mano, 36 % sostenido con una y tocando con la otra, 15 % dos pulgares [VERIFICADO vía resúmenes]; «75 % de toques con el pulgar»: UNVERIFIED. Sus trabajos posteriores indican preferencia por el centro de la pantalla: UNVERIFIED |
| **Estados de carga** | Doherty, umbrales de Nielsen, Peak-End, Flow | <0,1 s sin indicador; ~1 s feedback ligero; 2-10 s spinner/skeleton; >10 s porcentaje, estimación y cancelar; UI optimista; nunca un pico negativo sin explicación |
| **Indicadores de progreso** | Goal-gradient, Zeigarnik/Ovsiankina, Doherty | Barra/stepper visible; progreso dotado honesto; permitir guardar y retomar (la gente tiende a reanudar); no prometer recuerdo por Zeigarnik |
| **Precios / planes** | Choice overload, Hick, Von Restorff, Región común | 3-4 planes comparables lado a lado; uno recomendado destacado; atributos en las mismas filas; ética: el «señuelo» es manipulación si oculta el coste real |
| **Errores y vacíos** | Peak-End, Paradoja del usuario activo, Postel | Mensaje que explica causa y salida; estado vacío que enseña; aceptar y corregir entradas en vez de rechazarlas |
| **Rediseños** | Jakob, Modelo mental | Introducir gradualmente, con opción de volver; respetar la ubicación de lo frecuente |
| **Revisión / tests** | Estética-usabilidad, Sesgo cognitivo | Medir comportamiento, no opiniones; desconfiar de «qué bonito»; buscar evidencia que contradiga la propia hipótesis |

## 4. Contraste con NN/g (las más usadas)

- **Fitts** (Raluca Budiu, 31/07/2022): misma fórmula; añade iconos + etiqueta como un objetivo, menús radiales/rectangulares para acortar distancias, bordes «infinitos» solo con ratón. Coincide con el sitio; NN/g es más preciso sobre táctil.
- **Hick** (vídeo de Katie Sherwin, 2018): matiza que los menús largos funcionan si se agrupan y estructuran; el problema no es el número sino la falta de organización. Coincide con el aviso de «no simplificar hasta la abstracción».
- **Jakob** (Nielsen, 2000; vídeo NN/g y Substack del autor): igual al sitio; Nielsen añade que vale también para apps móviles por extensión y que las pequeñas variaciones se olvidan y lo común se graba.
- **Peak-End** (Lexie Kane, 30/12/2018): mismo origen (1993); añade no acabar con pop-ups que bloqueen la salida y explicar las disrupciones con plazos realistas.
- **Estética-usabilidad** (Kate Moran, 2024, revisado 2026): mismo estudio; subraya el riesgo en tests y que solo perdona fallos menores.
- **Tiempos de respuesta** (Nielsen, 1993): 0,1/1/10 s — es la referencia sólida; el «400 ms» de Doherty es más débil en origen (ver 2.1).

## 5. Exageraciones y malos usos (resumen)

1. **Miller → «máximo 7 elementos en el menú»**: falso; lo visible no carga memoria; capacidad real ~4 fragmentos (Cowan) y solo para lo que se retiene.
2. **Hick → «menos opciones siempre»**: solo para elecciones simples entre opciones conocidas; con búsqueda manda la organización (orden, grupos, búsqueda).
3. **Choice overload → «nunca más de N»**: efecto medio ≈ 0; depende de complejidad, incertidumbre y objetivo del usuario.
4. **Doherty → «400 ms es un umbral científico»**: el informe de 1982 defiende «subsegundo» con datos de IBM; usar 0,1/1/10 s.
5. **Zeigarnik → «lo inacabado se recuerda»**: no replica en meta-análisis 2025; lo que sí aparece es la tendencia a reanudar.
6. **Posición serial en navegación**: extrapolación de memoria de listas.
7. **Postel sin límites**: aceptar con flexibilidad no es adivinar en silencio.
8. **Pareto y Parkinson**: aforismos, no leyes medidas.
9. **Goal-gradient «progreso artificial»**: si es falso, es dark pattern.
10. **Estética-usabilidad como excusa**: lo bonito no arregla lo roto; y en tests oculta problemas.
11. **Fitts en táctil**: las esquinas no son «infinitas» con el dedo.

## 6. Otras URL usadas

- Cowan 2001: https://pubmed.ncbi.nlm.nih.gov/11515286/
- Scheibehenne et al. 2010: https://abcwest.cogs.indiana.edu/pmwiki/pdf/scheibehenne.options.2010.pdf · Chernev et al. 2015: https://www.kellogg.northwestern.edu/faculty/research/detail/2015/when-product-assortment-leads-to-choice-overload-a-conceptual
- Ghibellini & Meier 2025 (Zeigarnik): https://ideas.repec.org/a/pal/palcom/v12y2025i1d10.1057_s41599-025-05000-w.html
- Kivetz et al. 2006: https://business.columbia.edu/sites/default/files-efs/pubfiles/1200/goalgradient.pdf · Nunes & Drèze 2006: resúmenes en https://coglode.com/nuggets/endowed-progress-effect (primaria no consultada)
- Hoober (zona del pulgar): https://smashingmagazine.com/2016/09/the-thumb-zone-designing-for-mobile-users · https://alistapart.com (artículo de 2013 «How Do Users Really Hold Mobile Devices?»)
- RFC 9413: https://www.rfc-editor.org/rfc/rfc9413.html
- Hick, críticas a la fórmula: https://en.wikipedia.org/wiki/Hick%27s_law
