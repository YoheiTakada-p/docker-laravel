https://github.com/ucan-lab/docker-laravel より  

a. ローカル環境の場合
```bash
$ git clone <http/ssh>
$ cd docker-laravel
$ make create-project # a. 最新版で始める場合
$ make create-project-6.x # b1. laravel6.xで始める場合
$ make create-project-react # b2. laravel6.xにreactを入れた始める場合　※コンパイル遅すぎるからやめよう
$ make init # c. 既存のプロジェクトから始める場合
```
b. AWS EC2の場合
```bash
$ sudo git clone <http/ssh>
$ cd docker-laravel
$ sudo git clone <http/ssh>
$ mv <http/ssh> backend
$ sudo lsof -i :80 #確認
$ sudo apachectl stop　#apacheを止めよう
$ make init (or) make init-react 
$ sudo chmod -R 777 backend/storage/ #権限付与
$ sudo chmod -R 777 backend/bootstrap/cache/ #権限付与
```
Tailwind  
```bash
$ yarn add -D tailwindcss
$ yarn tailwindcss init
// webpack.mix.js
const mix = require('laravel-mix');
+ const tailwindcss = require('tailwindcss');

 mix.js('resources/js/app.js', 'public/js')
     .sass('resources/sass/app.scss', 'public/css')
+    .options({
+        processCssUrls: false,
+        postCss: [ tailwindcss('./tailwind.config.js') ],
+    });
$ yarn dev
```
注意  
ローカルで $ docker-compose up でマウントできなかった時は再起動しよう  
jetstreamをインストールする場合はyarnで入れよう  
```bash
$ composer require laravel/jetstream
$ php artisan jetstream:install livewire
$ php artisan migrate
$ yarn install
$ yarn dev #すんごい時間かかるAWSじゃできない
```
devでModule build failedエラー出たらもう一度devしよう  
多分ここら辺のエラー  
https://github.com/babel/babel/issues/8599  
修正  
・EC2でphp/DockerfileのENVのlocale関係の位置をlocale-genの後に移動しエラーが出ないように変更  
・Makefile追加
