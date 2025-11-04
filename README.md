# 🧩 Colección de Imágenes Base Personalizadas para Desarrollo

Este repositorio contiene una serie de **imágenes Docker personalizadas** pensadas para entornos de desarrollo modernos, ligeros y consistentes.

Las imágenes están optimizadas para proyectos que usan **Node.js**, **Laravel (PHP)** y otras tecnologías comunes del ecosistema web.

---

## 🚀 Imágenes disponibles

### 🟢 1. Node.js + pnpm (ligera)

**Base:** `node:22-slim`  
**Propósito:** Entorno de desarrollo para proyectos basados en React, Vite, Inertia o cualquier stack moderno con Node.js.

**Características:**
- Basada en Debian Slim (imagen ligera)
- Incluye `pnpm` mediante `corepack`
- Herramientas de desarrollo (`git`, `curl`, `bash`, `openssl`)
- Usuario `node` por defecto
- Directorio de trabajo: `/workspace`

**Uso:**
```bash
docker build -t node-slim-pnpm ./node
docker run -it --rm -v $(pwd):/workspace node-slim-pnpm bash
