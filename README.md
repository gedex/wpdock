wpdock
======

WordPress themes and plugins development using Docker and Compose.

## Requirements

* [Docker](https://docs.docker.com/installation/)
* [Compose](https://docs.docker.com/compose/install/)

## Install

```
git clone --recursive https://github.com/gedex/wpdock.git
cd wpdock
docker-compose build
docker up -d
```

Now open `http://[docker-ip]/`. If you're using [boot2docker](http://boot2docker.io/),
then replace `[docker-ip]` with your boot2docker IP, check it with:

```
boot2docker ip
```

Run the famous WP setup from there. 

## Running WP-CLI

```
docker-compose run wpcli --help
```

### Install theme:

```
docker-compose run wpcli theme install twentyfifteen --activate
```

### Install plugin:

```
docker-compose run wpcli plugin install woocommerce --activate
```

## Try various WP versions

Since WP installed as submodule, you can checkout different version of WP:

```
cd www/wp
git checkout 3.9
git checkout 4.2.2
git checkout master
```

## Stop the container

```
docker-compose stop
```

You changes are persisted. So when you do `docker-compose up -d` again you'll get the same
snapshot as before.

When you want to kill all the containers:

```
docker-compose kill
```

If you start again, you'll be prompted with WP install again.

## Remove completely

```
docker-compose kill
docker rm $(docker ps -a -q) # Warning: this will remove all containers
```

## Other services

These services are provided in case you're developing plugins that interact with them.

* Memcached
* Redis
* Elasticsearch

See [docker-compose.yml](./docker-compose.yml) file for service settings.

## LICENSE

MIT License -- see [LICENSE](./LICENSE) file.
