---
layout: post
title:      "React / Redux - How to refresh the data after creating a new item"
date:       2018-08-18 17:57:55 -0400
permalink:  react_redux_-_how_to_refresh_the_data_after_creating_a_new_item
---


For my final project I’ve decided to build a message board. Platform where anyone can leave a message, anonymous or not, specifying recipient or not. A collection of fun, informative, or inspirational messages.

![](../img/Message_Board_01.png)

One of the challenges for me was to update the Message Board with the newly created Message. The way I envisioned the flow of my application is: 

1. View all messages on Message Board
2. Add a new message => 
3. On Submit => Redirect to Message Board
4. View all messages on Message Board including the newly created one

Seems straightforward enough. The challenging part was going from step 3 to 4. 

So, what happens here? And what is so challenging?

As you know, web requests in JavaScript are *asynchronous*. As soon as we dispatch an action to create a new message (POST request to API), the next line of code starts running before the request resolves.

What does it mean for my application? It means that after submitting a POST request to create a new message, it redirects to Message Board before the new message is created and added to application state. So, by the time Message Board loads, application state doesn’t include the newly created message yet.

What do we do? Component Lifecycle methods to the rescue. ComponentWillReceiveProps()
This will help to re-render the component when the new props are received.

```
componentWillReceiveProps(nextProps) {
       if (this.props.isPosting === true && nextProps.isPosting === false) {
           this.props.fetchMessages();
       }
}
```

* **fetchMessages()** - action creator to fetch all messages from DB
* **isPosting** - one of state’s properties. Make it available to component in mapStateToProps()
* **(this.props.isPosting === true && nextProps.isPosting === false)** - only re-render after creating new message (when message is being created isPosting = true, right after it is created - isPosting = false)

Now, after a new message is being created, application redirect to Message Board. Then when the message is successfully created, the state of the app is apdated => component re-rendered.