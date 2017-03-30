# Getting Started

## Installation

Add the following to your `Gemfile`:

```ruby
gem 'hg'
```

## Configuration

Remember: **never save your secrets in code**. In order to configure Hg to work with Messenger, there are several secrets you'll need to keep track of. Use projects like [`dotenv-rails`](https://github.com/bkeepers/dotenv)to store your configuration, and be sure to add your secrets file \(e.g. `.env`\) to your `.gitignore` so that you aren't committing them.

You'll need to add the following `ENV` variables to your secrets file:

| `ENV` variable name | Purpose |
| --- | --- |
| `FB_ACCESS_TOKEN` | The access token granted by Facebook for the page on which the bot lives. |
| `APP_SECRET` | The app secret for the bot's Facebook app. |
| `VERIFY_TOKEN` | The verify token for the bot's Facebook app. |
| `HOSTNAME` | The hostname at which the Rails app is publicly available. |
| `API_AI_CLIENT_ACCESS_TOKEN` | The API.ai client access token for the bot's API.ai agent. |
| `REDIS_CONNECTION_POOL_SIZE` | The size of the Redis connection pool for Sidekiq. |

## Setup

In the following setup instructions, replace `BOTNAME` with the name of your bot \(in the below example, this would be `archmaester_bot`\).

* add `app/bot` directory
  * `BOTNAME_bot/` 
  * `BOTNAME_bot.rb`

A good starting point for `BOTNAME_bot.rb` :

```ruby
class ArchmaesterBot
  include Hg::Messenger::Bot

  VERSION='0.0.1-pre'

  # BUG: greeting_text and image_url_base have to appear first, or load errors will be thrown
  greeting_text 'Welcome'

  image_url_base ENV['HOSTNAME']

  persistent_menu do
    call_to_action 'Main menu', payload: {
      action: Actions::MAIN_MENU
    }
  end

  get_started action: Actions::MAIN_MENU

  class << self


  end
end
```

### Add an initializer

Add an initializer for your bot to `config/initializers`:

```ruby
ArchmaesterBot.init unless Rails.env.test?
```

### Set up autoload paths

Add the following to `config/environments/development.rb`:

```ruby
config.autoload_paths += Dir["#{Rails.application.config.root}/app/bot/BOTNAME_bot/**"]
```

## Using `ngrok` for local development



