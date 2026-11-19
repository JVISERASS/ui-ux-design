# Diseño visual: Refactoring UI + práctica moderna

Leer al escribir o pulir UI en código: jerarquía, espaciado, tipografía, color, profundidad, imágenes y toques finales, con valores y pistas de CSS/Tailwind. §10 cubre OKLCH, tokens, `clamp()`, cifras tabulares, modo oscuro y densidad; §11 es la chuleta. Si el proyecto tiene sistema de diseño propio, sus tokens mandan sobre los valores de aquí.

Libro de Adam Wathan y Steve Schoger (PDF, 218 págs., 9 secciones, ~50 capítulos cortos). Todo va **parafraseado**; ninguna cita larga.
Marcas: **[V]** verificado en al menos una fuente pública citada; **[UNVERIFIED]** sale de memoria o de una sola fuente secundaria poco fiable; **[TW]** valor por defecto de Tailwind (los autores son los de Tailwind y sus defaults heredan el libro, pero el valor exacto es de Tailwind, no del libro).

## Fuentes

- Índice oficial (capítulos verificados): https://www.refactoringui.com/
- Avances oficiales: https://www.refactoringui.com/previews/building-your-color-palette · https://www.refactoringui.com/previews/labels-are-a-last-resort
- «7 practical tips for cheating at design» (Medium, oficial; Medium da 403, leído por espejo): https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886 · espejo https://readmedium.com/7-practical-tips-for-cheating-at-design-40c736799886
- Notas de la charla de Steve Schoger en CSS Day 2019: https://gist.github.com/ynotdraw/9351627d7509cc35813eeac4245cab3b
- Resúmenes públicos detallados: https://www.sglavoie.com/posts/2023/09/09/book-summary-refactoring-ui/ · https://www.mohitkhare.com/blog/notes-refactoring-ui/ · https://gist.github.com/selcukcihan/b9418596a98abfcd4bbc622550820cc5 · https://www.joelsleppy.com/blog/notes-on-refactoring-ui/
- Luminosidad percibida y giro de tono (Erik Kennedy, coherente con el libro): https://www.learnui.design/blog/color-in-ui-design-a-practical-framework.html
- Tailwind (valores [TW]): https://tailwindcss.com/docs/font-size · https://tailwindcss.com/docs/box-shadow · https://tailwindcss.com/docs/letter-spacing · https://tailwindcss.com/docs/colors

Índice verificado del libro [V]: 1 Starting from scratch · 2 Hierarchy is everything · 3 Layout and spacing · 4 Designing text · 5 Working with color · 6 Creating depth · 7 Working with images · 8 Finishing touches · 9 Leveling up.

---

## 1. Empezar desde cero (Starting from scratch)

1. **Empieza por una funcionalidad, no por el «layout»** [V]. No diseñes primero el armazón (barra de navegación, sidebar, footer): diseña la pieza que hace algo (p. ej. el formulario de búsqueda de vuelos: origen, destino, fechas, botón). El armazón se decide cuando sabes qué tiene que alojar.
   - Código: construye primero el componente de la funcionalidad aislado; el layout de página después.
2. **El detalle viene después** [V]. En la primera pasada no elijas tipografías, sombras ni iconos; bocetos de baja fidelidad. **Diseña en escala de grises** primero: obliga a que espaciado, contraste y tamaño hagan el trabajo de jerarquía; el color se añade al final.
   - Código: primera versión solo con `text-gray-*`/`bg-white`/`border-gray-*`; si la jerarquía no funciona en gris, el color no la arreglará.
3. **No diseñes de más** [V]. Trabaja en ciclos cortos: diseña lo simple → constrúyelo → corrige con la cosa real delante. Diseña la versión mínima útil y deja lo «bonito de tener» para después. Sé pesimista: no diseñes algo que dependa de una funcionalidad que quizá no construyas [UNVERIFIED el matiz exacto].
4. **Elige una personalidad** [V] y mantenla:
   - Tipografía: serifa → elegante/clásico; sans redondeada → juguetón; sans neutra → sobrio.
   - Color: azul → seguro/familiar; dorado → lujo; rosa → divertido/desenfadado.
   - Radio de borde: pequeño → neutro; grande → juguetón; ninguno → serio/formal. **Uno solo en toda la app**; mezclar radios cuadrados y redondos es lo que se nota.
   - Lenguaje: el tono del copy también es personalidad.
   - Mira a la competencia para situarte.
5. **Limita tus opciones** [V]. Define sistemas **antes** y elige de ellos (decidir por eliminación, no inventar cada vez): tamaño de fuente, peso, interlineado, color, margin, padding, anchos, altos, sombras, radio, grosor de borde, opacidad.
   - Código: todo en tokens (`@theme` en Tailwind v4 o variables CSS); prohibido el valor arbitrario (`p-[13px]`, `text-[15px]`) salvo justificación.

## 2. La jerarquía lo es todo (Hierarchy is everything)

1. **No todos los elementos son iguales** [V]. Decide qué es primario, secundario y terciario antes de pintar. Si todo compite, nada destaca.
2. **El tamaño no lo es todo** [V]: jerarquiza con **peso y color** antes que con tamaño (un título enorme y un secundario diminuto se ven desequilibrados).
   - Valores [V]: 2–3 colores de texto: oscuro (primario), gris medio (secundario), gris claro (terciario: metadatos, pie). 2 pesos: normal (400–500) y negrita (600–700). **Evita pesos < 400 en UI**: para restar énfasis usa color más claro o tamaño menor.
   - Tailwind: `text-gray-900` / `text-gray-600` / `text-gray-400`; `font-normal`/`font-medium` y `font-semibold`/`font-bold`.
3. **No pongas texto gris sobre fondos de color** [V]. El gris sobre color se ve apagado o deshabilitado. Para restar contraste: (a) blanco con opacidad reducida, o mejor (b) **elige a mano un color del mismo tono que el fondo**, ajustando saturación y luminosidad (la opacidad deja ver lo de detrás y puede ensuciar sobre imágenes/patrones).
   - Tailwind: sobre `bg-blue-700`, texto secundario `text-blue-100`/`text-blue-200`, no `text-gray-400`.
4. **Enfatiza restando énfasis al resto** [V]. Si el elemento principal no destaca, en vez de subirlo, baja lo que compite con él: p. ej. ítems inactivos de navegación en un gris más suave; un sidebar sin fondo propio (mismo fondo que la página) para que no robe protagonismo.
5. **Las etiquetas son el último recurso** [V, avance oficial]. (a) Muchas veces el formato basta (email, teléfono, precio). (b) Integra la etiqueta en el valor («12 en stock» en vez de «Stock: 12»). (c) Si hace falta, trátala como contenido de apoyo: más pequeña, menos contraste, menos peso. (d) Excepción: en fichas densas donde el usuario **busca por etiqueta** (especificaciones), enfatiza la etiqueta y no el valor.
6. **Separa la jerarquía visual de la del documento** [V]. Usa `h1`…`h6` por semántica, pero no les dejes dictar el tamaño: un título de sección a menudo actúa como etiqueta y debe ser **pequeño** (incluso pequeño, en mayúsculas, color suave). El contenido manda, no el título.
   - Código: `<h2 class="text-sm font-semibold uppercase tracking-wide text-gray-500">`.
7. **Equilibra peso y contraste** [V]. Los elementos «pesados» (iconos sólidos, muchos píxeles de tinta) se compensan bajando su contraste (icono en gris más claro junto a texto). A la inversa, un elemento fino (borde de 1 px) que se pierde: súbele el grosor antes que oscurecerlo.
8. **La semántica es secundaria (botones)** [V]. Diseña acciones por importancia, no por significado:
   - Primaria: fondo sólido de alto contraste. Secundaria: contorno o fondo de bajo contraste. Terciaria: estilo enlace, descubrible pero discreta.
   - **Destructivo ≠ siempre grande y rojo**: si «Borrar» no es la acción principal de la página, va como secundaria/terciaria; el rojo sólido grande solo cuando es la acción primaria (p. ej. el botón de confirmación del diálogo «¿Seguro que quieres borrar?»).

## 3. Layout y espaciado (Layout and spacing)

1. **Empieza con demasiado espacio en blanco** [V] y quítalo hasta que esté bien; es más fácil ver «sobra» que «falta». La densidad está justificada en algunas pantallas (dashboards), pero como decisión, no por defecto.
2. **Sistema de espaciado y tamaños** [V]: base **16 px** (divide bien y es el tamaño de fuente por defecto). Regla clave [V]: **ningún par de valores contiguos a menos de ~25 %** de distancia → escala no lineal, con saltos mayores arriba.
   - Escala que se atribuye al libro: `4, 8, 12, 16, 24, 32, 48, 64, 96, 128, 192, 256, 384, 512, 640, 768` px [UNVERIFIED la lista exacta: una fuente secundaria; coherente con la regla del 25 %].
   - Tailwind: escala `--spacing: 0.25rem` → `p-1`=4, `p-2`=8, `p-3`=12, `p-4`=16, `p-6`=24, `p-8`=32, `p-12`=48, `p-16`=64, `p-24`=96, `p-32`=128 [TW]. Para el agente: **usar solo estos pasos** (evitar 5, 7, 9, 10, 11…).
3. **No hace falta llenar la pantalla** [V]. Da a cada elemento el ancho que necesita (si un formulario necesita 600 px, 600 px). Si sobra sitio, columnas o márgenes, no estirar. Diseña primero a ~**400 px** de ancho (móvil) y amplía.
   - Código: `max-w-md`/`max-w-xl`/`max-w-prose` + `mx-auto`; nunca `w-full` por inercia en formularios en escritorio.
4. **Las rejillas están sobrevaloradas** [V]. No todo debe ser fluido en %: un sidebar va a **ancho fijo** y el contenido flexible; un componente usa `max-width` y solo encoge cuando la pantalla es más estrecha que él.
   - Código: `grid-cols-[16rem_1fr]` o `flex` con `w-64 shrink-0` + `flex-1 min-w-0`; tarjetas `max-w-sm w-full`.
5. **El tamaño relativo no escala** [V]. Las proporciones no se mantienen entre pantallas: un titular grande debe **encoger más deprisa** que el cuerpo en móvil (la relación titular/cuerpo se reduce). Igual con botones: un botón grande no es un botón pequeño escalado; su padding crece más que proporcionalmente [UNVERIFIED el ejemplo del botón]. Por eso, no uses `em` para tamaños que deben ser independientes.
   - Código: titular `text-3xl md:text-5xl` con cuerpo `text-base` en ambos; padding de botón por talla (`px-3 py-1.5` / `px-4 py-2` / `px-6 py-3`), no derivado de la fuente.
6. **Evita el espaciado ambiguo** [V]. Más espacio **entre** grupos que **dentro** de un grupo: la etiqueta pegada a su input y lejos del input anterior; el título de sección más cerca de su párrafo que del bloque previo; los ítems de lista con separación interna < separación entre ítems.
   - Código: en formularios, `space-y-6` entre campos y `space-y-2` (o `mb-1.5`) entre etiqueta e input; `mt-10 mb-3` en encabezados de sección.

## 4. Diseñar texto (Designing text)

1. **Establece una escala tipográfica** [V] **hecha a mano**, no derivada de una razón modular (las razones producen decimales y pocos tamaños útiles en UI). Usa **px o rem, nunca em** (el em anidado rompe el sistema).
   - Escala que suele atribuirse al libro: `12, 14, 16, 18, 20, 24, 30, 36, 48, 60, 72` px [UNVERIFIED como cita literal del libro; coincide exactamente con Tailwind `text-xs`…`text-7xl` [TW]].
2. **Usa buenas fuentes** [V]. Para UI, una sans neutra; vale la **pila del sistema** (`-apple-system, "Segoe UI", Roboto, "Noto Sans", Ubuntu, Cantarell, "Helvetica Neue", sans-serif`). Prefiere familias con **≥ 5 pesos** (señal de cuidado) [V]; filtrar Google Fonts por 10+ estilos [UNVERIFIED]. Evita fuentes display/condensadas para texto corrido. Fíate de lo popular y copia lo que usan sitios que admiras.
3. **Controla la longitud de línea** [V]: **45–75 caracteres**; un ancho de **20–35 em** te deja en ese rango. Si mezclas párrafo con imágenes/elementos anchos, limita el párrafo aunque el contenedor sea más ancho.
   - Código: `max-w-prose` (65ch) o `max-w-[60ch]`.
4. **Alinea por línea base, no por el centro** [V]. Si en una fila conviven tamaños distintos (título + enlace de acción), alinéalos por la base del texto.
   - Código: `flex items-baseline` (no `items-center`).
5. **El interlineado es proporcional** [V]. Punto de partida ~**1,5** para cuerpo. Inversamente proporcional al tamaño: texto pequeño → interlineado más alto; titulares grandes → interlineado cercano a **1** [V parcial: Tailwind pone 1 a partir de 48 px [TW]]. Y proporcional al ancho: líneas largas necesitan más interlineado (hasta ~2) para no perder el salto de línea.
   - Tailwind: `text-base/7`, `text-sm/6`, titulares `leading-tight`/`leading-none`.
6. **No todo enlace necesita color** [V]. En interfaces con muchos enlaces (navegación, tablas), color de marca en todos es ruido: usa peso o color más oscuro, y subrayado/color solo al hover. Dentro de texto corrido sí deben distinguirse.
7. **Alinea pensando en la lectura** [V]. Texto a la izquierda; centrado solo para bloques de 2–3 líneas (titulares, CTAs). **Números a la derecha** en tablas. Justificar solo con guionado activado [UNVERIFIED].
   - Código: `text-right tabular-nums` en columnas de importes; `hyphens-auto` + `lang="es"` si se justifica.
8. **Usa bien el espaciado entre letras** [V]: **aprieta titulares** grandes (las fuentes vienen espaciadas para tamaño de lectura) y **abre las MAYÚSCULAS** (las versales se leen peor juntas).
   - Valores [TW]: `tracking-tight` −0,025em / `tracking-tighter` −0,05em en titulares; `tracking-wide` 0,025em / `tracking-wider` 0,05em / `tracking-widest` 0,1em en mayúsculas.

## 5. Trabajar con el color (Working with color)

1. **Deja el hex por HSL** [V]: tono (0–360°: 0 rojo, 120 verde, 240 azul), saturación (0 % gris – 100 % vivo), luminosidad (0 % negro – 100 % blanco). Razonar en HSL permite derivar variantes. *(Hoy: OKLCH, ver § complementos.)*
2. **Necesitas más colores de los que crees** [V, avance oficial]:
   - **Grises: 8–10 tonos**; no uses negro puro (parte de un gris muy oscuro).
   - **Primario(s)**: 1–2 colores con **5–10 tonos** cada uno.
   - **Acentos semánticos**: rojo (peligro), amarillo/ámbar (aviso), verde (éxito), y quizá otros para destacar; cada uno con varios tonos.
   - UI compleja: hasta ~10 colores × 5–10 tonos.
3. **Define los tonos de antemano** [V, avance oficial]. Proceso: (a) elige el **base** (el tono medio, que funcione como fondo de botón); (b) el **más oscuro** (para texto); (c) el **más claro** (fondo tintado, p. ej. de alerta); prueba los extremos en un componente de alerta. (d) Rellena **9 tonos 100–900**: 500 = base, 900 = oscuro, 100 = claro; luego 700 y 300 a medio camino, y después 800, 600, 400, 200. A ojo, no por fórmula. Ajustes pequeños sí; añadir tonos nuevos sobre la marcha, no.
   - Tailwind: 11 pasos 50–950 [TW]; mismo espíritu.
4. **Que la luminosidad no mate la saturación** [V]. En HSL, cuanto más lejos del 50 % de luminosidad, **más saturación** necesitas para que no salga lavado (tonos 100 y 900 más saturados que el 500).
   - **Gira el tono** para cambiar el brillo percibido sin lavar el color [V]: los tonos de brillo percibido alto son **amarillo 60°, cian 180°, magenta 300°**; los bajos, **rojo 0°, verde 120°, azul 240°**. Para aclarar, gira hacia el pico claro más cercano; para oscurecer, hacia el más oscuro cercano. No gires más de **~20–30°** o deja de parecer el mismo color [UNVERIFIED el límite].
   - Ejemplo: un amarillo oscuro sale marrón si solo bajas L; gíralo hacia naranja.
5. **Los grises no tienen que ser grises** [V]: satúralos un poco — **azul** para grises fríos, **amarillo/naranja** para cálidos. Sube la saturación en los extremos (claros y oscuros) para que la temperatura se mantenga.
   - Tailwind: `slate` (frío), `stone` (cálido), `zinc`/`neutral` (casi puro).
6. **Accesible no tiene que ser feo** [V]. WCAG AA: **4,5:1** texto normal; **3:1** texto grande. (WCAG define «grande» como ≥ 24 px normal o ≥ 18,66 px negrita; el libro lo simplifica en torno a ~18 px [UNVERIFIED la cifra del libro]. Fuente WCAG: https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)
   - **Invierte el contraste**: en vez de texto blanco sobre un fondo de color que tendría que ser muy oscuro, pon **texto oscuro del mismo tono sobre fondo claro tintado** (badges, píldoras: `bg-green-100 text-green-800`).
   - **Texto de color sobre fondo de color**: para ganar contraste sin acercarte al blanco, **gira el tono** hacia uno más brillante (cian/amarillo/magenta).
7. **No dependas solo del color** [V] (~daltonismo): añade icono, flecha, texto o patrón; en gráficos, diferencia por **claro/oscuro** (contraste) más que por tonos distintos.

## 6. Crear profundidad (Creating depth)

1. **Emula una fuente de luz desde arriba** [V].
   - Elemento **elevado** (botón): borde superior más claro (sombra interior blanca de 1 px arriba, sin desenfoque) + sombra oscura pequeña **hacia abajo** con desplazamiento vertical y poco desenfoque.
   - Elemento **hundido** (input, pozo): sombra interior oscura arriba + borde inferior más claro.
   - Prefiere **desplazamiento vertical** a desenfoque/spread grandes [V, 7 tips]. No te pases con el desenfoque: debe parecer físico.
   - CSS: `box-shadow: inset 0 1px 0 hsl(0 0% 100% / .15), 0 1px 3px hsl(220 40% 10% / .2);` · hundido: `inset 0 2px 2px hsl(220 40% 10% / .1)`.
2. **Sombras para expresar elevación** [V]: sombra pequeña y tensa = cerca (botones); media = desplegables; grande y difusa = lejos y con foco (modales). **Define ~5 sombras** y elige de ahí [V]. En interacción: al arrastrar, subir sombra; al pulsar un botón, bajarla (o quitarla) para que «se hunda».
   - Tailwind: `shadow-xs`→`shadow-2xl` [TW]; `active:shadow-none`, `hover:shadow-md`.
3. **Las sombras pueden tener dos partes** [V]: (a) una **grande, suave y desplazada** = luz directa; (b) una **pequeña, oscura y tensa** (poco offset, poco desenfoque) = luz ambiente, la zona bajo el objeto donde no llega luz. A mayor elevación, la sombra tensa se atenúa hasta desaparecer.
   - Valores [TW, ilustran el patrón]: `shadow-sm`: `0 1px 3px 0 rgb(0 0 0/.1), 0 1px 2px -1px rgb(0 0 0/.1)`; `shadow-lg`: `0 10px 15px -3px …/.1, 0 4px 6px -4px …/.1`; `shadow-2xl` (la más alta) ya es una sola: `0 25px 50px -12px rgb(0 0 0/.25)`.
   - Mejor aún: sombras tintadas con el tono del fondo en vez de negro puro (deducción, no del libro).
4. **También el diseño plano tiene profundidad** [V]: **color** (más claro que el fondo = parece cercano/elevado; más oscuro = hundido) y **sombras sólidas** cortas sin desenfoque (`0 4px 0 <color>`).
5. **Superpón elementos para crear capas** [V]: una tarjeta que cruza el límite entre dos franjas de fondo (margen negativo); imágenes/avatares solapados con un **«borde invisible»** del color del fondo para que no choquen.
   - Código: `-mt-16 relative`; avatares `-space-x-2` + `ring-2 ring-white`.

## 7. Trabajar con imágenes (Working with images)

1. **Usa buenas fotos** [V]: fotógrafo o stock de calidad (p. ej. Unsplash); una foto mala arruina un buen diseño.
2. **El texto necesita contraste constante sobre la imagen** [V]: (a) **capa superpuesta** semitransparente (negra para texto claro, blanca para oscuro); (b) **bajar el contraste** de la imagen (y ajustar brillo); (c) **colorear**: desaturar y multiplicar con un color; (d) **sombra de texto sutil**: mucho desenfoque, sin desplazamiento (un halo, no una sombra visible).
   - Código: `bg-black/50` encima; `mix-blend-multiply`; `text-shadow: 0 0 40px rgb(0 0 0 / .5)`.
3. **Todo tiene un tamaño pensado** [V]:
   - **No agrandes iconos** diseñados a 16–24 px a 3–4×: quedan toscos. Mételos en una forma con fondo (`rounded-full bg-blue-100 p-3` con icono a 24 px) o usa un set dibujado para tamaño grande.
   - **No encojas capturas de pantalla** de escritorio: el texto queda ilegible. Usa una captura a tamaño de móvil/tablet, una captura parcial, o una ilustración simplificada de la UI.
   - **Los iconos tampoco encogen bien**: para favicon (16 px) redibuja una versión simplificada.
4. **Cuidado con el contenido que suben los usuarios** [V]:
   - **Controla forma y tamaño**: contenedor fijo + recorte centrado.
     - Código: `aspect-square w-12 object-cover` (o `background-size: cover`).
   - **Evita el «sangrado» del fondo** (foto con fondo similar al de la página): **sombra interior sutil** en vez de borde (el borde choca con los colores de la foto).
     - Código: `ring-1 ring-inset ring-black/10` sobre el `img` (o un pseudo-elemento con `box-shadow: inset 0 0 0 1px rgb(0 0 0/.1)`; `inset` no pinta sobre un `<img>` sin envoltorio).

## 8. Toques finales (Finishing touches)

1. **Potencia los valores por defecto** [V]: viñetas → iconos (checks, flechas); citas/testimonios con comillas grandes como elemento visual; enlaces con estilo propio; **checkbox y radio personalizados** con el color de marca.
   - Código: `accent-color: var(--brand)` como mínimo; `list-none` + icono.
2. **Añade color con bordes de acento** [V]: una franja de color en el **borde superior** de una tarjeta, el **izquierdo** de una alerta, **debajo** del ítem activo de navegación, arriba del todo de la página, o bajo un titular. Barato y efectivo cuando el diseño se ve soso.
   - Tailwind: `border-t-4 border-blue-500`, `border-l-4 border-amber-500`, `border-b-2 border-current`.
3. **Decora los fondos** [V]: cambiar el color de fondo de una sección para destacarla; **degradado suave con dos tonos a ≤ 30°** entre sí; **patrón repetido** de bajo contraste (Hero Patterns, de Steve Schoger: https://www.heropatterns.com/); formas geométricas o ilustraciones sencillas en zonas puntuales. Siempre con bajo contraste respecto al contenido.
   - Código: `bg-gradient-to-br from-blue-600 to-indigo-600` (≈ 20–30° de tono).
4. **No descuides los estados vacíos** [V]: son la primera impresión. Ilustración o imagen + explicación + **CTA** claro. **Oculta la UI de apoyo** (pestañas, filtros, ordenación) mientras no haya contenido que filtrar.
5. **Usa menos bordes** [V]: demasiados = ruido. Alternativas: (a) **sombra** sutil (`shadow-xs` o `ring-1 ring-black/5`); (b) **dos colores de fondo** distintos en elementos contiguos; (c) **más espacio**. Para tablas: zebra o fondos en vez de líneas [V, CSS Day].
6. **Piensa fuera de la caja** [V]: un desplegable puede tener secciones, columnas, iconos y descripciones; una tabla puede **combinar columnas** relacionadas (nombre + email en una celda con jerarquía), usar texto secundario, avatares y badges de color; un grupo de **radios puede ser tarjetas seleccionables**.
   - Extras de la charla CSS Day 2019 [V]: inputs de **40–48 px** de alto total; títulos de sección pequeños, en negrita, mayúsculas y color suave; importes y fechas alineados a la derecha con `font-feature-settings: "tnum"`; badges con fondo suave y texto oscuro; alternar fondo entre secciones de la página.

## 9. Subir de nivel (Leveling up)

- **Busca las decisiones que tú no habrías tomado** [V] en interfaces que admiras (titular con interlineado muy apretado, letter-spacing, combinaciones de color inesperadas) y entiende por qué funcionan.
- **Reconstruye desde cero interfaces que te gustan** [V], sin mirar el código: al compararlas aparecen los detalles finos que no habrías visto.
- Para un agente: antes de dar una pantalla por buena, compárala contra 1–2 referencias del mismo tipo (no copiar, contrastar decisiones).

---

## 10. Práctica moderna complementaria (no está en el libro)

### 10.1 OKLCH en vez de HSL para paletas perceptualmente uniformes
- En HSL, la misma L tiene luminosidad **real** distinta según el tono (un amarillo HSL 50 % es mucho más claro que un azul HSL 50 %): por eso el libro tenía que «girar el tono» a mano. **OKLCH** usa luminosidad percibida: misma L ≈ mismo brillo en todos los tonos → contraste predecible y `darken`/`lighten` fiables. [V] https://evilmartians.com/chronicles/oklch-in-css-why-quit-rgb-hsl
- Sintaxis: `oklch(L C H / a)`; L 0–1 (o %), C croma ~0–0,37 (el máximo depende del tono), H 0–360 (rojo ≈ 20, amarillo ≈ 90, verde ≈ 140, azul ≈ 220). Soportado por todos los navegadores modernos (2025) [V, Evil Martians].
- Paleta: fija H y C, **varía solo L** para los pasos; reduce C en los extremos (L muy alta o muy baja) para no salir de gama. Un leve giro de H entre pasos sigue siendo válido como ajuste fino (el consejo del libro, ahora opcional). Selector visual: https://oklch.com/
- Colores relativos: `background: oklch(from var(--btn) calc(l + 0.1) c h);` para hover en cualquier variante [V].
- Gama P3: `@media (color-gamut: p3) { --accent: oklch(0.7 0.29 145) }` con versión sRGB por defecto [V].
- Tailwind v4 ya define su paleta por defecto en OKLCH (`--color-blue-500: oklch(62.3% 0.214 259.815)`, 11 pasos 50–950) [V] https://tailwindcss.com/docs/colors

### 10.2 Tokens de diseño: primitivos vs semánticos
- **Primitivos/referencia**: valores crudos con nombre de lo que son (`blue-600`, `space-4`, `radius-sm`). **Semánticos/sistema**: rol, no valor (`color-primary`, `color-text-muted`, `color-surface`, `color-danger`) → apuntan a primitivos. **De componente** (opcional): `button-primary-bg` → semántico.
- Material 3 lo formaliza en tres clases: referencia (`--md-ref-*`, valores concretos), sistema (`--md-sys-color-primary`, `--md-sys-typescale-body-medium-size`, `--md-sys-shape-corner-small`) y componente (`--md-filled-button-container-shape`) [V] https://material-web.dev/theming/material-theming/
- Formato estándar: W3C Design Tokens Community Group, JSON con `$value`/`$type` y alias `{grupo.token}`; borrador de comunidad (versión 2025.10), no define capas primitivo/semántico [V] https://www.designtokens.org/tr/drafts/format/
- Regla para el agente: **los componentes solo consumen tokens semánticos**; el tema (claro/oscuro, marca) se cambia reasignando semánticos, nunca tocando componentes.

### 10.3 Tipografía fluida con `clamp()`
- `font-size: clamp(min, preferido, max)`, p. ej. `clamp(1rem, 2.5vw, 2rem)`: escala con el viewport sin media queries [V] https://developer.mozilla.org/en-US/docs/Web/CSS/clamp
- Accesibilidad [V, MDN]: el término preferido debe incluir `rem` (p. ej. `0.9rem + 1.5vw`) para que el zoom del usuario lo afecte, y el **máximo ≥ 2× el mínimo** para que el texto pueda llegar al 200 % (WCAG 1.4.4 Resize Text).
- Encaja con «el tamaño relativo no escala» del libro: aplica fluidez sobre todo a **titulares** (rango amplio) y deja el cuerpo casi fijo. Generador de escalas fluidas: https://utopia.fyi/ [UNVERIFIED: no consultado en esta sesión].

### 10.4 Cifras tabulares
- `font-variant-numeric: tabular-nums` (OpenType `tnum`): todas las cifras del mismo ancho → columnas alineadas y números que no «bailan» al actualizarse (contadores, temporizadores, totales). `lining-nums` (`lnum`) alinea cifras en la línea base; `slashed-zero` distingue 0/O [V] https://developer.mozilla.org/en-US/docs/Web/CSS/font-variant-numeric
- Tailwind: `tabular-nums`, `lining-nums`, `slashed-zero`. Úsalo en toda tabla de importes, junto con `text-right`.

### 10.5 Modo oscuro: no es invertir
- Material (M2) [V] https://m2.material.io/design/color/dark-theme.html: superficie base **#121212** (no negro puro); la elevación se expresa **aclarando la superficie** (capas superpuestas más claras cuanto más alta), porque las sombras apenas se ven sobre oscuro; colores de marca **desaturados** (tonos tipo 200 en lugar de 500) para no vibrar; contraste mínimo 4,5:1 y fondo-texto blanco de hasta 15,8:1; texto en blanco al **87 % / 60 % / 38 %** de opacidad para alto/medio/deshabilitado.
- Consecuencias: (a) redefinir los **tokens semánticos**, no invertir la paleta (invertir convierte `gray-100` en `gray-900` pero rompe tintes, sombras y acentos); (b) reducir saturación de acentos; (c) bordes/hairlines con más peso relativo porque las sombras no funcionan; (d) imágenes e ilustraciones pueden necesitar `filter: brightness(.9)` o versión propia.
- CSS: `@media (prefers-color-scheme: dark)`, `color-scheme: light dark` (controles nativos y scrollbars) y `light-dark(<claro>, <oscuro>)` para valores puntuales (MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/light-dark).

### 10.6 Modos de densidad
- Material define densidad como una escala sin unidades: 0 por defecto, valores negativos más compactos (hasta −4 en Flutter), positivos más holgados; **cada paso ≈ 4 px** de alto/espaciado, interpretado por cada componente [V] https://api.flutter.dev/flutter/material/VisualDensity-class.html (blog de Material sobre densidad web: https://m3.material.io/blog/material-density-web [UNVERIFIED: no se pudo renderizar]).
- Reglas prácticas: densidad compacta solo en vistas de datos para uso experto y prolongado (tablas, listas, dashboards); **nunca bajar las áreas táctiles** de 44–48 px en táctil (WCAG 2.5.8 pide 24×24 px mínimo; 44 px es la recomendación de Apple/2.5.5 AAA); no densificar diálogos, notificaciones ni formularios de alta.
- Implementación: un atributo `data-density="compact|comfortable"` que cambia **tokens de espaciado y altura** (`--row-h: 40px → 32px`, `--cell-px`), no los componentes; mantener la escala de espaciado (bajar un paso, no inventar valores).

---

## 11. Chuleta mínima para el agente (síntesis)

- Gris primero; color al final. Jerarquía con peso/color antes que tamaño; 2 pesos, 3 tonos de texto; nada < 400.
- Sobre fondo de color: texto del mismo tono más claro, nunca gris.
- Espaciado solo de la escala (4/8/12/16/24/32/48/64/96…); más espacio entre grupos que dentro.
- Anchos con `max-w-*`; párrafos 45–75 ch; no estirar a pantalla completa.
- Escala tipográfica fija (12–72); interlineado ~1,5 cuerpo, ~1–1,25 titulares; tracking negativo en titulares, positivo en mayúsculas; `items-baseline` al mezclar tamaños.
- Paleta: 8–10 grises tintados + 9 tonos (100–900) por color; más saturación en extremos; mejor en OKLCH.
- Botones: primaria sólida, secundaria contorno/suave, terciaria enlace; destructivo grande-rojo solo si es la acción principal.
- Etiquetas como último recurso; títulos de sección pequeños.
- 5 sombras de dos capas; luz desde arriba; menos bordes (sombra, fondo, espacio); acentos con borde de color.
- Iconos sin escalar; imágenes de usuario en contenedor fijo + `object-cover` + `ring-inset` sutil; estados vacíos con CTA y sin filtros.
- Números: `tabular-nums` + `text-right`. Oscuro: tokens semánticos redefinidos, no inversión.
