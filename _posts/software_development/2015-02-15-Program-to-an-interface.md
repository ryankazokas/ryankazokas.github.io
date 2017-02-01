---
layout: post
title: Programming to an Interface
tags : [Software, tutorial]
categories:
- Software Patterns
---

> Program to an interface, not an implementation!
- A wise man.

What does it mean to program to an interface? First lets define what an interface is used for.
An interface is a binding contract between a classes and that interface.  Similar class can share an interface if they share the same functionality of some kind. They also don't provide any implementation details, they let the class decide what it will do with the set of functions.  This is useful for when a function accepts a type of interface as an argument, it won't care where the implementation comes from.  This means that any class that implements that interface can be passed into that function. <br />For example:

{% highlight java %}
Interface IEatable{
	public void eat();
}

class Pizza implements IEatable{
	public void eat(){
		//DO Pizza eating stuff.
	}
}

class Sandwich implements IEatable{
	public void eat(){
		//DO Sandwich eating stuff.
	}
}

{% endhighlight %}

 Both pizza and sandwich implement the eatable interface.  This interface encapsulates common functionality between the two classes. So why would this be good? It gives you the ability to say you want a certain functionality, but you do not care where it comes from.  Consider the main application:

{% highlight ruby %}


class Application{
	public void main(String[] args){
		IEatable pizza = new Pizza();
		IEatable sandwich = new Sandwich();

		IEatable [] foodList = [pizza, sandwich]
		eatDinner(foodlist);
	}

	public void eatDinner(IEatable[] foodList){

		for (IEatable food : foodList) {
			food.eat();
		}

	}
}

{% endhighlight %}

The eatDinnerFunction doesn't care what implementation type of IEatable its getting and whatever type of IEatable is passed in can  execute its eat function for each type of IEatable.
