PHP 開発テンプレート利用方法
==========

## これは何？

PHP + MySQL で Web アプリケーション開発を行うための Docker テンプレートです。

ミニマム構成です。  
必要に応じ、ライブラリ類を追加してください。


## ■ テンプレートの概要

### □ URL

|||
|:--|:--|
|ローカルホスト|[http://localhost:8080/](http://localhost:8080/)|
|phpMyAdmin|[http://localhost:8888/](http://localhost:8888/)|


### □ ドキュメントルート

`public` ディレクトリが、Web サーバーのドキュメントルートです。

`public` 以下のファイルは、ホスト側から編集可能です。

### □ 構成

|役割|名称||ポート|
|:--|:--|:--|:--|
|Web サーバ|web|Nginx|8080|
|AP サーバ|app|PHP 8.2 + PHP-FPM||
|DB サーバ|mysql|MySQL 8.0||
|DB 操作|phpmyadmin||8888|

### □ データベース

|||
|:--|:--|
|データベース|application|
|ユーザ|app_manager|
|パスワード|secret|
|ポート|3306|


## ■ 環境構築と利用
### □ Docker のインストール

Docker をインストールします。  

次など参考にインストールを行ってください。

参考 : Docker のインストール手順  
https://qiita.com/bezeklik/items/a6a7335acaec12edda45


### □ ファイルの用意

`docker-php-template.zip` ファイルを適当なフォルダーに移動し解凍します。

フォルダー名がコンテーの一部にあてられます。  
名前重複を避けるために、フォルダーを任意にリネームしてください。

### □ コマンドを実行前にチェック

あらかじめ Docker を起動してください。  
自動起動する設定にしておくとよいでしょう。

Docker コマンドは、ターミナルや PowerShell などのコマンドラインツールで操作します。

また、各種操作は `docker-compose.yml` のあるフォルダーで行います。


### □ ビルド、コンテナーを作成する

build コマンドはサービスの構築、再構築を行います。

```
$ docker-compose build --force-rm --no-cache
```

up コマンドはコンテナーを作成、開始します。

```
$ docker-compose up -d
```

正常に起動すれば、次のようなメッセージとなります。

```
Starting docker-webapp-template_phpmyadmin_1 ... done
Starting docker-webapp-template_mysql_1 ... done
Starting docker-webapp-template_app_1 ... done
Starting docker-webapp-template_web_1 ... done
```


### □ サービスを開始する

start コマンドは、サービスを開始します。

```
$ docker-compose start
```

### □ サービスを停止する

stop コマンドはサービスを停止します。

```
$ docker-compose stop
```

停止が完了すると、次のようなメッセージとなります。

```
Stopping docker-webapp-template_web_1 ... done
Stopping docker-webapp-template_app_1 ... done
Stopping docker-webapp-template_phpmyadmin_1 ... done
Stopping docker-webapp-template_mysql_1 ... done
```

### □ コンテナー類を削除する

down コマンドはコンテナー、イメージ、ボリュームを停止、削除します。

```
$ docker-compose down
```

### □ コンテナーにログインする

各コンテナー内で何か作業を行う場合、次コマンドでログインします。

```
$ docker exec -it --user root {コンテナ名} /bin/bash
```

### □ コンテナー一覧を表示する

ps コマンドはコンテナー一覧を表示します。

```
$ docker exec -it --user root {コンテナ名} /bin/bash
```
