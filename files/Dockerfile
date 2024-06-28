FROM ubuntu:latest

# Устанавливаем пакеты
RUN apt-get update \
    && apt-get install -y nginx php8.3-fpm php8.3-mysql php8.3-cgi php8.3 nginx-extras \
    && mkdir /sites \

# Очищаем кэш apt
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Создаём связку Nginx и PHP-FPM
RUN sed -i 's#listen = /run/php/php8.3-fpm.sock#listen = 127.0.0.1:9000#' /etc/php/8.3/fpm/pool.d/www.conf

# Ставим в авторан nginx и php8.3-fpm
ENTRYPOINT service nginx start && service php8.3-fpm start && /bin/bash

# Экспозиция порта Nginx
EXPOSE 80

VOLUME /home/nginx
VOLUME /home/www
VOLUME /var/lib/mysql

