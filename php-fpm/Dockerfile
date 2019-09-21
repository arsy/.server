FROM php:fpm-alpine

LABEL maintainer="Yakup Arslan <me@yakupars.pw>"

RUN docker-php-ext-install pdo_mysql mysqli

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug mysqli

ADD php.ini  /usr/local/etc/php/conf.d/
ADD xdebug.ini  /usr/local/etc/php/conf.d/

ENV PHP_IDE_CONFIG serverName=docker

ARG COMPOSE_PROJECT_NAME
ENV COMPOSE_PROJECT_NAME=${COMPOSE_PROJECT_NAME}

WORKDIR /var/www/$COMPOSE_PROJECT_NAME

RUN curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer && chmod +x /usr/bin/composer
RUN wget -O /usr/bin/phpunit https://phar.phpunit.de/phpunit-8.phar && chmod +x /usr/bin/phpunit

EXPOSE 9000