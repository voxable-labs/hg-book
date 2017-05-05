# Facebook Messenger

## Deploying your bot

### Heroku

#### 1. Create a new Heroku app

#### 2. Add a Redis Heroku Add-on

Heroku has [a number of great Redis providers](https://elements.heroku.com/addons/). Add one to your app from the Settings > Add-ons section.

#### 3. Add a Procfile to your project

You're going to need [a Procfile](https://devcenter.heroku.com/articles/procfile). This one should probably work to get you started:

```bash
web: bin/rails server -p $PORT -e $RAILS_ENV
worker: bundle exec sidekiq -c $SIDEKIQ_CONCURRENCY
```

#### 4. Configure the environment

You'll need to add the following config variables to your new Heroku app:

| Variable | Purpose |
|----------|---------|
|`API_AI_CLIENT_ACCESS_TOKEN`|Client access token for your production API.ai agent.|
|`APP_SECRET`|The app secret for the production version (i.e. not test) of your Facebook app.|
|`FB_ACCESS_TOKEN`|The access token for the Facebook page on which your production bot will live.|
|`HOSTNAME`|The public URL for this app.|
|`SIDEKIQ_CONCURRENCY`|The number of Sidekiq workers to run.|
|`VERIFY_TOKEN`|Your Facebook webhook verify token.|


#### 5. Push your project to Heroku

```console
$ git push heroku master
```

#### 6. Migrate the database

```console
$ heroku run rake db:migrate --app YOUR_APP
```

#### 7. Active your worker dynos

From the Resources tab, activate your worker dynos.


