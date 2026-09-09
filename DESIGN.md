# Sistema de Diseño Kazabi

> Categoría: Productivity & SaaS
> CRM inmobiliario para agentes en Ecuador. Densidad y calma — no espectáculo.

## 1. Tema Visual y Atmósfera

Kazabi es la herramienta diaria de agentes inmobiliarios en Ecuador. Se usa muchas horas seguidas, con mucha información en pantalla: tablas de contactos, bandejas de mensajes, fichas de propiedades, calendarios de visitas. La promesa de marca es **"se te acabó el desorden"**.

El resultado visual es una interfaz que respira calma sin sacrificar densidad. El fondo arena (`#F7F5EE`) aporta calidez sin cansar la vista — es más suave que un blanco puro pero más profesional que un beige decorativo. Sobre este lienzo, las tarjetas blancas (`#FFFFFF`) crean elevación limpia con sombras arena sutiles (`rgba(27,23,18,.04)`).

La tipografía combina Poppins (500/600/700) para display y titulares con Inter Variable para texto de trabajo. Poppins aporta la personalidad de marca — redondeada, contemporánea, accesible — mientras Inter resuelve la legibilidad en tablas densas, listas compactas y formularios largos. La base tipográfica es 14px, no 16px, porque una interfaz de trabajo diario necesita meter más información útil por pantalla.

Los radios de borde (8px, 12px, 20px) son generosos pero no infantiles. Las sombras son tenues y cálidas, nunca azuladas ni frías. El movimiento es rápido y funcional — 120ms para hovers, 200ms para transiciones de panel.

**Regla cardinal del color:**
El navy (`#0B2249`) es el color de la **MARCA** — aparece en sidebar, cabeceras institucionales, y elementos de identidad. El azul (`#3A54CC`) es el color de **ACCIÓN** — solo para botones primarios, estados de foco, enlaces activos, y selección. Estos dos roles nunca se mezclan. Navy no es acción. Azul no es marca.

**Características clave:**
- Fondo arena `#F7F5EE` con tarjetas blancas — calidez sin decoración
- Poppins 600 para display, Inter Variable para texto de trabajo
- Base tipográfica 14px para densidad de información
- Navy `#0B2249` = MARCA; Azul `#3A54CC` = ACCIÓN — roles separados
- Borde arena `#DDD8CC` — nunca gris frío
- Sombra cálida `rgba(27,23,18,.04)` — nunca azulada
- Radios 8/12/20px — generosos y consistentes
- Movimiento rápido: 120ms hover, 200ms transición

## 2. Paleta de Color y Roles

### Navy — Color de Marca

El navy es la identidad de Kazabi. Transmite solidez, profesionalismo, confianza. Se usa en superficies institucionales, no en controles interactivos.

| Token | Hex | Uso |
|-------|-----|-----|
| `--brand` | `#0B2249` | Sidebar, header principal, fondos de marca |
| `--brand-deep` | `#0C1F41` | Fondo oscuro profundo, lienzo en dark mode |
| `--brand-mid` | `#133C6F` | Superficies elevadas en dark mode |
| `--brand-steel` | `#2C5C93` | Iconografía, bordes sobre navy |
| `--brand-steel-light` | `#5985BD` | Solo gráficos o texto ≥24px (3.49:1 sobre arena) |
| `--brand-on` | `#FFFFFF` | Texto sobre cualquier superficie navy |

### Arena — Calidez y Fondo

La escala arena conecta el mundo claro con el navy. El detalle que unifica la paleta: `arena-400` (`#C5B69F`) funciona como texto legible sobre navy a 7.89:1 de contraste. No son "dos paletas pegadas" — son una sola que se cruza.

| Token | Hex | Uso |
|-------|-----|-----|
| `--bg` (arena-50) | `#F7F5EE` | Fondo de página principal |
| `--surface-warm` (arena-100) | `#F0EBE0` | Sidebar, fondo secundario |
| `--border-soft` (arena-200) | `#E3DBCB` | Divisores sutiles |
| arena-400 | `#C5B69F` | Texto sobre navy en dark (7.89:1) |
| `--meta` (arena-700) | `#6E6455` | Timestamps, contadores |
| arena-900 | `#1B1712` | Base de sombras, negro cálido |

### Azul de Acción

El azul es exclusivamente el color interactivo. Nunca aparece como fondo decorativo ni como identidad de marca.

| Token | Hex | Uso |
|-------|-----|-----|
| `--accent` | `#3A54CC` | Botón primario, foco, enlace activo |
| `--accent-hover` | `#2C40A0` | Hover de botón primario (más oscuro en light) |
| `--accent-soft` | `#E7EAF9` | Fondo de selección, badge activo, row selected |
| Azul claro | `#7488FF` | Acento en dark mode (brilla sobre navy) |

### Texto e Interfaz

| Token | Hex | Uso |
|-------|-----|-----|
| `--fg` | `#131A20` | Tinta — titulares y texto primario |
| `--muted` | `#57626C` | Texto secundario, descripciones |
| `--border` | `#DDD8CC` | Línea — separadores principales |

### Estados Semánticos

| Estado | Primario | Fondo suave |
|--------|----------|-------------|
| Éxito (OK) | `#147A46` | `#E0F0E7` |
| Crítico | `#BE3346` | `#F8E3E6` |
| Advertencia | `#765B12` | `#EFE4C8` |

El ámbar de advertencia se deriva de la familia arena: conserva su temperatura terrosa y evita introducir un amarillo externo a la marca.

**Tema oscuro sobre navy `#0B2249`**

| Estado | Primario | Contraste |
|--------|----------|-----------|
| Éxito (OK) | `#67C58A` | 7.41:1 |
| Advertencia | `#E4B95F` | 8.51:1 |
| Crítico | `#F0808E` | 6.11:1 |

### Contrastes Verificados

Estos ratios están medidos y son parte del contrato del sistema:

| Combinación | Ratio | Nivel |
|-------------|-------|-------|
| Navy `#0B2249` sobre arena-50 `#F7F5EE` | 14.37:1 | AAA |
| Blanco `#FFFFFF` sobre navy `#0B2249` | 15.68:1 | AAA |
| Arena-400 `#C5B69F` sobre navy `#0B2249` | 7.89:1 | AAA |
| Tinta `#131A20` sobre arena-50 `#F7F5EE` | 15.2:1 | AAA |
| Muted `#57626C` sobre arena-50 `#F7F5EE` | 5.4:1 | AA |
| Acero claro `#5985BD` sobre arena `#F7F5EE` | 3.49:1 | Solo gráfico/24px+ |
| Ámbar `#765B12` sobre arena-50 `#F7F5EE` | 5.88:1 | AA |
| Ámbar `#765B12` sobre ámbar suave `#EFE4C8` | 5.07:1 | AA |
| Éxito dark `#67C58A` sobre navy `#0B2249` | 7.41:1 | AAA |
| Advertencia dark `#E4B95F` sobre navy `#0B2249` | 8.51:1 | AAA |
| Crítico dark `#F0808E` sobre navy `#0B2249` | 6.11:1 | AA |

## 3. Reglas de Tipografía

### Familias

- **Display:** `Poppins` (pesos 500, 600, 700). Para titulares, KPIs, nombres de sección, y cualquier texto que represente la marca.
- **Texto de trabajo:** `Inter Variable` (pesos 400, 500, 600). Para cuerpo, tablas, formularios, mensajes, sidebar, y todo el texto operativo.
- **Monoespaciada:** `JetBrains Mono` (peso 400). Para IDs, códigos de referencia, y datos técnicos.

### Escala Tipográfica

8 pasos cerrados. Esta escala reemplaza los 25 valores ad-hoc que existían en el producto. Cada tamaño tiene un rol definido — no se usan tamaños fuera de esta tabla.

| Token | Tamaño | Peso | Interlineado | Tracking | Rol en producto |
|-------|--------|------|--------------|----------|-----------------|
| `--text-2xs` | 11px | Inter 400 | 1.35 | normal | Timestamps, contadores, metadata mínima. "Hace 3h", "12 mensajes" |
| `--text-xs` | 12px | Inter 500 | 1.35 | 0.02em (uppercase) | Etiquetas de columna en tabla, badges, cabeceras de grupo |
| `--text-sm` | 13px | Inter 400 | 1.5 | normal | Cuerpo de tabla, items de sidebar, listas de contactos |
| `--text-base` | 14px | Inter 400 | 1.5 | normal | **Texto por defecto.** Inputs, mensajes, descripciones, párrafos |
| `--text-md` | 16px | Poppins 500 | 1.35 | -0.01em | Títulos de tarjeta, items de nav, subtítulos de sección |
| `--text-lg` | 20px | Poppins 600 | 1.2 | -0.01em | Títulos de página, cabeceras de panel |
| `--text-xl` | 24px | Poppins 600 | 1.2 | -0.02em | Títulos de sección, headers de dashboard |
| `--text-2xl` | 32px | Poppins 700 | 1.1 | -0.02em | KPIs grandes, números hero, contadores de resumen |

### Principios Tipográficos

- **14px es la base, no 16px.** Una interfaz de trabajo diario necesita densidad. 16px está reservado para títulos de tarjeta (`--text-md`), no para texto corriente.
- **Poppins solo arriba de 16px.** No usar Poppins en texto de trabajo — ahí va Inter siempre.
- **Inter 500 (medium) para énfasis en tablas.** No usar bold (700) dentro de tablas; el medium es suficiente y no rompe la densidad.
- **Uppercase solo en `--text-xs`.** Las etiquetas uppercase usan `letter-spacing: 0.02em` para compensar la compactación visual.
- **Tracking negativo solo en display.** Los tamaños `--text-lg`, `--text-xl`, `--text-2xl` usan tracking negativo para que los titulares se sientan apretados y con peso.

## 4. Estilo de Componentes

### Botones

**Primario (Acción)**
- Fondo: `var(--accent)` (`#3A54CC`)
- Texto: `var(--accent-on)` (`#FFFFFF`)
- Padding: `8px 16px`
- Radio: `var(--radius-sm)` (8px)
- Fuente: Inter 500, `var(--text-base)` (14px)
- Hover: `var(--accent-hover)` (`#2C40A0`)
- Uso: La acción principal de la pantalla. Solo un botón primario por vista.

**Secundario**
- Fondo: `transparent`
- Texto: `var(--fg)` (`#131A20`)
- Borde: `1px solid var(--border)` (`#DDD8CC`)
- Hover: fondo `var(--surface-warm)` (`#F0EBE0`)
- Uso: Acciones complementarias — "Cancelar", "Ver detalles".

**Ghost**
- Fondo: `transparent`
- Texto: `var(--muted)` (`#57626C`)
- Sin borde
- Hover: fondo `rgba(19, 26, 32, 0.04)`
- Uso: Acciones terciarias, botones de toolbar.

**Destructivo**
- Fondo: `var(--danger)` (`#BE3346`)
- Texto: `#FFFFFF`
- Hover: más oscuro
- Uso: "Eliminar contacto", "Cancelar visita".

### Tarjetas (Cards)

- Fondo: `var(--surface)` (`#FFFFFF`)
- Borde: `1px solid var(--border-soft)` (`#E3DBCB`)
- Radio: `var(--radius-md)` (12px)
- Sombra: `var(--elev-raised)` — `0 1px 2px rgba(27,23,18,.04), 0 12px 32px -16px rgba(27,23,18,.18)`
- Padding: `var(--sp-5)` (20px)
- Hover: sombra ligeramente más pronunciada

### Inputs y Formularios

- Fondo: `var(--surface)` (`#FFFFFF`)
- Borde: `1px solid var(--border)` (`#DDD8CC`)
- Radio: `var(--radius-sm)` (8px)
- Padding: `8px 12px`
- Fuente: Inter 400, `var(--text-base)` (14px)
- Placeholder: `var(--meta)` (`#6E6455`)
- Foco: borde `var(--accent)`, focus ring `var(--focus-ring)`
- Error: borde `var(--danger)`, mensaje en `var(--danger)` debajo del campo

### Badges y Pills

**Badge de estado**
- Padding: `2px 8px`
- Radio: `var(--radius-pill)` (9999px)
- Fuente: Inter 500, `var(--text-xs)` (12px)
- Variantes: success (verde sobre `--success-soft`), danger (rojo sobre `--danger-soft`), neutral (muted sobre arena-200)

**Chip de filtro**
- Padding: `4px 10px`
- Borde: `1px solid var(--border)`
- Radio: `var(--radius-pill)`
- Activo: fondo `var(--accent-soft)`, borde `var(--accent)`, texto `var(--accent)`

### Tablas

Las tablas son el componente más usado en Kazabi. Optimizadas para densidad:
- Cabecera: `var(--text-xs)` (12px), Inter 500, uppercase, `letter-spacing: 0.02em`, color `var(--muted)`, fondo `var(--surface-warm)`
- Fila: `var(--text-sm)` (13px), Inter 400, padding `8px 12px`, borde inferior `var(--border-soft)`
- Hover de fila: fondo `rgba(240, 235, 224, 0.5)` (arena-100 al 50%)
- Fila seleccionada: fondo `var(--accent-soft)` (`#E7EAF9`)
- Celda de acción: texto `var(--accent)`, hover underline

### Navegación / Sidebar

- Fondo sidebar: `var(--brand)` (`#0B2249`)
- Texto: `var(--brand-on)` (`#FFFFFF`) al 80% opacidad por defecto
- Item activo: fondo `var(--brand-mid)` (`#133C6F`), texto blanco 100%
- Item hover: fondo `rgba(255,255,255,0.06)`
- Iconos: `var(--brand-steel-light)` (`#5985BD`) — 20px
- Fuente items: Inter 500, `var(--text-sm)` (13px)

## 5. Principios de Layout

### Sistema de Espaciado

Escala canónica `--sp-*`, base-4 y con 12 pasos. No existe una escala paralela `--sp-*`; los adaptadores deben mapear siempre desde `--sp-*`. Reemplaza los 48 valores ad-hoc del producto actual.

| Token | Valor | Uso típico |
|-------|-------|------------|
| `--sp-0.5` | 2px | Hairline gaps, ajuste óptico de iconos |
| `--sp-1` | 4px | Gap dentro de badges, padding mínimo |
| `--sp-1.5` | 6px | Gap icono-texto, padding horizontal de chip |
| `--sp-2` | 8px | Padding-y de input, gap entre elementos inline, espacio entre filas de tabla |
| `--sp-3` | 12px | Padding interno de tarjeta (compacta), gap de lista, margin de grupo |
| `--sp-4` | 16px | Gap entre campos de formulario, gutter entre tarjetas, padding de dropdown |
| `--sp-5` | 20px | Padding de tarjeta estándar, margin entre secciones dentro de un panel |
| `--sp-6` | 24px | Padding de panel lateral, gutter del sidebar, padding de modal |
| `--sp-8` | 32px | Espaciado entre bloques mayores, gap entre secciones de formulario |
| `--sp-10` | 40px | Vertical entre secciones de una página |
| `--sp-12` | 48px | Ritmo vertical de sección en desktop |
| `--sp-16` | 64px | Separación entre secciones principales de dashboard |

### Aplicación del Espaciado

**Dentro de un componente (micro):**
- Gap icono ↔ texto: `--sp-1.5` (6px)
- Gap entre badge y label: `--sp-1` (4px)
- Padding de input: `--sp-2` (8px) vertical, `--sp-3` (12px) horizontal

**Entre componentes (meso):**
- Campos de formulario: `--sp-4` (16px) entre campos
- Tarjetas en grid: `--sp-4` (16px) gap
- Lista de items: `--sp-2` (8px) entre items

**Entre secciones (macro):**
- Dentro de un panel: `--sp-5` (20px)
- Entre secciones de página: `--sp-10` (40px) a `--sp-12` (48px)
- Dashboard sections: `--sp-16` (64px)

### Grid y Contenedor

- Ancho máximo de contenido: `1280px`
- Sidebar: ancho fijo `240px` (colapsable a `64px` icon-only)
- Gutter desktop: `24px`
- Gutter tablet: `16px`
- Gutter mobile: `12px`
- Grid de dashboard: 12 columnas, gap `16px`

### Radio de Borde

| Token | Valor | Uso |
|-------|-------|-----|
| `--radius-sm` | 8px | Botones, inputs, badges, elementos funcionales |
| `--radius-md` | 12px | Tarjetas, dropdowns, popovers, tooltips |
| `--radius-lg` | 20px | Modales, sheets, paneles flotantes |
| `--radius-pill` | 9999px | Chips de filtro, tags de estado, avatares |

## 6. Profundidad y Elevación

| Nivel | Tratamiento | Uso |
|-------|-------------|-----|
| Plano (0) | Sin sombra, `var(--bg)` | Fondo de página |
| Anillo (1) | `0 0 0 1px var(--border)` | Inputs en reposo, separación sutil |
| Elevado (2) | `0 1px 2px rgba(27,23,18,.04), 0 12px 32px -16px rgba(27,23,18,.18)` | Tarjetas, dropdowns, tooltips |
| Foco | `0 0 0 2px var(--bg), 0 0 0 4px var(--accent)` | Anillo de foco accesible |

**Filosofía de sombra:** Las sombras de Kazabi son cálidas (`rgba(27,23,18,...)` — el negro cálido arena-900) y tienen un offset vertical sutil con un spread negativo grande (`-16px`) que concentra la sombra debajo del elemento sin crear una aureola difusa. Esto produce la sensación de "tarjeta que flota ligeramente" sin drama visual.

En dark mode, las sombras cambian a `rgba(0,0,0,...)` más intensas porque el lienzo navy absorbe la luz.

## 7. Haz y No Hagas

### Haz

- Usa `--accent` (`#3A54CC`) **solamente** para botones primarios, foco, enlaces activos, y selección
- Usa `--brand` (`#0B2249`) **solamente** para sidebar, header, y elementos institucionales de marca
- Mantén 14px como base tipográfica — no la subas a 16px "por si acaso"
- Usa Inter 500 (medium) para énfasis en tablas, no bold 700
- Usa la sombra cálida `rgba(27,23,18,...)` — nunca sombras frías
- Respeta los contrastes verificados — son parte del contrato
- En dark mode, usa `#7488FF` como acento (no el `#3A54CC` que no brilla sobre navy)
- Usa `arena-400` (`#C5B69F`) como texto body sobre navy en dark mode — tiene 7.89:1

### No hagas

- No uses navy como botón o control interactivo — eso es el azul de acción
- No uses azul de acción como fondo decorativo o elemento de marca — eso es navy
- No uses `--brand-steel-light` (`#5985BD`) como texto bajo 24px — solo tiene 3.49:1
- No uses Poppins en texto de trabajo (tablas, formularios, mensajes) — ahí va Inter
- No uses sombras frías `rgba(0,0,0,...)` en tema claro — usa la base arena-900
- No inventes tamaños tipográficos fuera de la escala de 8 pasos
- No inventes valores de espaciado fuera de la escala base-4
- No uses radios de borde que no sean 8, 12, 20, o 9999px
- No pongas más de un botón primario por vista
- No uses uppercase fuera del rol `--text-xs` para etiquetas

## 8. Comportamiento Responsive

### Breakpoints

| Nombre | Ancho | Cambios clave |
|--------|-------|---------------|
| Móvil | <640px | Columna única, sidebar oculta, padding `12px` |
| Tablet | 640–1024px | Grid 2 columnas, sidebar colapsada a iconos |
| Desktop | 1024–1440px | Layout completo, sidebar expandida |
| Pantalla ancha | >1440px | Contenido centrado, márgenes generosos |

### Estrategia de Colapso

- **Sidebar:** 240px → 64px (solo iconos) → oculta (hamburger en mobile)
- **Dashboard grid:** 3–4 columnas → 2 columnas → 1 columna apilada
- **Tablas:** Scroll horizontal en mobile, columnas prioritarias visibles
- **Titulares:** `--text-2xl` (32px) → `--text-xl` (24px) → `--text-lg` (20px)
- **Tarjetas:** Grid → stack vertical con padding reducido
- **Formularios:** 2 columnas → 1 columna, campos full-width

### Touch Targets

- Mínimo 44×44px en mobile para todos los controles
- Filas de tabla: mínimo 48px de alto en touch
- Items de sidebar: 44px de alto con padding generoso
- Botones: 36px mínimo de alto en desktop, 44px en mobile

## 9. Guía de Aplicación para Agentes

### Referencia Rápida de Color

- Fondo de página: `var(--bg)` — `#F7F5EE`
- Tarjetas: `var(--surface)` — `#FFFFFF`
- Sidebar: `var(--brand)` — `#0B2249`
- Texto primario: `var(--fg)` — `#131A20`
- Texto secundario: `var(--muted)` — `#57626C`
- Timestamps: `var(--meta)` — `#6E6455`
- Borde: `var(--border)` — `#DDD8CC`
- Botón primario: `var(--accent)` — `#3A54CC`
- Selección activa: `var(--accent-soft)` — `#E7EAF9`
- Éxito: `var(--success)` — `#147A46`
- Error: `var(--danger)` — `#BE3346`
- Advertencia: `var(--warn)` — `#765B12`

### Prompts de Ejemplo

- "Diseña una tabla de contactos en `#F7F5EE`. Cabecera: 12px Inter 500 uppercase, `#57626C`, fondo `#F0EBE0`. Filas: 13px Inter 400, padding 8px 12px, borde `#E3DBCB`. Hover: arena-100 al 50%. Selección: `#E7EAF9`."
- "Crea un card de propiedad: fondo `#FFFFFF`, borde `#E3DBCB`, radio 12px, sombra `0 1px 2px rgba(27,23,18,.04), 0 12px 32px -16px rgba(27,23,18,.18)`. Título en Poppins 500 16px `#131A20`. Precio en Poppins 700 24px `#0B2249`. Botón primario `#3A54CC` 8px radio."
- "Sidebar navy `#0B2249`. Items: Inter 500 13px, texto blanco 80%. Activo: fondo `#133C6F`, texto blanco 100%. Iconos: `#5985BD` 20px."
- "Badge de estado: pill radius, 12px Inter 500. Verde: `#147A46` texto sobre `#E0F0E7` fondo. Rojo: `#BE3346` sobre `#F8E3E6`."

### Guía de Iteración

1. Fondo siempre `#F7F5EE` (arena-50), nunca blanco puro ni gris
2. Tarjetas siempre `#FFFFFF` con borde `#E3DBCB` y sombra cálida
3. Navy solo en sidebar y header — nunca en botones ni badges
4. Azul `#3A54CC` solo en botón primario, foco, selección — nunca decorativo
5. Texto base 14px Inter 400 — subir a Poppins solo desde 16px para títulos
6. Sombras con base arena `rgba(27,23,18,...)` — nunca negro frío
7. Espaciado siempre de la escala base-4 — nunca valores ad-hoc
8. Un solo botón primario por pantalla — el resto son secundarios o ghost
