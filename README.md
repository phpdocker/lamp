# LAMP Docker

This is a very simple Docker bootstrap for your PHP application.

It includes:

* Apache 2.4
* PHP 7.1
* MariaDB 10.0

## Basic usage

You should read [official Docker documentation](https://docs.docker.com/) first.

### Install, Run

Just clone this repository and run:

```bash
docker-compose up -d
```

It builds (for the first time) and launches Docker container on background.

### Stop

```bash
docker-compose down
```

## Webserver

Everything you put inside `src` directory will be exposed via built-in webserver.

Just open your browser at:

```
http://localhost:8001/
```

You will see `phpinfo()` HTML output.

## Database

You can connect to database from your localhost:

```
host: localhost
port: 3307
user: root
password: root
database: database
```

Or from PHP file (inside `src` directory):

```
host: mysql
port: 3306
user: root
password: root
database: database
```

## Customization

TODO

## IDE (PHP interpreter, debugging, tests)

TODO

## Troubleshooting

TODO
