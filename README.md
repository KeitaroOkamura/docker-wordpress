# docker-wordpress

dockerでwordpress環境ビルドするやつ

## イメージ

- WordPress 最新版
- MySQL 5.7
- phpMyAdmin 最新版

https://github.com/docker-library/wordpress

## 前提条件

docker/docker-compose が使える状態にある

### 参考 URL

#### Docker for Mac

https://docs.docker.com/docker-for-mac/install/

#### Docker for Windows

https://docs.docker.com/docker-for-windows/install/


## セットアップ

### Docker イメージのビルド

1. ビルド実行時に DB 接続情報が必要 `.env` ファイルを作成し、以下のように記述する

```bash
touch .env
```

```
# DB
MYSQL_ROOT_PASSWORD=somewordpress
MYSQL_DATABASE=wordpress
MYSQL_USER=wordpress
MYSQL_PASSWORD=wordpress

# WordPress
WORDPRESS_DB_HOST=db:3306
WORDPRESS_DB_USER=wordpress
WORDPRESS_DB_PASSWORD=wordpress
WORDPRESS_DB_NAME=wordpress
```

2. プロジェクトをビルドする

イメージの構築から、コンテナの構築・起動まで行う
すでにイメージがある場合は、起動だけ行う

```bash
docker-compose up -d
```

3. Web ブラウザーでアクセス

[http://localhost:8080](http://localhost:8080)

※プロジェクトディレクトリから実行してね

## その他コマンド

### コンテナ起動

```bash
docker-compose start
```

### コンテナ停止

```bash
docker-compose stop
```

### シャットダウン

```bash
docker-compose down
```

### 起動確認

Status が `Up` になっていれば OK

```bash
docker-compose ps
```

option `--volumes`で、コンテナー、ネットワーク、および WordPress データベースも削除

### 起動中のコンテナに入る

```bash
docker exec -i -t コンテナ名 bash
```

## 参照
https://docs.docker.com/compose/wordpress/
