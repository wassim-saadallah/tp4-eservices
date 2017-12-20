# tp4-eservices : Microservices
This git repository serve the purpose of showing how we managed to **_dockerize_** the microservices that we develop throughout the lab
# Table of content
* What we Have
* Docker
* The steps
  * the _Dockerfile_
  * deploying the microservices in their corresponding instances
  * testing the enviroment

# What we have
## The application so far
It's a web REST service that display a list of products. The application is designed using the architecture of [Microservices](http://microservices.io).  
When building our microservices, we ensured that we respect a number of design patterns. Some of them related to microservices and others are general good practices when deploying the services like [Server-side Discorvery](http://microservices.io/patterns/server-side-discovery.html) and the [API gateway](http://microservices.io/patterns/apigateway.html).  
The final architecture of the application looks like this  
<p align="center"><img src="archi.png"/></p>  

An overview of the service is provided by the table below  

Name | Role | Port 
--- | --- | --- |  
product Service | The main service, an API for listing products | 8080
config Service | The configuration service used to centrelize all the app's configuration | 8888  
Discovery Service | A registery service for the application instances to get discovered by other services|8761
Proxy Service| An API Gateway for request routing and load balancing|9999  

to _containerize_ these microservices we will use [Docker](https://www.docker.com).  

# Docker
According to [wikipedia](https://en.wikipedia.org)
>"Docker is a software technology providing containers, promoted by the company Docker, Inc. Docker provides an additional layer of abstraction and automation of operating-system-level virtualization on Windows and Linux. Docker uses the resource isolation features of the Linux kernel such as cgroups and kernel namespaces, and a union-capable file system such as OverlayFS and others to allow independent "containers" to run within a single Linux instance, avoiding the overhead of starting and maintaining virtual machines (VMs)."

