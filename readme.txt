docker network create mushroom

netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:9555            0.0.0.0:*               LISTEN      32323/docker-proxy
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1446/sshd
tcp        0      0 0.0.0.0:9527            0.0.0.0:*               LISTEN      5118/docker-proxy
tcp        0      0 0.0.0.0:8600            0.0.0.0:*               LISTEN      5341/docker-proxy
tcp        0      0 0.0.0.0:9528            0.0.0.0:*               LISTEN      4708/docker-proxy
tcp        0      0 0.0.0.0:15672           0.0.0.0:*               LISTEN      616/docker-proxy
tcp        0      0 0.0.0.0:8601            0.0.0.0:*               LISTEN      6442/docker-proxy
tcp        0      0 0.0.0.0:8602            0.0.0.0:*               LISTEN      6264/docker-proxy
tcp        0      0 0.0.0.0:8603            0.0.0.0:*               LISTEN      6052/docker-proxy
tcp        0      0 0.0.0.0:8604            0.0.0.0:*               LISTEN      6615/docker-proxy
tcp        0      0 0.0.0.0:8607            0.0.0.0:*               LISTEN      6793/docker-proxy
tcp        0      0 0.0.0.0:8001            0.0.0.0:*               LISTEN      5353/docker-proxy
tcp        0      0 0.0.0.0:5672            0.0.0.0:*               LISTEN      630/docker-proxy
tcp        0      0 0.0.0.0:6379            0.0.0.0:*               LISTEN      1273/docker-proxy
tcp        0      0 0.0.0.0:3307            0.0.0.0:*               LISTEN      31382/docker-proxy
tcp        0      0 0.0.0.0:8848            0.0.0.0:*               LISTEN      32336/docker-proxy
tcp6       0      0 :::33060                :::*                    LISTEN      21309/mysqld
tcp6       0      0 :::3306                 :::*                    LISTEN      21309/mysqld

docker-compose -f yaml/portainer.yml up -d
Creating network "yaml_default" with the default driver
WARNING: Found orphan containers (mogu_gateway, mogu_web, mogu_sms, mysql, rabbitmq, redis, mogu_admin, vue_mogu_admin, nacos, mogu_data, vue_mogu_web, mogu_picture) for this project. If you removed or renamed this service in your compose file, you can run this command with the --remove-orphans flag to clean it up.
Pulling portainer (registry.cn-shenzhen.aliyuncs.com/mogublog/portainer:)...
latest: Pulling from mogublog/portainer
d1e017099d17: Pull complete
717377b83d5c: Pull complete
Digest: sha256:02c51e3116cddbeff35da5a968ce909fcb07ff1b9688faa2eaaa2c237e9f7548
Status: Downloaded newer image for registry.cn-shenzhen.aliyuncs.com/mogublog/portainer:latest
Creating portainer ... done
