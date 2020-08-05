FROM php:7.4-fpm
ENV TZ=Asia/Shanghai

RUN sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list && sed -i 's/security.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list

RUN apt-get update && apt-get install --assume-yes apt-utils
	
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# mysqli, pcntl, pdo_mysql, shmop, sysvmsg, sysvsem, sysvshm扩展
RUN docker-php-ext-install -j$(nproc) bcmath calendar exif gettext sockets dba mysqli pcntl pdo_mysql shmop sysvmsg sysvsem sysvshm iconv

# imagick 扩展
#RUN export CFLAGS="$PHP_CFLAGS" CPPFLAGS="$PHP_CPPFLAGS" LDFLAGS="$PHP_LDFLAGS" \
#    && apt-get install -y --no-install-recommends libmagickwand-dev \
#    && rm -r /var/lib/apt/lists/* \
#    && pecl install imagick-3.4.4 \
#    && docker-php-ext-enable imagick
    
# memcached 扩展
RUN apt-get update && apt-get install -y libmemcached-dev zlib1g-dev \
    && pecl install memcached \
    && docker-php-ext-enable memcached

# mcrypt  扩展 (php7.2~7.4)
#RUN pecl install mcrypt-1.0.2 && docker-php-ext-enable mcrypt
#ocker-php-ext-install

# redis 扩展
RUN pecl install redis && docker-php-ext-enable redis

# opcache 扩展
RUN docker-php-ext-configure opcache --enable-opcache && docker-php-ext-install opcache

# xdebug 扩展 (php7.2~7.4)
#RUN pecl install xdebug-2.7.2 && docker-php-ext-enable xdebug

#RUN pecl channel-update pecl.php.net

# mongodb 扩展
#RUN pecl install mongodb && docker-php-ext-enable mongodb

# swoole 扩展
RUN pecl install swoole && docker-php-ext-enable swoole

# amqp 扩展
RUN apt-get update && apt-get install -y librabbitmq-dev && pecl install amqp && docker-php-ext-enable amqp

WORKDIR /data/www

CMD ["php-fpm"]

EXPOSE 9000