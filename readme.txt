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

docker-compose -f yaml/portainer.yml down

curl 'http://localhost:8848/'
curl 'http://localhost:8848/nacos/v1/ns/service/list'

curl 'http://82.157.54.206:8848/'

com.alibaba.nacos.api.exception.NacosException: failed to req API:/nacos/v1/ns/service/list after all servers([nacos:8848]) tried: java.net.ConnectException: Connection refused (Connection refused)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:556)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:498)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:493)
        at com.alibaba.nacos.client.naming.net.NamingProxy.getServiceList(NamingProxy.java:481)
        at com.alibaba.nacos.client.naming.NacosNamingService.getServicesOfServer(NacosNamingService.java:502)
        at com.alibaba.nacos.client.naming.NacosNamingService.getServicesOfServer(NacosNamingService.java:490)
        at com.alibaba.cloud.nacos.discovery.NacosServiceDiscovery.getServices(NacosServiceDiscovery.java:69)
        at com.alibaba.cloud.nacos.discovery.reactive.NacosReactiveDiscoveryClient.lambda$getServices$1(NacosReactiveDiscoveryClient.java:75)
        at reactor.core.publisher.FluxDefer.subscribe(FluxDefer.java:46)
        at reactor.core.publisher.FluxSubscribeOn$SubscribeOnSubscriber.run(FluxSubscribeOn.java:194)
        at reactor.core.scheduler.WorkerTask.call(WorkerTask.java:84)
        at reactor.core.scheduler.WorkerTask.call(WorkerTask.java:37)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:180)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:745)

[mogu-gateway:172.18.0.6:8607] [,] 2021-03-24 16:27:28.778 ERROR 1 [com.alibaba.nacos.client.naming.updater] com.alibaba.nacos.client.naming [NA] failed to
request

java.net.ConnectException: Connection refused (Connection refused)
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:350)
        at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
        at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
        at java.net.Socket.connect(Socket.java:589)
        at sun.net.NetworkClient.doConnect(NetworkClient.java:175)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:432)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:527)
        at sun.net.www.http.HttpClient.<init>(HttpClient.java:211)
        at sun.net.www.http.HttpClient.New(HttpClient.java:308)
        at sun.net.www.http.HttpClient.New(HttpClient.java:326)
        at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:1202)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect0(HttpURLConnection.java:1138)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:1032)
        at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:966)
        at com.alibaba.nacos.common.http.client.request.JdkHttpClientRequest.execute(JdkHttpClientRequest.java:112)
        at com.alibaba.nacos.common.http.client.NacosRestTemplate.execute(NacosRestTemplate.java:482)
        at com.alibaba.nacos.common.http.client.NacosRestTemplate.exchangeForm(NacosRestTemplate.java:427)
        at com.alibaba.nacos.client.naming.net.NamingProxy.callServer(NamingProxy.java:603)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:526)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:498)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:493)
        at com.alibaba.nacos.client.naming.net.NamingProxy.queryList(NamingProxy.java:407)
        at com.alibaba.nacos.client.naming.core.HostReactor.updateService(HostReactor.java:378)
        at com.alibaba.nacos.client.naming.core.HostReactor$UpdateTask.run(HostReactor.java:460)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:180)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:745)

[mogu-gateway:172.18.0.6:8607] [,] 2021-03-24 16:27:28.779 ERROR 1 [com.alibaba.nacos.client.naming.updater] com.alibaba.nacos.client.naming [NA] failed to
request

java.net.ConnectException: Connection refused (Connection refused)
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:350)
        at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
        at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
        at java.net.Socket.connect(Socket.java:589)
        at sun.net.NetworkClient.doConnect(NetworkClient.java:175)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:432)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:527)
        at sun.net.www.http.HttpClient.<init>(HttpClient.java:211)
        at sun.net.www.http.HttpClient.New(HttpClient.java:308)
        at sun.net.www.http.HttpClient.New(HttpClient.java:326)
        at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:1202)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect0(HttpURLConnection.java:1138)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:1032)
        at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:966)
        at com.alibaba.nacos.common.http.client.request.JdkHttpClientRequest.execute(JdkHttpClientRequest.java:112)
        at com.alibaba.nacos.common.http.client.NacosRestTemplate.execute(NacosRestTemplate.java:482)
        at com.alibaba.nacos.common.http.client.NacosRestTemplate.exchangeForm(NacosRestTemplate.java:427)
        at com.alibaba.nacos.client.naming.net.NamingProxy.callServer(NamingProxy.java:603)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:526)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:498)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:493)
        at com.alibaba.nacos.client.naming.net.NamingProxy.queryList(NamingProxy.java:407)
        at com.alibaba.nacos.client.naming.core.HostReactor.updateService(HostReactor.java:378)
        at com.alibaba.nacos.client.naming.core.HostReactor$UpdateTask.run(HostReactor.java:460)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:180)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:745)

[mogu-gateway:172.18.0.6:8607] [,] 2021-03-24 16:27:28.781 ERROR 1 [com.alibaba.nacos.client.naming.updater] com.alibaba.nacos.client.naming [NA] failed to
request

java.net.ConnectException: Connection refused (Connection refused)
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:350)
        at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
        at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
        at java.net.Socket.connect(Socket.java:589)
        at sun.net.NetworkClient.doConnect(NetworkClient.java:175)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:432)
        at sun.net.www.http.HttpClient.openServer(HttpClient.java:527)
        at sun.net.www.http.HttpClient.<init>(HttpClient.java:211)
        at sun.net.www.http.HttpClient.New(HttpClient.java:308)
        at sun.net.www.http.HttpClient.New(HttpClient.java:326)
        at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:1202)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect0(HttpURLConnection.java:1138)
        at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:1032)
        at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:966)
        at com.alibaba.nacos.common.http.client.request.JdkHttpClientRequest.execute(JdkHttpClientRequest.java:112)
        at com.alibaba.nacos.common.http.client.NacosRestTemplate.execute(NacosRestTemplate.java:482)
        at com.alibaba.nacos.common.http.client.NacosRestTemplate.exchangeForm(NacosRestTemplate.java:427)
        at com.alibaba.nacos.client.naming.net.NamingProxy.callServer(NamingProxy.java:603)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:526)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:498)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:493)
        at com.alibaba.nacos.client.naming.net.NamingProxy.queryList(NamingProxy.java:407)
        at com.alibaba.nacos.client.naming.core.HostReactor.updateService(HostReactor.java:378)
        at com.alibaba.nacos.client.naming.core.HostReactor$UpdateTask.run(HostReactor.java:460)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:180)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:745)

[mogu-gateway:172.18.0.6:8607] [,] 2021-03-24 16:27:28.781 ERROR 1 [com.alibaba.nacos.client.naming.updater] com.alibaba.nacos.client.naming request: /nacos/v1/ns/instance/list failed, servers: [nacos:8848], code: 500, msg: Connection refused (Connection refused)
[mogu-gateway:172.18.0.6:8607] [,] 2021-03-24 16:27:28.781 WARN 1 [com.alibaba.nacos.client.naming.updater] com.alibaba.nacos.client.naming [NA] failed to update serviceName: DEFAULT_GROUP@@mogu-gateway

com.alibaba.nacos.api.exception.NacosException: failed to req API:/nacos/v1/ns/instance/list after all servers([nacos:8848]) tried: java.net.ConnectException: Connection refused (Connection refused)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:556)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:498)
        at com.alibaba.nacos.client.naming.net.NamingProxy.reqApi(NamingProxy.java:493)
        at com.alibaba.nacos.client.naming.net.NamingProxy.queryList(NamingProxy.java:407)
        at com.alibaba.nacos.client.naming.core.HostReactor.updateService(HostReactor.java:378)
        at com.alibaba.nacos.client.naming.core.HostReactor$UpdateTask.run(HostReactor.java:460)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:180)
        at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:745)