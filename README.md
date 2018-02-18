# LAMP Docker

This is a very simple Docker bootstrap for your PHP application.

It includes:

* Apache 2.4
* PHP 7.2
* MariaDB 10.2

## Usage

You should read [official Docker documentation](https://docs.docker.com/) first.

Inspect `docker` directory where you can find services configuration.

If you need to initialize database with specified scheme and content,
put your SQL files inside `docker/mysql/sql` directory.

Run services by command `docker-compose up -d`.

## Webserver

Everything you put inside `public` directory will be exposed via built-in webserver.

Open your browser at:

```
http://localhost:8080/
```

## Database

You can connect to database from your localhost:

```
host: localhost
port: 6446
user: root
password: root
database: database
```

Or from PHP files:

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
