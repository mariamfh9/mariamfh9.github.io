---
layout: post
title:      "Binding.pry: A Life Saver!"
date:       2020-08-28 16:09:34 +0000
permalink:  binding_pry_a_life_saver
---

One of the biggest challenges I've come across in programming has been debugging. That all ended when I learned to use Binding.pry. 

I simply add `gem 'pry'` to my Gemfile and run `bundle install`. Now any time I run across an issue, I insert a `binding.pry` in my code to check the input/output! 

In my example, I created an app where the user can store any kind of party planning data! That can range from their todo list to their grocery list. 

While working on my CRUD (create, read, update, destroy) actions, I ran into some issues while creating a new party. 

```
def create
      binding.pry
      @party = current_user.parties.build(party_params)
      binding.pry
       if @party.save
        binding.pry 
          redirect_to party_path(@party)
        else
          render :new 
        end
    end
```

As you can see, I have inserted `binding.pry` after each line of code. Now when I start the server and run my program, the user will input their information on the form here: 

![](https://ibb.co/TwBWxTz)

As soon as I submitted the form I hit my pry, and was able to use the console to figure out what my code was outputting or which lines were working. When the user adds a new party, the issue was that they were not being saved. I was able to figure out what was wrong all thanks to this trick! 

