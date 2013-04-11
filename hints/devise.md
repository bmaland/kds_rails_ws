# Hints for devise/authentication

## Navigation

The following snippet could be used in `_topnav.html.erb`:

```ruby
<% if user_signed_in? %>
  <li><%= link_to 'My account', main_app.edit_user_registration_path %></li>
  <li class="divider"></li>
  <li><%= link_to 'Log out', main_app.destroy_user_session_path, method: 'delete' %></li>
<% else %>
  <li><%= link_to 'Log in', main_app.new_user_session_path %></li>
<% end %>
```
