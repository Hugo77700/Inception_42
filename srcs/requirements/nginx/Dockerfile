FROM debian:buster

RUN sudo apt-get update -y \
    && sudo apt-get upgrade -y \
    && sudo apt-get install nginx -y

RUN mkdir -p /etc/nginx/ssl \
    && sudo apt-get install openssl -y \
    && mkdir -p /var/www/html

RUN openssl req\
    -new\
    -nodes\
    -x509\
    -newkey rsa:2048\
    -out etc/nginx/ssl/inception.crt\
    -keyout etc/nginx/ssl/inception.key\
    -subj "/C=FR/ST=IDF/L=PARIS/O=42School/CN=hcherpre.42.fr/UID=hcherpre"

COPY conf/nginx.conf /etc/nginx/conf.d/nginx.conf

RUN chmod -R 755 /var/www/html
    && chown -R www-data:www-data /var/www/html

EXPOSE 443

ENTRYPOINT ["nginx", "-g", "daemon off;" ]