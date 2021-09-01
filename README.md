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

## 備考
```
本来であればgqlgenはgo installで入れたいが、binのディレクトリ名にバージョンが入ってしまい、
上手く動作できないため、非推奨にはなっているが暫定的にgo getで対応
```
