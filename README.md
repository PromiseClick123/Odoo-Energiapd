# Odoo-Energiapd

Página de "Cargando…" que redirige automáticamente tras 4 segundos.

## Configurar destino

Edita `public/index.html` y cambia:

```js
const REDIRECT_URL = "https://example.com";
const SECONDS = 4;
```

## Probar en local

```bash
npm start   # http://localhost:3000
```

## Despliegue

Cada push a `main` publica la carpeta `public/` en GitHub Pages.
Activar una sola vez: **Settings → Pages → Source: GitHub Actions**.
