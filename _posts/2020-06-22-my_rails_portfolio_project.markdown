---
layout: post
title:      "My Rails Portfolio Project"
date:       2020-06-22 20:36:33 +0000
permalink:  my_rails_portfolio_project
---


The Rails Portfolio Project was definitely one of the most difficult thus far. I started off by trying to build it up myself, using the ```rails new``` command. This quickly generated the framework I needed to develop my project. I thought I was on a role! However, I ran into some issues when I started creating my Log In page. We had to create the app so that the user can log in with their email and password, or log in from an external source such as Github or Facebook. I realized I needed to use Omniauth for this. 

I quickly realized that the best way to go about this was using Devise. Devise is definitely the gem of 'gems' as I like to put it! By putting ```'gem devise'```  in my Gemfile and running ```bundle install```, following a few more steps, I was able to get my log in page up and running. My User model was automatically generated, along with all it's corresponding views. All I needed was to add a registrations controller to allow the user to Sign Up for an account and the lines:

```
 devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable, :omniauthable
        
```

in my user model. As soon as I started up the server, I had a log in page up and running. The next step was to add the gem ```'omniauth-github' ``` into my Gemfile. This allowed for the user to Log in, Sign up, or Log in with their Github account. Then the usual ```bundle install``` and adding 
```
 def self.from_omniauth(auth)
    where(provider: auth.provider, uid: auth.uid).first_or_create do |user|
    user.provider = auth.provider
    user.name = auth.info.name 
    user.uid = auth.uid
    user.email = auth.info.email 
    user.password = Devise.friendly_token[0,20]
    end 
  end 
```

to my User model. This allowed for the user to log in from an external source. All I had left to do was run ```rake db:migrate``` as I had my Omniauth and devise migrations automatically generated for me! 

Now I have a full log in page, with an option to log in with Github!!!

The rest of the project was just a lot of MVC logic. Now I can proudly say that I am done! 
