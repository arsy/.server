FROM mysql:5.7

LABEL maintainer="Yakup Arslan <me@yakupars.pw>"

ENV MYSQL_ROOT_PASSWORD root
ENV MYSQL_DATABASE default_dev

ADD init.sql /docker-entrypoint-initdb.d/

CMD ["mysqld", "--default-authentication-plugin=mysql_native_password"]

EXPOSE 3306