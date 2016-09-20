FROM php:7.0-fpm

MAINTAINER Mathieu Androz <mathieu@shareyourscript.me>

ENV DEBIAN_FRONTEND noninteractive

ENV TZ="Europe/Paris"
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/

COPY ./conf.d/php.ini /usr/local/etc/php/php.ini

RUN apt-get update && apt-get upgrade -qq -y && apt-get install -qq -y \
        apt-utils \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libxslt-dev \
        zlib1g-dev \
        libicu-dev \
        libedit-dev \
        libcurl4-gnutls-dev \
        g++ \
        less \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install intl \
    && docker-php-ext-install xsl \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install readline \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install opcache \
    && docker-php-ext-install curl \
    && apt-get clean \
    && apt-get autoclean
