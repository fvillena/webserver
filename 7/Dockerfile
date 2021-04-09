FROM php:7-fpm
RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev libmagickwand-dev
RUN pecl install imagick
RUN docker-php-ext-install mysqli pdo_mysql gd
RUN docker-php-ext-enable imagick

RUN apt-get install -y \
        apache2 wget

RUN apt-get install -y --no-install-recommends --no-install-suggests \
        supervisor

RUN cd /tmp && wget http://mirrors.kernel.org/ubuntu/pool/multiverse/liba/libapache-mod-fastcgi/libapache2-mod-fastcgi_2.4.7~0910052141-1.2_amd64.deb && dpkg -i libapache2-mod-fastcgi_2.4.7~0910052141-1.2_amd64.deb;apt-get install -f

RUN a2enmod actions proxy_fcgi fastcgi

RUN a2dismod mpm_prefork
RUN a2dismod mpm_worker
RUN a2enmod mpm_event
RUN a2enmod rewrite

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
COPY ./supervisord.conf /etc/supervisord.conf
COPY ./apache2.conf /etc/apache2/apache2.conf

EXPOSE 80
CMD ["/usr/bin/supervisord", "-n"]