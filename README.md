https://github.com/ucan-lab/docker-laravel

```bash
$ git clone <http/ssh>
$ cd docker-laravel
$ make create-project # 最新版で導入。前版使いたかったら別コマンドを使おう
#既存のプロジェクトから始める場合
$ make init
```
AWS EC2  
1 80ポートを開放しよう
```bash
$ sudo lsof -i :80 #確認
```
2 権限を付与しよう
```bash
$ sudo chmod -R 777 backend/storage/
$ sudo chmod -R 777 backend/bootstrap/cache/
```
注意  
docker-compose up でマウントできなかった時は再起動しよう  
jetstreamをインストールする場合はyarnで入れよう  
```bash
$ composer require laravel/jetstream
$ php artisan jetstream:install livewire
$ php artisan migrate

$ yarn install
$ yarn dev #すんごい時間かかる
```
devでModule build failedエラー出たらもう一度devしよう
多分ここら辺のエラー
https://github.com/babel/babel/issues/8599
修正  
・php/DockerfileのENVのlocale関係の位置をlocale-genの後に移動しエラーが出ないように変更    
