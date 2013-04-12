# Tips/hints for creating a simple blog engine

Simple engine for adding a blog section to your Rails app. Unlike the
[metrics engine](metrics_engine.md), it probably makes sense to make this behave
more tightly integrated with the main application, sharing it's layout etc. It
could look like this for example:

<img src=http://dl.dropbox.com/u/2733018/Screenshots/0l.png>

Note the link to the blog section in the header.

## Create the engine

The following command creates a new folder containing the code for your
engine. Don't do this inside your Rails app, it should be in it's own git
repository etc.

`rails plugin new your_engine_name --mountable`

## Clear out the TODO elements from the gemspec

`sed -i '' -e 's/TODO//' *.gemspec`

## Use scaffolding to create a good starting point

`bundle exec rails generate scaffold blogpost title body:text`

## Add a root route

Add the following to `config/routes.rb` in the engine folder.

`root to: 'blogposts#index'`

## Run your engine in isolation

```shell
cd test/dummy
rake -T # notice the install migrations rake task!

rake your_engine_name:install:migrations

rake db:migrate 

bundle exec rails s 
```
