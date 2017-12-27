# FuelPHP
* Version: 1.8
* [Website](http://fuelphp.com/)
* [Release Documentation](http://docs.fuelphp.com)
* [Release API browser](http://api.fuelphp.com)
* [Development branch Documentation](http://dev-docs.fuelphp.com)
* [Development branch API browser](http://dev-api.fuelphp.com)
* [Support Forum](http://fuelphp.com/forums) for comments, discussion and community support

___

## Description
デフォルトでORM/AuthパッケージとModule構造を持っているプロジェクトです。
どんなプロジェクトでもクリーンな状態から開発を始められるように不要なファイルを排除しました。
必要に応じて改修してご使用ください。

環境毎のdb.phpはクローン時には含まれていますが公開リポジトリで管理する場合は必ず管理対象外としてください。
クローン時のdb.phpの設定はMAMPのデフォルト値が含まれています。

その為、あなたはローカルサーバーのDB名をfuel_devとして作成することで、ターミナル上でのmigrateコマンドはdb.phpの情報からローカルサーバーDBへアクセスすることができます。
あたながすぐ開発を始めるにはcomposer updateの実行と各db.phpを設定するだけでMAMP上ですぐに動作するため、MVCをscaffoldなどで構築するだけで数秒後にはWEBアプリケーションが作れます。
その為の設定には[ドキュメンテーション](http://fuelphp.jp/docs/1.8/)の熟読が必要です。

___

## Precautions

### composer.lock
composer update の実行ではcontent-hashがオーバーライドされます。
チーム開発においては、リモートリポジトリにはcomposer.lockがあるべきです。
各ブランチが持つ意味にcomposer.lockが含まれることを敬遠されたい場合は、ワーキングツリーに残したままにするか管理対象外にしてしまうと良いでしょう。
しかし、composer.lockに追加パッケージを指定した場合は、プッシュしてください。
何故なら、リモートリポジトリにはcomposer.lockがあるべきだからです。


### .gitignore
セキュリティー的な観点から下記を管理対象外とすることを推奨します。

* `/fuel/app/config/db.php`
* `/fuel/app/config/*/db.php`
* `/fuel/app/config/auth.php`
* `/fuel/app/config/simpleauth.php`
* `/fuel/app/modules/*/config/db.php`
* `/fuel/app/modules/*/config/*/db.php`
* `/fuel/app/modules/*/config/auth.php`
* `/fuel/app/modules/*/config/simpleauth.php`

### auth.php
salt の値は不正ログイン防止の為にも必ず変更してください。

### simpleauth.php
login_hash_salt の値は不正ログイン防止の為にも必ず変更してください。

### Initial clone setup procedure

ORM/Authパッケージを有効にするには下記を実行します。

```
$ cd [インストールディレクトリ]/[ProjectName]
$ composer update
```

そうすることで下記がプロジェクトに導入されます。

* `/fuel/vendor`
* `/fuel/core/`
* `/fuel/packages/auth/`
* `/fuel/packages/email/`
* `/fuel/packages/oil/`
* `/fuel/packages/orm/`
* `/fuel/packages/parser/`

**
管理対象ファイルはこれらを参照して構成されているものがあります。
初回クローン時にはcomposer updateをしないとFuelPHPが動作をすることができません。
**

このように、これらのファイルはcomposer updateで復元できる為、リポジトリリソースを消費してまで管理対象とする必要がないと考えます。

___

## Other

### docs
所謂、上流工程でのドキュメント（要件定義、基本設計、詳細設計、各種定義書）を管理する為に用意しているディレクトリです。
しかし膨大なドキュメントはリポジトリのリソースを消費しますdocsを必要としなければ削除可能です。

___

## trouble shooting
* Oil がデータベースに接続できないがアプリケーションは接続できる。
[FuelPHP - トラブルシューティング](http://fuelphp.jp/docs/1.8/installation/troubleshooting.html#oil_db_error)を参照。

* ターミナル上でscaffoldなどDBに関わる操作ができない。
phpのversionが7.1.5以上であればStringをIntegerにキャストしていないことが原因です。
phpのversionを7.1.5以下に下げることで解決します。（ex:7.0.19）

___

## Developer
* [Masaya Goto](https://legendary-se.jp/)
