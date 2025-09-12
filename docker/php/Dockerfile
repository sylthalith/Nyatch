FROM php:8.4-fpm

RUN apt-get update && apt-get install -y \
    libpq-dev unzip curl \
    && docker-php-ext-install pdo pdo_pgsql

ARG USER_ID=1000
ARG GROUP_ID=1000

RUN groupadd -g ${GROUP_ID} laravel \
    && useradd -u ${USER_ID} -g laravel -m laravel

ENV COMPOSER_ALLOW_SUPERUSER=1
COPY --from=composer:2.8 /usr/bin/composer /usr/bin/composer

USER laravel
