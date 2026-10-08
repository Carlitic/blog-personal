# Blog Personal — Carlos Castaños

Blog técnico personal construido con [Astro](https://astro.build) y Markdown tipado mediante Content Collections.

## 🚀 Flujo de trabajo: Escribir un nuevo post

Para publicar un nuevo artículo:

1. Crea un archivo `.md` dentro de `src/content/posts/`, por ejemplo: `mi-nuevo-articulo.md`.
2. Incluye el encabezado (*frontmatter*) obligatorio:

```markdown
---
title: "Título de tu artículo"
description: "Breve resumen para el feed y etiquetas meta SEO."
pubDate: 2026-10-08
---

Tu contenido en Markdown acá...
```

3. Guarda los cambios, realiza el commit y empuja a GitHub:

```bash
git add src/content/posts/mi-nuevo-articulo.md
git commit -m "feat(blog): add post sobre mi-nuevo-articulo"
git push origin main
```

La **GitHub Action** configurada compilará y desplegará automáticamente el sitio en GitHub Pages.

---

## 🛠️ Comandos locales

| Comando | Acción |
| :--- | :--- |
| `npm run dev` | Inicia el servidor de desarrollo local en `http://localhost:4321` |
| `npm run build` | Compila el sitio estático optimizado en la carpeta `dist/` |
| `npm run preview` | Previsualiza localmente el resultado final de `dist/` |

---

## 🏗️ Arquitectura del proyecto

- **`src/content/posts/`**: Artículos en Markdown. Cada archivo genera su propia ruta `/posts/<slug>`.
- **`src/content.config.ts`**: Esquema de validación estricta (Zod) para el frontmatter.
- **`src/components/`**: Componentes reutilizables (`Header`, `Footer`, `Sidebar`, `PostCard`).
- **`src/layouts/`**: `Layout.astro` con metadatos y enlaces semánticos.
- **`src/styles/`**: Tokens de diseño y estilos nativos CSS (`estilos.css`).
- **`.github/workflows/deploy.yml`**: Pipeline de CI/CD para GitHub Pages.
