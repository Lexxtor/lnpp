FROM php:7.4.16-fpm-alpine

COPY php.ini $PHP_INI_DIR/conf.d/

# Install PHP extensions
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

RUN install-php-extensions xdebug redis pgsql

RUN set -ex \
    && apk --no-cache add \
    postgresql-dev

RUN docker-php-ext-install mysqli pdo pdo_mysql pdo_pgsql

# Install git
RUN apt-get update \
    && apt-get -y install git libpq-dev \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
