```
pm2 start /root/yapi/vendors/server/app.js --name yapi
root@VM-0-11-ubuntu:/usr/mongodb# ./bin/mongod -f ./mongodb.conf
```
mongodb.conf
```
dbpath=/data/mongo/
logpath=/data/mongo/mongo.log
logappend=true
bind_ip=0.0.0.0
fork=true
port=27017
auth=true
```

ypai
```
root@VM-0-11-ubuntu:~/yapi# ls
config.json  init.lock  log  vendors
```
