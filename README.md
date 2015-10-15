# Symfony Dockerized

Coming Soon...

## What's Inside?

In the `docker-compose.yml` you will find the complete setup for the following software.

* [Nginx](http://nginx.org/)
* [MySQL](http://www.mysql.com/)
* [MariaDB](https://mariadb.org/)
* [MongoDB](http://www.mongodb.org/)
* [PHP-FPM](http://php-fpm.org/)
* [HHVM](http://www.hhvm.com/)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [Elasticsearch](http://www.elasticsearch.org/)

## Requirements

In order to use Symfony Dockerized, you will need:

* [Docker Engine](https://docs.docker.com/installation/)
* [Docker Compose](https://docs.docker.com/compose/)
* [Docker Machine](https://docs.docker.com/machine/) (Mac and Windows only)

## Running

### Select your Services

If you don't mind about having all the proposed containers, you can skip this part. Otherwise, feel free to remove every component you don't need from the `docker-compose.yml`. Obiously, don't forget to delete accordingly every removed item from the `links` array of the `front` element.

### Installing Symfony

To be done.

### Run!

When you're good to go, just type

	$ docker-compose up

to build services and start everything you need.

The first time, the whole process will take some time. Go make yourself a coffee.

Your site will be available at `localhost` if you're using Linux, or at the Docker Machine address if you're on Mac OSX or Windows.

## Common Symfony Operations

### Connect to MySQL via CLI

If you need to connect to your MySQL instance in the related container, the `exec` command remains the best choice. Just type

	docker exec -it <mysqlcontainer_name> mysql -u root -p

and type your password. Press enter and it's done!

### Other CLI Operations

Remember: `docker exec` is your friend. Usually, if you want to ssh into a specific container, all you need to do is

	docker exec -it <container_name> bash

and you're done!

## To Do

- add support for MariaDB and not only MySQL

## Credits



## License

Copyright &copy; 2014-2015 [Kasper Kronborg Isager](http://github.com/kasperisager). Licensed under the terms of the [MIT license](LICENSE.md).
