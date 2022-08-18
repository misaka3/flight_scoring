# README

### 初めにやること
作業ディレクトリにgit clone
```
$ mkdir {appName}
$ cd {appName}
$ git clone https://github.com/misaka3/flight_scoring.git
```
imageのビルド
```
$ docker-compose build
```

### front側対応
frontコンテナを起動
```
$ docker-compose up -d
```
パッケージのインストール
```
$ docker-compose run --rm front yarn
```
nuxt.jsアプリにアクセス
```
http://localhost:8080/
```

### back(API)側対応
back,dbコンテナを起動
```
$ docker-compose up -d
```

back/environments/db.envの内容を修正

db.envで記載したuserに、権限を付与
```
$ docker-compose exec db mysql -u root -p -e"$(cat back/db/grant_user.sql)"
```

DBを作成
```
$ docker-compose run back rails db:create
```

railsアプリにアクセス
```
http://localhost:3000/
```