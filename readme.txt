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
