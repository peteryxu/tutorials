# start MySQL containers
docker-compose up 
(db/mysql/user.sql)

same as: 
docker run -e MYSQL_USER=petclinic -e MYSQL_PASSWORD=petclinic -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=petclinic -p 3306:3306 mysql:5.7.8

# Connect to db MYSQL
https://dev.mysql.com/doc/mysql-shell/8.0/en/mysql-shell-commands.html

spring-petclinic % mysqlsh 
MySQL Shell 8.0.23

Copyright (c) 2016, 2021, Oracle and/or its affiliates.
Oracle is a registered trademark of Oracle Corporation and/or its affiliates.
Other names may be trademarks of their respective owners.
Type '\help' or '\?' for help; '\quit' to exit.

\c root@localhost:3306 
Creating a session to 'root@localhost:3306'
Please provide the password for 'root@localhost:3306': 
Save password for 'root@localhost:3306'? [Y]es/[N]o/Ne[v]er (default No): Y
Fetching schema names for autocompletion... Press ^C to stop.
Your MySQL connection id is 3
Server version: 5.7.33 MySQL Community Server (GPL)
No default schema selected; type \use <schema> to set one.

\sql
use petclinic
SELECT DATABASE();
SHOW TABLES;
select * from owners;

# run apps
./mvnw package
java -jar target/*.jar

java -Dspring.profiles.active=mysql -jar  target/*.jar

