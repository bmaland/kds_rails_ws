# active_admin hints

Active Admin is a bit picky about the order of your routes. If you get errors,
look at this for inspiration:

```ruby
KdsTalks::Application.routes.draw do
  root to: 'home#index'

  resources :talks

  devise_for :users

  devise_for :admin_users, ActiveAdmin::Devise.config
  ActiveAdmin.routes(self)
end
```
