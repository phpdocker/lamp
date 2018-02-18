# LAMP Docker

This is a very simple Docker bootstrap for your PHP application.

It includes:

* Apache 2.4
* PHP 7.2
* MariaDB 10.2

## Intention

Provide a convenient way to start and develop new Linux+Apache+PHP+MySQL
applications inside Docker.

## Usage

Download contents of this repository as a ZIP file and extract.

You should read [official Docker documentation](https://docs.docker.com/) first.

Inspect `docker` directory where you can find all the configuration.

If you need to initialize database with specified scheme and content,
put your SQL files inside `docker/mysql/sql` directory.

Build and run containers with command `docker-compose up -d`.

# Symfony skeleton in Docker

You can easily create a Symfony application in Docker.

```
# Remove current directories
rm -rf public/{.,}*

# Install skeleton
docker exec -t -u me php composer create-project symfony/skeleton app

# Move to root
mv app/{.,}* .
rmdir app   
```

If you need to access Docker PHP itself, just login into container
console as a non-root user:

```
docker exec -it -u me php bash
```

## Webserver

Everything you put inside `app` directory will be seen by Apache and PHP.

Data inside `app/public` will be handled by webserver and reached at:

```
http://localhost:8080/
```

## Database

Connect as a root from your host:

```
host: localhost
port: 6446
user: root
password: root
database: database
```

Or from PHP scripts:

```
host: mysql
port: 3306
user: user
password: secret
database: database
```

## IDE (PHP interpreter, debugging, tests)

Since XDebug is disabled for performance reasons, you have to enable
it when you want to debug your code.

Just run PHP interpreter with `-dzend_extension=xdebug.so` command.
Additionally you can pass more configuration parameters like
`-dxdebug.remote_enable=1 -dxdebug.remote_mode=req -dxdebug.remote_port=9000 -dxdebug.remote_host=172.17.0.1`

This is useful in tests or in your IDE.

![i](https://i.imgur.com/yCaRZHs.png)
