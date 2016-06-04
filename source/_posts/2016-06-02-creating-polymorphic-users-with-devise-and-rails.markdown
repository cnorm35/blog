---
layout: post
title: "Creating Polymorphic Users With Devise and Rails"
date: 2016-05-30 21:44:36 -0400
comments: true
categories: 
---

#Add in links for an updated template to start the project with.
#create template just for the tutorial

# run rake routes to see all the routes and get an idea what pages were
# created

https://gist.github.com/043484e923f87840ca763f6b287a4bfc.git


First and foremost, if you're not familiar with Devise, or are looking
for a good place to get some good information on getting started with
Devise, this is not the post for you.  There are a ton of great
resources, incliding the Devise documentation for getting started.

Today were going to be talking about building differnt types of users
that will build off Devise.  It's a pretty common use case, the most
common of which is some type of service provider and a customer of that
service.  In this example we'll be using Provider and Customer.  

Once we're done, we'll be able to sign up users as either a Provider or
Customer, sign them in after registering, and have a single login page
regardless of the type of user.

To make it easy to get started, I've created a template to generate a
new application for us to jump into.  If you want to know more about
creating templates, or how to create your own, check out my other post.
If you have any problems creating the template, or just prefer to fork
or clone for github, you can do that.

```
$ rails new polymorphic_users -m WHATEVER THE URL OR SETUP IS
```

Once, you have the app up and running, lets take a look at the fields
Devise creates for the User model for us.

```
irb(main):001:0> user = User.new
=> #<User id: nil, email: "", encrypted_password: "", reset_password_token: nil, reset_password_sent_at: nil, remember_created_at: nil, sign_in_count: 0, current_sign_in_at: nil, last_sign_in_at: nil, current_sign_in_ip: nil, last_sign_in_ip: nil, created_at: nil, updated_at: nil>
```

`email`, `encrypted_password`, `reset_password_token`, `reset_password_sent_at`, `remember_created_at`, `sign_in_count`, `current_sign_in_at`, `last_sign_in_at`, `current_sign_in_ip`, `last_sign_in_ip`, `created_at`, `updated_at`

This gives us an idea of the structure that we're going to build on and
think about the best way to model our Users.  To keep the code DRY,
let's think about what fields both types of Users will have in common.
To keep it simple, let's just stick with first_name and last_name.  It's
a pretty reasonable assumption that every user that signs up for our
site will have a first_name and last_name so there's no point in
duplicating those fields in the Provider and Customer tables.  

#####Create migrations for adding first_name and last_name to tables,

#####views, and controllers (i think adding them to the controllers, it
####tricky?)

First, let's add our new fields to the Devise User model.

```
$ rails g migration add_names_to_users first_name last_name
```
That's going to create a migration file that looks like this

```ruby
class AddNamesToUsers < ActiveRecord::Migration
  def change
    add_column :users, :first_name, :string
    add_column :users, :last_name, :string
  end
end
```
Now that we have a new fields on the model, how do we add them to the
strong parameters for Devise? There are a couple ways to go about this.
You can check the recommeded way from Devise [https://github.com/plataformatec/devise#strong-parameters]

But I prefer, a slightly different way.  For both ways, you'll need to
add a `before_filter` inside the `ApplicationController`.  This filter
will run before any action from a Devise controller.

```ruby
  before_action :configure_permitted_parameters, if: :devise_controller?
```

Let's write our method that will run before each Devise action now

```ruby
  def configure_permitted_parameters
    devise_parameter_sanitizer.for(:sign_up) << [:first_name, :last_name]
    devise_parameter_sanitizer.for(:account_update) << [:first_name, :last_name]
  end
```

After that's taken care of, we can update our forms as we normally would
to add the new fields.  Here's what the new user form should look like
now

#check the formation on this, still looks crooked?

```html `app/views/devise/registrations/new.html.erb`
	<div class="panel panel-default">
	  <div class="panel-heading">
	    <h1>Sign up</h1>
	  </div>

	  <div class="panel-body">
	    <%= form_for(resource, :as => resource_name, :url => registration_path(resource_name)) do |f| %>
        <%= devise_error_messages! %>

        <div class="form-group">
	        <%= f.label :first_name %>
	        <%= f.text_field :first_name, autofocus: true, class: "form-control" %>
        </div>

        <div class="form-group">
	        <%= f.label :last_name %>
	        <%= f.text_field :last_name, class: "form-control" %>
	      </div>

	      <div class="form-group">
	        <%= f.label :email %>
	        <%= f.email_field :email, autofocus: true, class: "form-control" %>
	      </div>

	      <div class="form-group">
	        <%= f.label :password %>
	        <%= f.password_field :password, class: "form-control" %>
	      </div>

	      <div class="form-group">
	        <%= f.submit "Sign up", class: "btn btn-primary" %>
	      </div>
	    <% end %>
	  </div>

	  <div class="panel-footer">
	    <%= render "devise/shared/links" %>
	  </div>
	</div>

```
same thing goes for our `edit` page



```html `app/views/devise/registrations/edit.html.erb`
	<div class="panel panel-default">
	  <div class="panel-heading">
	    <div class="panel-title">
	      <h1>Edit <%= resource_name.to_s.humanize %></h1>
	    </div>
	  </div>
	  <div class="panel-body">
	    <%= form_for(resource, :as => resource_name, :url => registration_path(resource_name), :html => { :method => :put }) do |f| %>
        <%= devise_error_messages! %>

        <div class="form-group">
	        <%= f.label :first_name %>
	        <%= f.text_field :first_name, class: "form-control", :autofocus => true %>
	      </div>

        <div class="form-group">
	        <%= f.label :last_name %>
	        <%= f.text_field :last_name, class: "form-control" %>
	      </div>


	      <div class="form-group">
	        <%= f.label :email %>
	        <%= f.email_field :email, class: "form-control" %>
	      </div>


	      <div class="form-group">
	        <%= f.label :password %> <i>(leave blank if you don't want to change it)</i>
	        <%= f.password_field :password, class: "form-control", :autocomplete => "off" %>
	      </div>

	      <div class="form-group">
	        <%= f.label :current_password %> <i>(we need your current password to confirm your changes)</i>
	        <%= f.password_field :current_password, class: "form-control" %>
	      </div>

	      <div class="form-group">
	        <%= f.submit "Update", class: "btn btn-primary" %>
	      </div>
	    <% end %>
	  </div>
	  <div class="panel-footer">
	    <h3>Cancel my account</h3>

	    <p>Unhappy? <%= button_to "Cancel my account", registration_path(resource_name), :data => { :confirm => "Are you sure?" }, :method => :delete, class: "btn btn-warning" %></p>

	    <%= link_to "Back", :back %>
	  </div>
	</div>


```

