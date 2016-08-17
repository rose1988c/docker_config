FROM nginx:1.9

COPY ./nginx.conf /etc/nginx/

RUN usermod -u 1000 www-data && mkdir /data/www && chown -R www-data.www-data /data/www

EXPOSE 80
VOLUME ["/data/www", "/var/log/nginx", "/etc/nginx/conf.d"]
