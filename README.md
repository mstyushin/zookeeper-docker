# zookeeper-docker

My dockerized zookeeper installation.

## Supported tags
* `3.5.6`

### Sample compose file:
```
version: '2.1'
services:
 zoo1:
   image: mstyushin/zookeeper:3.5.6
   container_name: zoo1
   ports:
     - "2181:2181"
   expose:
     - "2181"
   environment:
     - ZOO_MY_ID=1
     - ZOO_SERVERS=server.1=0.0.0.0:2888:3888;2181 server.2=zoo2:2888:3888;2181 server.3=zoo3:2888:3888;2181
 zoo2:
   image: mstyushin/zookeeper:3.5.6
   container_name: zoo2
   ports:
     - "2182:2181"
   environment:
     - ZOO_MY_ID=2
     - ZOO_SERVERS=server.1=zoo1:2888:3888;2181 server.2=0.0.0.0:2888:3888;2181 server.3=zoo3:2888:3888;2181
 zoo3:
   image: mstyushin/zookeeper:3.5.6
   container_name: zoo3
   ports:
     - "2183:2181"
   environment:
     - ZOO_MY_ID=3
     - ZOO_SERVERS=server.1=zoo1:2888:3888;2181 server.2=zoo2:2888:3888;2181 server.3=0.0.0.0:2888:3888;2181
```

This compose file will bring up 3 zookeeper instances on your localhost's ports 2181,2182,2183.

