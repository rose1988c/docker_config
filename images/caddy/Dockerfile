FROM scratch
MAINTAINER Josh Wood <j@joshix.com>
COPY ./caddy.conf /
EXPOSE 80 443 1988 2015
WORKDIR /opt/www
CMD ["/bin/caddy", '-conf=/caddy.conf']