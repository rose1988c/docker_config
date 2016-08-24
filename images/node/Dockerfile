FROM node:6.4

COPY ./config/npmrc /root/.npmrc
COPY ./config/sources.list /etc/apt/sources.list

RUN apt-get update && \
    apt-get clean && \
    npm install -g pm2

RUN cd /opt/www/n.aacc.in && npm install

# supervisor
RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor
COPY ./supervisord.conf /etc/supervisor/conf.d/supervisord.conf

VOLUME ["/opt/www"]

CMD ["/usr/bin/supervisord"]
