# Odoo-Energiapd

Página de inicio de sesión (reforzamiento) portada desde el componente React
`InicioReforzamientoPage.tsx` a HTML estático para GitHub Pages.

Al iniciar sesión registra el acceso (mejor esfuerzo) y redirige a la suite privada.

## Configurar destino

Edita `public/index.html` y cambia:

```js
const URL_SUITE_PRIVADA = 'http://89.167.20.163:8080';
```

El fondo está en `public/reforzamiento/fondo-login.webp` y el logo es un SVG inline.

## Probar en local

```bash
npm start   # http://localhost:3000
```

## Despliegue

Cada push a `main` publica la carpeta `public/` en GitHub Pages.
Activar una sola vez: **Settings → Pages → Source: GitHub Actions**.
