# Docker Compose handson

## Require for mac

- Install [Homebrew](https://brew.sh/index_ja)
- Install [Docker for mac](https://docs.docker.com/docker-for-mac)

```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
$ brew cask install docker
```

## Build

```
$ git clone https://github.com/ucan-lab/infra-handson-docker-compose.git
$ git clone https://github.com/ucan-lab/infra-handson-shop.git infra-handson-docker-compose/shop
$ cd infra-handson-docker-compose

$ docker-compose build
$ docker-compose up -d
```

### SQL

```
$ docker-compose exec db bash
$ mysql -u $MYSQL_USER -p$MYSQL_PASSWORD $MYSQL_DATABASE
```

```
create table shop.items (
  id int primary key auto_increment,
  name varchar(30) comment '商品名',
  stock int default 0 comment '在庫数'
) comment='商品テーブル';

INSERT INTO shop.items (name, stock) VALUE ("Apple", 10);
INSERT INTO shop.items (name, stock) VALUE ("Bad Apple", 1);
```

http://127.0.0.1:8200

## Clear

```
$ docker-compose down --rmi all --volumes
```
