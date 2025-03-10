# dockerfile before best practises

FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 
RUN groupadd -r expense && useradd -r -g expense raghu && \
    chmod -R 770 /var/lib/mysql /var/run/mysqld && \
    chown -R raghu:expense /var/lib/mysql /var/run/mysqld /docker-entrypoint-initdb.d
COPY backend.sql /docker-entrypoint-initdb.d
USER raghu
   
# below steps are not required because schema file itself creates 
# MYSQL_USER=expense 
# MYSQL_PASSWORD=ExpenseApp@1