---
version: alpha
name: Dr. Ronny Kershenovich · Genética Médica
description: Sitio estático de un médico genetista en CDMX. Dos páginas (index.html, prensa.html), bilingüe ES/EN.
colors:
  navy: "#1a237e"
  navy-deep: "#0d1340"
  blue: "#1565c0"
  sky: "#42a5f5"
  sky-soft: "#90caf9"
  bg-light: "#f4f7fb"
  white: "#f7f9ff"
  text: "#0d1b4b"
  gray: "#56637f"
  border: "#dce3f0"
  whatsapp: "#15803d"
  whatsapp-hover: "#166534"
typography:
  display:
    fontFamily: Cormorant Garamond
    fontSize: 4.5rem
    fontWeight: 300
    lineHeight: 1.1
  heading:
    fontFamily: Cormorant Garamond
    fontSize: 2.8rem
    fontWeight: 300
    lineHeight: 1.2
  card-heading:
    fontFamily: Cormorant Garamond
    fontSize: 1.1rem
    fontWeight: 400
  body:
    fontFamily: DM Sans
    fontSize: 1.0625rem
    fontWeight: 400
    lineHeight: 1.8
  body-sm:
    fontFamily: DM Sans
    fontSize: 0.95rem
    fontWeight: 400
    lineHeight: 1.6
  meta:
    fontFamily: DM Sans
    fontSize: 0.875rem
    fontWeight: 400
  label:
    fontFamily: DM Sans
    fontSize: 0.75rem
    fontWeight: 500
    letterSpacing: 0.25em
rounded:
  none: 0px
  sm: 2px
  md: 4px
  pill: 20px
spacing:
  gutter-mobile: 1.5rem
  gutter-desktop: 4rem
  section: 6rem
components:
  button-whatsapp:
    backgroundColor: "{colors.whatsapp}"
    textColor: "{colors.white}"
    rounded: "{rounded.sm}"
    padding: 0.85rem 1.8rem
  button-whatsapp-hover:
    backgroundColor: "{colors.whatsapp-hover}"
  button-doctoralia:
    backgroundColor: "{colors.sky}"
    textColor: "{colors.navy}"
    rounded: "{rounded.sm}"
    padding: 0.85rem 1.8rem
  nav-bar-scrolled:
    backgroundColor: "rgba(26,35,126,0.85)"
    textColor: "{colors.white}"
  filter-chip:
    backgroundColor: "transparent"
    textColor: "{colors.gray}"
    rounded: "{rounded.pill}"
  filter-chip-active:
    backgroundColor: "{colors.navy}"
    textColor: "{colors.white}"
---

# Dr. Ronny Kershenovich · DESIGN.md

## Overview

Sitio de un médico genetista que habla en primera persona y de tú al paciente. El tono es sereno y clínico: azul marino profundo, un video tenue de ADN de fondo y tipografía serif clásica para los títulos. El objetivo de cada página es que el paciente agende por WhatsApp o Doctoralia.

La referencia de movimiento es una app de Apple: respuesta inmediata al tocar, transiciones cortas e interrumpibles, y respeto total a "Reducir movimiento" y "Reducir transparencia". Los detalles viven en `plans/`.

## Colors

- **Navy (#1a237e):** el color de marca. Barra superior, secciones oscuras, filtros activos.
- **Navy deep (#0d1340):** fondo de la página detrás del video.
- **Blue (#1565c0):** texto de acento sobre fondo claro (etiquetas, enlaces). Pasa AA sobre blanco (5.7:1).
- **Sky (#42a5f5):** acento sobre fondo oscuro y botón de Doctoralia. No usar como texto sobre blanco (2.6:1).
- **Sky soft (#90caf9):** texto pequeño de acento sobre la barra de vidrio.
- **Gray (#56637f):** texto secundario. Oscurecido desde #6b7a99 para pasar AA sobre `bg-light` (5.6:1).
- **WhatsApp (#15803d):** verde oscurecido para que el texto blanco pase AA (5.0:1). El verde de marca #25d366 solo llega a 2:1.

## Typography

- **Cormorant Garamond 300** para nombre, títulos de sección y títulos de tarjeta. Los títulos van en un solo estilo y color: sin palabras en cursiva ni de otro color dentro del título (regla de Hallmark).
- **DM Sans** para todo lo demás. El texto corrido va a 15–17px; nada de contenido baja de 14px.
- **Etiquetas** (menú, subtítulos, tipo de nota en Prensa) en DM Sans, tamaño normal o un poco menor, en minúsculas normales y sin espaciado extra. Nada en MAYÚSCULAS espaciadas. No se ponen etiquetas encima de un título que ya dice lo mismo.
- **Puntuación:** no se unen datos con "·" ni con guiones largos; se usan comas, saltos de línea o "y". Las comillas son tipográficas (“ ”, ’).

## Layout

- Contenedor con márgenes de 4rem en escritorio y 1.5rem en móvil.
- Secciones alternan fondo claro (`bg-light` o blanco) y oscuro (navy translúcido sobre el video).
- Puntos de quiebre: 960px (menú hamburguesa, una columna en la mayoría de grids), 768px (Prensa), 600px (especialidades a una columna).

## Elevation & Depth

- La barra superior es vidrio: navy al 85% con `blur(20px) saturate(180%)`, y sólida con "Reducir transparencia".
- Sombra suave solo en la foto del hero, en su insignia y en las tarjetas de Prensa al pasar el mouse.

## Shapes

- Esquinas casi rectas: 2px en botones, 4px en tarjetas. Píldora (20px) solo en filtros y en el botón EN/ES de Prensa.

## Components

- **Botones:** al presionar se encogen a 97% en 100ms y vuelven en 160ms con `--ease-out`. El hover (subir 2px) solo existe con mouse.
- **Menú móvil:** se desenrolla desde la barra con `clip-path` y `--ease-drawer`; el ☰ se convierte en ✕.
- **Filtros de Prensa:** al cambiar, las tarjetas entran con un fundido de 250ms y 30ms entre una y otra.
- **Iconos:** SVG de trazo 2px estilo Lucide. Nada de emoji como icono.

## Do's and Don'ts

- Do mantener contraste AA en todo el texto; revisar con `npx @google/design.md lint DESIGN.md`.
- Do escribir en primera persona del doctor y de tú al lector, sin frases de eslogan ni superlativos sin fuente.
- Do usar `var(--ease-out)` y `var(--ease-drawer)`; no escribir curvas a mano.
- Don't poner etiquetas pequeñas encima de los títulos ni numerar secciones (01, 02…).
- Do escribir todo color y tipografía como token en `:root`; nada de colores sueltos en las reglas (Hallmark lo revisa con `sloplint.mjs`).
- Do dar a cada enlace y botón un contorno visible al navegar con teclado (`:focus-visible`).
- Don't usar `transition: all` ni animar `padding`, `width` o `height`.
- Don't presentar puestos pasados como actuales: el cargo actual es Director Médico en Géntodos.
