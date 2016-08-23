FROM php:5.6-fpm

# Install env
COPY ./pkg/* /tmp/
RUN cp /tmp/sources.list /etc/apt/sources.list
RUN apt-get update && apt-get install -y \
      git \
      g++ \
      wget \
      curl \
      make \
      autoconf \
      lrzsz \
      vim \
      libmemcached-dev \
      libmcrypt-dev \
      libfreetype6-dev \
      libjpeg62-turbo-dev \
      libpq-dev \
      libsqlite3-dev \
      libpng12-dev \
      libicu-dev \
      supervisor \
      && apt-get clean && rm -r /var/lib/apt/lists/*

# supervisor
RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor
COPY ./supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Install modules
RUN docker-php-ext-configure gd \
      --with-freetype-dir=/usr/include/ \
      --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install \
      gd \
      zip \
      intl \
      pcntl \
      bcmath \
      iconv \
      opcache \
      tokenizer \
      mbstring \
      mcrypt \
      pdo \
      sockets \
      pdo_mysql

# Install PHP extensions (OR docker-php-pecl-install)
RUN pecl install \
    /tmp/memcached.tgz \
    /tmp/memcache.tgz \
    /tmp/apcu.tgz \
    /tmp/msgpack.tgz \
    /tmp/xhprof.tgz \
    /tmp/xdebug.tgz \
    /tmp/mongo.tgz \
    /tmp/redis.tgz \
    /tmp/swoole.tgz

RUN cd /home \
     && tar -xvf /tmp/cphalcon.tar.gz \
     && mv cphalcon-* phalcon \
     && cd phalcon/build && ./install

# node
RUN cd /home \
     && tar -xvf /tmp/node-v6.4.0-linux-x64.tar.gz \
     && mv node-* node \
     && ln -s /home/node/bin/* /usr/local/bin/ \
     && npm install -g pm2 --registry=https://registry.npm.taobao.org \
     && ln -s /home/node/bin/pm2 /usr/local/bin/

# PHP config
COPY ./php.ini /usr/local/etc/php/php.ini
COPY ./php-fpm.conf /usr/local/etc/php-fpm.conf
COPY ./extension.ini /usr/local/etc/php/conf.d/extension.ini

# Install Composer
RUN cp /tmp/composer.phar /usr/local/bin/composer && \
    chmod 755 /usr/local/bin/composer && \
    usermod -u 1000 www-data

VOLUME ["/opt/www"]

EXPOSE 9000

CMD ["/usr/bin/supervisord"]
