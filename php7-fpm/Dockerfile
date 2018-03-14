FROM php:7.1-fpm

MAINTAINER Joseph Selven <joseph.selven@gmail.com>

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    vim

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Set timezone
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Paris /etc/localtime
RUN "date"

# Type docker-php-ext-install to see available extensions
RUN docker-php-ext-install pdo pdo_mysql

RUN echo 'alias sf="php bin/console"' >> ~/.bashrc

RUN mkdir -p /var/www/symfony/var/cache
RUN mkdir -p /var/www/symfony/var/log

WORKDIR /var/www/symfony

RUN usermod -u 1000 www-data
RUN chown -R www-data:www-data /var/www/symfony/var/cache
RUN chown -R www-data:www-data /var/www/symfony/var/log