FROM php:7.1.5-fpm

MAINTAINER Anatoliy Lyovkin <anatoliymolinari@gmail.com>

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libssl-dev \
    zlib1g-dev

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Kiev /etc/localtime
RUN "date"

RUN docker-php-ext-install mbstring zip bcmath opcache

RUN pecl install mongodb && docker-php-ext-enable mongodb

RUN pecl install apcu xdebug \
        && docker-php-ext-enable xdebug \
        && echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini \
        && echo "apc.enable_cli=1" >> /usr/local/etc/php/conf.d/apcu.ini \
        && echo "zend_extension=xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_autostart=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_connect_back=on" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN echo 'alias sf="php app/console"' >> ~/.bashrc

WORKDIR /var/www/symfony
