FROM php:7.2-fpm

MAINTAINER me@hranicka.cz

RUN apt-get update && apt-get upgrade -y

RUN apt-get update \
  && apt-get install -y wget libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
  && docker-php-ext-install -j$(nproc) pdo pdo_mysql zip mbstring gd iconv

RUN pecl install xdebug-2.6.0

COPY ./php.ini /usr/local/etc/php/

# Install Composer
COPY ./install-composer.sh /usr/local/bin/
RUN install-composer.sh && mv composer.phar /usr/local/bin/composer

# Create a non-root user to be able to create non-root files in mounted volumes
RUN useradd me
RUN cp -ra /root/ /home/me/ && chown -R me:me /home/me/
