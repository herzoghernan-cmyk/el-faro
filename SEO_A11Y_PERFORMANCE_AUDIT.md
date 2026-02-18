# Auditoría técnica: SEO, accesibilidad y performance (EL FARO)

Este documento resume hallazgos y mejoras recomendadas para el sitio estático, priorizando cambios sin impacto visual.

## 1) SEO técnico

### Hallazgos
- Existía una directiva `noindex` en la home, lo que bloqueaba indexación orgánica.
- Había placeholders en metadatos sociales (`TU-DOMINIO.com`) para Open Graph y Twitter.
- `robots.txt` y `sitemap.xml` tenían dominio placeholder y ya fueron alineados al dominio actual de publicación.
- Hay más de un `<h1>` en la página principal (riesgo de ambigüedad semántica).

### Mejoras aplicadas
- Se habilitó indexación con `robots: index,follow` y previews enriquecidas.
- Se normalizó `og:image` y `twitter:image` a ruta local (`/assets/og-image.png`).
- Se completaron campos `og:image:alt` y `twitter:image:alt`.
- Se alinearon `robots.txt` y `sitemap.xml` al dominio actual y se añadieron señales regionales (`hreflang="es"`, `og:locale`).
- Se incorporó datos estructurados adicionales de organización (`Organization`) y se endurecieron enlaces externos con `rel="noopener noreferrer"`.

### Mejoras recomendadas (siguiente iteración)
1. Consolidar estructura de headings para dejar un único `<h1>` principal.
2. Añadir datos estructurados más específicos (Organization / ProfessionalService / ContactPoint).
3. Verificar estado HTTP de `404` en hosting/CDN (la página ya no usa meta refresh).

---

## 2) Accesibilidad (A11y)

### Hallazgos
- Campo de formulario principal sin `name`, sin `required` y sin `autocomplete`.
- Varias imágenes con `alt=""`; algunas pueden ser decorativas, otras no.

### Mejoras aplicadas
- Se mejoró el input de contacto con:
  - `name="fullName"`
  - `required`
  - `aria-required="true"`
  - `autocomplete="name"`

### Mejoras recomendadas (siguiente iteración)
1. Auditar imagen por imagen para distinguir decorativas (`alt=""`) vs. informativas (`alt` descriptivo).
2. Asegurar foco visible robusto para navegación con teclado en botones/enlaces críticos.
3. Añadir mensaje de error accesible (`aria-live`) para validación de formulario.
4. Revisar contraste real de texto sobre imágenes (WCAG AA) con herramienta automatizada.

---

## 3) Performance web

### Hallazgos
- El HTML exportado contiene scripts/estilos de herramientas de terceros y código embebido extenso.
- Se detectaron restos de extensión de navegador inyectados en el HTML exportado (ruido innecesario).

### Mejoras aplicadas
- Se removieron nodos inyectados por extensión (`glasp-extension`) del HTML final.
- Se añadieron metadatos de plataforma seguros (`theme-color`, `referrer`) sin costo de render visual.

### Mejoras recomendadas (siguiente iteración)
1. Medir con Lighthouse/WebPageTest (móvil) y priorizar LCP/CLS/INP.
2. Evaluar self-hosting y compresión de assets críticos (imágenes en WebP/AVIF cuando sea posible).
3. Revisar JS de engagement/terceros para cargar condicionalmente (solo cuando aporte valor real).
4. Configurar headers de caché agresiva para `assets/*` con nombres versionados.

---

## 4) Checklist de despliegue profesional (sin cambiar diseño)

- [x] Dominio actual aplicado en `sitemap` y `robots` (pendiente actualizar si cambia en producción).
- [ ] `sitemap.xml` validado en Search Console.
- [ ] Propiedad de Search Console y Bing Webmaster Tools verificadas.
- [ ] Medición base Lighthouse guardada (antes/después).
- [ ] Validación WCAG AA (automática + revisión manual de teclado).

