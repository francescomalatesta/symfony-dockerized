# Laravel Dockerized

Laravel Dockerized is an all-in-one repository with everything you need to start developing Laravel application locally, using **docker-compose**. It's a fork of the awesome [php-dockerized by kasperisager](https://github.com/kasperisager/php-dockerized). I modified some settings and made some tweaks to let you work with a fully functional Laravel 5.1 install.

PHP Dockerized gives you everything you need for developing PHP applications locally. The idea came from the need of having an OS-agnostic and virtualized alternative to the great [MNPP](https://github.com/jyr/MNPP) stack as regular LAMP stacks quite simply can't keep up with the Nginx + PHP-FPM/HHVM combo in terms of performance. I hope you'll find it as useful an addition to your dev-arsenal as I've found it!

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

In order to get this environment to work with Laravel, I did some little modifications to the `sites/default.vhost` file.

## Requirements

In order to use Laravel Dockerized, you will need:

* [Docker Engine](https://docs.docker.com/installation/)
* [Docker Compose](https://docs.docker.com/compose/)
* [Docker Machine](https://docs.docker.com/machine/) (Mac and Windows only)

## Running

### Select your Services

If you don't mind about having every container, you can skip this part. Otherwise, feel free to remove every component you don't need from the `docker-compose.yml`. Obiously, don't forget to delete accordingly every removed item from the `links` array of the `front` element.

### Installing Laravel

Create your new Laravel project in the `www` folder and name it `default`.

	composer create-project laravel/laravel default

Don't forget to edit your `.env` file, updating your services credentials. 

You can find them in the `docker-compose.yml` file.

**Note:** the default credentials for the database are `homestead/secret`, so you will not have to change them unless you want something different. **The only thing you will have to update is the `DB_HOST` environment variable, to `mysql` or `mariadb`.

### Run!

When you're good to go, just type

	$ docker-compose up

to build services and start everything you need.

The first time, the whole process will take some time. Go make yourself a coffee.

Your site will be available at `localhost` if you're using Linux, or at the Docker Machine address if you're on Mac OSX or Windows.

## Common Laravel Operations

### Use Artisan

Laravel without Artisan is like a life without pizza. In order to use `artisan` on your application, you will need to type:

	docker exec -it <mycontainer_name> bash

where `<mycontainer_name>` is the one (associated to the `front` container) you can get when you type

	docker ps

in your terminal. Once in, you will have to reach the project folder, with

	cd /var/www

and then you will be able to use

	php artisan

as usual.

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

Many thanks to Ivan Palladino, for his great assistance about Docker.

## License

Copyright &copy; 2014-2015 [Kasper Kronborg Isager](http://github.com/kasperisager). Licensed under the terms of the [MIT license](LICENSE.md).
