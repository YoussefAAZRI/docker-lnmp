FROM php:7.0.4-fpm
MAINTAINER Youssef AAZRI <you.aazri@gmail.com>
RUN usermod -u 1000 www-data
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libxslt1-dev

RUN docker-php-ext-configure \
        gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install \
        bcmath \
        gd \
        intl \
        mbstring \
        mcrypt \
        opcache \
        pdo_mysql \
        xsl \
        zip \
        soap

RUN echo "memory_limit=2048M" > /usr/local/etc/php/conf.d/magento.ini \
    && echo "realpath_cache_size=2M" >> /usr/local/etc/php/conf.d/magento.ini \
    && echo "opcache.max_accelerated_files=200000" >> /usr/local/etc/php/conf.d/magento.ini \
    && echo "opcache.memory_consumption=512M" >> /usr/local/etc/php/conf.d/magento.ini \
    && echo "zlib.output_compression=1" >> /usr/local/etc/php/conf.d/magento.ini
