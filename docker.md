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

consul （Nacos）
```
8300：RAFT协议端口，保持分布式集群的一致性，端口处理复制和领导者选举
8301：LAN Gossip的端口，局域网内部进行节点通信和信息传播的协议
8302：WAN Gossip的端口，广域网内部节点的通信和信息传播协议
8500：web ui的端口，用来访问consul的图形化界面
8600：DNS解析端口

docker pull consul
docker run -d -p 8500:8500 --restart=always --name=consul consul:latest agent -server -bootstrap -ui -node=1 -client='0.0.0.0'
```
[参考文献](https://www.cnblogs.com/summerday152/p/14013439.html)