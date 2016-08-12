FROM node:5.8

COPY ./npmrc /root/.npmrc
COPY ./sources.list /etc/apt/sources.list

RUN apt-get update && apt-get install -y git vim libkrb5-dev && \
    apt-get clean && \
    npm install -g pm2

COPY ./package.json /opt/node-deploy/package.json
RUN cd /opt/node-deploy && npm install

COPY ./bin/btsync /usr/bin/btsync
RUN chmod a+x /usr/bin/btsync

WORKDIR /opt/node-deploy

CMD [ "pm2", "logs" ]
