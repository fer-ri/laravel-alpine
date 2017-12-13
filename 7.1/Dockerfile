FROM php:7.1-fpm-alpine

MAINTAINER Ferri Sutanto <greenhouseprod@gmail.com>

RUN set -x; \
    \
    apk add --no-cache \
        wget \
        curl \
        git \
        grep \
        nginx \
        build-base \
        libmcrypt-dev \
        libxml2-dev \
        zlib-dev \
        autoconf \
        cyrus-sasl-dev \
        libgsasl-dev \
        supervisor;

RUN php -r "readfile('http://getcomposer.org/installer');" \
        | php -- --install-dir=/usr/local/bin/ --filename=composer; \
    \
    mkdir -p /.composer; \
    chmod -R ugo+rw /.composer;

RUN docker-php-ext-install \
    mysqli \
    mbstring \
    pdo \
    pdo_mysql \
    mcrypt \
    tokenizer \
    xml;

RUN mkdir -p /var/www;

COPY nginx.conf /etc/nginx/nginx.conf
COPY www.conf /usr/local/etc/php-fpm.d/www.conf
COPY supervisord.conf /etc/supervisord.conf

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]