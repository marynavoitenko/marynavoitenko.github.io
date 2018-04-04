---
layout: post
title:      "The Rails way"
date:       2018-04-04 20:18:54 +0000
permalink:  the_rails_way
---


It feels like an eternity since I’ve started learning Rails, but at the same time like I’ve barely scratched the surface. They didn’t lie when said that Rails is huge, on another level huge, comparing to Sinatra. 

So I’ve been learning Sinatra for a month and a half or so, writing many lines of code, learning MVC and RESTful routes. And then I get to Rails and with 1 line of code, I can basically have a RESTful MVC application running successfully on a local environment (I’m talking about scaffold generators, of course). 

Moving from Sinatra to Rails is pretty much like comparing swimming pool to an ocean.

No doubt the number of requirements for portfolio project grew significantly as well.

Some of the most fun and different from Sinatra are:

* Log in from any of the known providers: Facebook, Twitter, Google, Github, etc. 
* Nested resources
* Helper methods
* Partial views

I still stand by my workflow from previous projects: [data model visualization](http://mindthequality.com/visualization_in_sinatra_portfolio_project) and [Trello board for requirements](http://mindthequality.com/cli_project_-_lessons_learned). 

For my Rails project, I went with something that has been on my mind lately. Vinyls. And since I’ve been buying quite a few vinyls lately and trying to find rare items that are not in production anymore, I decided to work on Vinyl Exchange. A platform for buying and selling vinyls. A user can create a new vinyl, set a price, inventory, and mark for sale, or buy a vinyl that any other user has posted. 

**Result of my data modeling session:**

* Vinyl <> Artist :: one-to-many
* Vinyl <> Genre :: many-to-many
* User <> Vinyl :: one-to-many
* User <> Cart :: one-to-many
* Cart <> Vinyl :: many-to-many


![](../img/Vinyl Exchange - ER Model.png)


Happy coding!
