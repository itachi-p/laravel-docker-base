# Laravel11 & PHP8.2 & MySQL8.0 & Nginx(Latest) & Docker

## どっかーに新規Laravelプロジェクトを作成するまでの雛形

### Usage

各設定ファイルが適切に配置され、中身のバージョン等が問題なければ、即ビルド

```bash
docker compose up -d --build
```

ビルドが無事に終われば、以下の３つのコンテナが起動する。

- web: Webサーバ (NginX 最新バージョン)
- mysql: DBサーバ (MySQL 8.0)
- app: Laravel11 (PHP 8.2) ※但しプロジェクト作成前は空っぽ

その後下記コマンドで新規Laravelプロジェクト生成

```bash
docker-compose exec app composer create-project --prefer-dist laravel/laravel .
```

これでルート直下の/src/以下にLaravelアプリが作られる。
また、src直下の.envの編集も必要(主にsqliteからmysqlへの変更)

ただし、どのみちマイグレーションなどしないといけないので、
Webサーバコンテナの中に入っての作業が必要。

```bash
docker compose exec web /bin/bash
```

上記で中に入ってから新規プロジェクト生成及びマイグレーションなどを行う。

また、DBサーバに入る場合は以下のコマンド

```bash
docker compose exec mysql /bin/bash/
```

それ以降の操作については何卒よしなにね。zzz
