# site

* [chenyunwen.cn](https://chenyunwen.cn/)
* [记事本](http://n.aacc.in/)  mongo
* [代码](http://code.aacc.in/) node-python
* [api](http://115.api.aacc.in/) php
* [ssdb](http://ssdb.aacc.in/) ssdb
* [torrent2magnet](http://t.aacc.in/) php

# start

```sh
docker-compose up -d
```

# When up
#!/bin/sh
/usr/bin/docker daemon -D -g /var/lib/docker -H unix:// -H tcp://0.0.0.0:2376 --registry-mirror=https://docker.mirrors.ustc.edu.cn
docker-compose start
docker-compose ps
