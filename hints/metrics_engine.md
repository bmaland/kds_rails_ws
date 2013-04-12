# Tips/hints for creating a simple metrics engine

Simple engine for storing controller events in the database. In it's simplest
form, it could look something like this:

<img src=http://dl.dropboxusercontent.com/u/2733018/Screenshots/0k.png>

Feel free to actually make this useful! Feature ideas:

- Sorting on columns
- Pagination
- Authentication (you could assume that the "main app" had devise installed
  already)
- Nicer UI/styling

## Create the engine

The following command creates a new folder containing the code for your
engine. Don't do this inside your Rails app, it should be in it's own git
repository etc.

`rails plugin new your_engine_name --mountable`

## Clear out the TODO elements from the gemspec

`sed -i '' -e 's/TODO//' *.gemspec`

## Use scaffolding to create a good starting point

`bundle exec rails generate scaffold event controller:string path:string status:integer view_runtime:float db_runtime:float duration:float`

## Add a root route

`root to: 'clogs#index' `

## Run your engine in isolation

```shell
cd test/dummy
rake -T # notice the install migrations rake task!

rake your_engine_name:install:migrations

rake db:migrate 

bundle exec rails s 
```

## Subscribe to controller events

Create a `config/initializers` folder in your engine root and create a file
called `metrics.rb` with the following contents:

```ruby
ActiveSupport::Notifications.subscribe(/process_action.action_controller/) do |*args| 
  event = ActiveSupport::Notifications::Event.new(*args)

  # TODO make sure these params match your database columns
  params = event.payload.slice(:controller, :path, :status, :view_runtime, :db_runtime)
  params[:duration] = event.duration

  # TODO update with a reference to your actual model name
  YourEngine::YourModel.create!(params)
end
```

## The easy way out

If you're stuck, you can clone a
[basic working implementation](https://github.com/bmaland/clogs):

`git clone git://github.com/bmaland/clogs.git`
