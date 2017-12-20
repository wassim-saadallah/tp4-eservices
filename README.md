# tp4-eservices : Microservices
This git repository serve the purpose of showing how we managed to **_dockerize_** the microservices that we develop throughout the lab
# Table of content
* What we Have
* Docker
* The steps
  * What we'll need
  * _Dockerfile_
  * Deploying the microservices in their corresponding instances
  * _Dockercompose_

# What we have
## The application so far
It's a web REST service that display a list of products. The application is designed using the architecture of [Microservices](http://microservices.io).  
When building our microservices, we ensured that we respect a number of design patterns. Some of them related to microservices and others are general good practices when deploying the services like [Server-side Discorvery](http://microservices.io/patterns/server-side-discovery.html) and the [API gateway](http://microservices.io/patterns/apigateway.html).  
The final architecture of the application looks like this  
<p align="center"><img src="archi.png"/></p>  

An overview of the service is provided by the table below  

Name | Role | Port 
--- | --- | --- |  
Product Service | The main service, an API for listing products | 8080
Config Service | The configuration service used to centrelize all the app's configuration | 8888  
Discovery Service | A registery service for the application instances to get discovered by other services|8761
Proxy Service| An API Gateway for request routing and load balancing|9999  

to _containerize_ these microservices we will use [Docker](https://www.docker.com).  

# Docker
According to [wikipedia](https://en.wikipedia.org)
>"Docker is a software technology providing containers, promoted by the company Docker, Inc. Docker provides an additional layer of abstraction and automation of operating-system-level virtualization on Windows and Linux. Docker uses the resource isolation features of the Linux kernel such as cgroups and kernel namespaces, and a union-capable file system such as OverlayFS and others to allow independent "containers" to run within a single Linux instance, avoiding the overhead of starting and maintaining virtual machines (VMs)."

Furthermore, [this article](http://microservices.io/patterns/deployment/service-per-container.html) as well as [this](https://dzone.com/articles/dockercontainers-microservices) helps to understand the importance of containers in a microservice architecture.  
Now let's start building some containers!  

# The Steps

## What we'll need
- [Docker](https://www.docker.com/get-docker) (For windows 10 Pro install Docker or for Windows or install "Docker tools" on previous systems)
- Text Editor or an IDE
- Terminal
- Some Patience

```
├───product-service
│      └───Dockerfile
├───config-service
│      └───Dockerfile
├───discovery-service
│      └───Dockerfile
├───proxy-service
│      └───Dockerfile
└───docker-compose.yml
```

There are **two ways** to deploy your services into docker container but the two of them require setting up a **Dockerfile** first  
## Dockerfile
this file contains the set of commands that the docker command line will execute on build
in our case a _dockerfile_ looks like this
```Dockerfile
FROM openjdk:8
ADD target/config-spring-boot.jar config-spring-boot.jar
EXPOSE 8888
ENTRYPOINT ["java", "-jar", "config-spring-boot.jar"]
CMD	java -Dfile.encoding=UTF-8 -Djava.security.egd=file:/dev/./urandom -jar /config-spring-boot.jar
```
