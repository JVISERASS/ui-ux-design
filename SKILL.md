---
name: ui-ux-design
description: Diseña, implementa, revisa y critica interfaces (web apps, SaaS B2B, dashboards, formularios, tablas, móvil) con criterio de usabilidad y diseño visual verificable — heurísticas de Nielsen, Leyes de UX (Yablonski), Refactoring UI, diseño centrado en el usuario (Lowdermilk, ISO 9241), WCAG 2.2 AA y patrones con evidencia (NN/g, GOV.UK, Baymard). Úsala siempre que se cree o se toque UI en código (componentes, pantallas, estilos, Tailwind/CSS), se pida revisar o mejorar una pantalla o una captura, una revisión heurística o de accesibilidad, decidir entre dos diseños, diseñar formularios, estados vacíos, de carga o de error, tablas o dashboards, escribir microcopy, convertir una petición de funcionalidad en un flujo, o preparar un test de usabilidad — aunque no se diga «UX» ni «diseño», si el resultado lo va a usar una persona en una pantalla.
---

# UI/UX Design

Skill personal. Destila con palabras propias tres libros (Lowdermilk, *User-Centered Design*; Yablonski, *Laws of UX*; Wathan y Schoger, *Refactoring UI*) más NN/g, WCAG 2.2 y sistemas de diseño públicos. El detalle, con fuentes y lo no verificado marcado, está en `references/`. Este fichero es lo que hay que tener en la cabeza siempre.

## 0. Quién manda

Cuando dos consejos chocan, gana el de arriba:

1. **El sistema de diseño y las instrucciones del proyecto** (CLAUDE.md, tokens, primitivas, guía de marca). Si el proyecto dice «radio 0 y sin sombras», no se proponen sombras aunque Refactoring UI las recomiende: se consigue la profundidad con lo que el sistema permite (filete, fondo, espacio). Leer los tokens y componentes existentes antes de inventar ninguno.
2. **Reglas duras**: accesibilidad WCAG 2.2 AA y no engañar al usuario. Si el sistema del proyecto incumple contraste o foco, se señala con el criterio WCAG y una alternativa dentro del sistema.
3. **Evidencia**: estudios y guías con datos (NN/g, Baymard, GOV.UK, normas ISO).
4. **Oficio**: los consejos tácticos de Refactoring UI y similares. Son buenos por defecto, no leyes.

Decir siempre a qué nivel pertenece una recomendación: «WCAG 1.4.3 (obligatorio)» no pesa lo mismo que «suele quedar mejor así».

## 1. Antes de pintar nada: la necesidad

Las peticiones llegan como soluciones («añade exportar a CSV», «pon un botón aquí»). Debajo hay una necesidad, y diseñar la solución literal suele dar más superficie y peor resultado. Por eso, antes de diseñar:

- **Reformular** la petición como: *cuando [situación], [persona] quiere [resultado] para [motivo]*. Si no se puede rellenar la situación ni el motivo, preguntar o declarar la suposición.
- **Contexto de uso** (ISO 9241-11): quién, qué tarea, dónde y con qué (móvil al sol, escritorio con dos pantallas, uso diario experto o una vez al año). «Usable» no existe en abstracto: siempre para alguien, para una tarea, en un contexto.
- **Buscar el apaño actual** (Excel, WhatsApp, papel): es la mejor especificación de lo que hace falta.
- **Ofrecer al menos una alternativa** que resuelva la misma necesidad con menos interfaz, si existe.
- **Camino feliz primero**, y enseguida los estados: carga, vacío (primera vez / por filtro / sin permisos), error, éxito, parcial. Una pantalla sin sus estados no está diseñada.

Para entrevistas, tests de usabilidad, número de usuarios, métricas y SUS → `references/centrado-en-usuario.md`.

## 2. Estructura e interacción (lo que más pesa en la usabilidad)

**Heurísticas de Nielsen**, como lista de comprobación de un vistazo:

1. Estado visible: el sistema dice qué pasa (guardando, guardado, cargando, error).
2. Lenguaje del usuario, no del modelo de datos.
3. Control y libertad: deshacer, cancelar, volver.
4. Consistencia: lo mismo se ve y se comporta igual, y se respetan las convenciones.
5. Prevención de errores: restricciones, buenos valores por defecto, aceptar formatos variados.
6. Reconocer mejor que recordar.
7. Atajos para expertos sin estorbar a los novatos.
8. Minimalismo: cada elemento compite con los demás.
9. Errores que dicen qué pasó y cómo arreglarlo.
10. Ayuda en contexto.

**Leyes de UX que más se usan, con su límite**:

| Ley | Aplicar | Cuidado con |
|---|---|---|
| Jakob | Patrones convencionales; innovar en el valor, no en la navegación | Las convenciones del sector (ERP, CAD) pesan más que las de la web general |
| Fitts | Objetivos grandes y cerca de donde está la atención; botón de enviar junto al último campo | Las esquinas «infinitas» solo valen con ratón, no en táctil |
| Hick | Menos opciones donde hay prisa; destacar la recomendada; revelar progresivamente | Solo vale para elegir entre opciones conocidas; para buscar, manda la organización (orden, grupos, búsqueda) |
| Miller / memoria de trabajo | Agrupar (chunking); que el sistema recuerde por el usuario | El «7±2» **no** limita menús: lo visible no carga la memoria. La capacidad real ronda ~4 bloques (Cowan) |
| Tesler | Que la complejidad la absorba el sistema (valores por defecto, autocompletar, cálculo) | Esconder no es simplificar: solo desplaza la complejidad |
| Postel | Aceptar formatos variados y normalizar | Aceptar no es adivinar en silencio: si es ambiguo, mostrar la interpretación o preguntar |
| Peak-End | Cuidar el momento de más valor y el cierre; vigilar los picos negativos | — |
| Von Restorff | Un solo elemento destacado por zona | Si todo destaca, nada destaca, y lo destacado puede parecer un anuncio |
| Tiempos de respuesta | <0,1 s nada; ~1 s feedback ligero; 2–10 s esqueleto o spinner; >10 s % + cancelar | El «400 ms» de Doherty no aparece en el informe original de 1982; usar 0,1/1/10 s de Nielsen |
| Goal-gradient | Progreso visible y honesto en procesos largos | El progreso falso es un patrón engañoso |

Las 30 leyes, el mapa por situación (formularios, onboarding, checkout, tablas, móvil…) y los malos usos → `references/leyes-ux.md`.

**Patrones con evidencia** (detalle y fuentes → `references/patrones.md`):

- **Formularios**: etiqueta encima y visible (nunca el placeholder como etiqueta); una columna; `autocomplete` e `inputmode` correctos; no partir teléfono, fecha ni IBAN en varios campos; validar al salir del campo o al enviar y quitar el error en cuanto se corrige («premiar pronto, castigar tarde»); el error junto al campo, que diga qué pasó y cómo arreglarlo, con las palabras de la etiqueta; conservar siempre lo escrito.
- **Botones**: verbo + objeto («Guardar factura», no «Aceptar»); un solo botón principal por vista; evitar los deshabilitados que no explican el porqué (mejor dejar pulsar y explicar); evitar el doble envío.
- **Destructivo**: mejor deshacer que confirmar; confirmar solo lo irreversible, diciendo qué se pierde y con botones con la acción («Borrar 3 facturas» / «Conservar»), no Sí/No.
- **Vacíos**: decir que está vacío (y no cargando), qué aparecerá aquí y el botón para empezar; esconder filtros y ordenación mientras no haya nada.
- **Tablas**: identificador legible en la primera columna; números a la derecha con `tabular-nums` y los mismos decimales; cabecera fija; filtros visibles con lo activo a la vista; acciones de fila visibles, no solo al pasar el ratón; alternativa al arrastre. En móvil: tarjetas para revisar registros y tabla con la primera columna fija para comparar.
- **Dashboards**: una tarea; cada cifra con comparación, unidad y periodo; barras y líneas antes que tartas o velocímetros; el color con significado, nunca como única pista.
- **Navegación**: visible en escritorio (la hamburguesa reduce el descubrimiento); en móvil, barra inferior de 3–5 destinos con icono y texto; lo frecuente en zonas alcanzables y nada crítico en las esquinas superiores.
- **Microcopy**: lo importante en las dos primeras palabras; quitar la mitad de las palabras; subtítulos que se puedan escanear; frases cortas en voz activa; sin «Por favor», «Ups» ni «inválido».

## 3. Diseño visual (Refactoring UI, en corto)

Detalle con valores y CSS/Tailwind → `references/diseno-visual.md` (la §11 es la chuleta).

- **Empezar por la funcionalidad, no por el layout**, y **en escala de grises**: si la jerarquía no funciona en gris, el color no la arregla. El color va al final.
- **Sistemas antes que valores**: escalas fijas de espaciado, tamaño de fuente, color, sombra y radio, y decidir eligiendo de ellas. En código: tokens; nada de valores arbitrarios (`p-[13px]`) sin motivo.
- **Jerarquía con peso y color antes que con tamaño**: 2–3 tonos de texto (primario, secundario, terciario) y 2 pesos (normal y semibold/bold); nada por debajo de 400. Destacar algo es a menudo **atenuar lo que compite**.
- **Las etiquetas son el último recurso**: formatos que se explican solos («12 en stock» mejor que «Stock: 12»); si hace falta etiqueta, que pese menos que el valor. Los títulos de sección suelen funcionar como etiquetas pequeñas: la jerarquía visual no tiene por qué seguir la de los `h1…h6`.
- **Espaciado**: empezar con demasiado aire y recortar; escala no lineal (4, 8, 12, 16, 24, 32, 48, 64, 96…) en la que ningún paso esté a menos de ~25 % del siguiente; **más espacio entre grupos que dentro de un grupo** (la etiqueta pegada a su campo).
- **Anchos**: no estirar a toda la pantalla; `max-width` por componente; párrafos de 45–75 caracteres; barra lateral de ancho fijo y contenido flexible.
- **Texto**: escala tipográfica hecha a mano (12/14/16/18/20/24/30/36/48…) en px o rem, nunca em; interlineado de ~1,5 en el cuerpo y ~1–1,25 en titulares; titulares grandes con el tracking algo cerrado y mayúsculas con el tracking abierto; alinear por línea base cuando se mezclan tamaños; texto centrado solo en 2–3 líneas.
- **Color**: 8–10 grises (ligeramente tintados) y 5–10 tonos por color (100–900) definidos de antemano, mejor en **OKLCH** (luminosidad percibida uniforme); más croma en los extremos; **nunca texto gris sobre fondo de color** (usar un tono del mismo color); badges con contraste invertido (fondo claro tintado y texto oscuro del mismo tono); el color nunca como única señal.
- **Botones por importancia, no por semántica**: principal sólido, secundario con contorno o fondo suave, terciario como enlace. Lo destructivo solo es grande y rojo cuando es la acción principal (el botón final del diálogo de confirmación).
- **Profundidad** (si el sistema la admite): luz desde arriba; unas 5 sombras de dos capas; menos bordes (separar con espacio, fondo o sombra); borde de acento para dar color. Sin sombras: diferencias de fondo y filetes finos.
- **Imágenes**: los iconos no se escalan (meterlos en una forma con fondo); las imágenes subidas por usuarios van en un contenedor fijo con `object-fit: cover`; el texto sobre una imagen necesita una capa que garantice el contraste.
- **Modo oscuro**: reasignar los tokens semánticos, no invertir; superficies que se aclaran con la elevación; acentos menos saturados.
- **Cifras**: `font-variant-numeric: tabular-nums` en todo lo que se compara o se actualiza.

## 4. Accesibilidad: el mínimo que no se negocia

WCAG 2.2 AA es el objetivo (y lo que pide la EN 301 549 V4.1.1 en la UE). Checklist completa con los 55 criterios A/AA, ARIA, modales, regiones vivas y receta de pruebas → `references/accesibilidad.md`.

- HTML nativo antes que ARIA (`button`, `a href`, `label`, `fieldset`, `dialog`); cero `div` clicables.
- Contraste: texto ≥ 4,5:1; texto grande (≥ 24 px, o ≥ 18,66 px en negrita), bordes de input, iconos que informan y foco ≥ 3:1. Se mide con la fórmula de WCAG 2.x, no con APCA.
- Teclado completo; foco visible (`:focus-visible`) y **no tapado** por cabeceras o barras fijas (`scroll-padding`); modales con el foco dentro, Esc y devolución del foco al cerrar.
- Objetivos ≥ 24×24 px CSS como suelo legal; diseñar a 44–48 px en táctil.
- Todo lo que se arrastra tiene alternativa sin arrastrar (kanban, ordenar, sliders).
- Errores en texto junto al campo, con `aria-invalid` y `aria-describedby`; nada solo por color.
- Estados asíncronos anunciados con `role="status"` (o `alert` si son urgentes), con la región montada de antemano.
- Login: se puede pegar; `autocomplete` con `username`, `current-password` y `one-time-code`; sin pruebas cognitivas.
- No volver a pedir lo ya introducido en el mismo proceso.
- Reflow a 320 px sin scroll horizontal (salvo tablas de datos); zoom al 200 %; `prefers-reduced-motion`.
- Un axe en verde no significa accesible: en el estudio de GOV.UK la mejor herramienta encontró ~41 % de las barreras (todas juntas, ~71 %), y Deque calcula que axe detecta ~57 % de las incidencias. Hace falta también una pasada con teclado y una prueba rápida con lector de pantalla.

## 5. Cómo trabajar según la petición

**Implementar o mejorar UI en código**

1. Leer el sistema de diseño del proyecto (tokens, primitivas, componentes parecidos ya hechos) y reutilizar antes de crear.
2. Escribir la necesidad, el contexto y los estados (§1).
3. Construir primero la funcionalidad, con la jerarquía en gris; después espaciado, tipografía y color con los tokens.
4. Cubrir los estados: default, hover, focus-visible, active, disabled (con motivo), loading, vacío, error, éxito.
5. Comprobar: ancho de móvil (320–380 px) y escritorio, teclado, contraste y textos largos o datos extremos (nombres de 60 caracteres, importes de 7 cifras, listas de 0 y de 500 filas). Si hay navegador disponible, mirar la pantalla de verdad: una captura enseña lo que el código no.

**Revisar una pantalla, una captura o un PR**

Pasar §2–§4 y devolver:

1. **Resumen** en 2–3 líneas: qué funciona y cuál es el problema más caro.
2. **Hallazgos** ordenados por severidad (escala de Nielsen: 4 catastrófico, arreglar antes de publicar · 3 mayor · 2 menor · 1 cosmético). En cada uno: dónde, qué principio incumple (heurística, ley o criterio WCAG con número), a quién afecta y cómo, y **el arreglo concreto** (valor, componente, copy), separando lo obligatorio del gusto. Declarar que la severidad es la de un solo evaluador.
3. **Arreglos rápidos**: como mucho 5, los de mayor impacto y menor esfuerzo.
4. **Preguntas abiertas**: lo que solo se resuelve con datos o con usuarios.

**Decidir entre alternativas**

Comparar contra la tarea principal y el contexto (§1), no por gusto. Si la diferencia depende del comportamiento real, decirlo y proponer la prueba más barata que la resolvería (test con 5 usuarios, A/B, analítica): `references/centrado-en-usuario.md` §5.

**Diseñar sin código (flujo o wireframe)**

Entregar la necesidad reformulada, el flujo del camino feliz con sus estados, la estructura de cada pantalla justificada con un principio por decisión y lo que queda por validar con usuarios.

## 6. Reglas de comportamiento

- **Concreto antes que general**: «sube el texto secundario de `gray-400` a `gray-600` de Tailwind v3 (2,5:1 → 7,6:1 sobre blanco; WCAG 1.4.3 pide 4,5:1)» en vez de «mejora el contraste».
- **Una línea de porqué** por recomendación, con la fuente o el principio. Sin sermones.
- **No exagerar la evidencia**: Miller, Hick, choice overload, Zeigarnik, Pareto y la zona del pulgar se citan mal muy a menudo (ver `leyes-ux.md` §5). Si algo es criterio propio, decirlo.
- **Respetar las decisiones**: si piden algo que viola un principio, decirlo una vez con una alternativa y después hacerlo como se pidió, salvo que sea un fallo de accesibilidad grave o un patrón engañoso, que se señala claramente.
- **Nada de patrones engañosos**: rechazar tan fácil como aceptar; nada premarcado que solo beneficie al negocio; darse de baja tan fácil como darse de alta; sin urgencia ni escasez falsas; sin «No, gracias» culpabilizador. Las mismas leyes que hacen fácil un producto sirven para manipular (Yablonski, cap. de ética).
- **Las fuentes no se copian**: se parafrasean y se enlazan (`references/fuentes.md`).

## Mapa de referencias

| Fichero | Leer cuando… |
|---|---|
| `references/centrado-en-usuario.md` | haya que pasar de la petición a la necesidad, preparar entrevistas o un test, elegir método de investigación, puntuar la severidad o medir (éxito, tiempo, SUS) |
| `references/leyes-ux.md` | haga falta justificar con una ley, revisar un flujo por situación o comprobar si una ley se está usando mal |
| `references/diseno-visual.md` | se escriba o se pula UI: valores de espaciado, tipografía, color (OKLCH), sombras, imágenes, tokens, modo oscuro, densidad |
| `references/patrones.md` | toque formularios, estados, tablas, dashboards, navegación móvil, microcopy o patrones engañosos (y la DSA) |
| `references/accesibilidad.md` | toque una auditoría, componentes interactivos complejos, login, o surja una duda legal (EAA, EN 301 549, Ley 11/2023) |
| `references/fuentes.md` | se quiera saber de dónde sale algo, cuánto fiarse o qué leer |
