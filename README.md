# ✨ impressionist
Hi! This is my personal fork / notes for the impressionist gem.
It’s a lightweight Rails plugin that logs impressions for actions or models.

# 💡 What it does

  - Logs impressions (page views, model views, etc.) inside your Rails app.
  - You can attach custom messages to impressions.
  - Impressions are stored in your database so you can build your own stats.
  - Bots are ignored automatically.

# ⚡️ How to use
Add to your Gemfile:

```
gem 'impressionist'
```

Install and run the migration:

```
bundle install
rails g impressionist
rails db:migrate
```

Make a model impressionable:

```
class Widget < ApplicationRecord
  is_impressionable
end
```

Log impressions in your controller:

```
class WidgetsController < ApplicationController
  impressionist actions: [:show]
end
```

Or on a specific instance:

```
def show
  @widget = Widget.find(params[:id])
  impressionist(@widget, "custom message")
end
```

Get counts:

```
@widget.impressionist_count          # total unique by request
@widget.impressionist_count(filter: :all)  # all impressions
```

# ✍️ Personal note
I’m keeping this here as a reference for my Rails projects.
Feel free to explore, fork, and tweak it to your needs. ✨
