FROM php:8.2-fpm

# System dependencies
RUN apt-get update && apt-get install -y \
    cron \
    rsync \
    vim \
    unzip \
    git \
    curl \
    libonig-dev \
    libpng-dev \
    libzip-dev \
    zip \
    sqlite3 \
    libsqlite3-dev

# PHP extensions
RUN docker-php-ext-install pdo pdo_sqlite mbstring zip bcmath

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/my_laravel_app

COPY . .

RUN composer install --no-dev --optimize-autoloader

# Permissions
RUN chmod -R 775 storage bootstrap/cache database
RUN chown -R www-data:www-data storage bootstrap/cache database
