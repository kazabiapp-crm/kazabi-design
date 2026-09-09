# Kazabi Design System

Fuente única de la identidad visual de Kazabi: la app, el sitio, los correos y las
presentaciones salen de aquí. Si un color, un tamaño de letra o un espaciado no está
en `tokens.css`, no existe.

## Qué hay dentro

| Archivo | Para qué |
|---|---|
| `DESIGN.md` | El contrato de marca en prosa. Lo que lee un agente antes de dibujar. |
| `tokens.css` | **La fuente de verdad.** Variables CSS, tema claro y oscuro. |
| `design-tokens.json` | Los mismos tokens en JSON, para scripts (correos, generadores). |
| `tailwind-v4.css` | Bloque `@theme` para el sitio Astro. |
| `components.html` | Los componentes canónicos: botón, campo, tabla, badge, card. |
| `preview/` | Colores, tipografía y espaciado para mirar. |
| `USAGE.md` | Cómo aplicarlo. |

## Las reglas que no se negocian

**El navy es la marca. El azul es la acción.** `#0B2249` da el peso; `#3A54CC` es
solo botón primario, foco y estado activo. No se intercambian.

**Una sola escala de espaciado: `--sp-*`.** No existe `--space-*`. Si aparece, es un
error de copia.

**Una sola escala tipográfica**, de `--text-2xs` (11px) a `--text-2xl` (32px). Ocho
pasos. Nada de 9,5px ni 12,5px: si un tamaño no está en la escala, no se usa.

**Los contrastes están medidos, no estimados.** Cualquier color nuevo entra con su
ratio comprobado o no entra.

## Usarlo en OpenDesign

Clonar este repo dentro de la carpeta de sistemas del usuario:

```
%APPDATA%\Open Design\namespaces\release-stable-win\data\design-systems\kazabi
```

El catálogo se re-escanea solo; no hace falta reiniciar la app. Después aparece
como **Kazabi** en el selector `Sistema de diseño`.

## Usarlo en el código

- **webapp** (React): `tokens.css` reemplaza a `webapp/src/styles/tokens.css`.
- **sitio** (Astro + Tailwind v4): `tailwind-v4.css` alimenta el bloque `@theme`.
- **correos**: `design-tokens.json`, compilado a estilos inline — los clientes de
  correo no leen variables CSS.

## Pendiente

- El logo son tres PNG a 1080px. **No hay vector maestro.** Se nota en PPTX y en
  pantallas grandes.
- La migración del código existente a estas escalas no está hecha.
