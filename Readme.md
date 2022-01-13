# Application using Spring Boot, Angular, Kafka, Webpack, Microservices, Microfrontends

![App Screenshot](documentation/1.png)
![App Screenshot](documentation/2.png)
![App Screenshot](documentation/3.png)

# Endpoint for Microservices:
- https://api.domainsdb.info/v1/domains/search?domain=facebook-shops&zone=us” - to pull all facebook related web domain names

# Microservices
- ‘domain-crawler’ - uses Spring Kafka
- 'domain-processor' - uses Spring Cloud Stream with Kafka Streams binder (producer)
- 'domain-service' - uses Spring Cloud Stream with Kafka Streams binder (consumer)

# Microfrontends
- ‘mfe1’ - consumes REST services exposed by the controller of the  domain crawler
- ‘mfe2’ - consumes REST services exposed by the controller of the  domain crawler
- ‘shell’ - centralizes all the microfrontends (the center microfrontend)

# The technologies used are:
- Microfrontends: Angular (Webpack, Module Federation Plugin)
- Microservices: Spring Boot, Kafka Platform



## Detail Description of the app
The Domain Crawler application was developed using Spring Boot, Kafka, Angular (with Webpack, 
Module Federation Plugin), microservices and microfrontends. The application is a platform 
that besides the web crawling of existing domains from an api made through microservices and 
microfrontends mechanism, it has a client-server architecture offering read and create functionalities 
to the client through API (Application Programming Interface) requests. There are 3 microfrontends build 
in Angular which consume REST services exposed by the microservices. The microfrontends provide the 
possibility to see the active web domains from a specific name accessing the https://api.domainsdb.info/v1/domains/search?domain=<name>-shops&zone=us" 
api and also to add the domains that were found from a specific name into a local .txt file in order to keep 
a track of them. In order to deploy the approach solution, we are using docker images for 
constructing the containers in order to build the microservices and microfrontends and 
access them on different ports. For accessing Kafka we used Zookeeper and for both of them we used docker 
images already existing. 

```
In order to access the application through docker. We made a docker container for 
each microservices, each microfrontends and also each tool or platform that we use 
aside. After making those containers, we could access the applications at different 
ports(localhost:3000 for mfe1, localhost:3001 for mfe2), but the main one is localhost:5000.
```


## run docker-compose 
```
- in root (SOA-microservices-Kafka-SpringBoot) for microservices: docker-compose up
- in root (SOA-microfrontends-module-federation-with-angular-dynamic) for microfrontends: docker-compose up
```

## Access the application within the browser
```
For microservices:
- (run ``` docker-compose up ``` before)
- open browser (any) and access: localhost:8080/domain/lookup, localhost:8080/domain/save, localhost:8080/domain/active

For microfrontends:
- (run ``` docker-compose up ``` before)
- open browser (any) and access: localhost:3000, localhost:3001, localhost:5000
```

## Configure mysql db with bind address and date time zone
```
On MacOS: sudo nano /etc/my.cnf 
add:
-bind-address:0.0.0.0
-date-time-zone: +03.00
```

## Use case UML diagram
![Use Case UML Screenshot](documentation/diagrams/UMLDiagagram-UseCase.png)

## C4Model

## System Context diagram
## 1. Whole Flow
![SystemContextDiagram Screenshot2](documentation/diagrams/ContextDiagram.png)

## Container diagram
## 1. Container Diagram for Spring Boot on Microservices with Kafka
![SystemContextDiagram Screenshot2](documentation/diagrams/ContainerMicroservicesDiagram.png)

## 2. Container Diagram for Angular(Webpack) Microfrontends
![SystemContextDiagram Screenshot2](documentation/diagrams/containerDiagramMFE.png)

## Component diagram

### 1. Component Diagram for Microservices:
![SystemComponentDiagram Screenshot2](documentation/diagrams/ComponentDiagramMicroservices.png)

### 2. Component Diagram for Microfrontends:
![SystemComponentDiagram Screenshot2](documentation/diagrams/ComponentDiagramMfe.png)

## Code
### 1. Code Diagram for Microservices:
![CodeDiagram Screenshot1](documentation/diagrams/CodeDiagramMicroservices.png)

### 2. Code Diagram for Microfrontends:
![CodeDiagram Screenshot1](documentation/diagrams/CodeDiagramMfe.png)


## UBB Cluj-Napoca - Faculty of Mathematics and Computer Science

### Software Engineering, 2020 - 2022

- 2st year � 1st semester
- Software Oriented Architecture - Assessment
