FROM php:8.0-fpm
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-install pcntl posix \
    && apt-get install -y zlib1g-dev libicu-dev g++ \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && apt-get install -y zip unzip libzip-dev \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && apt-get install -y git \
    && apt-get install -y nano \
    && pecl install -f xdebug-3.0.4 \
    && docker-php-ext-enable xdebug


RUN touch /tmp/xdebug.log && chmod 777 /tmp/xdebug.log

RUN curl -sS https://getcomposer.org/installer | \
            php -- --install-dir=/usr/bin/ --filename=composer --version=2.1.5


ARG UID
ARG USER_NAME

RUN useradd -m -u ${UID} -g root ${USER_NAME}

#socket dir
RUN mkdir /run/php-fpm/ && chmod 777 /run/php-fpm/
