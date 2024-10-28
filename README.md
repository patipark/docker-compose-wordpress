# docker-compose-wordpress
This is a copy of  [https://github.com/aschmelyun/docker-compose-wordpress](https://github.com/aschmelyun/docker-compose-wordpress)
A simplified yet refined Docker Compose workflow that sets up a LEMP network of containers for local WordPress development.
We make update to wordpress latest version (6.6) , php 8.3 , nginx:stable-alpine

## Usage

To get started, make sure you have [Docker installed](https://docs.docker.com/docker-for-mac/install/) on your system, and then clone this repository.

Next, navigate in your terminal to the directory you cloned this, and spin up the containers for the web server by running `docker-compose up -d --build site`.

Bringing up the Docker Compose network with `site` instead of just using `up`, ensures that only our site's containers are brought up at the start, instead of all of the command containers as well. The following are built for our web server, with their exposed ports detailed:

- **nginx** - `xxxx:80`   xxxx is port number which you want to run for nginx service.
- **mysql** - `yyyy:3306` yyyy is port number which you want to run for mysql service.
- **php** - `zzzz:9000`   zzzz is port number which you want to run for php-fpm service.

An additional container is included that lets you use the wp-cli app without having to install it on your local machine. Use the following command examples from your project root, modifying them to fit your particular use case.

- `docker-compose run --rm wp user list`

## Persistent MySQL Storage

By default, whenever you bring down the Docker network, your MySQL data will be removed after the containers are destroyed. If you would like to have persistent data that remains after bringing containers down and back up, do the following:

1. Create a `mysql` folder in the project root, alongside the `nginx` and `src` folders.
2. Under the mysql service in your `docker-compose.yml` file, add the following lines:

```
volumes:
  - ./mysql:/var/lib/mysql
```

