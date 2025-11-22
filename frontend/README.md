Frontend
========
UI pública con estética zen (beige + verdes + marrones). El objetivo es mantener responsabilidades claras:

- `src/pages`: vistas completas (home, servicios, contacto).
- `src/components`: piezas reutilizables (hero, cards, botones, formulario).
- `src/styles`: tema y estilos globales; cambiar la paleta en `theme.css` evita tocar múltiples archivos (DRY).
- `src/utils`: helpers de formato, validación en cliente, hooks o adaptadores de API.
- `public`: fuentes y assets estáticos (imágenes, íconos, manifiestos).

Buenas prácticas
----------------
- Importa `styles/global.css` en el entrypoint.
- Mantén los componentes puros y recibe datos via props; evita lógica de red en la vista.
- Usa variables CSS de `theme.css` para colores y espaciados.
- Prioriza accesibilidad (labels, aria, contrastes) y layout fluido para móvil/desktop.
