FROM php:7-fpm

# Install dependencies.
RUN apt-get update && apt-get install -y \
	zlib1g-dev \
	vim

# Install php modules.
RUN docker-php-ext-install pdo pdo_mysql pcntl zip mbstring

# Add common config.
COPY php.ini /usr/local/etc/php/conf.d/api-fpm.ini

# Override with our fpm conf.
COPY php-fpm.conf /usr/local/etc/php-fpm.conf

WORKDIR /var/www/html

CMD ["php-fpm", "--allow-to-run-as-root"]
