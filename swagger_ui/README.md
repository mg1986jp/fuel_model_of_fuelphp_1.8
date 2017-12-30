# Swagger
* Version: 3.8.1
* [Release Documentation](https://github.com/swagger-api/swagger-ui/tree/master/)

___

## Description

Swagger-phpはcomposer.jsonに組み込んでいます。
$ composer update
これで**fuel/vendor/bin/swagger**が生成されます。

各プログラムでHTTPメソッドやリクエストパラメーターやレスポンスパラメーターをアノテーション形式で指定します。

```
<?php
/**
 * @SWG\Swagger(
 *   @SWG\Info(
 *     title="API Document",
 *     description="一般ユーザーから呼ばれる API",
 *     version="1.0.0"
 *   )
 * )
 */

 /**
  * 抽象コントローラークラス。
  */
 abstract class Controller_Abstract extends Controller_Rest
 {
 }
```

```
 <?php
 class Controller_Ranking extends Controller_Abstract
 {

      /**
       * @SWG\Post(
       *     path="/Dev/personal/fuel_model_of_fuelphp_1.8/public/ranking/index",
       *     summary="テスト投稿",
       *     description="リクエストパラメータに応じて真偽値を返す",
       *     tags={"hoge"},
       *     produces={"application/json","application/xml"},
       *     @SWG\Parameter(
       *         name="number",
       *         description="作品 ID",
       *         type="string",
       *         in="query",
       *     ),
       *     @SWG\Response(
       *         response=200,
       *         description="成功",
       *         @SWG\Schema(
       *         @SWG\Property(
       *                 property="is_success",
       *                 type="boolean",
       *                 description="存在確認フラグ",
       *             )
       *         )
       *     )
       * )
       */
  	public function post_index()
  	{
         var_dump(Input::method());
         $number = Input::param('number', null);
         var_dump($number);
         if(is_null($number)) {
             return $this->response([
                 'is_success' => false,
             ]);
         }
         return $this->response([
             'is_success' => true,
         ]);
  	}
 }
```

この様にアノテーションを指定したAPIが**fuel/app/classes/controller**にあったとします。

これでSwagger-UIを生成する準備ができました。
Swagger-UIはSwagger.jsonを元に生成されます。
Swagger.jsonは各APIに記述されているアノテーションから生成されます。

$ cd [インストールディレクトリ]/[ProjectName]
$ ./fuel/vendor/bin/swagger fuel/app/classes/controller/ --output swagger_ui/swagger.json


___

## Developer
* [Masaya Goto](https://legendary-se.jp/)
