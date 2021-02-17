FROM php:7.4-fpm

RUN mkdir -p /var/lib/php/sessions
RUN chmod -R 777 /var/lib/php/sessions

# Install dependencies
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libmemcached-dev \
    libpng-dev \
    zlib1g-dev \
    libzip-dev

# Install extensions
RUN docker-php-ext-install \
    gd \
    json \
    pdo_mysql \
    zip

# Install pecl extensions
RUN pecl install \
    apcu-beta \
    memcached \
    redis \
    xdebug
#    mcrypt-1.0.3 \
#    && docker-php-ext-enable mcrypt

# Configure xdebug extension
COPY ./xdebug.ini /tmp/
RUN cat /tmp/xdebug.ini >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && rm -f /tmp/xdebug.ini

# Enable pecl extensions
RUN docker-php-ext-enable \
    apcu \
    memcached \
    redis \
    xdebug

# Configure xdebug extension
COPY ./xdebug.ini /tmp/
RUN cat /tmp/xdebug.ini >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && rm -f /tmp/xdebug.ini

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
#    && php composer-setup.php --install-dir=$WORKDIR \
    && mv composer.phar /usr/local/bin/composer \
    && php -r "unlink('composer-setup.php');"