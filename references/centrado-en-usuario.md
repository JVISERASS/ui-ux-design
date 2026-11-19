# Diseño centrado en el usuario: Lowdermilk (2013) + ISO 9241 + NN/g

Leer cuando haya que convertir una petición en necesidad, preparar entrevistas o un test de usabilidad, puntuar hallazgos o medir. Cada afirmación lleva su fuente.
Convención: **[VERIFICADO]** = leído en la fuente citada; **[RESEÑA]** = solo lo cuenta una reseña de terceros;
**UNVERIFIED** = no se pudo comprobar (el texto del libro está tras muro de pago; solo se leyeron índice y reseñas).

---

## 0. Qué sale del libro y qué de otras fuentes

- El libro de Lowdermilk no tiene capítulos de «peticiones de funcionalidades», «analítica» ni «presentar el diseño». Lo más parecido es:
  - alcance → cap. 4 «Having a Plan» (misión del equipo, definir proyecto, requisitos);
  - peticiones → cap. 3 «Knowing When to Listen to Users and When to Not» + cap. 5 «Exercising Restraint»;
  - métricas → cap. 9 (cronómetro, hoja de cálculo, compilar hallazgos) + A/B testing en el cap. 8;
  - presentar el diseño → nada específico (UNVERIFIED que exista).
  Fuente del índice: https://helion.pl/ksiazki/usercentered-design-a-developer-s-guide-to-building-userfriendly-applications-travis-lowdermilk,e_2ghj.htm
- Lo de «qué problema resuelve esto», preguntas de comportamiento pasado, 5 usuarios, think-aloud, severidad, SUS y métricas se ha sacado de NN/g, MeasuringU e ISO, no del libro.

## 1. El libro: ficha e índice [VERIFICADO]

- Travis Lowdermilk, *User-Centered Design: A Developer's Guide to Building User-Friendly Applications*, O'Reilly, marzo 2013, ~154 págs. Dirigido a programadores sin formación en UX. https://www.i-programmer.info/bookreviews/159-uiux/7172-user-centered-design.html
- Autor: hoy Principal UX Researcher en Microsoft; luego coescribió *The Customer-Driven Playbook* (2017, con Jessica Rich) y *The Customer-Driven Culture*. https://www.microsoft.com/en-us/research/people/travisl/
- Índice (títulos de capítulo y sección, fuente Helion arriba):
  1. Our World Has Changed
  2. What Is User-Centered Design? — UCD no es (solo) usabilidad / no es subjetivo / no es solo diseño / no es pérdida de tiempo ni dinero / no es un parte de bugs / no es una distracción
  3. Working with Users — sin acceso a usuarios; cuándo escucharles y cuándo no; tipos de usuario (Information Overloader, Control Freak, Devil's Advocate); lidiar con la negatividad
  4. Having a Plan — elegir plan; misión del equipo; definir el proyecto; requisitos de usuario; requisitos funcionales; modelos de datos y flujo; documentar prototipos; revisar la documentación
  5. Creating a Personal Manifesto — contención (Exercising Restraint); narrativa; personas; escenarios
  6. Creativity and User Experience — objetivos de UX; coger el lápiz; entender el objetivo; «robar» de otros; cuestionar
  7. Design Principles — proximidad (Gestalt); visibilidad, feedback y prominencia visual; jerarquía; modelos mentales y metáforas; divulgación progresiva; consistencia; affordance y restricciones; confirmación; Ley de Hick; Ley de Fitts
  8. Gathering Feedback — cuántos usuarios; encuestas; entrevistas; análisis de tareas; evaluación heurística; storyboards; prototipos; A/B testing
  9. Usability Studies — plan de test (introducción, tranquilizar, normas, tareas, cierre, agradecimiento); material (cronómetro, libreta, entorno, hoja de cálculo/base, cámara/audio); conducir el estudio; ensayar antes; compilar hallazgos
  10. You're Never Finished — imposible acertar a la primera; estar dispuesto a reiniciar
  11. Other Resources
  - Apéndice A: plantilla de proyecto (resumen de ciclo de vida, detalles, requisitos de usuario, hoja de especificaciones funcionales, modelos de datos y flujo, prototipos, notas de mantenimiento), persona de ejemplo y guion de ejemplo de un estudio de usabilidad.

## 2. Ideas accionables por capítulo

Los títulos están verificados; el contenido interno viene de reseñas (marcado) o es inferencia razonable a partir del título (UNVERIFIED).

- **Cap. 1** — Abre con la presentación del iPhone (enero 2007) y la frase de Jobs de que la gente a menudo no sabe lo que quiere hasta que se lo enseñas [RESEÑA i-programmer, tewarid]. Moraleja usable: no diseñar por votación ni por grupo focal; enseñar algo concreto y observar.
- **Cap. 2 — qué es UCD** — Define por negación: no es subjetivo, no es solo estética, no es un tracker de bugs, no es un lujo [RESEÑA tewarid: https://tewarid.github.io/2013/06/24/user-centered-design-by-travis-lowdermilk;-o'reilly-media.html]. Distingue usabilidad, HCI, UCD y UX como campos relacionados [RESEÑA].
  - Regla: «usable» se mide (ver ISO 9241-11 abajo), no se opina.
- **Cap. 3 — trabajar con usuarios** — Conocer a la base de usuarios y sus tipos; **discernir cuándo una sugerencia se implementa y cuándo se ignora su forma literal** [RESEÑA tewarid]. Arquetipos de usuario difícil: el que satura de información, el que quiere controlarlo todo, el abogado del diablo; tratar la negatividad como pista de mejora [RESEÑA i-programmer].
  - Regla: la petición literal es una hipótesis de solución; la queja es un dato sobre un problema.
- **Cap. 4 — tener un plan** — Plantilla: misión del equipo → detalles del proyecto (título, descripción, stakeholders, impacto) → **requisitos de usuario recogidos sin pensar aún en la solución** → requisitos funcionales → modelos de datos/flujo → prototipos [RESEÑA tewarid].
  - Regla: separar «qué necesita la persona» de «qué construimos». Escribir lo primero antes que lo segundo.
- **Cap. 5 — manifiesto personal** — Cada proyecto con una declaración de visión respaldada por una narrativa; **contención con las funcionalidades**; personas y escenarios para afinar la visión y decidir qué entra [RESEÑA i-programmer, tewarid].
  - Regla: toda funcionalidad nueva se contrasta con la visión y con un escenario de una persona concreta; si no encaja, no entra.
- **Cap. 6 — creatividad** — Bocetar a lápiz, mirar cómo trabajan otros y tomar prestado, cuestionar supuestos; usar la intuición además de la lógica de programador [RESEÑA].
- **Cap. 7 — principios** — Lista verificada en el índice. Aplicación directa en revisión de UI: agrupar por proximidad, feedback visible a cada acción, jerarquía clara, metáforas del modelo mental del usuario, revelar lo avanzado solo cuando haga falta, consistencia, affordances y restricciones que impidan el error, confirmación en acciones destructivas, pocas opciones a la vez (Hick), objetivos grandes y cercanos (Fitts).
- **Cap. 8 — recoger feedback** — Encuestas (la reseña dice 5-10 usuarios con escalas Likert [RESEÑA i-programmer]; cifra no comprobada en el libro, UNVERIFIED), entrevistas estructuradas / no estructuradas / contextuales, análisis de tareas, evaluación heurística, storyboards, prototipos, A/B [RESEÑA i-programmer, tewarid].
- **Cap. 9 — estudios de usabilidad** — **Observar en vez de preguntar**: mirar lo que hace la persona [RESEÑA i-programmer]. Guion con bloques fijos (intro, tranquilizar —«se prueba la app, no a ti»—, normas, tareas, cierre, gracias) [índice VERIFICADO; contenido de cada bloque UNVERIFIED]. Medir con cronómetro y apuntar en hoja de cálculo; grabar si se puede; ensayar el test antes.
- **Cap. 10 — nunca se acaba** — No se acierta a la primera; si el producto no funciona, iterar e incluso tirar código [RESEÑA i-programmer].
- Críticas de lectores: optimista, no trata plazos apretados; superficial para diseñadores expertos [RESEÑA Goodreads: https://www.goodreads.com/book/show/16173753-user-centered-design].

## 3. Técnicas concretas para un desarrollador / agente IA

### 3.1 De petición de funcionalidad a necesidad real
- Una petición describe una **solución imaginada**; la necesidad es el **progreso o resultado** que busca la persona. «Exportar a CSV» puede ser informar al jefe, pasar datos a contabilidad, copia de seguridad o cumplimiento. https://echai.ventures/startingup/jobs-to-be-done/customers-say-they-want-feature-x-but-is-that-the-job-or-just-a-solution-they-ve-imagined
- Proceso (Superbloom, 2015): (1) preguntar qué necesidad hay debajo; (2) **agrupar peticiones por necesidad**, no tratarlas como señales sueltas; (3) investigar con el que la pidió (pedir contacto, recorrido cognitivo con él). https://superbloom.design/learning/resources/handling-feature-requests/
- Nielsen: que muchos digan en una encuesta que usarían X solo indica que X «suena bien»; no predice uso. Las peticiones hipotéticas no deben dirigir el desarrollo. https://www.nngroup.com/articles/first-rule-of-usability-dont-listen-to-users/
- Reglas para el agente:
  - Antes de diseñar, reformula la petición como «Cuando [situación], quiere [resultado] para [motivo]». Si no puedes rellenar situación y motivo, pregunta.
  - Pide el último caso real: «¿Cuándo fue la última vez que necesitaste esto? ¿Qué hiciste en su lugar?» (incidente concreto, no hipótesis).
  - Busca el apaño actual (Excel, WhatsApp, papel): es la mejor especificación de la necesidad.
  - Ofrece al menos una alternativa a la solución pedida que resuelva la misma necesidad con menos superficie.

### 3.2 Entrevistas: comportamiento, no opiniones
- Lo que se dice y lo que se hace difieren; la memoria falla y la gente racionaliza. Las entrevistas sirven para actitudes e impresiones acumuladas, **no** para predecir uso futuro ni para decidir detalles de diseño (colores, navegación). https://www.nngroup.com/articles/interviewing-users/ (Nielsen, 2010)
- Usar la **técnica del incidente crítico**: pedir un episodio concreto, especialmente difícil o memorable; se recuerda bien y muestra el flujo real (mismo enlace).
- Preguntas abiertas para explorar («Cuéntame la última vez que…», «Llévame por un día normal»); cerradas solo para datos de filtro. https://nngroup.com/articles/open-ended-questions
- Evitar preguntas que contienen la respuesta (Schade, 2017): no parafrasear al usuario con tus palabras, no sugerir respuestas, no nombrar elementos de la interfaz, no dar por hecho emociones. Ej.: no «¿Por qué te costó la navegación?», sí «¿Qué fue fácil o difícil para llegar a la información?». https://www.nngroup.com/articles/leading-questions/
- Las opiniones/preferencias se piden **después** de usar el diseño, no antes; correlación preferencia–rendimiento medida ≈ 0,44. https://www.nngroup.com/articles/first-rule-of-usability-dont-listen-to-users/
- Si el usuario comenta algo **sin que se lo pregunten**, probablemente importa. https://www.nngroup.com/articles/interviewing-users/

### 3.3 Observación / indagación contextual
- Indagación contextual: observación + entrevista en el entorno real con pocos usuarios; modelo **maestro–aprendiz** (el investigador aprende mirando y preguntando mientras la persona trabaja). Principios: contexto, colaboración, interpretación (validada con el usuario), foco. https://www.nngroup.com/articles/contextual-inquiry/ (Flaherty, 2020)
- Sesión en 4 partes: preparación (confianza, objetivo, confidencialidad) → transición explícita a observar → entrevista contextual (alternar mirar y comentar, validar interpretaciones) → cierre resumiendo lo entendido para que lo corrija (mismo enlace).

### 3.4 Encuestas
- Cortas: 20 preguntas son demasiadas salvo público muy motivado; una sola pregunta da la mayor participación. Probar primero con preguntas abiertas para ver la variedad de respuestas y luego cerrar. No preguntar lo que ya da la analítica. Evitar listas alfabéticas de respuestas (sesgo). Pilotar con 1 persona por ronda en varias rondas. https://www.nngroup.com/articles/qualitative-surveys/ (Farrell, 2016)

### 3.5 Personas y escenarios
- Persona = personaje ficticio pero realista que resume **investigación real** (campo, entrevistas, encuestas); sin investigación detrás es ficción. Solo los detalles que sirvan para decidir (comportamientos, objetivos, preocupaciones, cita); lo irrelevante resta. Uso: vocabulario común en el equipo, revisión experta, reclutar participantes, segmentar analítica. https://www.nngroup.com/articles/persona/ (Dykes, 2025)
- Lowdermilk las usa con escenarios para filtrar funcionalidades (ver cap. 5) [RESEÑA].

### 3.6 Cuántos usuarios probar
- Cualitativo: **5 usuarios** encuentran ~85 % de los problemas si cada uno descubre ~31 % (modelo Nielsen–Landauer: hallados = N·(1−(1−L)^n)). Mejor **tres rondas de 5 con arreglos entre medias** que una de 15. Mínimo 3 para no fiarse de un individuo raro. https://www.nngroup.com/articles/why-you-only-need-to-test-with-5-users/ (Nielsen, 2000)
- Varios perfiles muy distintos (p. ej. profesional que usa la herramienta a diario vs. cliente final que entra una vez): 3-4 por grupo. Procesos ágiles muy baratos: hasta 2 por ronda. https://www.nngroup.com/articles/how-many-test-users/ (Nielsen, 2012)
- Excepciones al 5: cuantitativo ≥20 (Nielsen 2012) — NN/g recomienda hoy **40** para métricas binarias con ±15 % y 95 % de confianza; 20-25 para métricas continuas (tiempo, satisfacción) y recalcular el margen. Card sorting ≥15 por grupo; eyetracking 39. https://www.nngroup.com/articles/summary-quant-sample-sizes/ (Budiu y Moran, 2021)
- **Caveat empírico**: Faulkner (2003) remuestreó 60 usuarios: grupos de 5 encontraron entre 55 % y ~99 % de los problemas; con 10, mínimo 80 %; con 20, mínimo 95 %. El 31 % es una media, no una ley: con tareas variadas o usuarios heterogéneos, 5 puede quedarse corto. https://doi.org/10.3758/BF03195514 ; resumen: https://www.humanfactors.com/newsletters/enough_is_enough.html
- El 5 sirve para **encontrar** problemas, nunca para **cuantificar** («el 60 % falló» con n=5 no es un dato).

### 3.7 Pensar en voz alta (think-aloud)
- La persona usa el sistema verbalizando lo que piensa; el facilitador la anima a seguir hablando. Barato, robusto ante facilitación imperfecta, sirve con prototipos o producto acabado y convence a escépticos. https://www.nngroup.com/articles/thinking-aloud-the-1-usability-tool/ (Nielsen, 2012)
- Riesgos: situación poco natural, autocensura para parecer listo, el facilitador sesga si interviene de más; no da estadística. Tres pasos: usuarios representativos, tareas realistas, dejar que hablen y callar (mismo enlace).
- Regla: no medir tiempo de tarea en una sesión con think-aloud (hablar ralentiza) — inferencia razonable, UNVERIFIED como regla explícita de NN/g.

### 3.8 Escribir tareas de test
- Tres reglas (McCloskey, 2014): **realista** (dar el objetivo, no la ruta: «compra unas zapatillas por menos de 40 $», no «compra las Nike naranjas»); **accionable** (que lo haga, no que diga dónde haría clic); **sin pistas** (no usar los nombres de menús ni botones de la interfaz). https://www.nngroup.com/articles/task-scenarios-usability-testing/
- Plantilla para el agente: «[Situación del usuario]. [Objetivo con criterio de éxito comprobable].» Revisar que ninguna palabra de la tarea aparezca literal en la UI que se prueba.

### 3.9 Severidad de problemas
- Factores: frecuencia, impacto (cuánto cuesta superarlo), persistencia (una vez o siempre) e impacto de mercado. Escala 0-4: 0 no es problema · 1 cosmético · 2 menor · 3 mayor (prioridad alta) · 4 catastrófico (arreglar antes de publicar). Una sola persona puntuando no es fiable: media de **3 evaluadores**. https://www.nngroup.com/articles/how-to-rate-the-severity-of-usability-problems/ (Nielsen, 1994)
- Regla para el agente: al listar hallazgos, cada uno con severidad 0-4 y su porqué (frecuencia/impacto/persistencia), ordenados de 4 a 1; declarar que la puntuación es de un solo evaluador.

### 3.10 Métricas: éxito, tiempo, errores, satisfacción
- Cuatro métricas básicas: tasa de éxito, tiempo de tarea, tasa de error, satisfacción subjetiva. Para comparar diseños con varias tareas, media **geométrica** de las ratios. https://www.nngroup.com/articles/usability-metrics/ (Nielsen, 2001)
- Tasa de éxito: % que completa la tarea. Se pueden definir niveles (éxito, éxito con fallo menor, con fallo grave, fracaso) pero **reportarlos por separado con su intervalo de confianza, con etiquetas de texto, nunca promediarlos como números**. https://www.nngroup.com/articles/success-rate-the-simplest-usability-metric/
- Tiempo de tarea: distribución sesgada a la derecha; con n<25 usar **media geométrica**; con n>25, la mediana vale. La media aritmética se dispara con un solo rezagado. https://measuringu.com/average-times/ (Sauro, 2010)
- SUS (System Usability Scale): 10 ítems Likert 1-5 alternando positivos (impares) y negativos (pares). Puntuación: impares → respuesta−1; pares → 5−respuesta; sumar y ×2,5 → 0-100. **Media de referencia ≈ 68**; >80,3 ≈ top 10 %. No es un porcentaje. Funciona con muestras pequeñas pero dar intervalo de confianza. https://measuringu.com/sus/ (Sauro, 2011)
- Pedir SUS (o cualquier satisfacción) **tras** las tareas, nunca antes (coherente con §3.2).

## 4. ISO 9241 [VERIFICADO en vista previa oficial]

### 4.1 ISO 9241-11:2018 — definición de usabilidad
Fuente: vista previa SIST de la norma: https://preview.sist.si/sist-preview/63500/33c267a5a7564f298f02bbd65721a181/ISO-9241-11-2018.pdf
- Usabilidad (3.1.1): grado en que **usuarios especificados** pueden usar un sistema, producto o servicio para lograr **objetivos especificados** con **eficacia, eficiencia y satisfacción** en un **contexto de uso especificado**. Nota: lo «especificado» es la combinación concreta de usuarios, objetivos y contexto que se esté considerando → la usabilidad no existe en abstracto.
- Eficacia (3.1.12): exactitud y compleción con que se logran los objetivos.
- Eficiencia (3.1.13): recursos empleados en relación con los resultados (tiempo, esfuerzo, coste, materiales).
- Satisfacción (3.1.14): grado en que las respuestas físicas, cognitivas y emocionales derivadas del uso cubren necesidades y expectativas (incluye la experiencia de uso real).
- Contexto de uso (3.1.15): usuarios + objetivos y tareas + recursos + entorno (técnico, físico, social, cultural, organizativo).
- La norma presenta la usabilidad como **resultado del uso**. https://www.iso.org/standard/63500.html
- Traducción a regla: toda afirmación «esto es usable» debe decir **para quién, para qué tarea y en qué contexto** (p. ej. «técnico de campo, con guantes, a pleno sol, móvil a 380 px»), y medirse con eficacia (éxito), eficiencia (tiempo/pasos) y satisfacción (SUS o similar).

### 4.2 ISO 9241-210:2019 — principios del diseño centrado en las personas
Fuente: vista previa STN EN ISO 9241-210:2020 (índice e introducción): https://normy.normoff.gov.sk/norma/130333/nahlad
- Principios (cláusula 5, títulos verificados; parafraseados):
  1. El diseño parte de una comprensión **explícita** de usuarios, tareas y entornos (5.2).
  2. Los usuarios participan **durante todo** el diseño y desarrollo (5.3).
  3. El diseño lo **guía y afina la evaluación centrada en el usuario** (5.4).
  4. El proceso es **iterativo** (5.5).
  5. El diseño abarca **toda la experiencia de usuario** (5.6).
  6. El equipo reúne **habilidades y perspectivas multidisciplinares** (5.7).
- Actividades (cláusula 7, títulos verificados): entender y especificar el contexto de uso → especificar requisitos de usuario (necesidades de usuarios y otros interesados, derivar requisitos, resolver conflictos entre ellos, asegurar su calidad) → producir soluciones (tareas, interacción e interfaz; concretarlas con prototipos; modificarlas según evaluación; comunicarlas a quien implementa) → evaluar (tests con usuarios, inspección, seguimiento a largo plazo).
- La introducción dice que el enfoque busca sistemas **usables y útiles**, mejora eficacia, eficiencia, bienestar, satisfacción, accesibilidad y sostenibilidad, y es compatible con cascada, orientado a objetos o desarrollo rápido; los principios apenas han cambiado desde ISO 13407 (mismo enlace).
- El texto completo de cada principio (5.2-5.7) no se leyó: solo los títulos. Su contenido detallado queda UNVERIFIED.

## 5. Qué método usar (NN/g, corto)

Fuente: Rohrer, «When to Use Which User-Experience Research Methods», NN/g, 2022 (revisado 2026): https://www.nngroup.com/articles/which-ux-research-methods/
- **Actitudinal vs. conductual**: lo que la gente **dice** vs. lo que **hace**. Para decidir diseño, prima lo conductual.
- **Cualitativo vs. cuantitativo**: cuali responde **por qué** y **cómo arreglarlo** (observación directa, pocos usuarios); cuanti responde **cuántos / cuánto** (datos codificados, muestras grandes).
- **Contexto de uso**: natural, guionizado (tareas), limitado (partes abstraídas, p. ej. card sorting) o sin producto.
- Por fase:
  - Estrategia / descubrir dirección → estudios de campo, entrevistas, encuestas, test de concepto.
  - Diseño / mejorar usabilidad → card sorting, tree testing, test de usabilidad (cuali, 5 por ronda).
  - Lanzar y evaluar → benchmarking, A/B, analítica, encuestas (cuanti).
- Atajo para el agente:
  - «¿Por qué no lo usan / dónde se atascan?» → test cualitativo con think-aloud (conductual, cuali).
  - «¿Cuántos se atascan / mejoró el rediseño?» → analítica, A/B o benchmark (conductual, cuanti).
  - «¿Qué problema tienen hoy?» → indagación contextual / entrevista sobre incidentes pasados.
  - «¿Les gusta?» → solo después de que lo usen; SUS o pregunta de satisfacción.
- Usabilidad = facilidad de uso; utilidad = que haga lo que hace falta; útil = ambas. Algo fácil que no sirve no vale. Cinco componentes: aprendibilidad, eficiencia, memorabilidad, errores (frecuencia, gravedad, recuperación) y satisfacción. https://www.nngroup.com/articles/usability-101-introduction-to-usability/ (Nielsen, 2012)

## 6. Reglas condensadas para la skill (síntesis propia sobre lo anterior)

1. Ninguna funcionalidad se diseña sin escribir antes la necesidad (situación → resultado → motivo) y el último caso real que la motivó (§3.1).
2. Preguntar por **hechos pasados concretos**, nunca «¿usarías…?» ni «¿te gustaría…?» (§3.2).
3. Observar antes que preguntar; la opinión se recoge después del uso (§3.2, §3.7, cap. 9).
4. «Usable» siempre con usuario + tarea + contexto y medido con eficacia, eficiencia y satisfacción (§4.1).
5. Iterar: rondas pequeñas (3-5 usuarios), arreglar, volver a probar; con perfiles distintos, 3-4 por perfil (§3.6).
6. Con 5 usuarios se **descubre**, no se **cuantifica**; para cifras, ≥20-40 y con intervalo de confianza (§3.6, §3.10).
7. Tareas de test con objetivo, sin ruta y sin vocabulario de la UI (§3.8).
8. Hallazgos con severidad 0-4 justificada y ordenados; no mezclar cosméticos con catastróficos (§3.9).
9. Métricas: éxito por niveles sin promediar, tiempo con media geométrica si n<25, SUS sobre 68 de referencia (§3.10).
10. Contención: cada funcionalidad se contrasta con la visión del producto y con un escenario de una persona basada en investigación (cap. 5, §3.5).
11. Agrupar peticiones por necesidad subyacente antes de priorizar (§3.1).
12. El trabajo nunca está acabado: prever reiniciar si los datos lo piden (cap. 10).

## 7. Fuentes consultadas

- Índice del libro: https://helion.pl/ksiazki/usercentered-design-a-developer-s-guide-to-building-userfriendly-applications-travis-lowdermilk,e_2ghj.htm
- Reseña i-programmer (Lucy Black): https://www.i-programmer.info/bookreviews/159-uiux/7172-user-centered-design.html
- Reseña tewarid (2013): https://tewarid.github.io/2013/06/24/user-centered-design-by-travis-lowdermilk;-o'reilly-media.html
- Goodreads: https://www.goodreads.com/book/show/16173753-user-centered-design
- Autor: https://www.microsoft.com/en-us/research/people/travisl/
- ISO 9241-11:2018 (vista previa): https://preview.sist.si/sist-preview/63500/33c267a5a7564f298f02bbd65721a181/ISO-9241-11-2018.pdf
- ISO 9241-210:2019 (vista previa STN): https://normy.normoff.gov.sk/norma/130333/nahlad
- NN/g: why-you-only-need-to-test-with-5-users, how-many-test-users, summary-quant-sample-sizes, which-ux-research-methods, thinking-aloud-the-1-usability-tool, task-scenarios-usability-testing, how-to-rate-the-severity-of-usability-problems, first-rule-of-usability-dont-listen-to-users, interviewing-users, contextual-inquiry, open-ended-questions, leading-questions, qualitative-surveys, persona, usability-metrics, success-rate-the-simplest-usability-metric, usability-101-introduction-to-usability (todas en https://www.nngroup.com/articles/<slug>/)
- MeasuringU: https://measuringu.com/sus/ , https://measuringu.com/average-times/
- Faulkner 2003: https://doi.org/10.3758/BF03195514
- Peticiones de funcionalidad: https://superbloom.design/learning/resources/handling-feature-requests/ , https://echai.ventures/startingup/jobs-to-be-done/customers-say-they-want-feature-x-but-is-that-the-job-or-just-a-solution-they-ve-imagined

## 8. No verificado (UNVERIFIED)

- Contenido interno de los capítulos del libro más allá de títulos y reseñas (O'Reilly y Google Books bloquearon el acceso).
- Si el libro da una cifra concreta de «cuántos usuarios» en el cap. 8 (la reseña habla de 5-10 para encuestas).
- Que el libro trate analítica web o cómo presentar diseños: no aparece en el índice.
- Texto completo de los principios 5.2-5.7 de ISO 9241-210 (solo títulos).
- La regla «no cronometrar con think-aloud» como recomendación explícita de NN/g.
