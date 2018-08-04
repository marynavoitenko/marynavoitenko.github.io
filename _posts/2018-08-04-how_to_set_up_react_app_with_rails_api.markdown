---
layout: post
title:      "How to set up React App with Rails API"
date:       2018-08-04 19:28:04 +0000
permalink:  how_to_set_up_react_app_with_rails_api
---

A big part of the final project goes into setup. A lot of moving parts to consider:

* Rails API
* Postgres DB (I decided to use Postgres instead of default SQLite so that later on I can deploy my app to Heroku)
* React client
* Being able to run 2 servers at once

After spending quite a bit of time digging the web, these are the steps that I took to make it happen.

**Set up Git Repository**

* Create folder
```
mkdir project-name-app
```
* Change directory into that folder
```
cd project-name-app
```
* Initialize new git repo
```
git init
```
* Create git repo for your app on Github
  * https://github.com/new

* Create README.md, LICENSE.md, CONTRIBUTING.md

* Stage and commit newly created files
```
git add .
git commit -m "First commit"
```
* Set remote (HTTPS or SSH)
```
git remote add origin https://github.com/user/repo.git
git remote add origin git@github.com:user:repo.git
```
* Verify you set up remote correctly
```
git remote -v
```
* Push committed changes to github and set up tracking
```
git push -u origin master
```

**Set up Rails API with Postgres**

* Install postgres with Homebrew
```
brew install postgres
```
* Create new Rails API with Postgres DB
```
rails new project-name-api --api --database=postgresql
```
* Install dependencies with Bundle
```
bundle install
```

**Set up React client**

* Change directory into your main project folder 
* Install create-react-app globally
```
npm i -g create-react-app
```
* Create React client
```
create-react-app client
```


**Test Servers**

Solution to running both servers at the same time is to run them on different ports

* Change directory into your rails api and run server on port 3001
```
rails s -p 3001
```
* In a new Terminal tab change directory into your react client and run server on port 3000
```
npm start
```


Voila! 
