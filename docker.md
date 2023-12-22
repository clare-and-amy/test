alpine && debian
```
alpine 
apk add busybox-extras(telnet)
docker exec -it gocron /bin/sh // 这里是sh
docker exec -it --user=root sh

debian 
apt-get install xxx
docker exec -it gocron /bin/bash // 这里是bash
```


docker 
```
docker run -d --name websocket2 -v C:\Users\SY008\Desktop\web\docker\swoole:/var/www phpswoole/swoole:latest

docker exec -it websocket2 /bin/bash
```

meilisearch
```
docker run -itd -p 7700:7700 -v C:\Users\SY008\Desktop\web\docker\meili:/meili_data getmeili/meilisearch

https://www.meilisearch.com/movies.json
```