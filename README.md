# Plantilla NoExpertise · Óptica y farmacia

Web nítida para farmacias, ópticas y ortopedias, con guardias, promociones y revisión visual.

- Sectores: optica, farmacia, ortopedia, audiologia, parafarmacia. Estilo: nítido. Plan mínimo: gratis.
- Secciones: hero, servicios, guardia, ofertas, cita, marcas, equipo, cifras, consejos, preguntas, contacto (y `texto` para apartados nuevos).
- Diseño a ancho completo: bandas de borde a borde (blanco, azul, azul noche y menta), fotos a sangre en filas 50/50 y la «lente»: un círculo nítido con graduación sobre la foto desenfocada. Brief completo en `DISEÑO.md`.
- SEO de base incluido (`src/lib/seo.ts`): canónica, og:image, JSON-LD del negocio (`Pharmacy`) y de las preguntas frecuentes, `robots.txt`, `sitemap.xml` y `llms.txt`; `noindex` si `seo.indexable: false`.
- Contenido editable en `site.yaml`; metadatos y guion del asistente en `template.yaml`; fotos de partida en `fotos.json`; reglas para el agente en `CLAUDE.md`.

## Campos propios

| Sección | Campo | Qué es |
|---|---|---|
| `hero` | `items` {titulo, texto, icono} | Franja blanca de utilidades bajo la portada (horario, revisión, WhatsApp, guardia) |
| `servicios` | `items[].categoria` | Agrupa los servicios: una columna a sangre por categoría («Óptica», «Farmacia») |
| `servicios` | `galeria` | Franja de fotos de borde a borde |
| `guardia` | `destacado` {titulo, telefono, texto} | Teléfono de guardia enorme con la cruz luminosa (sin teléfono, el de contacto) |
| `guardia` | `turnos` {fecha, horas, texto} | Próximos turnos de guardia |
| `ofertas` | `ofertas` {titulo, texto, precio, validez}, `nota` | Promociones con etiqueta de precio (cadena) |
| `cita` | `items` {titulo, texto}, `cta` | Pasos de la revisión visual; WhatsApp y teléfono salen de `contacto` |
| `marcas` | `items` {titulo, texto} | Cinta de marcas que corre (quieta con «reducir movimiento») |
| `cifras` | `items` {titulo, texto} | La cifra va en `titulo` |
| `consejos` | `noticias` {fecha, titulo, texto, imagen, url} | El primero a lo ancho; el resto en rejilla |
| `contacto` | `horario` {dia, horas}, `opciones` | Horario por días (va al JSON-LD) y motivos del formulario separados por «;» |

```
npm ci
npm run dev      # desarrollo
npm run build    # web estática en dist/
```

Basada en [AstroWind](https://github.com/onwidget/astrowind) © onWidget, licencia MIT (`LICENSE-ASTROWIND.md`). Imágenes de relleno (`public/placeholders/`) hechas para esta plantilla, sin licencias de terceros.
