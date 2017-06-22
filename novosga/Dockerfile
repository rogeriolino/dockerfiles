FROM php:5.6-apache
MAINTAINER rogeriolino <rogeriolino@gmail.com>

RUN a2enmod rewrite

RUN set -xe \
    && apt-get update \
    && apt-get install -y libpng12-dev libjpeg-dev libpq-dev libxml2-dev \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
    && docker-php-ext-install gd gettext mbstring pdo_mysql pdo_pgsql soap xml zip \
    && rm -rf /var/lib/apt/lists/*

ENV NOVOSGA_VER 1.5.1
ENV NOVOSGA_MD5 a201469188d7209c20a473f34a1c2d21
ENV NOVOSGA_URL https://github.com/novosga/novosga/archive/v${NOVOSGA_VER}.tar.gz
ENV NOVOSGA_FILE novosga.tar.gz

RUN curl -fSL https://getcomposer.org/composer.phar -o /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

RUN set -xe \
    && curl -fSL ${NOVOSGA_URL} -o ${NOVOSGA_FILE} \
    && echo "${NOVOSGA_MD5}  ${NOVOSGA_FILE}" | md5sum -c \
    && tar -xz --strip-components=1 -f ${NOVOSGA_FILE} \
    && rm ${NOVOSGA_FILE} \
    && composer install -o \
    && chown -R www-data:www-data .

RUN set -xe \
    && ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime \
    && echo 'date.timezone = "America/Sao_Paulo"' > /usr/local/etc/php/php.ini \
    && echo 'session.save_path = "/tmp"' >> /usr/local/etc/php/php.ini
