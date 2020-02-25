---
layout: post
title:      "Models, Views, and Controllers...What Goes Where?"
date:       2020-02-25 00:15:26 -0500
permalink:  models_views_and_controllers_what_goes_where
---

We have all been there. Working on a problem or adding a fun new feature into our projects, and you cant decide where to properly add the code we want to implement. Rails, though magical, should be implemented properly to remain as efficient, developer friendly, and least repetitive as possible by being DRY while using MVC pattern principals. When programming functionality into your rails app it is important to know what kind of logic should go where.

![confused](https://media.giphy.com/media/y65VoOlimZaus/giphy.gif)

Recently I was feeling slightly confused between helper methods and which logic should go in the model itself. Refactoring your program to be DRY and efficient is an important part of the Rails Final Project, and in MVC the goal is to separate each piece, and put code where it belongs. Here are some helpful explanations and takeaways about where to place what in the MVC. 

### **Models:**
Where the actual data lives. This is the direct link to the database, and is where data should be manipulated and altered.
#### ***So ... what goes in the model?***
For the most part, when you are dealing with code that relates to your data (such as saving, updating, or manipulating an object entry), place it in the model. These methods can easily be called upon and re-used in a DRY fashion from the controller or view.

### **Views:**
What the end user sees when they interact with the app. This should have HTML and CSS specific code, along with some Ruby passed in through ERB tags.
#### ***So ... what goes in the view?***
A view should contain as little to no processing or calculating. This should be done through the model or controller, though at times that may not be fitting, and should be added to a Helper model.

### **Controllers:**
What manages the communication between the View and the Model. The controller takes the data from the Model and prepares it for implementation within the view. 
#### ***So ... what goes in the controller?***
The controller should handle all of the prep work for handling what in the view the user will need to see. This can include setting instance variables of models, calling model methods to manipulate specific data, deciding if a user is logged in, and what to allow or not to allow within the view. The controller will take requests, and apply logic within the requests method to prepare the method data for the upcoming view. They should be skinny, and you should keep as much data manipulating functionality to the model as possible.

### and finally ... **Helpers:**
Helper methods dont manipulate data like a model, but instead are a great way to extract common presentation logic from multiple views. Helpers are methods that are available to your views and encapsulate a common bit of code. They can be seen within a Controller, but are commonly housed within the ```/app/helpers``` folder. Helper methods are generally organized by  controller (remember they help with refactoring heavily repeated bits of code), so would typically be housed under the ```object_helper.rb``` file name.
#### ***So ... what can go in a Helper?***
If you need to build a function that will make creating the view easier, or more DRY, that is a great place to use a Helper. For example, if you are iterating over a list of objects frequently to display a particular piece of information, or see something within your views that is heavily repeated, those can go into a Helper. Helpers can be a great way to keep your views DRY, easier to update, and less bug prone.

## **Conclusion**
When you are busy getting lost in Rails Land, adding fun new functionality to your application, try to think about your placing code within the MVC pattern. Is your code manipulating or working with the database, is it preparing the data for a view, or is it working WITHIN a view, where you may want to refactor to make that view more DRY. This will not only help your fellow developers understand the code you wrote in the future, but also keep the MVC gods happy!

![success](https://media.giphy.com/media/KJwhyORloye76/giphy.gif)

##### Some additional resources for this subject:
- [Stackoverflow Question](https://stackoverflow.com/questions/60658/rails-model-view-controller-and-helper-what-goes-where)
- [Learn Model Methods](https://learn.co/tracks/online-software-engineering-structured/rails/refactoring-with-helpers-and-model-methods/model-class-methods)
- [Learn Helper Methods](https://learn.co/tracks/online-software-engineering-structured/rails/refactoring-with-helpers-and-model-methods/refactoring-views-with-helpers)
