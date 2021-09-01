# go-gqlgen-template
このリポジトリはgo/gqlgenを用いたWebAPI実装のベースとなる試験的なリポジトリです。

## TODO
- [ ] DB/ORM
- [ ] token認証

## Dockerコンテナ環境自動構築
```
$ docker/bootstrap
```

## Dockerコンテナ起動
```
$ docker-compose up

# デーモン起動の場合には-dオプション付きで
$ docker-compose up -d
```

## 依存モジュールのインストール&参照されていないモジュールの削除
```
※ ホストから
$ docker-compose run --rm web go mod tidy

or

# コンテナから
$ docker-compose run --rm web bash
$ go mod tidy
```

## gqlgenのインストールについて
```
本来であればgqlgenはgo installでのツールのグローバルインストールに限定したいが、binのディレクトリ名にバージョンが入ってしまい、CMDが上手く動作できない。

そのため、Dockerfileでgo installをしてgqlgenコマンドをコンテナ内で使用できるようにしつつ、
go getでモジュールとしても入れた上でgo mod tidyで不要な依存モジュールは削除している。
```
