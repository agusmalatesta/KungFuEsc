# El Camino del Puño — blog de kung fu

Sitio estático hecho con Jekyll, listo para GitHub Pages, con búsqueda (Pagefind) y comentarios (Giscus).

## Puesta en marcha (una sola vez)

1. **Crea un repositorio en GitHub** (por ejemplo `kungfu-blog`) y sube todos estos archivos.

2. **Activa GitHub Pages vía Actions:**
   - Ve a *Settings → Pages*.
   - En "Build and deployment", selecciona **Source: GitHub Actions**.
   - Haz push a `main` — el workflow en `.github/workflows/deploy.yml` construye el sitio, indexa la búsqueda y lo publica solo.

3. **Ajusta `_config.yml`:**
   - `url`: la URL que te da GitHub Pages (ej. `https://tu-usuario.github.io`).
   - `baseurl`: `/nombre-del-repo` (déjalo vacío `""` si usas un dominio propio o un repo `tu-usuario.github.io`).

4. **Activa los comentarios (Giscus):**
   - En tu repo: *Settings → General → Features → activa "Discussions"*.
   - Instala la app en https://github.com/apps/giscus (dale acceso a este repo).
   - Ve a https://giscus.app, mete la URL de tu repo, elige la categoría de Discussions (ej. "General"), y copia los valores `data-repo-id` y `data-category-id`.
   - Pégalos en `_config.yml` dentro de la sección `giscus:`.

5. **Escribe tu primer post real:**
   - Copia `_posts/2026-07-09-bienvenida-al-dojo.md` como plantilla.
   - Nombra el archivo `AAAA-MM-DD-titulo-corto.md`.
   - Usa `categories:` con una de: Formas, Filosofía, Historia, Entrenamiento (o agrega más en `_config.yml` → `categories_list`, y crea la carpeta correspondiente en `categoria/`).

## Probarlo en tu computadora antes de publicar (opcional)

Necesitas Ruby instalado.

```bash
bundle install
bundle exec jekyll serve
```

Abre `http://localhost:4000`. Nota: la búsqueda (Pagefind) solo se genera en el build de GitHub Actions/producción, no en `jekyll serve` local, a menos que corras `npx pagefind --site _site` manualmente después de un `jekyll build`.

## Estructura

```
_posts/          → tus entradas (Markdown)
_layouts/        → plantillas HTML (default, home, post, category)
_includes/       → piezas reutilizables (comentarios)
categoria/       → una carpeta por categoría, genera /categoria/nombre/
assets/css/      → estilos (identidad "tinta y sello")
.github/workflows/deploy.yml → build + búsqueda + publicación automática
```
