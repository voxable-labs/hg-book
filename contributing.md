# Contributing

## Developing against a local gem

If you want to make changes to Hg gems as part of a project you're working on, simply clone the gem you'd like to change, and reference the path to the gem in your `Gemfile`:

```ruby
# Uncomment below line when working on local version of hg
gem 'hg', path:  '../../hg'
# gem 'hg', github: 'techpeace/hg', ref: '806655ab9eea68b725a745f45e4a79f37f6583f9'
```

Be sure not to commit your `Gemfile` in this state, as this will break the bundle for everyone else working on your project. Push your commits to your fork of the gem, then reference the specific commit project and commit hash in your `Gemfile`, and commit the `Gemfile` and `Gemfile.lock` in that state.

Once your changes are ready to go, be sure to send us a pull request!