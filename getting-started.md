# Getting Started

## Installation

Add the following to your `Gemfile`:

```ruby
gem 'hg'
```

## Configuration

Remember: **never save your secrets in code**. In order to configure Hg to work with Messenger, there are several secrets you'll need to keep track of. Use projects like [`dotenv-rails`](https://github.com/bkeepers/dotenv)to store your configuration, and be sure to add your secrets file \(e.g. `.env`\) to your `.gitignore` so that you aren't committing them.

You'll need to add the following `ENV` variables to your secrets file:

|`ENV` variable name|Purpose|
|-----------------------------|--------------------------------------------------------------------------|
|`FB_ACCESS_TOKEN`            | The access token granted by Facebook for the page on which the bot lives.|
|`APP_SECRET`                 | The app secret for the bot's Facebook app.                               |
|`VERIFY_TOKEN`               | The verify token for the bot's Facebook app.                             |
|`HOSTNAME`                   | The hostname at which the Rails app is publicly available.               |
|`API_AI_CLIENT_ACCESS_TOKEN` | The API.ai client access token for the bot's API.ai agent.               |
|`REDIS_CONNECTION_POOL_SIZE` | The size of the Redis connection pool for Sidekiq.                       |


## Using `ngrok` for local development
