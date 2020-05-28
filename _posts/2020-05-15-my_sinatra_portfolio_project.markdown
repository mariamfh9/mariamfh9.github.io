---
layout: post
title:      "My Sinatra Portfolio Project!"
date:       2020-05-15 19:25:57 -0400
permalink:  my_sinatra_portfolio_project
---


I've finally completed my Sinatra Project, and to say it feels good is an understatement. At first, this project was very confusing even though I was able to complete the assignments in this section successfully. I thought I had it almost done with on the first day of project week. However, I quickly realized that wasn't the case when I realized how careful I had to be because of the topic I chose. My project is an account for users to store their passwords. Basically, a virtual password vault. This entails that the project must be extremely careful and protective of arguably, a persons most valuable set of data: their passwords. 

This part took me about 2 days to complete and master, as I tried to break my program for hours and then come up with a fix. Something that I really had trouble with was user validation. As simple as it may seem to use 'validates' to validate the user's password and username in my models, I didn't realize there was a second part to it all: error handling. 

I ran into many issues when coming up with a solution for handling the errors. I started off by using the Ruby Flash gem, to throw error messages such as "Please fill in all the fields." if the user left the password and/or username field blank, and  of course "This username already exists." if the user tried to sign up with an existing username. 

However, I wasn't sure where to place these error messages in my code. I finally realized I needed conditions, such as: 

```
if params[:username] == "" || params[:password] == ""
        flash[:alert] = "Please fill in all the fields."
``` 

Here, I was able to check if any one of the password and/or username fields were blank before throwing the error message. At this point, I knew I was very close to the finish line, and I just needed a way to handle the error!  I just needed to redirect the user to the correct page. With some trial and error, running through my program on the browser, I realized that the user needed to be redirected back to the sign up page if they had left any of the signup fields blank. I was easily able to do that with `redirect to '/signup'`. Hereis some of my completed code for error handling!
```
if params[:username] == "" || params[:password] == ""
        flash[:alert] = "Please fill in all the fields."
          redirect to '/signup'
      else 
        @owner = Owner.new(params)
         if @owner.save
          session[:owner_id] = @owner.id
          redirect to '/accounts'
         else 
          flash[:alert] = "This username already exists."
          redirect to '/signup'
         end   
      end
```
In this code, I am successfully able to check to make sure none of the sign up fields are left blank, as well as making sure that the user creates a new username, not one that already exists. 

I was able to finally make my project work without any errors, and I was overjoyed. I was now going to stylize my webpage, something I've always loved about web design! 

Now I can say that I've finally gotten it done with, and I can't wait for this short break! Whew!
