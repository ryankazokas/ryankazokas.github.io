----
 -layout: post
 -title:  "The Journey into React JS"
 -date:   2016-10-08 23:16:24 -0400
 -categories: javascript react
 ----
 -
 -## Early Javascript
 ----
 Like most software developers, front end engineering is lacking in academia,(whether it be lack of knowledge by professors or by universities afraid to add it as part of the cirriculum)
 so my professional knowledge of javascript was limited to job experience from an internship. A goal of mine
 was to get a grasp on vanilla javascript. So i had bought a book and started hacking away at and understanding javascript. Doing things like this was great for a while.
 It satisfied my need to make asynchronous actions, hide/show text, etc. However a few years ago I had discovered a 'dollar sign' synatax:
 
 {% highlight javascript %}
 $( document ).ready(function() {
     console.log( "Hello World!" );
 });
 {% endhighlight %}
 
 I had come across the world of jquery, which allowed for a lot cleaner syntax for selecting elements outside of plain javascript and a tad bit easier DOM manipulation, AJAX
 calls were very simple. 
 I instantly fell in love because front end
 development wasn't my niche, but it made it very easy for me to hack up quick things I had to do such as remove an entire div, or highlight a span of text. It was front
 end development for "dummies". I actually used that for quite a while, but things started to get out of hand as JQuery code was developed by pieces. 
 
 ## React Framework
 ----
 As the JQuery code was piling up, I had more of a need for the sense of structure on in my front end. So I started looking to JS frameworks. I read about angular, React, Ember, and backbone. 
 I started with angular since it seemed the closest to what I knew; plain javascript. It's what I felt comfortable with, however, without reinventing some of the wheel,
 I had to make angular work how I wanted. The 2-way data-binding is great, but a little difficult to understand at first, but once yuou get the hang of things it is quite easy.
 But it still wasn't enough structure for some reason.
 
 I was very apprehensive about [React][react], mainly for the fact that it was created by the people at facebook. I thought maybe the people who worked on JS frameworks would
 better understand how a UI would/should work. I was very wrong with this assumption. It was the first time I saw "Component" based javascript development. I have worked
 a little with extjs, but since it's propietary, it was out for my personal projects since it seems geared more toward medium/enterprise business scale. However, I admired the way
 extjs carried itself as far as gearing itself towards pre built components.
 
 After doing some research I finally decided to buy a [Udemy][udemy] class on React(all credit goes to Stephen Grider) and dive right in. I immediately fell in love with it. I found the framework to be structured,
 yet complete enough to not have to reinvent anything, especially with ES6. React is Component based, and it makes things simpler when it comes to constructing UI's.
 
 For example:
 {% highlight javascript %}
 class SearchBar extends Component {
   render(){
     return(
       <div>
         <input type="text" className="form-control" />
       </div>
     );
   }
 }
 
 export default SearchBar;
 {% endhighlight %}
 
 Which could then be used like this:
 
 {% highlight javascript %}
 export default class App extends Component {
   constructor(props) {
     super(props);
   }
 
 
   render() {
 
 
     return (
       <div>
           <Sidebar />
       </div>
     );
   }
 }
 
 {% endhighlight %}
 
 The search bar, can then be imported into any other component. React will force you to think of the UI as a hierarchy of components.
 
 ## Conclusions
 ---
 Overall, It is a great framework. However, react is just the "view".  Out of the box it doesn't do too much outside of rendering components and plain javascript, but 
 there are also a lot of things that play nice with react. One of the larger ones is [Redux][redux]. Redux works well with react once you understand how redux itself works.
 Another one to note is react-router, which handles the URI changes and directs the URI to render certain components. React router provides a way to configure routes to URI changes. This is ideal for SPA's
 
 References: 
 Check out
 [ReactJS][react]
 [Udemy][udemy]
 [Redux][redux]
  
  [react]: https://facebook.github.io/react/
  [udemy]:   https://www.udemy.com/react-redux
  [redux]:   http://redux.js.org/