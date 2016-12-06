---
title: Why Use Dependency Inversion?
date: '2016-12-01 22:52:06'
layout: 
---
## Dependency Inversion Principle

The design step is integral to the development of well-developed software. Without having a good design plan, down the line software can become very coupled, rigid, and very hard to expand. Nobody wants to be the person working on a system where change propagators run rampant and changing/adding a small feature can become a nightmare very quickly.  However, we all have been guilty of jumping the gun where we jump right into coding(myself included).

Now that we established that good design is important, what should be considered when planning software. The SOLID design principles are a great foundation for designing maintainable/extendable software. The D in solid, stands for Dependency Inversion Principle which states:

> Depend upon Abstractions. Do not depend upon concretions

This means that, if we use abstractions in our code base, we should depend on those, rather than the implementations of that class, so that you can write a new implementation and just plug it in where you need it. High level policy, shouldn't depend on low level detail and vice versa. They should both depend on abstractions. The example below illustrates the dependency inversion principle in practice:

![{{ site.baseurl }}/forestryio/images/DI_user_service.jpg]({{ site.baseurl }}/forestryio/images/DI_user_service.jpg){:style="float: none;"}

The client code depends on the high level abstraction UserService interface. The calling code can use whatever interface implements the UserService.

https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)