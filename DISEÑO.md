# Óptica y farmacia: brief de diseño

Plantilla `optica-farmacia` creada el 29/10/2026 a partir de `salud` con `php artisan plantillas:nueva` y rediseñada
entera a ancho completo. Este fichero se queda en el repo: es lo que lee quien (persona o agente) rediseñe la plantilla.

## Brief

- **Para quién**: farmacias de barrio y de pueblo, ópticas, ortopedias, centros auditivos y parafarmacias (y las
  farmacias que tienen óptica dentro). Quien entra quiere saber si está abierta o de guardia, qué hacen, qué
  promociones hay y cómo pedir una revisión de la vista o de la audición.
- **Qué tiene que conseguir la web**: que llamen al teléfono de guardia sin buscar (banda azul noche con el
  número enorme), que pidan la revisión visual (botón de la cabecera, banda azul con WhatsApp y teléfono) y que
  escriban o pasen por el mostrador (contacto con horario y «Cómo llegar»).
- **Tono y estilo** (`nitido`): limpio, preciso, de confianza. Sí: la claridad de una óptica bien iluminada y la
  cruz verde de la farmacia. No: la web médica fría de tarjetas blancas en una columna estrecha ni el hero partido
  con foto redondeada de `salud`.
- **Concepto «enfoque»**: la foto a sangre se ve desenfocada y, dentro de una lente circular con graduación
  (marcas finas alrededor y un punto menta arriba), nítida (`src/components/ui/Lente.astro`). Aparece en el hero
  y en la revisión visual. El resto del sistema lo acompaña: líneas finas de 1 px en lugar de tarjetas, iconos
  dentro de un aro con brillo menta (`.icono-lente`), esquinas casi vivas (0,3 rem), cruz luminosa en la guardia y
  símbolo de lente con cruz en la marca y el favicon.
- **Paleta de ejemplo**: primario azul `#1747a6`, acento menta `#5fe0b4`, fondo `#ffffff`, texto `#0b1b33`.
  Derivados con `color-mix`: `--noche` (primario casi negro: hero, guardia, pie), `--azul-suave` (primario al 9 %),
  `--menta-suave` (acento al 20 %), `--sobre-acento` (texto sobre menta). Texto blanco sobre azul y noche; tinta
  sobre menta; la última palabra de cada título va en primario (fondos claros y menta) o en menta (fondos oscuros).
- **Ritmo de bandas** (ejemplo): hero noche con foto y lente → franja blanca de utilidades → servicios blanco con
  dos columnas a sangre (azul suave «Óptica», menta suave «Farmacia») y franja de 4 fotos → guardia noche (foto a
  sangre izquierda) → promociones menta (foto a sangre izquierda) → revisión azul (lente a sangre derecha) → marcas
  blanco con cinta entre líneas → equipo azul suave con mosaico de retratos sin margen → cifras menta → consejos
  blanco (el primero 50/50 a sangre) → preguntas azul suave → contacto blanco (fachada a sangre derecha) → pie noche
  con el nombre enorme perfilado y recortado por abajo.
- **Tipografía**: pila de sistema («Segoe UI Variable Display», system-ui) a 800 con interletrado negativo
  (-0,04 em); hero a 6,75 rem en escritorio y 2,6 rem en móvil; antetítulos en mayúsculas con 0,2 em de
  interletrado y una línea menta de 2,5 rem; números de pasos y marcas alternas en letra perfilada.
- **Apartados**: hero, servicios (`items` con `categoria`, `galeria`), guardia (`destacado` con teléfono,
  `turnos`), ofertas (`ofertas` con precio y validez), cita (revisión visual: pasos y botones), marcas (`items`),
  equipo (`personas`), cifras (`items`), consejos (`noticias` con foto), preguntas, contacto (`horario`,
  `opciones` del formulario). `texto` genérico con foto a sangre.
- **Fotos** (`fotos.json`, 12): interior de farmacia con óptica para el hero, cuatro detalles verticales (monturas,
  gabinete, dermofarmacia, cajonera), escaparate de guardia de noche con la cruz encendida, bodegón de gafas de sol
  y cuidado, gabinete de optometría con el aparato centrado (queda dentro de la lente), tres consejos (nieve en el
  Pirineo, neceser de viaje, escritorio con gafas) y la fachada. Sin texto legible, sin logotipos, sin personas.
- **Qué no hacer**: volver a las tarjetas blancas con sombra; meter las secciones en una columna estrecha; poner
  dos bandas oscuras seguidas (si se reordena, alterna); usar la lente en más de dos sitios (pierde fuerza);
  tipografías externas.

## Responsive

Móvil primero. A 375 px: 16 px de margen del texto, fotos a sangre arriba de cada fila (4:3), lente arriba a la
derecha del hero, franja de utilidades en 2×2, servicios por categorías apiladas, equipo en 2 columnas, cifras en
2, turnos y promociones en filas; menú plegable y botón de la cabecera desde 640 px. A 768: franja de fotos y
equipo en 4 columnas, formulario en 2 columnas. Desde 1024: filas 50/50 con la foto tocando el borde, servicios
en columnas por categoría, titulares partidos (título a la izquierda, texto a la derecha), preguntas con el
titular fijo. Desde 1180: menú en línea. A 1440: servicios con 2 columnas por categoría.

## Pendiente fuera de esta plantilla

- [ ] Fotos de `fotos.json` y previews definitivas (`preview/card.jpg`, `preview/full.jpg`) con `tools/plantillas/previews.mjs` (las de ahora salen con los placeholders).
- [ ] Repo `Veleta-Com-y-Serv/plantilla-optica-farmacia` con la etiqueta `v1.0.0`.
- [ ] En la plataforma: `config/plantillas.php` (`repos` y `refs`) y `php artisan plantillas:sync --demos`.
