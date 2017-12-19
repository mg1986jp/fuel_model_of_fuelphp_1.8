## FuelPHP
* Version: 1.8
* [Website](http://fuelphp.com/)  
* [Release Documentation](http://docs.fuelphp.com)  
* [Release API browser](http://api.fuelphp.com)  
* [Development branch Documentation](http://dev-docs.fuelphp.com)  
* [Development branch API browser](http://dev-api.fuelphp.com)  
* [Support Forum](http://fuelphp.com/forums) for comments, discussion and community support  

## Description
デフォルトでORM/AuthパッケージとModule構造を持っているプロジェクトです。  
どんなプロジェクトでもクリーンな状態から開発を始められるように不要なファイルを排除しました。  
必要に応じて改修してご使用ください。  

環境毎のdb.phpはクローン時には含まれていますが公開リポジトリで管理する場合は必ず管理対象外としてください。  
クローン時のdb.phpの設定はMAMPのデフォルト値が含まれています。  

その為、あなたはローカルサーバーのDB名をfuel_devとして作成することで、ターミナル上でのmigrateコマンドはdb.phpの情報からローカルサーバーDBへアクセスすることができます。  
あたながすぐ開発を始めるにはcomposer updateの実行と各db.phpを設定するだけでMAMP上ですぐに動作するため、MVCをscaffoldなどで構築するだけで数秒後にはWEBアプリケーションが作れます。  
その為の設定に[ドキュメンテーション](http://fuelphp.jp/docs/1.8/)の熟読が必要です。  

## Precautions

### composer.lock
composer update の実行ではcontent-hashがオーバーライドされます。  
管理対象に含めても（コミットしても）構いませんが、各ブランチが持つ意味にcomposer.lockが含まれることを嫌う人は、ワーキングツリーに残したままにするか管理対象外にしてしまうと良いでしょう。  

### .gitignore
セキュリティー的な観点から下記を管理対象外とすることを推奨します。  

* /fuel/app/config/db.php  
* /fuel/app/config/*/db.php  
* /fuel/app/config/auth.php  
* /fuel/app/config/simpleauth.php  
* /fuel/app/modules/*/config/db.php  
* /fuel/app/modules/*/config/*/db.php  
* /fuel/app/modules/*/config/auth.php  
* /fuel/app/modules/*/config/simpleauth.php

### auth.php & simpleauth.php
salt 及び login_hash_salt の値は不正ログイン防止の為にも必ず変更してください。  

## Other

### docs
所謂、上流工程でのドキュメント（要件定義、基本設計、詳細設計、各種定義書）をまとめるために用意しているディレクトリです。
しかし膨大なドキュメントはリポジトリのリソースを消費します。
docsを必要としなければ削除可能です。

## trouble shooting
* Oil がデータベースに接続できないがアプリケーションは接続できる。  
[FuelPHP - トラブルシューティング](http://fuelphp.jp/docs/1.8/installation/troubleshooting.html#oil_db_error)を参照。  

* ターミナル上でscaffoldなどDBに関わる操作ができない。  
phpのversionが7.1.5以上であればStringをIntegerにキャストしていないことが原因です。  
phpのversionを7.1.5以下に下げることで解決します。（ex:7.0.19）

## Developer
* [Masaya Goto](https://legendary-se.jp/)
