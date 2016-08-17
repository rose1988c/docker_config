FROM mysql:5.6

# Write Permission
RUN usermod -u 1000 mysql && chown mysql.mysql /var/run/mysqld/

ENV MYSQL_ROOT_PASSWORD ele_2016

EXPOSE 3306

VOLUME ["/opt"]
