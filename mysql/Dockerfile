# dockerfile before best practises

FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 
COPY backend.sql /docker-entrypoint-initdb.d/
   
# below steps are not required because schema file itself creates 
# MYSQL_USER=expense 
# MYSQL_PASSWORD=ExpenseApp@1