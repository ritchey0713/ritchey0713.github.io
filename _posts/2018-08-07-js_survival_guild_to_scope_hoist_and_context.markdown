---
layout: post
title:      "JS Survival guild to Scope, Hoist, and Context"
date:       2018-08-07 19:47:53 +0000
permalink:  js_survival_guild_to_scope_hoist_and_context
---

A fundamental part of a journey in JavaScript is understanding Scope, Hoisting, and Context. They aren't the most complex, but they can really give you a hard time to find and fix. The first we are going to tackle is Scope. 

Scope is basically the visibility of things, variables, objects, arrays, functions, the whole kit. You have two scopes Global, and Local. or even simply, what is available and where is it available. 

```
const scope = "Hi, I'm in the global scope!"

function localScope(){
    const localScope = "Hi I am in the local scope!"
		return localScope
}

``` 
So here we can see we have a variable named scope, not inside anything, or is it? It is! it is in the Global, or "Window" scope, this is available everywhere, more on that in a second. In our function we have a variable named localScope, this is as you guessed a local scope. We can access this anywhere inside this function we want, but we cannot access it outside. Now what we can do is use the global inside this function, I find it easiest to think of scope as a ladder, when you are looking for a variable to use or "reference" you can climb up the ladder to find it so if we call global we can use that in the function, but outside that function we cannot go into it and pull out localScope. Nothing too crazy, and simple enough right? 

Well now lets look at Hoisting. The easiest way to explain is hoisting moves only the declaration. lets look at another example! 

```
console.log(hoistEx())

function hoistEx(){
return "hello world" }

```

will this work? yep! Even though we have build our function under the console.log Hoist will push up our function at runtime, giving us that reference to console.log it! that was pretty easy so lets break it down a little more... 
The deep secret is, your code isn't moving, during the compile phase function and variable declarations are allotted and thus, we then have access in the example above. Remember initializations are NOT hoisted. i.e. var a = 1 (var a gets hoisted, but your a =1 does not!) until you get to the a =1 it will be undefined because thats the default for a variable when it hasn't been initialized!

The easiest way to keep yourself sane and your code working, is to build your functions at the top, and variables in functions at the top so you won't have to fight with hoisting, which is what you do already anyway right? 

This last bit is kinda tricky.  This can really give you heartache. This is context. It is a little hard to grasp at first go, so don't worry! in JavaScript the context is called by keyword: this.  this also has a default "value" if you console.log(this) you see Window, when we talked about scope i brought it up, here it is again, basically it is your root or global scope context. lets make an example 

```
var person = {
foo: function(name, address){
console.log(this)
}  }

person.foo()
```
if you put this in your console, you will get back the object. the context you are in when you console.log here is the object person. You have to be careful though the context of this can change! you also cannot assign this, JavaScript will set it based on where it is and how its called. Tricky isn't it? Mostly you call this in a function so lets look at an example!

```
var o = {
  prop: 37,
  f: function() {
    return this.prop;
  }
};

console.log(o.f()); 
```

so just like before what is this? this is referring to our object here. and just like changing anything .prop is referring to our prop. so when we log it what does it return??? 37! See, you got it already. remember when i told you JS assigns this? well we have some tools to get it to do somethings for us. lets look at those now, they will be important! They are call, apply, bind. 




.call allows you to change the context that this fires in so you could person.foo.call(window) and now this will refer to the window object nice!

```
var person = {
foo: function(name, address){
console.log(this)
}  }

person.foo()
```

Also if we have to pass additional args to a function we are calling with call we can do it like so person.foo.call(window, "john", "123 Fake St.") assuming we have to pass name and address to our person object. and so with apply it works the same, but how we pass things is a little different. we have to pass them as an array because apply only takes two args so we simply person.foo(window, ["john", "123 Fake St"])

.bind is whole different animal though. bind returns a bound function so if we continue our example with this call const myPerson = person.foo.bind(window) whenever we call myPerson() it will run with this as window. This you'll find is used a lot in constructors, prototypes, more on that in the future! and quite a bit with DOM events. Just remember that it has a context you don't set and if in doubt console.log your this to see what the context is! i hope this was helpful.  
