---
title: Why Use Dependency Inversion?
date: '2016-12-01 00:00:00'
layout: page
---
## Dependency Inversion Principle

The design step is integral to the development of well-developed software. Without having a good design plan, down the line software can become very coupled, rigid, and very hard to expand. Nobody wants to be the person working on a system where [change preventers](https://sourcemaking.com/refactoring/smells/change-preventers) run rampant and changing/adding a small feature can become a nightmare very quickly.  However, we all have been guilty of jumping the gun where we jump right into coding(myself included).

Now that we established that good design is important, what should be considered when planning software? The [SOLID design principles](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) are a great foundation for designing maintainable/extendable software. The D in solid, stands for Dependency Inversion Principle. This is also known as inversion of control, IOC, or the most popular, dependency injection. The principle relies primarily on the notion:

> Depend upon Abstractions. Do not depend upon concretions

This means that, if we use abstractions in our code base, we should depend on those, rather than the implementations of that class, so that you can write a new implementation and just plug it in where you need it. High level policy, shouldn't depend on low level detail and vice versa. They should both depend on abstractions.  Understanding this, helped me to know when to create abstractions as well as designing loosely coupled dependency.

The example below illustrates the dependency inversion principle in practice:

![{{ site.baseurl }}/forestryio/images/DI_user_service.jpg]({{ site.baseurl }}/forestryio/images/DI_user_service.jpg){:style="float: none;"}

The client code depends on the high level abstraction UserService interface. The calling code can use whatever interface implements the UserService.  The same goes for the UserServiceImpl class depending upon the UserDao abstraction. What benefits does this provide? The calling code doesn't need to be changed since it depends on the implementer of the abstraction and not on the concretion. Down the road, this helps against anti-patterns such as change preventers because we would only have to change the current implementation or create a new one. An example would be if we had to write a new UserDao for a different DBMS.(Say you store some data in a relational database, and you store other data in a NoSQL database)

## Types of Dependency Injection

There are two main types of ways to use the dependency inject: setter injection or constructor injection.

**Setter Injection:** The dependency is provided to the setter of the dependent implementation.

{% highlight java %}

public class Client{ private UserService userService;

    //use the setter when setting the dependency
    public void setService(UserService userService) {
    	this.userService = userService;
    }

}

public class Application{

    public void main(String[] args){
    	Client client = new Client();
    	client.setService(new UserServiceImpl());

    }

}

{% endhighlight %}

**Benefits:** Setters can be called at any time. This provides a flexible solution if you want to be able to change the implementation based on conditional statements. This is good for optional dependencies that may not need to be defined.

**Disadvantages:** Since the setter can be called at anytime, it is harder to differentiate if the dependency was changed during the life-cycle of the object.

* * *

**Constructor Injection**: The dependency is provided to the setter of the dependent implementation.

{% highlight java %}

public class Client{ private UserService userService;

    //use the constructor when setting the dependency
    public Client(UserService userService) {
    	this.userService = userService;
    }

}

public class Application{

    public void main(String[] args){
    	Client client = new Client(new UserServiceImpl());

    }

}

{% endhighlight %}

**Benefits**: Since the dependency is set at the creation of the object, you only have to worry about defining it once, and it will not change.

**Disadvantages**: The dependency is forced during the creation of the object and the object can't work without providing an implementation for the dependency.

## DI Frameworks

Using frameworks can make it a little easier to abide by the dependency inversion principle. In past experiences I have used spring and guice. Spring loads all of your dependencies into the "ApplicationContext". This makes it so that you don't have to instantiate any of your dependencies in calling code, but in configuration files or classes. Here is a list of a few other DI frameworks:  

*   [Spring](https://projects.spring.io/spring-framework/)  

*   [Guice](https://github.com/google/guice/wiki/Motivation)
*   [HK2](https://hk2.java.net/2.5.0-b30/)
*   [Spring.NET](http://springframework.net/)
*   [CastleWindor](http://www.castleproject.org/projects/windsor/)
*   [Spring Python](http://springpython.webfactional.com/)