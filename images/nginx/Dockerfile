FROM nginx:1.9

COPY ./nginx.conf /etc/nginx/

RUN usermod -u 1000 www-data && mkdir /opt/www && chown -R www-data.www-data /opt/www

EXPOSE 80
VOLUME ["/opt/www", "/var/log/nginx", "/etc/nginx/conf.d"]
