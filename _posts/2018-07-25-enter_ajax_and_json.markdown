---
layout: post
title:      "Enter AJAX and JSON "
date:       2018-07-25 20:26:50 +0000
permalink:  enter_ajax_and_json
---

I wanted to do something with this topic for a while now, it is one of the more difficult concepts, but once you understand it, and are comfortable you get to see the big picture, and you can feel confident in your abilities! 

Ajax is a client-side script that communicates to and from a server/database without the need for a postback or a complete page refresh. The best definition I've read for Ajax is “the method of exchanging data with a server, and updating parts of a web page – without reloading the entire page.” - https://www.seguetech.com/ajax-technology/

In computing, JavaScript Object Notation or JSON is an open-standard file format that uses human-readable text to transmit data objects consisting of attribute–value pairs and array data types. -https://www.wikipedia.com 

I wont go into detail of wiring it up, as you might not be using rails as I have. But it's not so bad once you take a step back and look at what all you have to do! I'll go over each one in detail.

STEP 1: Have a clear idea of what you are trying to accomplish and where.
        Say our html page is a simple to-do(like every other one everyone teahces in each language...) after our form we have          a submit button, when we submit we want it to pop up where the form one, awesome! step complete!

Step 2: Wire up your event function (I'll be using Jquery, because it's awesome!)
         However you want, wire your function to grab your event, so youll want to grab something like the class on the submit button, and then call a preventDefault(); 
Nice! on to step three!

step 3: what to do with the information??? 
now you can build out something, like a div tag, usually like div class="js-formData" or however you like, and then you create just add whatever tags you like and give them classes, then pop in your info such as $("#body-" + id).text(data);
youll also want to assign you id with a variable **this** works very well, and then chain data onto to to go a level deeper where the object id will be exposed to you. 

step 4: testing, make sure it reacts as suspected, one thing you might want to include here is a .reset() on your form fields! 

Side note: I understand this is the absolute bare bones of it, but looking at it this way took all the stress from it when I was learning about it, and I thought maybe this view might help someone else in the future, I'll be adding a live coding on youtube ill drop the link here for you to follow along shortly! 
				 
				 
				 
				 
