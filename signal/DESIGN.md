# Sistema de Diseño Kazabi Signal

> Categoría: Productivity & SaaS
> CRM inmobiliario para agentes en Ecuador. Calma editorial, marca navy, un solo azul de acción.
>
> **Estado:** aprobado por Matías el 2026-09-11 · **sin aplicar** a la app ni al sitio. Ver `README.md`.

## 1. Tema visual y atmósfera

Signal toma la disciplina editorial de Apple (cromo silencioso, tipografía apretada, el producto como protagonista) y la ancla con el navy de la marca Kazabi. La interfaz se siente como un instrumento, no como un tablero decorado.

El lienzo es un gris frío muy claro (`--bg` `#f4f6f8`). Encima viven paneles blancos (`--surface`) que no flotan: se separan con líneas finas (`--border` `#e3e7ed`) y cambios de superficie. La sombra queda para lo que de verdad se levanta de la página: modales, toasts y bottom sheets.

La promesa de producto se mantiene: **"se te acabó el desorden"**. Signal la expresa ordenando por urgencia: tarjetas de atención, filas con el próximo paso visible y un dossier lateral con todo el contexto.

**Características clave**
- Lienzo `--bg` + paneles `--surface` + líneas `--border`: profundidad sin sombras
- Navy `--brand` `#0b2249` = MARCA · Azul `--accent` `#0071e3` = ACCIÓN
- Titulares display 600–650 con tracking negativo; cuerpo de lectura a 17px
- Botones y chips en cápsula (`--radius-pill`); tarjetas y mesa a 18px; campos a 12px
- Chips de estado: color sobre su `-soft`, siempre con punto y palabra
- Tema oscuro sobre navy, con estados recalibrados
- Movimiento corto y decelerado: 150 / 220ms, `cubic-bezier(.28,0,.22,1)`

## 2. Paleta y roles

Los nombres son los del contrato de Kazabi. Entre paréntesis, el alias que usa Open Design.

### Marca

| Token | Hex | Uso |
|---|---|---|
| `--brand` (`--navy`) | `#0b2249` | Logotipo, avatar propio, capítulos institucionales, superficie del tema oscuro |
| `--brand-deep` (`--navy-2`) | `#071a39` | Marca profunda, pie de página, fondo de capítulo |
| `--brand-mid` · `--brand-steel` · `--brand-steel-light` | `#133c6f` · `#2c5c93` · `#5985bd` | Gráficos e ilustración. `steel-light` nunca en texto |

### Acción

| Token | Claro | Oscuro | Uso |
|---|---|---|---|
| `--accent` | `#0071e3` | `#0071e3` | Fondo de botón primario, marca de selección, anillo de foco |
| `--accent-hover` | `#0066cc` | `#0066cc` | Hover del primario |
| `--accent-active` | `#005bb8` | `#005bb8` | Presionado |
| `--accent-on` | `#ffffff` | `#ffffff` | Texto sobre azul |
| `--link` (`--accent-text`) | `#0066cc` | `#69b1ff` | **Todo texto azul**: eyebrows, enlaces, chip Nuevo, iconos azules |
| `--accent-soft` (`--blue-soft`) | `#eaf3ff` | `#102f60` | Fondo de icono, chip Nuevo, avatar de contacto |

> El hover **oscurece**. Aclarar a `#0077ed` como Apple deja el texto blanco en 4.32:1, por debajo de AA.

### Superficies, texto y líneas

| Token | Claro | Oscuro | Uso |
|---|---|---|---|
| `--bg` (`--canvas`) | `#f4f6f8` | `#07172f` | Lienzo de página |
| `--surface` (`--panel`) | `#ffffff` | `#0b2249` | Paneles, tarjetas, mesa |
| `--surface-subtle` (`--panel-subtle`) | `#f8f9fb` | `#102a54` | Fila seleccionada, dossier, búsqueda |
| `--fg` (`--ink`) | `#10213d` | `#f5f8ff` | Texto primario y titulares |
| `--fg-2` (`--ink-2`) | `#35435a` | `#d2dbeb` | Texto de apoyo, valores en listas |
| `--muted` | `#6e6e73` | `#a9b6cc` | Descripciones y **todo texto secundario**: cabeceras de lista, fechas, títulos del dossier |
| `--meta` | `#86868b` | `#8c9bb4` | **Solo iconos y marcas no textuales** en claro |
| `--border` (`--line`) | `#e3e7ed` | `#243c65` | Separador principal |
| `--border-strong` (`--line-strong`) | `#cfd5df` | `#36527f` | Borde de botón secundario, guía de línea de tiempo |
| `--border-control` | `#858f9e` | `#6380ad` | Borde de input y select (≥3:1) |

### Estados de relación

Nunca solo con color: el chip lleva punto + palabra.

| Estado | Texto claro | Fondo claro | Ratio | Texto oscuro | Fondo oscuro | Ratio | Tokens |
|---|---|---|---|---|---|---|---|
| Nuevo | `#0066cc` | `#eaf3ff` | 4.97 | `#69b1ff` | `#102f60` | 5.84 | `--link` / `--accent-soft` |
| Contactado | `#0f6e80` | `#e6f5f8` | 5.27 | `#67c7d4` | `#143b47` | 6.13 | `--cyan` / `--cyan-soft` |
| Visita agendada | `#157f3d` | `#e9f7ef` | 4.60 | `#67c58a` | `#143c33` | 5.76 | `--success` / `--success-soft` |
| Seguimiento | `#8f6000` | `#fff5dc` | 5.04 | `#e4b95f` | `#42351d` | 6.48 | `--warn` / `--warn-soft` |
| Negociación | `#a84b17` | `#fff0e7` | 5.12 | `#f2a36e` | `#4b3024` | 5.86 | `--orange` / `--orange-soft` |
| No responde | `#c9272c` | `#ffedef` | 4.88 | `#f0808e` | `#472735` | 5.08 | `--danger` / `--danger-soft` |

### Contrastes medidos (WCAG 2.x, 2026-09-11)

| Combinación | Ratio | Nivel |
|---|---|---|
| `--fg` sobre `--bg` | 14.83:1 | AAA |
| `--fg-2` sobre `--surface` | 9.99:1 | AAA |
| `--muted` sobre `--bg` | 4.68:1 | AA |
| Blanco sobre `--accent` | 4.70:1 | AA |
| Blanco sobre `--accent-hover` | 5.57:1 | AA |
| `--link` sobre blanco | 5.57:1 | AA |
| Blanco sobre `--brand` | 15.68:1 | AAA |
| `--border-control` sobre `--bg` / `--surface-subtle` | 3.02 / 3.11:1 | Límite de control (1.4.11) |
| Oscuro: `--fg` sobre `--bg` | 16.85:1 | AAA |
| Oscuro: `--link` sobre `--surface` | 6.97:1 | AA |
| Oscuro: `--muted` sobre `--surface` | 7.65:1 | AAA |
| Oscuro: `--meta` sobre `--surface` | 5.57:1 | AA |
| Oscuro: `--border-control` sobre `--surface-subtle` | 3.53:1 | Límite de control |
| Foco: `--accent` sobre blanco / sobre navy | 4.70 / 3.34:1 | Indicador ≥3:1 |
| `--meta` sobre blanco | 3.62:1 | ❌ No apto para texto |

## 3. Tipografía

### Familias

Una sola familia: **Geist** (Vercel, SIL Open Font License 1.1), autoalojada, igual en todos los equipos.

- **Display — Geist:** titulares, contadores, nombres de panel.
- **Texto — Geist:** cuerpo, listas, formularios, navegación.
- **Mono — Geist Mono:** atajos (`⌘ K`), identificadores y cifras que se alinean.

> El diseño se dibujó con SF Pro, pero su licencia no permite servirla como webfont. Geist se eligió el 2026-09-11 frente a Inter, Instrument Sans y Hanken Grotesk: es precisa en cifras, precios y tablas. Se siente más fría que SF en textos largos, así que el cuerpo a 17px con interlineado 1.47 no se aprieta.

### Escala

| Rol | Token | Tamaño | Peso | Interlineado | Tracking |
|---|---|---|---|---|---|
| Hero de marketing | `clamp(44px, 7vw, var(--text-4xl))` | 44–80px | 620 | 1.02 | -0.045em |
| Titular de página | `clamp(var(--text-2xl), 3.3vw, var(--text-3xl))` | 32–48px | 610 | 1.02 | -0.042em |
| Titular de sección | `clamp(30px, 4vw, var(--text-3xl))` | 30–48px | 620 | 1.06 | -0.042em |
| Modal / capítulo / contador | `--text-xl` | 24px | 620 | 1.06 | -0.025em |
| Panel / dossier / lead móvil | `--text-lg` | 20px | 620 | 1.35 | -0.025em |
| Cuerpo de lectura | `--text-base` | 17px | 400 | 1.47 | -0.018em |
| Lista, botón, nav, input | `--text-ui` | 14px | 600–620 (nav 520) | 1.35 | -0.012em |
| Próxima acción, tabla | `--text-sm` | 13px | 400–580 | 1.35 | normal |
| Descripción, label | `--text-xs` | 12px | 400–620 | 1.35 | normal |
| Eyebrow, cabecera, chip | `--text-2xs` | 11px | 600–650 | 1 | +0.055em, uppercase |

### Principios

- **Apretado arriba, aireado abajo.** Display a 1.02–1.06 con tracking negativo; cuerpo a 1.47.
- **El peso manda, no el color.** Jerarquía con 600–650 contra 400. Nunca un tercer tipo.
- **Uppercase solo en etiquetas de 11–12px**, con `--tracking-label`.
- **Cifras con unidad en `nowrap`**: `$148.000`, `Hoy · 15:00`. Columnas con `tabular-nums`.
- Con una fuente no variable, 520 cae a 500 y 620 a 600: la jerarquía tiene que seguir leyéndose.

## 4. Componentes

### Botones

- **`primary-button`**: fondo `--accent`, texto `--accent-on`, `--radius-pill`, alto mínimo 44px, padding `--sp-2` × `--sp-4`, `--text-ui`/600. Hover `--accent-hover`; presionado `scale(.97)` + `--accent-active`. **Uno por vista.**
- **`secondary-button`**: fondo `--surface`, borde 1px `--border-strong`, texto `--fg`. Hover: borde `--border-control`, fondo `--surface-subtle`.
- **`icon-button`**: círculo de 40px, sin borde, icono `--fg-2` de 19px. Hover: fondo `--surface`.
- **`nav-item`**: 36px de alto, `--radius-sm`, texto `--muted` `--text-ui`/520. Actual: fondo `--surface`, texto `--fg`, `--elev-ring`.

### Tarjetas de atención (`attention-grid`)

Una sola tarjeta contenedora con celdas separadas por líneas verticales, no cuatro tarjetas flotantes. Cada celda: padding `--sp-5`, icono en cuadrado de 34px con `--radius-icon` sobre `-soft`, contador `--text-xl`, título `--text-ui`/620, descripción `--text-xs` `--muted`. Presionada: fondo `--surface-subtle` y marca inferior de 20×2px.

### Mesa y filas (`desk`, `contact-row`)

- Mesa: `--surface`, borde `--border`, `--radius-lg`; grid `1fr 380px` con dossier.
- Cabecera de lista: `--text-2xs` uppercase **`--muted`**, 40px de alto.
- Fila: 80px mínimo, borde inferior `--border`; seleccionada con fondo `--surface-subtle` y barra izquierda de 3px en `--accent`.
- Avatar: círculo de 40px, iniciales `--text-2xs`/700 `--brand` sobre `--accent-soft`.
- Próxima acción: punto con aro de 8px en el color de prioridad + título `--text-sm` + fecha `--text-2xs` **`--muted`**.

### Chip de estado (`status`)

`--radius-pill`, padding `--sp-1` × `--sp-2`, `--text-2xs`/620, punto de 6px en `currentColor`, texto del estado sobre su `-soft`.

### Dossier

Panel lateral `--surface-subtle`, padding `--sp-6`, secciones separadas por `--border`, títulos `--text-2xs` uppercase **`--muted`**. Lista de definición a 92px + 1fr. Línea de tiempo con punto de 12px en `--accent` y guía de 1px `--border-strong`. En ≤820px pasa a bottom sheet con `--radius-sheet` y `--scrim`.

### Formularios

- Label visible `--text-xs`/620 siempre encima del campo.
- Control: 44px de alto, borde **`--border-control`**, **`--radius-md`**, fondo `--surface`.
- Foco: borde `--accent` + `--focus-ring`. Error: borde `--danger`, mensaje `--text-2xs` debajo, resumen `--danger-soft` arriba.
- Validación al salir del campo; envío con spinner y estado "Guardando".

### Búsqueda

`search-shell` de 44px, `--radius-md`, fondo `--surface-subtle`, borde `--border-control`, icono `--meta`, atajo `kbd` en mono `--text-2xs` con `--radius-xs`.

### Navegación

- Header fijo de 56px, fondo `--bg` al 92% con `backdrop-filter: saturate(180%) blur(18px)` y línea inferior.
- Marca: cuadrado `--brand` de 24px con `--radius-xs` + nombre en display `--text-base`/650.
- Móvil (≤820px): barra inferior de 72px con 4 destinos icono + texto; actual en `--link`.

### Toast y modal

Toast: `--surface`, borde `--border`, `--radius-md`, `--shadow`, punto de estado de 8px. Modal: ancho máximo 520px, `--radius-lg`, `--shadow`, `--scrim` con blur 3px; en móvil pasa a sheet.

### Iconografía

Una sola familia: SVG de trazo, `stroke-width` 1.75, extremos redondeados, sin rellenos. 16–20px en controles, 28px en estados vacíos.

## 5. Layout

### Espaciado

Solo `--sp-*` (base 4): `2, 4, 6, 8, 12, 16, 20, 24, 32, 40, 48, 64`. Ritmo de sección en marketing: 100px escritorio, 64px tablet, 48px móvil.

### Contenedor

- Ancho máximo `--container-max` 1440px en la app; `--container-text` 1200px en marketing.
- Gutters: 32px escritorio, 20px tablet, 16px móvil.

### Radios

| Token | Valor | Uso |
|---|---|---|
| `--radius-xs` | 6px | `kbd`, marca de 24px |
| `--radius-sm` | 8px | Nav items |
| `--radius-icon` | 10px | Cuadrado de icono de 32–34px |
| `--radius-md` | 12px | Campos, búsqueda, selects, toast, paso siguiente |
| `--radius-lg` | 18px | Tarjetas, mesa, modal |
| `--radius-sheet` | 22px | Bottom sheet móvil |
| `--radius-pill` | 980px | Botones, chips |
| 50% | — | Avatares, icon-button |

## 6. Profundidad y elevación

| Nivel | Tratamiento | Uso |
|---|---|---|
| 0 | `--bg` plano | Página |
| 1 | `--surface` + borde `--border` | Tarjetas, mesa, grid de atención |
| 2 | `--surface-subtle` | Selección, dossier, búsqueda |
| 3 | `--shadow` | Modal, toast, sheet |
| Foco | `--focus-ring`: 2px de `--surface` + 2px de `--accent` | Todo control interactivo |

La sombra tiene tinte navy (`rgba(11,34,73,…)`), nunca negro puro en claro. En oscuro sube a `rgba(0,0,0,.36)`.

## 7. Haz y no hagas

### Haz

- Separa con líneas y superficies antes de pensar en sombras.
- Pon el próximo paso visible en cada fila: qué hacer y cuándo.
- Ordena por urgencia; el color de prioridad acompaña al texto, no lo reemplaza.
- Usa `--link` para cualquier texto azul, en los dos temas.
- Diseña el oscuro con sus propios valores, no invirtiendo el claro.
- Hover solo bajo `@media (hover: hover)`; `prefers-reduced-motion` siempre respetado.

### No hagas

- No uses navy como botón ni azul como fondo decorativo.
- No uses `--meta` para texto en tema claro.
- No apiles tarjetas con sombra en reposo.
- No uses degradados, brillos ni glassmorphism fuera del header translúcido.
- No pongas más de un botón primario por vista.
- No inventes radios, tamaños ni espaciados fuera de las tablas.

## 8. Responsive

| Breakpoint | Cambios |
|---|---|
| ≤1100px | Gutter 20px; atención en 2×2; dossier a 340px; se oculta la columna de estado |
| ≤820px | Nav superior oculta → barra inferior; dossier como bottom sheet; mesa en una columna |
| ≤640px | Gutter 16px; atención como carrusel horizontal con snap; filas en dos líneas; modal como sheet |

- Objetivos táctiles mínimos de 44px.
- Las barras fijas reservan su alto con padding en el contenido.
- Nunca scroll horizontal de página.

## 9. Guía para agentes

### Referencia rápida

- Lienzo `var(--bg)` · Panel `var(--surface)` · Línea `var(--border)`
- Texto `var(--fg)` / `var(--fg-2)` / `var(--muted)`
- Marca `var(--brand)` · Acción `var(--accent)` · Texto azul `var(--link)`

### Prompts de ejemplo

- "Grid de atención Signal: una tarjeta `--surface` con borde `--border` y `--radius-lg`, cuatro celdas separadas por líneas verticales, icono de 34px con `--radius-icon` sobre `--accent-soft`, contador `--text-xl` display, título `--text-ui`/620."
- "Fila de contacto Signal: 80px, avatar de 40px sobre `--accent-soft`, nombre `--text-ui`/620 truncado, próxima acción con punto de color y fecha `--text-2xs` `--muted`, chip de estado en cápsula."
- "Capítulo de marketing navy: fondo `--brand`, titular blanco display 48px con tracking -0.042em, texto `#d2dbeb`, botón primario `--accent` en cápsula."

### Orden de iteración

1. Fija lienzo, panel y línea.
2. Separa marca (navy) y acción (azul).
3. Ajusta titulares, luego cuerpo, luego etiquetas.
4. Aplica radios por clase de componente.
5. Revisa el tema oscuro por separado y mide el contraste de todo color nuevo.
