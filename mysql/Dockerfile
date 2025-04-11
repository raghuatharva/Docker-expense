# dockerfile before best practises

FROM mysql:8.0
#ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 
COPY backend.sql /docker-entrypoint-initdb.d/
   
# user=expense is must becuase Even though you have a Linux user named expense, 
# this ensures a matching MySQL user exists too. and expense user has all the permisions to access 
# the mysql database --> read backend.sql and you ll know

   
# If you're deploying MySQL in Kubernetes and you’re using a Kubernetes Secret, then you should NOT mention
# ENV MYSQL_ROOT_PASSWORD=... in the Dockerfile at all.

# below steps are not required because schema file itself creates 
# MYSQL_USER=expense 
# MYSQL_PASSWORD=ExpenseApp@1