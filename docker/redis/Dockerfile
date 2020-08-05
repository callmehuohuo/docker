FROM redis:latest

ENV TZ "Asia/Shanghai"

FROM redis
COPY redis.conf /usr/local/etc/redis/redis.conf
CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]


#通话脚本创建六个redis配置
#for port in $(seq 1 6); \
#do \
#mkdir -p /home/docker/redis/node-${port}/conf
#touch /home/docker/redis/node-${port}/conf/redis.conf
#cat <<EOF>>/home/docker/redis/node-${port}/conf/redis.conf
#port 6379
#bind 0.0.0.0
#cluster-enabled yes
#cluster-config-file nodes.conf 
#cluster-node-timeout 5000
#cluster-announce-ip 172.38.0.1${port}
#cluster-announce-port 6379
#cluster-announce-bus-port 16379 
#appendonly yes
#EOF
#done

#运行镜像
#docker run -p 6376:6379 --name redis-6 -v /home/docker/redis/node-6/data:/data/data -v /home/docker/redis/node-6/conf/redis.conf:/etc/redis/redis.conf -d --net redis --ip 172.38.0.16 redis redis-server /etc/redis/redis.conf

#创建集群
#redis-cli --cluster create 172.38.0.11:6379 172.38.0.12:6379 172.38.0.13:6379 172.38.0.14:6379 172.38.0.15:6379 172.38.0.16:6379 --cluster-replicas 1
