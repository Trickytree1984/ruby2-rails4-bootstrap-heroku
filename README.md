# Rails Starter App
[![Build Status](https://travis-ci.org/diowa/ruby2-rails4-bootstrap-heroku.svg?branch=mongoid)](https://travis-ci.org/diowa/ruby2-rails4-bootstrap-heroku) [![Dependency Status](https://gemnasium.com/diowa/ruby2-rails4-bootstrap-heroku.svg)](https://gemnasium.com/diowa/ruby2-rails4-bootstrap-heroku) [![Code Climate](https://codeclimate.com/github/diowa/ruby2-rails4-bootstrap-heroku/badges/gpa.svg)](https://codeclimate.com/github/diowa/ruby2-rails4-bootstrap-heroku) [![Coverage Status](https://coveralls.io/repos/diowa/ruby2-rails4-bootstrap-heroku/badge.svg?branch=mongoid)](https://coveralls.io/r/diowa/ruby2-rails4-bootstrap-heroku?branch=mongoid)

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)


This is a starter web application based on the following technology stack:

* [Ruby 2.2.2][1]
* [Rails 4.2.1][2]
* [Puma][3]
* [MongoDB][4]
* [RSpec][5]
* [Twitter Bootstrap for Sass 3.3.4][6]
* [Autoprefixer][7]
* [Font Awesome 4.3.0][8]
* [SLIM][9]
* [RuboCop][10]

[1]: http://www.ruby-lang.org/en/
[2]: http://rubyonrails.org/
[3]: http://puma.io/
[4]: http://www.mongodb.org/
[5]: http://rspec.info/
[6]: http://getbootstrap.com/
[7]: http://github.com/ai/autoprefixer/
[8]: http://fontawesome.io/
[9]: http://slim-lang.com/
[10]: http://github.com/bbatsov/rubocop

Starter App is deployable on [Heroku](http://www.heroku.com/). Demo: http://ruby2-rails4-mongodb-bootstrap.herokuapp.com/

```Gemfile``` also contains a set of useful gems for performance, security, api building...

### Thread safety

We assume that this application is thread safe. If your application is not thread safe or you don't know, please set the minimum and maximum number of threads usable by puma on heroku to 1:

```sh
$ heroku config:set MIN_THREADS=1 MAX_THREADS=1
```

### Heroku Platform API

This application supports fast setup and deploy via [app.json](https://devcenter.heroku.com/articles/app-json-schema):

```sh
$ curl -n -X POST https://api.heroku.com/app-setups \
-H "Content-Type:application/json" \
-H "Accept:application/vnd.heroku+json; version=3" \
-d '{"source_blob": { "url":"https://github.com/diowa/ruby2-rails4-bootstrap-heroku/tarball/mongoid/"} }'
```

More information: [Setting Up Apps using the Platform API](https://devcenter.heroku.com/articles/setting-up-apps-using-the-heroku-platform-api)

### Mandatory add-ons

You need a MongoDB database for your application. We choose the [MongoLab addon](https://addons.heroku.com/mongolab):

```sh
$ heroku addons:add mongolab:sandbox
```

### Recommended add-ons

Heroku's [Production Check](https://blog.heroku.com/archives/2013/4/26/introducing_production_check) recommends the use of the following add-ons, here in the free version:

```sh
$ heroku addons:add newrelic:stark # App monitoring
$ heroku config:set NEW_RELIC_APP_NAME="Rails Starter App" # Set newrelic app name
$ heroku addons:add papertrail # Log monitoring
```

### Secrets.yml

Rails 4.1.0 introduced [secrets.yml](http://edgeguides.rubyonrails.org/upgrading_ruby_on_rails.html#config/secrets.yml). Heroku automatically sets a proper configuration variable in new applications. Just in case you need, the command line is:

```sh
$ heroku config:add SECRET_KEY_BASE="$(bundle exec rake secret)"
```

**NOTE**: If you need to migrate old cookies, please read the above guide.

### Tuning Ruby's RGenGC

Generational GC (called RGenGC) was introduced from Ruby 2.1.0. RGenGC reduces marking time dramatically (about x10 faster). However, RGenGC introduce huge memory consumption. This problem has impact especially for small memory machines.

Ruby 2.1.1 introduced new environment variable RUBY_GC_HEAP_OLDOBJECT_LIMIT_FACTOR to control full GC timing. By setting this variable to a value lower than the default of 2 (we are using the suggested value of 1.3) you can indirectly force the garbage collector to perform more major GCs, which reduces heap growth.

```sh
$ heroku config:set RUBY_GC_HEAP_OLDOBJECT_LIMIT_FACTOR=1.3
```

More information: [Change the full GC timing](https://bugs.ruby-lang.org/issues/9607)

### Nitrous.IO

Starter App supports online development on [Nitrous.IO](http://www.nitrous.io).

**TODO**
