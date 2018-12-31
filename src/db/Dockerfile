FROM mysql:5.5.46

ENV MYSQL_DATABASE="odinms" MYSQL_ROOT_PASSWORD="root"

EXPOSE 3306

COPY /ms-sql/*.sql ./docker-entrypoint-initdb.d/
