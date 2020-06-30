# microservice-s1-day2

1000 Microservices

- Dev, Test, Prod

3000 .properties

----------------------------------------------------------

1) Distributed COnfiguration: (Spring Cloud COnfig)

-------

git (repository) - application.properties

-------

https://spring.io/projects/spring-cloud-config

Spring Cloud Config Server:
- Server <-> Git

Features
Spring Cloud Config Server features:
a) HTTP, resource-based API for external configuration (name-value pairs, or equivalent YAML content)
b) Encrypt and decrypt property values (symmetric or asymmetric)
c) Embeddable easily in a Spring Boot application using @EnableConfigServer

------------

Config Client features (for Spring applications):
a) Bind to the Config Server and initialize Spring Environment with remote property sources
b) Encrypt and decrypt property values (symmetric or asymmetric)

------------------------------------------------

Step 1:

https://github.com/mnadiger/microservices

--------

Step 2:
Spring Cloud Config Server

2.1) Create a new project (cloudserver-config)
- select Config Server & Actuator Starters

2.2) Add @EnableConfigServer in Application file

2.3) In application.properties:

server.port=8888
spring.cloud.config.server.git.uri=https://github.com/ManpreetSinghBindra/microservices

2.4) Check it:

http://localhost:8888/{name}/{profile}/{label}

http://localhost:8888/application/default/master
http://localhost:8888/application/default

---------

Step 3:

Spring Cloud Config Client: (storeapp microservice)

3.1) Add spring-cloud-config-client starter in pom.xml

3.2) In application.properties:

server.port=8080
spring.cloud.config.uri=http://localhost:8888

3.3) Start the config server (cloudserver-config)

3.4) Then start the Product Microservice (storeapp)

--------------------------------------------------------

application.properties:
http://localhost:8888/application/default/master

Multiple files:

application-dev.properties
http://localhost:8888/application/dev/master

application-prod.properties
http://localhost:8888/application/prod/master

--------------------------------------------------------

VM Arguments:

-Dspring.profiles.active=dev	in VM Arguments
-Dspring.profiles.active=prod	in VM Arguments

--------------------------------------------------------

1000 Microservices

- Dev, Test, Prod

3000 .properties

--------------------------------------------------------

application-dev.properties
application-prod.properties

renamed to

product-service-dev.properties
product-service-prod.properties

http://localhost:8888/product-service/dev/master
http://localhost:8888/product-service/dev/master

--------------------------------------------------------

Changes in Config Client (Microservices):

In application.properties:
spring.application.name=product-service

--------------------------------------------------------
