# betelgeuse
rails-docker-ansible

# Requirement
- docker-compose 1.16.1+
- ansible 2.4.0.0+

# Docker set up

```
$ cd /path/to/betelgeuse/
$ docker-compose build
$ docker-compose up -d
```

# Provisioning

- {environment}には対象環境名(localなど)を入れる

### exce rovisioning

```
$ cd /path/to/betelgeuse/
$ ansible-playbook -i ansible/inventories/{environment} site.yml
```

### docker exec web container

```
$ cd /path/to/betelgeuse/
$ docker exec -it betelgeuse_web /bin/bash --login

ユーザ名指定する場合
docker exec -it -u rails betelgeuse_web /bin/bash --login
```

# DB setup

### ridgepole

- dry run

```
$ bundle exec ridgepole -c config/database.yml -E development --apply --dry-run -f db/Schemafile
```

- exec

```
$ bundle exec ridgepole -c database.yml -E development --apply -f db/Schemafile
```

# Add gem
- 初回プロビジョニング以降に追加のgemがある場合、以下のコマンドを実行する。

### gem install

```
$ cd /var/www/betelgeuse
$ bundle install --path vendor/bundle
```

# Rails server
- `rails server`を使用する場合、以下のコマンドを実行する。

### exec rails server

```
$ cd /var/www/betelgeuse/
$ bundle exec rails server -b 0.0.0.0 --environment=development
```
