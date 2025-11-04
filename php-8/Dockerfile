# Usamos la imagen oficial de PHP CLI
FROM php:8.4-cli

# Instalamos dependencias necesarias para Laravel y extensiones de PHP para MySQL/MariaDB
RUN apt-get update && apt-get install -y \
    git \
    curl \
    zip \
    unzip \
    libzip-dev \
    libonig-dev \
    libxml2-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libmariadb-dev-compat \
    && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath gd xml zip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copiamos Composer desde la imagen oficial de Composer
COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer

# Instalamos Laravel Installer globalmente
RUN composer global require laravel/installer

# Añadimos Composer bin al PATH
ENV PATH="/root/.composer/vendor/bin:${PATH}"

# Instalamos Node.js (LTS) y pnpm
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g pnpm \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
    
# Configuramos el directorio de trabajo
WORKDIR /workspace

# Exponemos el puerto de Laravel
EXPOSE 8000

# Comando por defecto al iniciar el contenedor
# CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]