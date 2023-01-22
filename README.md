# docker-rpi-graylog
RaspberryPi(64bit)にDockerでGraylogを構築

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
