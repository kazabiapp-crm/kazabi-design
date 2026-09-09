# Kazabi — Guía de Uso

Paquete Design System 2.0 para agentes y revisores de OpenDesign.

## Orden de Lectura

1. Lee este archivo primero para entender el contrato del paquete.
2. Lee `DESIGN.md` para intención visual, restricciones y anti-patrones.
3. Pega `tokens.css` en el primer bloque `<style>` del artefacto antes de escribir CSS de componentes.
4. Usa `components.manifest.json` para el inventario compacto de componentes; abre `components.html` cuando necesites selectores exactos o estados.
5. Inspecciona las páginas en `preview/` para verificación visual rápida.

## Regla Cardinal

**Navy (#0B2249) = MARCA.** Solo sidebar, header, fondos institucionales.
**Azul (#3A54CC) = ACCIÓN.** Solo botón primario, foco, enlaces activos, selección.

Nunca mezclar estos roles. Un botón navy es un error. Un fondo decorativo azul es un error.

## Highlights del Diseño

- Fondo arena `#F7F5EE` con tarjetas blancas `#FFFFFF` — calidez sin decoración
- Poppins 600 para display (≥16px), Inter Variable para texto de trabajo
- Base tipográfica 14px — interfaz densa para jornadas de trabajo largas
- Escala tipográfica cerrada: 8 pasos de 11px a 32px — no inventar valores
- Escala de espaciado base-4: 12 pasos de 2px a 64px — no inventar valores
- Sombras cálidas `rgba(27,23,18,...)` — nunca frías
- Radios 8/12/20/9999px — no otros valores

## Haz

- Preserva los nombres de token del esquema para que el switch entre marcas funcione.
- Usa `--accent` para acciones primarias, enlaces, foco, y un solo elemento focal claro.
- Reutiliza los grupos de componentes de `components.manifest.json` antes de inventar controles nuevos.
- En dark mode usa `#7488FF` como acento y `#C5B69F` como texto body sobre navy.

## Evita

- No uses hex crudos fuera del bloque `:root` de tokens.
- No redefinir valores de Tailwind o design tokens independientemente de `tokens.css`.
- No agregar recetas de componentes que no estén representadas en `components.html` o `DESIGN.md`.
- No uses Poppins en texto de trabajo (tablas, formularios, mensajes).
- No pongas más de un botón primario por vista.
