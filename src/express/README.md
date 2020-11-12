### Redis
1. 创建 redis 父镜像：
```
cd redis/
docker build -t jervis/redis .
```

2. 创建 redis 主节点镜像：
```
cd primary/
docker build -t jervis/redis_primary .
```

3. 创建 redis 子节点镜像：
```
cd replica/
docker build -t jervis/redis_replica .
```

4. 创建网络 express：
```
docker network create express
```

5. 运行主节点，
```
docker run -d -h redis_primary --net express --name redis_primary jervis/redis_primary
```

6. 查看主节点日志：
```
docker run -ti --rm --volumes-from redis_primary ubuntu cat /var/log/redis/redis-server.log
```

7. 运行副本节点1：
```
docker run -d -h redis_replica1 --name redis_replica1 --net express jervis/redis_replica
```

8. 查看副本节点1日志：
```
docker run -ti --rm --volumes-from redis_replica1 ubuntu cat /var/log/redis/redis-replica.log
```

9. 运行副本节点2：
```
docker run -d -h redis_replica2 --name redis_replica2 --net express jervis/redis_replica
```

### Nodejs
1. 创建 node 镜像：
```
docker build -t jervis/nodejs .
```

2. 运行 node：
```
docker run -d --name nodeapp -p 3000:3000 --net express jervis/nodejs
```

3. 访问站点
```
curl http://localhost:3000
```

### Logstash
1. 创建 logstash 镜像：
```
docker build -t jervis/logstash .
```

2. 运行 logstash，并挂载 redis_primary 和 nodeapp 的卷用于获取日志：
```
docker run -d --name logstash --volumes-from redis_primary --volumes-from nodeapp jervis/logstash
```

3. logstash 将内容输出到标准输出，监控容器的标准输出：
```
docker logs -f logstash
```