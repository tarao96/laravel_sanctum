FROM php:8.1-fpm

COPY /docker/app/php.ini /usr/local/etc/php/

ENV TZ=Asia/Tokyo

# Composerのインストール
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer


RUN apt-get update \
    && apt-get install -y \
    git \
    zip \
    unzip \
    vim \
    libpng-dev \
    libpq-dev \
    libxrender-dev \
    libfontconfig \
    libssl-dev

# phpredisソースを取得
RUN git clone https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis
# 拡張を入れる
RUN docker-php-ext-install pdo_mysql redis pcntl

COPY ./api /var/www/html

WORKDIR /var/www/html
RUN chmod 777 -R /var/www/html/storage

#CMD php artisan serve --host 0.0.0.0
#CMD php artisan serve
#CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
#TEST