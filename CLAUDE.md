# Plantilla «Óptica y farmacia» (NoExpertise)

Web estática Astro 5 + Tailwind 4, derivada de AstroWind (MIT, ver `LICENSE-ASTROWIND.md`). Estilo: **nítido**.
Todo en castellano de España, frases cortas, sin jerga. El brief de diseño está en `DISEÑO.md`.

## Dónde está cada cosa
- **Textos, contacto, menú, SEO y secciones**: `site.yaml` (raíz). Es la única fuente de contenido. `src/data/site.ts` lo carga y lo tipa (también `ofertas` y `turnos`); no pongas textos fijos en los componentes.
- **Colores**: `site.yaml → colores` (primario, acento, fondo, texto). `src/layouts/Base.astro` los convierte en variables CSS (`--c-primario`…); `src/styles/global.css` saca de ellas con `color-mix` el azul noche (`--noche`), los tintes (`--azul-suave`, `--menta-suave`) y el texto sobre menta (`--sobre-acento`).
- **Tipografías y aspecto general**: `src/styles/global.css` (bandas `.banda--clara|suave|menta|azul|noche`, botones `.btn`/`.btn-sec`, lente, cabecera y pie). Fuentes del sistema: no añadas fuentes externas.
- **Imágenes**: en `public/`. Las de relleno están en `public/placeholders/`. En `site.yaml` se referencian con ruta absoluta (`/fotos/hero.jpg`). Las fotos de partida salen de `fotos.json`; las personas usan `/placeholders/persona.svg` hasta que el cliente sube las suyas.
- **Logo**: `site.yaml → logo` (ruta en `public/`); vacío = símbolo de lente con cruz + nombre en texto.
- **Pie «Web creada con NoExpertise»**: `site.yaml → marca_pie` (true en plan gratis).

## Secciones
Cada sección es un componente que solo se pinta si `site.yaml → secciones.<id>.activa` es `true`. Se pintan en el orden en que aparecen en `site.yaml`.
- `hero` → `src/components/secciones/hero.astro` (foto con la lente nítida, franja de `items`)
- `servicios` → `servicios.astro` (`items` con `categoria`: una columna a sangre por categoría; `galeria`: franja de fotos)
- `guardia` → `guardia.astro` (`destacado` {titulo, telefono, texto}, `turnos` {fecha, horas, texto}, `imagen`)
- `ofertas` → `ofertas.astro` (`ofertas` {titulo, texto, precio, validez}, `imagen`, `nota`, `cta`)
- `cita` → `cita.astro` (revisión visual: `items` como pasos, `cta`, `imagen` con lente; WhatsApp y teléfono de `contacto`)
- `marcas` → `marcas.astro` (`items` {titulo, texto}: cinta que corre)
- `equipo` → `equipo.astro` (`personas`: mosaico a sangre)
- `cifras` → `cifras.astro` (`items`: titulo = cifra; sin cifras no se pinta)
- `consejos` → `consejos.astro` (`noticias` {fecha, titulo, texto, imagen, url})
- `preguntas` → `preguntas.astro` (`preguntas` {pregunta, respuesta})
- `contacto` → `contacto.astro` (`horario` {dia, horas}, `opciones` del desplegable «Motivo» separadas por «;», `imagen` de la fachada)
- `texto` → `texto.astro` (genérico para apartados nuevos, `tipo: texto`)

## Reglas para órdenes
1. **Activar o quitar una sección**: cambia `activa: true|false` en `site.yaml`. No borres componentes.
2. **Reordenar secciones**: mueve el bloque dentro de `secciones:` en `site.yaml`. Procura alternar bandas claras y de color.
3. **Cambiar textos, teléfonos, horarios, fotos, turnos de guardia y promociones**: solo en `site.yaml`. Si un texto contiene comas o «: » dentro de `{ … }`, ponlo entre comillas. Precios siempre como cadena (`"39 €"`, `"-50 %"`, `"Consultar"`).
4. **Listas planas**: nunca una lista dentro de un elemento de lista; máximo 24 elementos. Para agrupar servicios usa `categoria`.
5. **Página nueva**: crea `src/pages/<slug>.astro` usando `import Base from '../layouts/Base.astro'` y `<Base titulo="…" descripcion="…">…</Base>`; enlázala en `site.yaml → menu`. Ejemplo: `src/pages/aviso-legal.astro`.
6. **Sección nueva**: crea `src/components/secciones/<id>.astro` (estructura: `seccion(id)`, `Banda`, `Titular`) y añade `secciones.<id>` en `site.yaml`. `src/pages/index.astro` la recoge sola.
7. **No tocar** `src/layouts/Base.astro`, `tailwind.config.mjs` ni `src/styles/comun.css` salvo orden explícita de diseño. Tampoco `src/lib/seo.ts` ni `src/pages/robots.txt.ts`, `sitemap.xml.ts` y `llms.txt.ts`: son el SEO de base, salen solos de `site.yaml` y el fichero es el mismo en todas las plantillas. `seo.url` y `seo.indexable` los pone la plataforma: no los cambies.
8. Mantén: `lang="es-ES"`, imágenes con `Imagen.astro` (carga diferida), sin JavaScript nuevo salvo necesidad real, 16 px de margen lateral del texto en móvil (las fotos y fondos sí tocan el borde), sin scroll horizontal. Imágenes de contenido con `alt` sacado del contenido (`altHero`, `altFicha`, `altGaleria`, `altSeccion`); las decorativas, `alt=""`.
9. El formulario no tiene servidor: abre el correo (`mailto`) con el email de `site.yaml`.

## Construir
```
npm ci && npm run build      # resultado en dist/
npx astro preview            # ver dist/ en http://localhost:4321
```
Antes de dar una orden por buena: `npm run build` sin errores.
