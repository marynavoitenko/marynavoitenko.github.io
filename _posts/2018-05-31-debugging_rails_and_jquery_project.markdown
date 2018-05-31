---
layout: post
title:      "Debugging Rails and JQuery Project"
date:       2018-05-31 20:36:04 +0000
permalink:  debugging_rails_and_jquery_project
---

I have to say I couldn’t wait to start learning the ropes of JavaScript. I was so excited but also terrified. Just because JavaScript is one of the most talked about programming languages, but also the one to have so many mixed opinions, of the most loved and hated (or should I better say misunderstood) at the same time. Working in tech for quite a few years, I see engineers pull their hair out all the time while screaming all kinds of things about JavaScript. 

New language => new bugs. I was ready to fasten my belt. Haha.

I’m going to share one of my bug experiences that actually happened this morning, right after I’ve merged last updates into master and was ready to record user walkthrough. I pressed ‘record’ and … I can’t sign up or log in to my app … what happened?!?! I haven’t even touched my authentication while working on jQuery front-end.

I check my server logs and see: 

```
Completed 401 Unauthorized in 1ms (ActiveRecord: 0.0ms)
```

That doesn’t make sense, everything worked perfectly yesterday. I flip the table!!! Ok, just kidding :) I drink some water and take a deep breath. I try again and look at server logs..again.

![](../img/rails_jquery_project_blogpost_01.png)

Hmmm, that doesn’t look right. *‘vinyls’*... But I shouldn’t be hitting vinyls controller at this point... I open browser console and repeat steps.

![](../img/rails_jquery_project_blogpost_03.png)

*POST request to "/vinyls"* Huh?!

I started deduction method in my head: I haven’t touched authentication and users controller, it has to be my js file and all the event handlers that get loaded on page load. … and then I remembered what I did. Duh!!! I’ve added callback a function to a form submit event. But which form?? Every form… 

```
$('form').submit(function(e) {
       e.preventDefault();
       let values = $(this).serialize();
       $('.alert').hide();
       $.ajax({
           type: 'POST',
           data: values,
           url: '/vinyls/',
           dataType: 'json'
       }).done(function(data) {
```

I’ve attached it to *$(‘form’)* … wow… so, basically, my callback function was getting executed on each form submit. Since Sign up / Sign in are my first forms in the app => I was not able to log in / sign up. 

As soon as I updated selector to a specific class of my form, I was able to successfully log in and record walkthrough. 

```
$('.js-new-vinyl-form').submit(function(e) {
       e.preventDefault();
       let values = $(this).serialize();
       $('.alert').hide();
       $.ajax({
           type: 'POST',
           data: values,
           url: '/vinyls/',
           dataType: 'json'
       }).done(function(data) {
```

Great success!

