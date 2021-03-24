FROM php:7-apache
RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev
RUN docker-php-ext-install mysqli pdo_mysql gd
RUN a2enmod rewrite