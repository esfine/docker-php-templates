構築⼿順
==========

## ■ テンプレートの概要

### □ URL

|||
|:--|:--|
|ローカルホスト|[http://localhost:8080/](http://localhost:8080/)|
|phpMyAdmin|[http://localhost:8888/](http://localhost:8888/)|


### □ ドキュメントルートと編集

ドキュメントルートは `src` です。
`src` 内に PHP 等のファイルを追加します。

ファイル編集はホスト側から行うことができます。


### □ 構成

|||||
|:--|:--|:--|:--|
|Web サーバ|web|Nginx|8080|
|AP サーバ|app|PHP 8.1 + PHP-FPM||
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

Docker をインストールします

次など参考になさってください。

Docker のインストール⼿順  
https://qiita.com/bezeklik/items/a6a7335acaec12edda45


### □ ファイルの⽤意

`docker-php-template.zip` ファイルを適当なフォルダーに移動し解凍します。

解凍後、フォルダーを任意の名前にリネームしてください。
（フォルダー名がコンテーの一部にあてられ、名前重複が発生するため）


### □ ビルド

ターミナルを起動し、Zip 解凍したフォルダーに移動します。
コンテナイメージをビルドします。
初回ビルドは 5 - 10 分程度を要することがあります。

```
$ docker-compose build --force-rm --no-cache
```

### □ 起動

コンテナーを起動します。
```
$ docker-compose up -d
```

次のような起動メッセージとなれば OK です。
```
Starting docker-webapp-template_phpmyadmin_1 ... done
Starting docker-webapp-template_mysql_1 ... done
Starting docker-webapp-template_app_1 ... done
Starting docker-webapp-template_web_1 ... done
```

起動しない場合、「ポートが使⽤中でないか」などを確認してください。


### □ AP サーバにログインする

AP サーバ上での作業が必要な場合は次コマンドでログインします。

```
$ docker-compose exec app bash
```


### □ 停止

コンテナーを停⽌します。

```
$ docker-compose stop
```

次のように、停⽌すればOKです。

```
Stopping docker-webapp-template_web_1 ... done
Stopping docker-webapp-template_app_1 ... done
Stopping docker-webapp-template_phpmyadmin_1 ... done
Stopping docker-webapp-template_mysql_1 ... done
```

#### 注意

`docker-compose down` はコンテナーを削除を実⾏します。  
あやまって down すると、環境の作り直しになります。

