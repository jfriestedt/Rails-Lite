# Monorail
Monorail is a lightweight MVC framework inspired by Rails.

## Features
Monorail provides you with session cookies, a base controller, ERB views, and a router to direct HTTP requests

## Getting Started
1. Clone this repo and use `cd` to navigate to it
2. Run `bundle install`
3. Start a server
4. Follow the instructions below to add Controllers, Routes, and Views.

## Adding controllers
Controllers should be added to ``app/controllers`` and must inherit from ``lib/controller_base.rb``

```ruby
# app/controllers/my_controller.rb
require '../../lib/controller_base'

class MyController < ControllerBase
  # ...
end
```

## Constructing routes

Construct routes by passing a regex, controller name, and action symbol to ``Router.draw``
```ruby
# config/routes.rb

MyRouter.draw do
  get Regexp.new("^/posts$"), PostsController, :index
  get Regexp.new("^/posts/new$"), PostsController, :new
  post Regexp.new("^/posts$"), PostsController, :create
  get Regexp.new("^/posts/(?<id>\\d+)$"), PostsController, :show
  get Regexp.new("^/posts/(?<id>\\d+)/edit$"), PostsController, :edit
  patch Regexp.new("^/posts/(?<id>\\d+)$"), PostsController, :update
  delete Regexp.new("^/posts/(?<id>\\d+)$"), PostsController, :destroy
end
```

## Creating ERB Views

Add ERB views to ``app/views/``

```html
<!-- app/views/posts/show.html.erb -->

<h1><%= @post.title %></h1>
<h3>by <%= @post.author %></h3>

<br />

<p><%= @post.body %></p>
```

## Technologies
* Ruby
* Rack
* ERB
* JSON
