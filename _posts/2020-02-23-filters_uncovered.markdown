---
layout: post
title:      "Filters Uncovered"
date:       2020-02-23 15:13:01 -0500
permalink:  filters_uncovered
---


When it comes to creating your Rails Final Project, the  possibilities seem endless.  Where do you start, what features should you impliment, and what kind of additional improvements can you make near the end. 

For my final project, I made an app called Filtered. This application allows a user to create coffee reviews while adding coffee bean names, details and company information. One of the features I felt would be a great add-on was the ability to filter the reviews you see on the index page. 

![](https://imgur.com/DPbdg6j)

The ability for filters to happen is done through [Scope Methods](https://api.rubyonrails.org/classes/ActiveRecord/Scoping/Named/ClassMethods.html). A **Scope Method** is an ActiveRecord class method available on Rails models which can query the database through ActiveRecord and return the queried result. 

***Scope Model Methods***
![](https://drive.google.com/open?id=11a1tp8H5114xdY1hPM59nKEnioZbS1g_)

To implement these **methods** in your view, you have to first create a *form* which will return the users query request. The return value for this form will submit as a *"post" request*, which your *routes* file will need to direct back to the same *controller method* `(ie. "users#index")` of the original page, but this time when the *get request* hits the controller, the controller's params hash will be populated with the form request.

***Scope Form***
![](https://drive.google.com/open?id=1S1mQA9fxPo4UBDSP-HlXIRKrAqEdhf3D)

Goes to:

***Scope Routes***
![](https://drive.google.com/open?id=1XJ3hbQWDOhyhZnN60iYhW1pOJzOXLxwM)

When implementing these *model **scope methods*** in your *controller*, you have to set conditions for the *view's instance variable* based on the filter *form params* it recieved. These conditions will call on the *model's **scope methods*** you created, and pass the resulted *object instance* to the view with the requested query.

***Scope Controller***
![](https://drive.google.com/open?id=1i38FCgYAwmILbolAu886FDt1sT0QjC-A)

Once the view loads again, that *object instance* `(ie. @reviews)` will be queried based on the requested *params*:

***Result***
![](https://drive.google.com/open?id=1eGUW9re_ezdt220LzbpVo50CMZXDTQjt)

I had a ton of fun implementing **Scope Method Filters** into my [Rails Final Project App: Filtered.](https://github.com/lukekyl/rails_portfolio_project)
Hopefully this blog post helps someone out as they work on their own apps in the future.
I would love to hear your own success stories/struggle points with setting scope method filters in your app in the comments!




