# When up
#!/bin/sh
/usr/bin/docker daemon -D -g /var/lib/docker -H unix:// -H tcp://0.0.0.0:2376 --registry-mirror=https://docker.mirrors.ustc.edu.cn
docker-compose start
docker-compose ps


# Dobe

Dobe WebServer gives you everything you need for developing PHP applications locally. I hope you'll find it as useful an addition to your dev-arsenal as I've found it!

## What's inside

* [Nginx](http://nginx.org/)
* [PHP-FPM](http://php-fpm.org/)
* [MySQL](http://www.mysql.com/)
* [MongoDB](http://www.mongodb.org/)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [Node](https://nodejs.org/)
* [Elasticsearch](http://www.elasticsearch.org/)

## Requirements

* [Docker ToolBox](https://www.docker.com/docker-toolbox) (Mac and Windows only)

## Running

Set up a Docker Machine and then run:

```sh
$ make install
$ docker-compose up -d
```

That's it! You can now access your configured sites via the IP address of the Docker Machine or locally if you're running a Linux flavour and using Docker natively.

## License

Copyright &copy; 2016-2018 [Janfy](http://github.com/JanfyLiu). Licensed under the terms of the [MIT license](LICENSE.md).
