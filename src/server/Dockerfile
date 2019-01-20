FROM openjdk:7

ENV MYSQL_DATABASE="odinms" MYSQL_ROOT_PASSWORD="root" ZMS_HOST="localhost"

EXPOSE 8484 7575-7578

WORKDIR /app

COPY /zms-*.sh ./
COPY /ms-server/ ./

CMD ["./zms-wait.sh", "db:3306", "-t", "0", "--", "./zms-start.sh"]
