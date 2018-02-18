FROM mariadb:10.2

MAINTAINER me@hranicka.cz

COPY ./my.cnf /etc/mysql/conf.d/
COPY ./sql /docker-entrypoint-initdb.d/
