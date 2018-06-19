FROM php:7.2-fpm

MAINTAINER me@hranicka.cz

RUN apt-get update && apt-get upgrade -y

# Basic
RUN apt-get update && apt-get install -y \
        wget \
        gnupg2 \
        git \
    && docker-php-ext-install -j$(nproc) \
        opcache \
        pdo \
        pdo_mysql \
        mbstring \
        iconv \
        bcmath

# ZIP
RUN apt-get update && apt-get install -y \
        zlib1g-dev \
    && docker-php-ext-install -j$(nproc) \
        zip

# Gd2
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) \
        gd \
        exif

# Intl
RUN apt-get update && apt-get install -y \
        libicu-dev \
        g++ \
    && docker-php-ext-install -j$(nproc) \
        intl

# XML
RUN apt-get update && apt-get install -y \
        libxml2-dev \
        libxslt-dev \
	&& docker-php-ext-install -j$(nproc) \
		dom \
		xmlrpc \
		xsl

# PECL extensions
RUN pecl install \
        xdebug-2.6.0 \
        apcu-5.1.10 \
    && docker-php-ext-enable \
        apcu

COPY ./php.ini /usr/local/etc/php/

# Composer
COPY ./install-composer.sh /usr/local/bin/
RUN install-composer.sh && mv composer.phar /usr/local/bin/composer

# Create a non-root user and make it default
RUN groupadd --gid 1000 php \
    && useradd --uid 1000 --gid php --shell /bin/bash --create-home php

USER php
