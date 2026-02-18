# EL FARO — Sitio estático (PRO)

Este proyecto es un export estático (HTML/CSS/JS) listo para publicar **sin build**.

## Estructura
- `index.html` (entrada principal)
- `assets/` (CSS/JS/imagenes)
- `robots.txt`, `sitemap.xml`, `404.html`
- `.nojekyll` (recomendado para GitHub Pages)

## Publicar en GitHub Pages (rápido)
1. Subí esto a un repo (rama `main`).
2. GitHub → **Settings → Pages**
3. **Deploy from branch** → `main` / **root**
4. Guardar.

> Nota: reemplazá `TU-DOMINIO.com` en `index.html`, `robots.txt`, `sitemap.xml` por tu dominio real cuando lo tengas.

## Publicar en Hostinger (File Manager / FTP)
Subí todos los archivos al directorio `public_html/`.

## Checklist SEO (pendiente de completar)
- [ ] Reemplazar `TU-DOMINIO.com` por el dominio final
- [ ] Agregar `assets/og-image.png` (1200x630 recomendado)
- [ ] Agregar favicon real (`assets/favicon.ico`)
