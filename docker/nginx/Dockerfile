FROM nginx:1.20

# COPY ./nginx.conf /etc/nginx/nginx.conf
COPY /docker/nginx/default.conf /etc/nginx/conf.d/default.conf
# COPY ./ssl/ /etc/nginx/ssl/
COPY /docker/app/php.ini /usr/local/etc/php/


COPY ./api /var/www/html
WORKDIR /var/www/html