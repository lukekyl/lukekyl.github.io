---
layout: post
title:      "Snow Conditions Reporter - Ruby CLI Program"
date:       2019-10-11 23:24:37 -0400
permalink:  snow_conditions_reporter_-_ruby_cli_program
---


Dang! 

What a wild ride this course has already been.

Going into the Online Software Engineering course I knew there would be challenges, times of joy and also times of total frustration. The latter seems to stick out alot more in memory, but when finishing my first actual running program in Ruby, I have come to realize that all of those hours stuck and working through crazy errors have helped me actually retain the information and learn many of the concepts required for programming.

The idea behind my first final project, a Snow Conditions Reporter CLI (Command Line Interface) program, is to find the current weather conditions and snow depth report for certain ski resorts (the list is limited in this program, but is easily scalable). On the front end I wanted the user to start the program, be able to pick the resort their favorite resort from the list, and the program would automatically show them the current weather conditions and snow report. In the background, the program would scrape Weather Underground in each resort location and report current conditions. The result would display a weather report like this:

  Vail Ski Resort:
  Current Weather is 29°f and Sunny
  Todays High - 45°f
  Todays Low - 19°f
  Snow Depth - 29 inches
	
The concept felt simple, the application was much more challenging. The hardest part I struggled with on this project was actually just getting the environment for development set up! I followed the tutorial videos, was able to learn the concepts of cloning and pushing on git, and eventually was able to stumble my way to building a functioning environment similar to what Avi built in his tutorial.

Developing the program was more straight-forward then I thought to get a functioning program actually running. My program has three classes; the CLI, Links, and Resort. The CLI opens initially, running the command line menu. The CLI menu calls on the class "Links" (containing an array of hashes that include a resort name and a url link to scrape), which displays a list of available resorts to choose from. After the user selects the resort whos conditions they would like to view, the program calls upon the array of resorts, and uses the name and url as inputs to create an object in the Resorts class, which scrapes the current weather information from the input link. With that resort's information held in an object, the menu then displays the information in a user friendly format.

Getting the program working originally was a fairly quick process The fine tuning, error management, and dry code adjustments took me much longer, and I am sure can always be improved upon.

I am super excited about what my corhort and I have achieved so far, and can't wait to see all of the amazing programs that my Online Software Engineering classmates create. Where will this course take us next...

Dang!
	
