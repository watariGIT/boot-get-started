Spring-get-boot
====

Overview
SpringBootとmysqlをDockerで動かすサンプル


## Description

docker-compose upでdbとappを実行します。
getするとuserを取ってきます。

参考にしたもの
- [Spring Boot with Docker な開発環境を考える](https://blog.tiqwab.com/2017/03/21/docker-java.html)
- [Spring Boot の Docker コンテナと MySQL の Docker コンテナの接続
](https://hirooka.pro/?p=8895)

## DEMO
入力1
```bash
$ curl http://localhost:8080/api/users
```

結果1
```shell-session
{
  "_embedded" : {
    "users" : [ {
      "firstName" : "Taro",
      "lastName" : "Yamada",
      "_links" : {
        "self" : {
          "href" : "http://localhost:8080/api/users/1"
        },
        "user" : {
          "href" : "http://localhost:8080/api/users/1"
        }
      }
    }, {
      "firstName" : "Hanako",
      "lastName" : "Tanaka",
      "_links" : {
        "self" : {
          "href" : "http://localhost:8080/api/users/2"
        },
        "user" : {
          "href" : "http://localhost:8080/api/users/2"
        }
      }
    } ]
  },
  "_links" : {
    "self" : {
      "href" : "http://localhost:8080/api/users"
    },
    "profile" : {
      "href" : "http://localhost:8080/api/profile/users"
    }
  }
}
```

入力2
```bash
$ curl -X POST http://localhost:8080/api/users -d '{"firstName": "Jiro", "lastName": Ohta"}' -H "Content-Type:application/json"
```
結果2
```shell-session
{
  "firstName" : "Jiro",
  "lastName" : "Ohta",
  "_links" : {
    "self" : {
      "href" : "http://localhost:8080/api/users/3"
    },
    "user" : {
      "href" : "http://localhost:8080/api/users/3"
    }
  }
}
```
