# angular-spring-phonegap-curd
 
# make sure u have made changes in application.yml file ,
---
server:
  port: 8080
  contextPath: /SpringBootCRUDApp
---
spring:
  profiles: local
datasource:
  sampleapp:
    url: jdbc:h2:~/test
    username: SA
    password:
    driverClassName: org.h2.Driver
    defaultSchema:
    maxPoolSize: 10
    hibernate:
      hbm2ddl.method: create-drop
      show_sql: true
      format_sql: true
      dialect: org.hibernate.dialect.H2Dialect
---
spring:
  profiles: prod
datasource:
  sampleapp:
    url: jdbc:mysql://localhost:3306/test
    username: root
    password: root
    driverClassName: com.mysql.jdbc.Driver
    defaultSchema:
    maxPoolSize: 20
    hibernate:
      hbm2ddl.method: update
      show_sql: true
      format_sql: true
      dialect: org.hibernate.dialect.MySQLDialect





#db queries
use test;
create table APP_USER (
   id BIGINT NOT NULL AUTO_INCREMENT,
   name VARCHAR(30) NOT NULL,
   age  INTEGER NOT NULL,
   salary REAL NOT NULL,
   PRIMARY KEY (id)
);
   
/* Populate USER Table */
INSERT INTO APP_USER(name,age,salary)
VALUES ('Sam',30,70000);
   
INSERT INTO APP_USER(name,age,salary)
VALUES ('Tom',40,50000);
 
commit;
      
# right click on Spriong Boot CrudAPP.java-> run configuration -> inside vm arguments pass these as params 
-Dspring.profiles.active=prod
      
