# Getting Started

## Installation

Add the following to your `Gemfile`:

```ruby
gem 'hg'
```

## Configuration

Remember: **never save your secrets in code**. In order to configure Hg to work with Messenger, there are several secrets you'll need to keep track of. Use projects like [`dotenv-rails`](https://github.com/bkeepers/dotenv)to store your configuration, and be sure to add your secrets file \(e.g. `.env`\) to your `.gitignore` so that you aren't committing them.

You'll need to add the following `ENV` variables to your secrets file:

* `FBACCESSTOKEN`



