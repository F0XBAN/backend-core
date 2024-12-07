FROM php:8.3-fpm

RUN apt-get update
RUN apt-get install -y $PHPIZE_DEPS \
    libssl-dev \
    postgresql postgresql-contrib \
    curl \
    npm \
    git \
    nano \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libpq-dev \
    zip

RUN docker-php-ext-install zip
RUN chmod 777 /tmp

RUN docker-php-ext-install pdo pdo_pgsql
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN docker-php-ext-configure gd --with-freetype --with-jpeg \ 
        && docker-php-ext-install -j$(nproc) gd \
        && docker-php-ext-configure zip

# Install Debug
RUN pecl install xdebug && docker-php-ext-enable xdebug

ADD ./php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/html

CMD ["php-fpm"]