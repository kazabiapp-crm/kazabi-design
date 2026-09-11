# Kazabi Signal — Guía de uso

Paquete Design System 2.0 para agentes y revisores (Kazabi y OpenDesign).

> **Estado:** aprobado el 2026-09-11, **sin aplicar**. La app y el sitio siguen con `../tokens.css`.
> No uses estos tokens en código de producción hasta que `README.md` diga que la migración se hizo.

## Orden de lectura

1. Este archivo: el contrato del paquete.
2. `DESIGN.md`: intención visual, restricciones y anti-patrones.
3. `tokens.css` completo (claro, oscuro y alias) en el primer bloque `<style>`, antes del CSS de componentes.
4. `components.manifest.json`: inventario de componentes y sus clases.
5. Referencias vivas, ya corregidas: `referencias/app.html` (aplicación) y `referencias/landing.html` (marketing).

## Regla cardinal

**Navy (`--brand` `#0b2249`) = MARCA.** Logotipo, capítulos institucionales, superficie del tema oscuro.
**Azul (`--accent` `#0071e3`) = ACCIÓN.** Botón primario, foco, selección.

Un botón navy es un error. Un fondo decorativo azul es un error.

## Temas

- Claro por defecto en `:root`.
- Oscuro con `data-theme="dark"` en `<html>` (la app), `.dark` o `.theme-dark` (Open Design), o por sistema con `prefers-color-scheme` si no hay `data-theme="light"`.

## Haz

- Texto con `--fg` / `--fg-2` / `--muted`. `--meta` solo para iconos en claro.
- Texto o enlaces azules con `--link` (funciona en los dos temas).
- Bordes de campo con `--border-control`; `--border` es decorativo.
- Un solo botón primario por vista; el resto `secondary-button` o `nav-item`.
- Hover solo dentro de `@media (hover: hover)`.
- Nombres del contrato (`--bg`, `--surface`, `--sp-*`). Los alias `--canvas`, `--panel`, `--space-*` existen para compatibilidad.

## Evita

- Hex crudos fuera de `tokens.css`.
- `--accent-active` o `--accent` como color de texto.
- Sombras en tarjetas en reposo.
- Color como única señal de estado.
- Paletas secundarias que compitan con el azul de acción.
