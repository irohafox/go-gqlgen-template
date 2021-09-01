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


## エンドポイント
```
http://localhost:5001/がPlayground
http://localhost:5001/queryがWebAPIエンドポイント
```

## 実装済みのresolverに対するサンプルqueries
```
mutation createTodo {
  createTodo(input:{text:"todo", userId:"1"}) {
    user {
      id
    }
    text
    done
  }
}

query findTodos {
    todos {
      text
      done
      user {
        name
      }
    }
}
```

## gqlgenのインストールについて
```
本来であればgqlgenはgo installでのツールのグローバルインストールに限定したいが、
binのディレクトリ名にバージョンが入ってしまい、CMDが上手く動作できない。

そのため、Dockerfileでgo installをしてgqlgenコマンドをコンテナ内で使用できるようにしつつ、
go getでモジュールとしても入れた上でgo mod tidyで不要な依存モジュールは削除している。
```
