---
layout: post
title: Object Oriented Software Development
categories:
- Software
---

<p>Understanding software can be the largest difficulty in our profession, but if code is written well, whoever is working on it should have an easy time expanding upon the foundation.  Procedural style code can look daunting if it is long, and can be very hard to decipher what is going on in the code.  In short spurts procedural code is a lot easier to understand because of the linear pattern of implementations.  Your code says do this, and the code does it.  This is great for scripts that only have a few lines, but what about long pieces of code?</p>
<p>Once your code base starts becoming more complex, procedural style coding can start to become a pain. Object oriented programming takes real world objects how humans think of them(ie. a ball, a bike, a car) and turns them into software objects. Some think that may add complexity to their code, but in reality, in a large project this might save your life! Object programming takes actions (how humans relate them to an object) and place their functionality within those objects. For example a ball may have a diameter characteristic, and a bounce method. </p>

{% highlight java %}

class Pizza{
	private amountPepperonni	//amount of slices of pepperonni per pizza.
	
	public void eat(){
		//eat the pizza
	}
	
}//Pizza

class Ball{
	private double diameter;	//used to measure diameter of the ball.
	
	public void bounce(){
		//bounce the ball
	}

}//Ball

class Application{
	public static void main(String [] args){
		Ball ball = new Ball();
		Pizza pizza = new Pizza();
		ball.bounce();
		pizza.eat();
		
	}
}//Application

{% endhighlight %}
<p>In a large procedural code base, you see the bounce() and eat() functions called, what does it do, and where do you find it. If you are the second person working on the project you might have a hard time with finding it, but now you can easily see that the ball is the one doing a bounce and pizza is being eaten. It can even be assumed that the ball is the one calling the function bounce and pizza calling eat, due to the nature of the activity being called. This naive example is a good way to think of things even though they might not be this explicit in a real world problem.</p>