# Dockerfile para Entorno de Desarrollo Laravel

Este Dockerfile crea una imagen de Docker completa y lista para usar, optimizada para el desarrollo de aplicaciones **Laravel**.  
La imagen incluye todas las dependencias necesarias para empezar a trabajar de inmediato, sin necesidad de instalaciones adicionales en el contenedor.

---

## 📦 Contenido de la Imagen

La imagen `php-laravel:8.4` contiene la siguiente pila de desarrollo:

- **PHP 8.4**: La última versión de PHP, proporcionando las características más recientes y mejoras de rendimiento.  
- **Composer**: La herramienta de gestión de dependencias para PHP.  
- **Laravel Installer**: Un instalador global para iniciar nuevos proyectos de Laravel rápidamente con el comando `laravel new`.  
- **Extensiones de PHP**:  
  - `pdo_mysql`: Driver necesario para conectarse a bases de datos MySQL y MariaDB.  
  - `mbstring`, `exif`, `pcntl`, `bcmath`, `gd`, `xml`, `zip`: Extensiones comunes y requeridas por el framework Laravel y sus paquetes.  
- **Node.js (LTS) y pnpm**: Para la gestión de dependencias de frontend y la compilación de activos con Vite.  

---

## ⚙️ Instrucciones de Construcción

Para construir la imagen de Docker, navega al directorio que contiene el `Dockerfile` y ejecuta el siguiente comando:

```bash
docker build . -t php-laravel:8.4
