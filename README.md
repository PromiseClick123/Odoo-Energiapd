# Odoo-Energiapd

Página de inicio de sesión (reforzamiento) portada desde el componente React
`InicioReforzamientoPage.tsx` a HTML estático para GitHub Pages.

Al iniciar sesión registra el acceso (mejor esfuerzo) y redirige a la suite privada.

## Configurar destino y bitácora

Edita `public/index.html` (bloque de configuración del `<script>`):

```js
const API_BASE = 'https://reforzamiento.energiapd.com'; // backend que guarda la bitácora
const URL_SUITE_PRIVADA = 'http://89.167.20.163:8080';  // destino tras el login
```

El fondo está en `public/reforzamiento/fondo-login.webp` y el logo es un SVG inline.
La página siempre se muestra en **tema claro** (las variantes `dark:` están desactivadas).

## Bitácora de accesos (backend)

GitHub Pages es estático y no puede guardar nada. Al pulsar "Iniciar sesión", la
página hace un POST (mejor esfuerzo) a:

```
POST {API_BASE}/api/v1/reforzamiento/acceso   body: { "identificador": "<correo o usuario>" }
```

Ese endpoint ya existe en el backend NestJS de `energiapd-portal-publico`: guarda
el identificador + fecha como bitácora, y la suite privada la sincroniza vía
`GET/POST /api/v1/sync/reforzamiento/...` con `SYNC_TOKEN`. La contraseña **no** se
envía ni se guarda; la autenticación real la hace la suite privada tras el redirect.

**Requisito CORS:** el backend permite orígenes por la variable `FRONTEND_URL`
(separados por coma). Añade ahí el origen de Pages:

```
FRONTEND_URL=https://reforzamiento.energiapd.com,https://promiseclick123.github.io
```

Si el POST falla (backend caído, CORS, etc.) la página redirige igualmente.

## Probar en local

```bash
npm start   # http://localhost:3000
```

## Despliegue

Cada push a `main` publica la carpeta `public/` en GitHub Pages.
Activar una sola vez: **Settings → Pages → Source: GitHub Actions**.
