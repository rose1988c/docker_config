FROM php:7.0-fpm

# Install env
COPY ./assets/* /tmp/
RUN cp /tmp/sources.list /etc/apt/sources.list
RUN apt-get update && apt-get install -y \
        git \
        g++ \
        wget \
        curl \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        libicu-dev \
        libmcrypt-dev \
        libmemcached-dev \
        libsqlite3-dev \
        libpq-dev \
        && apt-get clean && rm -r /var/lib/apt/lists/*

# Install modules
RUN docker-php-ext-configure gd \
        --with-freetype-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install \
      gd \
      zip \
      intl \
      bcmath \
      iconv \
      opcache \
      tokenizer \
      mbstring \
      mcrypt \
      pdo \
      pdo_mysql

RUN pecl install /tmp/xdebug.tgz && \
    cd /tmp/ && \
    tar -xvf /tmp/memcached.tgz && \
    mv php-memcached-* memcached && \
    cd memcached && phpize && ./configure && make install && \
    cd /tmp/ && \
    tar -xvf /tmp/swoole.tgz && \
    mv swoole-* swoole && \
    cd swoole && phpize && ./configure && make install && \
    cd /tmp/ && \
    tar -xvf /tmp/redis.tgz && \
    mv phpredis-* redis && \
    cd redis && phpize && ./configure && make install

# Install Composer
RUN cp /tmp/composer.phar /usr/local/bin/composer \
    && chmod 755 /usr/local/bin/composer

# PHP Config
COPY ./php.ini /usr/local/etc/php/php.ini
COPY ./php-fpm.conf /usr/local/etc/php-fpm.conf
COPY ./extension.ini /usr/local/etc/php/conf.d/extension.ini

# Write Permission
RUN usermod -u 1000 www-data

CMD ["php-fpm", "-F"]

WORKDIR /data/www

VOLUME ["/data/www"]
