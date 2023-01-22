# docker-rpi-graylog
RaspberryPi(64bit)にDockerでGraylogを構築

# 注意：エラーになる
```
$ docker logs [コンテナID]

 INFO : org.mongodb.driver.cluster - Exception in monitor thread while connecting to server localhost:27017
com.mongodb.MongoSocketOpenException: Exception opening socket
        at com.mongodb.internal.connection.SocketStream.open(SocketStream.java:70) ~[graylog.jar:?]
        at com.mongodb.internal.connection.InternalStreamConnection.open(InternalStreamConnection.java:180) ~[graylog.jar:?]
        at com.mongodb.internal.connection.DefaultServerMonitor$ServerMonitorRunnable.lookupServerDescription(DefaultServerMonitor.java:193) [graylog.jar:?]
        at com.mongodb.internal.connection.DefaultServerMonitor$ServerMonitorRunnable.run(DefaultServerMonitor.java:157) [graylog.jar:?]
        at java.lang.Thread.run(Unknown Source) [?:?]
Caused by: java.net.ConnectException: Connection refused
        at sun.nio.ch.Net.pollConnect(Native Method) ~[?:?]
        at sun.nio.ch.Net.pollConnectNow(Unknown Source) ~[?:?]
        at sun.nio.ch.NioSocketImpl.timedFinishConnect(Unknown Source) ~[?:?]
        at sun.nio.ch.NioSocketImpl.connect(Unknown Source) ~[?:?]
        at java.net.SocksSocketImpl.connect(Unknown Source) ~[?:?]
        at java.net.Socket.connect(Unknown Source) ~[?:?]
        at com.mongodb.internal.connection.SocketStreamHelper.initialize(SocketStreamHelper.java:107) ~[graylog.jar:?]
        at com.mongodb.internal.connection.SocketStream.initializeSocket(SocketStream.java:79) ~[graylog.jar:?]
        at com.mongodb.internal.connection.SocketStream.open(SocketStream.java:65) ~[graylog.jar:?]
```

## 環境
- kernel：Linux ホスト名 5.15.32-v8+ #1538 SMP PREEMPT Thu Mar 31 19:40:39 BST 2022 aarch64 GNU/Linux
- OS：Debian GNU/Linux 11 (bullseye)

# .envファイルの下記に値をセット
- GRAYLOG_PASSWORD_SECRET
- GRAYLOG_ROOT_PASSWORD_SHA2

## Dockerコマンド
```bash
# Docker-compose実行
$ docker-compose up -d

# Docker コンテナ確認
$ docker ps

# Docker イメージ確認
$ docker images

# Docker コンテナの中に入る
$ docker exec -it [コンテナID] /bin/sh

# dokcer-composeのリビルド
$ docker-compose up -d --build  --force-recreate

# dokcer-composeの一括削除（滅びの呪文）
$ docker-compose down --rmi all --volumes --remove-orphans
```

## ブラウザからアクセスして起動確認
```js
http://[ホストPCのipアドレス]:9000
```

## 参考リンク
- [Graylog2/docker-compose](https://github.com/Graylog2/docker-compose)
