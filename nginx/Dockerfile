FROM nginx:latest

# Создание необходимых директорий и генерация SSL-сертификата
RUN /bin/bash -c "mkdir -p /var/lib/nginx/body && \
mkdir -p /var/lib/nginx/fastcgi && \
mkdir -p /var/lib/nginx/proxy && \
mkdir -p /etc/nginx/ssl && \
openssl req -new -newkey rsa:2048 -days 365 -nodes -x509 -keyout /etc/nginx/ssl/nginx.key -out /etc/nginx/ssl/nginx.crt -subj '/C=RU/ST=Moscow/L=Moscow/O=MyOrg/OU=MyUnit/CN=mydomain.com'"

# Копирование файлов конфигурации и кода сайта
COPY fastcgi-php.conf /etc/nginx/snippets/
COPY nginx.conf /etc/nginx/nginx.conf
COPY ./site /var/www/html

# Открытие портов для HTTP и HTTPS
EXPOSE 80 443

# Запуск Nginx в режиме ожидания
CMD ["nginx", "-g", "daemon off;"]
