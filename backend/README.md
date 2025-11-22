Backend (API de contacto)
==========================
Objetivo: exponer un endpoint POST `/contact` que valide y envíe mensajes por correo de forma segura.

Capas
-----
- `src/routes`: define rutas y middlewares de entrada (rate limit, CSRF, CORS).
- `src/controllers`: orquesta validación y delega en servicios.
- `src/services`: lógica de dominio (envío de email, logging).
- `src/config`: configuración (dotenv, transporte SMTP, cors).
- `src/middlewares`: seguridad y observabilidad (helmet, limiter, sanitización).
- `src/utils`: helpers puros (validaciones, formateo).

Seguridad mínima esperada
-------------------------
- Forzar HTTPS en despliegue y enviar `Strict-Transport-Security`.
- Desinfectar entrada y validar contra un esquema antes de tocar servicios.
- Rate limiting en rutas públicas y bloqueo por IP tras exceso.
- Cabeceras de seguridad (CSP, X-Frame-Options, X-Content-Type-Options).
- Registrar auditoría de envíos para detectar abuso (sin almacenar contenido sensible en claro).

Configuración
-------------
1) Copia `.env.example` a `.env` y completa SMTP y secretos.
2) En local, usa túnel HTTPS (ngrok o similar) si pruebas formularios; evita enviar datos en HTTP.
3) Añade pruebas en `backend/tests` para validar payload y manejo de errores de SMTP.
