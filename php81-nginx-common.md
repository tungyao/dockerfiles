```dockerfile
FROM php:8.1-fpm
RUN rm -rf /etc/apt/sources.list
RUN echo "deb https://mirrors.aliyun.com/debian/ bullseye main non-free contrib" > /etc/apt/sources.list
RUN echo  "deb-src https://mirrors.aliyun.com/debian/ bullseye main non-free contrib" >> /etc/apt/sources.list
RUN echo  "deb https://mirrors.aliyun.com/debian-security/ bullseye-security main" >> /etc/apt/sources.list
RUN echo  "deb-src https://mirrors.aliyun.com/debian-security/ bullseye-security main" >> /etc/apt/sources.list
RUN echo  "deb https://mirrors.aliyun.com/debian/ bullseye-updates main non-free contrib" >> /etc/apt/sources.list
RUN echo  "deb-src https://mirrors.aliyun.com/debian/ bullseye-updates main non-free contrib" >> /etc/apt/sources.list
RUN echo  "deb https://mirrors.aliyun.com/debian/ bullseye-backports main non-free contrib" >> /etc/apt/sources.list
RUN echo  "deb-src https://mirrors.aliyun.com/debian/ bullseye-backports main non-free contrib" >> /etc/apt/sources.list
RUN docker-php-ext-install pdo_mysql
RUN pecl install redis && docker-php-ext-enable redis
RUN apt-get update && apt-get install -y nginx wget
RUN wget -c https://raw.githubusercontent.com/tungyao/dockerfiles/main/php81-nginx-common-nginx.conf -O /etc/nginx/nginx.conf
RUN wget -c https://raw.githubusercontent.com/tungyao/dockerfiles/main/php81-nginx-common-php.ini -O /usr/local/etc/php/php.ini
RUN docker-php-ext-install sockets && docker-php-ext-enable sockets
```
