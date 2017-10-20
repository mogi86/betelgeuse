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

### dry run

```
$ cd /path/to/betelgeuse/
$ ansible-playbook -i ansible/inventories/{environment} site.yml --check
```

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
