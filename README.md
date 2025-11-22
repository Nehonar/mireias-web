Mireias Web
============
Base de proyecto para la web de una psicóloga con estética zen y backend ligero para gestión de consultas por correo.

Estructura
----------
- `frontend/`: Código público (HTML/CSS/JS), organizado para maximizar reutilización (DRY) y aislar responsabilidades (SOLID).
- `backend/`: API mínima para recibir solicitudes y enviarlas por email, separada por capas (config, routes, controllers, services).

Flujo recomendado
-----------------
1) Diseñar vistas en `frontend/src/pages` y componentes reutilizables en `frontend/src/components`.
2) Centralizar colores y espaciados en `frontend/src/styles/theme.css` para cambiar la paleta sin tocar múltiples archivos.
3) Añadir lógica client-side en `frontend/src/utils` si es necesaria; mantener la UI desacoplada de efectos y servicios.
4) Implementar el endpoint de contacto en `backend/src/routes` → `controllers` → `services` con validación y seguridad por defecto.

Seguridad y cifrado
-------------------
- Servir siempre bajo HTTPS y con HSTS; los formularios deben enviar datos cifrados en tránsito.
- Configurar variables sensibles via `.env` (ver `backend/.env.example`), nunca hardcodear secretos.
- Añadir rate limiting y CSRF en el backend al exponer endpoints públicos (middleware en `backend/src/middlewares`).
- Definir cabeceras de seguridad (CSP, X-Frame-Options, etc.) en la capa de middleware.

Paleta inicial (zen, naturaleza)
--------------------------------
- Fondo: `--color-sand` (beige suave)
- Acentos verdes: `--color-sage`, `--color-olive`
- Marrones de detalle: `--color-bark`, `--color-clay`
- Contraste de texto: `--color-ink`

Próximos pasos
--------------
- Crear la página principal en `frontend/src/pages/home` usando las variables de `theme.css`.
- Levantar un servidor estático sencillo (ej. Vite o Express estático) y una API POST `/contact` en `backend`.
- Añadir pruebas unitarias para validación de payload y envío de correo en `backend/tests`.
