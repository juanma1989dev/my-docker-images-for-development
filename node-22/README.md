# 🐳 Imagen base ligera de Node.js (Debian Slim + pnpm)

Esta imagen Docker proporciona un entorno ligero y optimizado para el desarrollo de aplicaciones Node.js, basada en **Debian Slim** y con **pnpm** preinstalado mediante **Corepack**.

Está pensada para entornos de desarrollo o CI/CD que buscan rapidez, limpieza y facilidad de extensión.

---

## 🚀 Características principales

- 🧱 **Basada en `node:22-slim`** → pequeña, rápida y estable  
- ⚙️ **Corepack + pnpm** preconfigurados (gestor de paquetes eficiente)  
- 🔐 Incluye herramientas útiles para desarrollo:
  - `git`
  - `curl`
  - `bash`
  - `openssl`
- 🧑‍💻 Usuario `node` por defecto (no root)
- 📂 Directorio de trabajo predefinido: `/workspace`

---

## 🧩 Contenido del Dockerfile

```dockerfile
# Imagen base ligera de Node.js basada en Debian Slim
FROM node:22-slim

# Configurar variables de entorno recomendadas
ENV NODE_ENV=development
ENV PNPM_HOME="/usr/local/share/pnpm"
ENV PATH="$PNPM_HOME:$PATH"

# Instalar dependencias necesarias del sistema (útiles en desarrollo)
RUN apt-get update && apt-get install -y \
    git \
    curl \
    bash \
    openssl \
    && rm -rf /var/lib/apt/lists/*

# Habilitar e instalar pnpm usando corepack
RUN corepack enable && corepack prepare pnpm@latest --activate

# Crear y usar un directorio de trabajo
WORKDIR /workspace

# Cambiar el propietario del directorio al usuario node (ya existe en la imagen base)
RUN chown -R node:node /workspace
USER node
