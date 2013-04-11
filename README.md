# Maintainable Ruby on Rails

This repository contains material for the Maintainable Ruby on Rails workshop at
[Knowit Developer Summit 2013](http://kds.knowit.no). Presented by
[@bmaland](https://github.com/bmaland) and
[@edmellum](https://github.com/edmellum).

## Requirements

You'll need Ruby 1.9.3 or newer + git. If you don't have this already:

* Windows/Mac: Install Rails using [RailsInstaller](http://railsinstaller.org).
* Linux: Install Ruby 1.9.3 or newer using your package manager or [RVM](https://rvm.io).

Also make sure that you have Rails 3.2.x installed by running `gem install
rails`. Verify by running `rails --version`.

## Resources

These are some excellent resources for tips/inspiration on using Rails and Rails
engines. These will probably useful while you're working on the exercies. :-)

### Rails specific

* [Rails API docs](http://api.rubyonrails.org)
* [Rails Tutorial](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book)

### Engine specific

* [Getting Started with Engines](http://edgeguides.rubyonrails.org/engines.html)
* [Rails::Engine API docs](http://api.rubyonrails.org/classes/Rails/Engine.html)

## Exercises

Form small teams, 2-3 people.

### Up and running

Start by cloning the starter app: 
`git clone git://github.com/bmaland/kds_talks.git`.

Run the following steps:

```shell
cd kds_talks
bundle install
rake db:migrate
bundle exec rake kds:import_talks
bundle exec rails server
```

In theory you should now have a working Rails application running at 
`http://localhost:3000`. If not, shout out and we'll help you along.
