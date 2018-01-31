---
layout: post
title:      "Visualization in Sinatra Portfolio Project"
date:       2018-01-31 04:43:17 +0000
permalink:  visualization_in_sinatra_portfolio_project
---


Aaand here we go again - 2nd Portfolio Project. How exciting and terrifying! But I have to say much less terrifying than the 1st project. Is it only me?

I definitely took [my learnings from the CLI project](http://mindthequality.com/cli_project_-lessonslearned) and applied here. Great success!

**Requirements for the project included:**

* MVC design pattern
* ActiveRecord
* Multiple models
* Associations: at least one has_many relationship
* Must have user accounts
* CRUD
* Validations

Oooff a lot of stuff to keep in your head and design an application out of it.

Be kind to yourself, let it all out, talk it out, draw it out.

**Data Modeling**

Start with Models - the brain of your application. From the first sight at the requirements, you see that you need a `User` model.

Now it’s time to think about what kind of application you actually want to build.
What is the resource that `belongs_to` a user in your application? See, you already talk in associations :-) 
Being a QA Analyst for many years, I decided to build something that I use constantly. You might ask why would I build something that already exists. Great question! I am just learning and building something that I use but have no idea how it works behind the scenes sounds exciting to me and a great learning experience along the way. So, I decided to build Test Case Library. 

Q: What is the resource that belongs_to a user in my application?
A: Test Case

User `has_many` Testcases
Testcase `belongs_to` User

Thinking about the application as an end user, I know that having many test cases is not enough. I need categorization of some sort. I decided to do it by Feature. 

Feature `has_many` Testcases
Testcase `has_many` Features

Sounds like a `many-to-many` relationship, that screams for join table. 

Next step in visualizing your project is an Entity Relationship Diagram. 

> An [entity–relationship diagram](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model) describes inter-related things of interest in a specific domain of knowledge. An ER model is composed of entity types and specifies relationships that can exist between instances of those entity types.

![](../img/Test Case Library - ER model.png)

From there, it was clear how to write down my models, validations, and migrations. 

Good luck with your project! :-)


