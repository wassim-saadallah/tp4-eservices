# tp4-eservices : Microservices
This git repository serve the purpose of showing how we manage to **_dockerize_** the microservices that we develop throughout the lab
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



