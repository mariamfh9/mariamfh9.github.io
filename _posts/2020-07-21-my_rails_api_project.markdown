---
layout: post
title:      "My Rails API Project"
date:       2020-07-21 21:54:34 +0000
permalink:  my_rails_api_project
---


One of the most complicated topics in this course for me was definitely Rails. In the last two projects, I got used to the idea of building a Rails app with views, or erb files that worked with my controllers. The biggest change here was that there were no views, and the controllers were working directly with my index.js file, using 'fetch' functions. 

I started off by creating a model of what I wanted my project to be: a grocery store. The api lists grocery store inventory, as well as product details such as quantity, product category and product name. This part was very simple to make--all I had to do was create migrations with the attributes like so: 

```class CreateItems < ActiveRecord::Migration[6.0]
  def change
    create_table :items do |t|
      t.string :title
      t.text :product_details
      t.integer :quanity
      t.string :img_url
      t.integer :category_id

      t.timestamps
    end
  end
end ```

I quickly finished up the backend of the lab as it was something I had done time and time again. Now came the challenge: building the frontend. I realized I needed fetch functions as well as a change in my controllers. Instead of using erb:, I needed to now render json. So my controller actions now looked something like this: 

``` def show
        category = Category.find_by(id: params[:id])
        render json: category
    end ```
		
I found this to be a little easier, but it did take some getting used to. The 'render json' part served as the connection between the frontend and backend. Soon I was on my way  to creating a Rails API!
