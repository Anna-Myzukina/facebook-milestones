# Project: Building Facebook

* NOTE before start chreate project using this command (name_of_project it`s example, you should change it on your own name of your project for example: facebook-clone...)

        rails new name_of_project --database=postgresql


## Milestone 1:

* In this project you should create ERD(Entity Relationship Diagram) diagram, it`s image of your future database. I used online tool [lucidchart](https://www.lucidchart.com/) to draw that diagram, create folder "docs" and add to folder that image with diagram. Follow this video to understand how it works [Entity Relationship Diagram (ERD) Tutorial - Part 1](https://www.youtube.com/watch?v=QpdhBUYk7Kk&vl=en)
* Watch next video to be familiar with Primary and Foreign Keys [Entity Relationship Diagram (ERD) Tutorial - Part 2](https://www.youtube.com/watch?v=-CuY5ADwn24)

Here is a screenshot with example of such image with diagram:
![screen]()


## Milestone 2:

* In this Milestone you need to setup project as it is described in Odin requirements. It means that you should add necessary gems to your Gemfile.
I recommended to add next gems:

* gem ['bootstrap-sass', '3.3.7'](https://github.com/twbs/bootstrap-rubygem)
* gem ['bcrypt',         '3.1.12'](https://github.com/codahale/bcrypt-ruby)
* gem ['faker',          '1.7.3'](https://github.com/faker-ruby/faker)
* gem ['will_paginate', '3.1.6'](https://github.com/mislav/will_paginate)
* gem ['bootstrap-will_paginate', '1.0.0'](https://github.com/yrgoldteeth/bootstrap-will_paginate) 
* gem ['rubocop'](https://www.rubocop.org/en/stable/)
* gem ['devise'](https://github.com/plataformatec/devise)
* gem ['omniauth-facebook'](https://github.com/mkdynamic/omniauth-facebook)
* gem ["font-awesome-rails"]()
* gem ['gravatar_image_tag'](https://github.com/mdeering/gravatar_image_tag)

group :development, :test do
* gem ["rspec-rails"](https://github.com/rspec/rspec-rails) 
* gem ['sqlite3', '1.3.13'](https://github.com/sparklemotion/sqlite3-ruby)
end
        
 
 Than use next command in your terminal
 
      $  bundle install
      $  bundle updete

1. Cause we added bootstrap to Gemfile in next step we should create file and add bootstrap to our application

        touch app/assets/stylesheets/custom.scss

Inside this file app/assets/stylesheets/custom.scss add next code

        @import "bootstrap-sprockets"; 
        @import "bootstrap";

2. Cause we added font-awesom in your application.css, include next:

/*
 *= require font-awesome
 */

 Inside this file app/assets/stylesheets/custom.scss add next code

        @import "font-awesome";

On this site https://fontawesome.com/?from=io you can choose any icons you want


## Milestone 3:

I this project we Create models with associations and implement all requested features for users and posts. Add authentication with Devise as described in requirements.

rails generate scaffold User first_name:string last_name:string email:string password:string birthday:string gender:string

rails db:migrate