FROM php:8.2-fpm-alpine

RUN apk add --no-cache curl bash icu-dev libzip-dev git \
    && apk add --no-cache --virtual .build-deps $PHPIZE_DEPS linux-headers \
    && pecl install xdebug apcu \
    && docker-php-ext-enable xdebug apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip pdo_mysql opcache intl \
    && docker-php-ext-enable pdo_mysql opcache \
    && apk del .build-deps

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
    && chmod +x /usr/bin/composer \
    && curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

RUN git config --global user.email "tssee.ram@gmail.com" \
    && git config --global user.name "sergey-telegin"
