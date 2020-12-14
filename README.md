https://github.com/ucan-lab/docker-laravel

```bash
$ git clone git@github.com:ucan-lab/docker-laravel.git
$ cd docker-laravel
$ make create-project # Install the latest Laravel project
$ make install-recommend-packages # Not required
```

修正  
・php/DockerfileのENVのlocale関係の位置をlocale-genの後に移動しエラーが出ないように変更    
