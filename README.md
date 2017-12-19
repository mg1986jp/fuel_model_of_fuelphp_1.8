## FuelPHP

* Version: 1.8
* [Website](http://fuelphp.com/)
* [Release Documentation](http://docs.fuelphp.com)
* [Release API browser](http://api.fuelphp.com)
* [Development branch Documentation](http://dev-docs.fuelphp.com)
* [Development branch API browser](http://dev-api.fuelphp.com)
* [Support Forum](http://fuelphp.com/forums) for comments, discussion and community support

## 注意事項

### .gitignore

db.phpの初期値はMAMPでの利用を想定した設定としています。  
db.phpの設定をご自身の開発環境以外（本番環境およびステージング環境）にする場合は、セキュリティー観点から管理対象外としてください。  
modulesをご使用の場合でも最低限、全てのdb.phpは必ず管理対象外としてください。  

* /fuel/app/config/db.php  
* /fuel/app/config/*/db.php  
* /fuel/app/config/auth.php  
* /fuel/app/config/simpleauth.php  
* /fuel/app/modules/*/config/db.php  
* /fuel/app/modules/*/config/*/db.php  
* /fuel/app/modules/*/config/auth.php  
* /fuel/app/modules/*/config/simpleauth.php  

## トラブルシューティング

* Oil がデータベースに接続できないがアプリケーションは接続できる。  
[こちら](http://fuelphp.jp/docs/1.8/installation/troubleshooting.html#oil_db_error)を参照。  
* ターミナル上でscaffoldなどDBに関わる操作ができない。  
phpのversionが7.1.5以上であれば7.0.19以下に落としてみる。  

### 開発者

* [Masaya Goto](https://legendary-se.jp/)
