# Caudal · San Pedro — Landing

Landing page single-page de **Caudal**, hamburguesería y birrería en el centro de San Pedro (Buenos Aires).
Stack: HTML5 + Tailwind CSS vía CDN + JavaScript vanilla. Cero build tools, cero dependencias a instalar — abrís `index.html` con doble click y anda.

## URL pública

`TODO: completar tras el deploy a GitHub Pages`

## Contacto de marca (ya integrado)

- **WhatsApp:** +54 9 11 5459-6266 → `https://wa.me/5491154596266`
- **Email:** alannaimtapia@gmail.com
- **Instagram:** @caudal.sanpedro *(reservar handle definitivo)*

## TODOs de datos

Reemplazar en `index.html` (buscar `TODO:`):

- Dirección exacta del local (`[calle + número]`) — aparece en navbar, sección "Dónde estamos" y footer.
- Coordenadas / embed real de Google Maps — iframe de la sección "Dónde estamos".
- Handle definitivo de Instagram si difiere de `@caudal.sanpedro`.
- URL canonical (`TODO_DOMAIN`) — meta OG, twitter, `<link rel=canonical>`.
- Archivo `carta.pdf` en `/assets/` para el botón "Ver carta completa".

## TODOs de assets

Subir a `/assets/` con estos nombres exactos para que la landing los tome:

- `logo.svg` — logo color sobre fondo verde (versión hero + navbar).
- `logo-mono.svg` — logo monocromo crema brioche para el footer.
- `favicon.ico` 32x32 + `favicon.svg` vectorial.
- `og-image.jpg` 1200x630 — preview de redes y WhatsApp.
- `hero.jpg` 1920x1080 — fondo del hero (hay fallback de Unsplash mientras tanto).
- `carta.pdf` — carta completa para imprimir / descargar.
- `lugar-1.jpg` a `lugar-4.jpg` — reemplazan las imágenes temporales de Unsplash en la sección "El lugar".

Los prompts de generación de imagen (Midjourney / Flux) están embebidos como comentarios HTML justo arriba de cada `<img>` en `index.html`. Para generar: copiar prompt, tirar 8-12 generaciones, elegir, pasar por Squoosh (WebP 80 con fallback JPG), renombrar al nombre exacto del asset, commit + push.

## Cómo reemplazar assets

1. Dejá tu archivo en `/assets/` con el nombre exacto de la lista de arriba.
2. `git add assets/<archivo> && git commit -m "feat: <descripción>"`.
3. `git push`. GitHub Pages actualiza en 1-2 minutos.

## Stack y decisiones técnicas

- **HTML5 + Tailwind CDN** — sin build, sin Node, sin npm install.
- **Google Fonts** (Archivo Black + Inter) con `preconnect`.
- **Paleta** como CSS variables en `:root` + extendida en `tailwind.config`.
- **Animaciones:** fade + translateY + scale vía `IntersectionObserver` con staggering. Respeta `prefers-reduced-motion`.
- **Imágenes temporales:** Unsplash con `loading="lazy"`. Se reemplazan con assets propios cuando estén.
- **Form de reserva:** vanilla JS, sin backend. Dos destinos — WhatsApp (primario) o email — usando `wa.me` y `mailto:` respectivamente.
- **Accesibilidad:** un solo `<h1>`, jerarquía de `<h2>`, `aria-label` en íconos, `aria-invalid` en errores de form, outline de focus amarillo, soporte `prefers-reduced-motion`.
- **Mobile-first:** navbar con drawer lateral, botón WhatsApp flotante, grids que colapsan a 1 columna, tipografía con `clamp()`.

## Cómo correrlo localmente

Opción 1 — doble click en `index.html`.

Opción 2 — servidor simple:

```bash
cd caudal-landing
python3 -m http.server 8766
# abrir http://localhost:8766
```

## Deploy

Configurado para **GitHub Pages** desde `main` / root.

## Licencia

Código del sitio: uso libre para Caudal · San Pedro.
Imágenes temporales: provenientes de Unsplash (uso comercial permitido, ver [licencia](https://unsplash.com/license)). Reemplazar por material propio antes del lanzamiento oficial.
