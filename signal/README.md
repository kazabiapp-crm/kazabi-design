# Kazabi Signal — la dirección visual que viene

**Estado: aprobada por Matías el 2026-09-11 · SIN APLICAR.**

La app (`webapp/`) y el sitio (`sitio/`) siguen leyendo `../tokens.css`, que es la dirección arena de
septiembre. Esta carpeta es la referencia de lo que viene. **No se usa en código de producción** hasta que
este archivo diga que la migración se hizo.

## Qué se decidió (2026-09-11)

| Tema | Decisión | Reemplaza a |
|---|---|---|
| Dirección visual | **Signal**: lienzo gris frío, paneles blancos con líneas, azul de acción `#0071e3`, botones en cápsula | Arena `#F7F5EE` + azul `#3A54CC` + Poppins/Inter (`../tokens.css`) |
| Tema oscuro | **Navy** (`#07172f` / `#0b2249`). A Matías le gusta el de Signal | Grafito frío (`3721d76`, 2026-09-10) |
| Cuerpo de lectura | **17px** | 14px |
| Alcance | **Todo al estilo de la app**: webapp y sitio con la misma marca | Sitio en arena + Poppins |
| Fuente | **Geist** (+ Geist Mono), autoalojada | SF Pro del diseño original, Poppins + Inter de hoy |

## Qué hay acá

| Archivo | Para qué |
|---|---|
| `tokens.css` | **La fuente de verdad de Signal.** Claro, oscuro y alias. Nombres del contrato de Kazabi |
| `DESIGN.md` | El contrato en prosa: paleta con contrastes medidos, tipografía, componentes, reglas |
| `USAGE.md` | Cómo aplicarlo |
| `components.manifest.json` | Inventario de componentes y los tokens que usa cada uno |
| `manifest.json` | Ficha para registrarlo en OpenDesign |
| `referencias/app.html` | La pantalla de Contactos de Signal, ya con los tokens corregidos |
| `referencias/landing.html` | La landing de Signal, ya con los tokens corregidos |

Los originales sin corregir siguen en el proyecto de OpenDesign (`0144ebf5-…/signal/` y
`kazabi-signal-landing/`). Allá quedan como mesa de trabajo, no como referencia.

## Qué se corrigió respecto al paquete de OpenDesign

Todos los contrastes están **medidos**, no estimados.

| Problema | Antes | Ahora |
|---|---|---|
| Chip Contactado no llegaba a AA | `#147d92` · 4.29:1 | `#0f6e80` · 5.27:1 |
| Chip Seguimiento no llegaba a AA | `#9a6700` · 4.48:1 | `#8f6000` · 5.04:1 |
| Hover del primario aclaraba y bajaba de AA | `#0077ed` · 4.32:1 | `#0066cc` · 5.57:1 (active `#005bb8`) |
| Borde de campos invisible | `#cfd5df` · 1.48:1 | `--border-control` `#858f9e` ≥3.02 · oscuro `#6380ad` ≥3.53 |
| Foco en halo al 35% (no llegaba a 3:1) | halo translúcido | 2px de superficie + 2px de `--accent` (4.70 / 3.34) |
| `--meta` usado en texto (3.4–3.6:1) | cabeceras, fechas, títulos del dossier | esos textos pasan a `--muted`; `--meta` solo iconos |
| Dos capas con valores distintos (`--bg #fff` vs `--canvas #f4f6f8`, `--surface` gris) | tarjetas grises sobre blanco si se pegaba | una sola capa; `--canvas`, `--panel`, `--ink`… son alias sin valor propio |
| Nombres fuera del contrato | `--space-*`, `--navy`, `--accent-text`, `--blue-soft` | `--sp-*`, `--brand`, `--link`, `--accent-soft` (los viejos quedan como alias) |
| Faltaban tokens que la app usa | sin `--accent-soft`, `--brand-*`, `--link`, `--text-2xs`, `--leading-snug` | todos definidos |
| Radios inventados en la referencia | 5, 7, 9, 10px sueltos | `--radius-xs` 6 y `--radius-icon` 10 entran a la tabla |
| DESIGN.md contradictorio | "inputs a 12px" vs `--radius-sm` 8 · ink-2 10.2 vs 9.6 | campos a `--radius-md` 12 · ink-2 9.99 medido |
| Oscuro solo con `.theme-dark` en `<body>` | la app usa `data-theme` en `<html>` | los dos, más `prefers-color-scheme` con guarda |
| Alias que no cambiaban de tema | `--canvas: var(--bg)` resuelto solo en `:root` | alias redeclarados donde se aplica el tema |
| `signal/index.html` con el verde viejo | `#16a34a` · 2.98:1 | referencia regenerada |

## Fuentes candidatas (licencia libre)

SF Pro no se puede servir como webfont: la licencia de Apple la limita a sus plataformas. En Windows y
Android se ve Arial. Estas son las alternativas con licencia **SIL Open Font License 1.1** (uso comercial,
se pueden autoalojar en la app y el sitio, sin pagar):

| Fuente | Por qué | Ojo |
|---|---|---|
| **Inter** (Rasmus Andersson) | La más parecida a SF Pro en proporciones y lectura en pantalla. Variable con eje óptico: corte *Display* para titulares y *Text* para cuerpo, igual que SF | Es la fuente más usada en SaaS: no diferencia |
| **Geist** (Vercel) | Neutra y precisa, un poco más técnica; muy buena en números y tablas | Menos cálida que SF en textos largos |
| **Instrument Sans** | Más carácter en titulares, algo más angosta: entra más texto por fila | Menos pesos intermedios |
| **Hanken Grotesk** | Grotesca amable, buena a 17px de cuerpo | Titulares menos apretados que SF |

**Elegida: Geist** (2026-09-11, Matías). Se autoaloja en la app y el sitio (paquete `geist` de npm o los
archivos de la release de Vercel); nunca se deja librada a la fuente del sistema.

## Cómo se aplica cuando llegue el momento

1. Autoalojar Geist y Geist Mono en `webapp/` y `sitio/` (hoy la webapp no carga ninguna fuente web).
2. Etiquetar la versión actual del repo como `v1-arena` y promover `signal/` a la raíz (`tokens.css`,
   `DESIGN.md`, `USAGE.md`, manifests). Regenerar `design-tokens.json` y `tailwind-v4.css`.
3. En `kit-real-estate`: copiar a `design/`, ajustar `scripts/sincronizar-tokens.mjs` y la capa de
   compatibilidad (tabla de abajo), `node scripts/generar-preview.mjs` y `node scripts/verificar-diseno.mjs`.
4. Sitio: el bloque `@theme` sale del `tailwind-v4.css` nuevo; se van la arena y Poppins.
5. Migrar componentes (botón en cápsula, grid de atención, fila con próxima acción, dossier). Con cambiar
   solo los tokens cambian color, letra y radios, pero no la estructura.
6. Actualizar la skill `kazabi-diseno`, el índice de decisiones y la copia del catálogo de OpenDesign.

### Nombres que cambian de significado al migrar

| Token | Hoy (`../tokens.css`) | Signal | Qué hacer en la app |
|---|---|---|---|
| `--text-base` | 14px, UI | **17px**, lectura | los usos de UI pasan a `--text-ui` |
| `--text-md` | 16px | no existe | pasar a `--text-base` o `--text-ui` según el caso |
| `--surface-warm` | arena-100 | no existe | alias a `--surface-subtle` en la capa de compatibilidad |
| `--border-soft` | arena-200 | no existe | alias a `--border` |
| `--radius-lg` | 20px | 18px | — |
| `--focus-ring` | 2px + 2px accent | igual forma, colores Signal | — |
| oscuro `--accent` | `#7488FF`, texto oscuro encima | `#0071e3`, texto blanco | revisar botones en oscuro |
