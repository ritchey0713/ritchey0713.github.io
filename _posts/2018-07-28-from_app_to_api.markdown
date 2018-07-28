---
layout: post
title:      "From app to API"
date:       2018-07-28 17:50:51 +0000
permalink:  from_app_to_api
---


After fixing the last few bugs and running my local server, seeing my hard work in action was great, it really was. I didn't have any CSS or cool memes, so it wasn't very pretty, but it reacted just the way i envisioned. It was fast, took me through errors, tested validations, saved, allowed me to log in with a third party app. This is what being a rubyist must be. I was on top of the mountian... Oh no, no I was not. I merely just got to the first summit for a rest. 

Enter JavaScript, or more specificlly Jquery, and AJAX/JSON. Playing around with it, I was instantly able to see so much about how all these amazing web apps work. But, still so new, I was ready to defend my rails app as is. There's nothing wrong with renders, and redirects and having to navigate all over the place right? There is, people don't want to do that, and firms don't want to see you build apps like this. Then I learned like everything else, my predessors we're thinking of me. API, what a glorious thing, all kinds of info for almost anything, and its so easy to gain access, and with rails we have gems to make it even easier. SCORE! Really, all you have to do is follow convention of naming and structure, and for a follw up run it through a responds_to method. Easy Peasy. 

Now that i have converted my Rails app, I can see such a distinction between front and back end, and now how important communication is. Although I thought this was silly to do as a project, I see the sheer weight of what we were learning. Or,  maybe i'm just looking in too deep, who knows. But the way my app works is simple from every aspect, as I think thats ultimately half of our job. Make it easy to adapt, and for the next guy to build with. I found all i really needed to do was create my JS file, hijack some events, parse my data to json find a way to insepct my objects, break them up or pass them where they need to go, and then... well? 

Handlebars! a template, how amazing is it, that i just need one template and it will do everything i need for a CRUD app. again, SCORE. i compile and pass everything back and boom. It does all the hard thinking, and plugging in for me, sweet. The last big hurdle i had was, where do I put it all? Of my own opinion, i wanted to have the flexibility to click around like an older site, and not deal with AJAX/JSON, or use ALL THE JSON. I made a new index, for a current user, and then gave them a nav bar to go to which ever side they want. I struggled a lot here, but on the other side, I feel much stronger, with areas I can improve, and a stronger foundation of what to expect, or what is expected of me as a developer. It might be the first time I've felt this confident this entire time through all of this craziness. But even so, i understand just how much is out there that is still so advanced. Never, ever stop learning. 
