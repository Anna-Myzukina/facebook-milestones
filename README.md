# Project: Building Facebook

* NOTE before start chreate project using this command (name_of_project it`s example, you should change it on your own name of your project for example: facebook-clone...)

        rails new name_of_project --database=postgresql
       
* NOTE itis very important!!! You should install postgresql in your operating system! Next article should help: [How To Install and Use PostgreSQL on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)
        
* This article and video can be useful [The Ultimate Intermediate Ruby on Rails Tutorial: Let’s Create an Entire App!](https://www.freecodecamp.org/news/lets-create-an-intermediate-level-ruby-on-rails-application-d7c6e997c63f/) , also this article [Adding Authentication with Devise](https://guides.railsgirls.com/devise) and video: [Testing with RSpec](https://www.youtube.com/watch?v=71eKcNxwxVY)

* If you forgot during creating your app add next peace of code --database=postgresql please follow next article [Making the Change From SQLite3 to PostgreSQL - Ruby on Rails](https://dev.to/torianne02/making-the-change-from-sqlite3-to-postgresql-ruby-on-rails-2m0p) and add postgresql manually : But main you should add lat version of postgress.

## Milestone 1:

* In this project you should create ERD(Entity Relationship Diagram) diagram, it`s image of your future database. I used online tool [lucidchart](https://www.lucidchart.com/) to draw that diagram, create folder "docs" and add to folder that image with diagram. Follow this video to understand how it works [Entity Relationship Diagram (ERD) Tutorial - Part 1](https://www.youtube.com/watch?v=QpdhBUYk7Kk&vl=en)
* Watch next video to be familiar with Primary and Foreign Keys [Entity Relationship Diagram (ERD) Tutorial - Part 2](https://www.youtube.com/watch?v=-CuY5ADwn24)

Here is a screenshot with example of such image with diagram:
![screen](https://github.com/Anna-Myzukina/facebook-milestones/blob/master/docs/ERD-facebook.jpeg)


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


* I had error with migration so this link helps me https://github.com/rack/rack/commit/f80e65d5dde251ee446e4c0bd038f8bc4ec30314


https://stackoverflow.com/questions/11789867/error-while-dbmigrate-for-an-existing-model



devise/seccions/new.html.erb

<div class="row">
<div class="col-md-4 img">
  <%= image_tag 'facebook1.png' %>
</div>
<div class="col-md-2">
</div>
<div class="col-md-5">
<h2>Log in</h2>

<%= form_for(resource, as: resource_name, url: session_path(resource_name)) do |f| %>
    <div class="form-row">
      <div class="field">
    <%= f.label :email %><br />
    <%= f.email_field :email, autofocus: true, autocomplete: "email" %>
  </div>

    <div class="field">
    <%= f.label :password %><br />
    <%= f.password_field :password, autocomplete: "current-password" %>
  </div>

  <% if devise_mapping.rememberable? %>
      <div class="field">
      <%= f.check_box :remember_me %>
      <%= f.label :remember_me %>
    </div>
  <% end %>

  <div class="actions">
    <%= f.submit "Log in" %>
  </div>
<% end %>

<%= render "devise/shared/links" %>

devise/registrations/new.html.erb


<%= form_for(resource, as: resource_name, url: registration_path(resource_name)) do |f| %>
  <%= render "devise/shared/error_messages", resource: resource %>
  
<div class="row">
<div class="col-md-4 img">
  <%= image_tag 'facebook1.png' %>
</div>
<div class="col-md-2">
</div>
  <div class="col-md-5">
  <h2 class="pl">Create a New Account</h2>
  <h4 class="pl">It`s quick and easy</h4>
  <div class="form-row">
    <div class="field">
    <%= f.label :username%><br/>
    <%= f.text_field :username, autofocus: true, autocomplete: "name", placeholder: "First name" %>
    </div>

      <div class="field">
      <%= f.label :sirname%><br/>
    <%= f.text_field :sirname, autofocus: true, autocomplete: "name", placeholder: "Last name" %>
    </div>

      <div class="field">
      <%= f.label :email%><br/>
    <%= f.email_field :email, autofocus: true, autocomplete: "email", placeholder: "Email"  %>
    </div>

      <div class="field">
      <%= f.label :password%><br/>
    <% if @minimum_password_length %>
    <em>(<%= @minimum_password_length %> characters minimum)</em>
    <% end %><br />
    <%= f.password_field :password, autocomplete: "new-password", placeholder: "New password" %>
    </div>

 
    <label class="form-group col-md-12 text-muted birthday-gender" for="inlineFormCustomSelect">Birthday</label>
    <div class="form-group col-md-4">
        <select class="custom-select" id="inlineFormCustomSelect">
        <option selected>Month...</option>
        <option value="1">Jan</option>
        <option value="2">Feb</option>
        <option value="3">Mar</option>
        <option value="3">Apr</option>
        <option value="3">May</option>
        <option value="3">Jun</option>
        <option value="3">Jul</option>
        <option value="3">Aug</option>
        <option value="3">Sep</option>
        <option value="3">Oct</option>
        <option value="3">Nov</option>
        <option value="3">Dec</option>
      </select>
    </div>
    <div class="form-group col-md-4">
        <select class="custom-select" id="inlineFormCustomSelect">
        <option selected>Day...</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
        <option value="16">16</option>
        <option value="17">17</option>
        <option value="18">18</option>
        <option value="19">19</option>
        <option value="20">20</option>
        <option value="21">21</option>
        <option value="22">22</option>
        <option value="23">23</option>
        <option value="24">24</option>
        <option value="25">25</option>
        <option value="26">26</option>
        <option value="27">27</option>
        <option value="28">28</option>
        <option value="29">29</option>
        <option value="30">30</option>
        <option value="31">31</option>
      </select>
    </div>
    <div class="form-group col-md-4">
        <select class="custom-select" id="inlineFormCustomSelect">
        <option selected>Year...</option>
        <option value="2000">2000</option>
        <option value="1999">1999</option>
        <option value="1998">1998</option>
        <option value="1998">1997</option>
        <option value="1998">1996</option>
        <option value="1998">1995</option>
        <option value="1998">1994</option>
        <option value="1998">1993</option>
        <option value="1998">1992</option>
        <option value="1998">1991</option>
        <option value="1998">1990</option>
        <option value="1998">1989</option>
        <option value="1998">1988</option>
        <option value="1998">1987</option>
        <option value="1998">1986</option>
        <option value="1998">1985</option>
        <option value="1998">1984</option>
        <option value="1998">1983</option>
        <option value="1998">1982</option>
        <option value="1998">1981</option>
        <option value="1998">1980</option>
      </select>
    </div>

    <label class="form-group col-md-12 text-muted birthday-gender" for="">Gender</label>
    <div class="form-group col-md-4 custom-control custom-checkbox">
    <input type="checkbox" class="custom-control-input" id="customControlAutosizing">
    <label class="custom-control-label text-dark" for="customControlAutosizing">Female</label>
    </div>

    <div class="form-group col-md-4 custom-control custom-checkbox">
    <input type="checkbox" class="custom-control-input" id="customControlAutosizing">
    <label class="custom-control-label text-dark" for="customControlAutosizing">Male</label>
    </div>

    <div class="form-group col-md-4 custom-control custom-checkbox">
    <input type="checkbox" class="custom-control-input" id="customControlAutosizing">
    <label class="custom-control-label text-dark" for="customControlAutosizing">Custom</label>
    </div>

    <p class="pl">
    By clicking SignUp, you agree to our <a href="#">Terms</a>,
    <a href="#">Data Policy</a> and <br> <a href="Cookies Policy.">
    You may recieve SMS Notifications from us and can opt any time.
    </p>



</div>

  <div class="actions pl">
    <button class="btn">Sign up</button>
  </div>
  <hr>
  <h4 class="pl"><a href="#">Create a Page</a> for a celebrity, band or busyness.</h3>
    </div>
</div>
<% end %>

<%= render "devise/shared/links" %>


## Milestone 4:
