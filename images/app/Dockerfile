FROM php:7-fpm

RUN apt-get update

# Install mysql pdo module.
RUN docker-php-ext-install pdo pdo_mysql

# Install MB String
RUN docker-php-ext-install mbstring

# Install opcache
RUN docker-php-ext-install opcache

# Install various modules.
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
    && docker-php-ext-install iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

# Add common config.
COPY php.ini /usr/local/etc/php/conf.d/api-fpm.ini

# Override with our fpm conf.
COPY php-fpm.conf /usr/local/etc/php-fpm.conf

WORKDIR /var/www/html

CMD ["php-fpm", "--allow-to-run-as-root"]
