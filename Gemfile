# frozen_string_literal: true

source 'https://rubygems.org'

ruby '2.4.1'
gem 'rails', '4.2.8'

# Servers
gem 'puma'

# API
# gem 'rabl'

# ODM
gem 'mongoid'

# Pagination
# gem 'kaminari'

# App monitoring
# gem 'airbrake'
gem 'newrelic_rpm'

# Security
# gem 'secure_headers'

# Miscellanea
# gem 'google-analytics-rails'
# gem 'http_accept_language'
# gem 'resque', require: 'resque/server' # Resque web interface
gem 'slim-rails'

# Assets
gem 'autoprefixer-rails'
gem 'coffee-rails', '~> 4.2'
gem 'i18n-js'
gem 'jquery-rails'
gem 'sass-rails', '~> 5.0'
gem 'slim_assets'
gem 'turbolinks'
gem 'twbs_sass_rails'
gem 'uglifier', '>= 1.3.0'

group :development, :test do
  gem 'byebug'
  gem 'factory_girl_rails'
  gem 'faker'
  gem 'pry'
  gem 'pry-byebug'
  gem 'pry-rails'
  gem 'rspec-rails'
  gem 'rubocop', require: false
  gem 'scss_lint', require: false
  gem 'slim_lint', require: false
end

group :development do
  gem 'better_errors'
  gem 'binding_of_caller'
  gem 'bullet'
  gem 'meta_request'
  gem 'spring'
  gem 'spring-commands-rspec'
  gem 'web-console'
end

group :test do
  gem 'capybara'
  gem 'capybara-screenshot'
  gem 'coveralls', require: false
  gem 'database_cleaner'
  gem 'email_spec'
  gem 'mongoid-rspec'
  gem 'poltergeist'
  gem 'rspec'
  gem 'simplecov', require: false
  gem 'webmock', require: false
end

group :staging, :production do
  gem 'rack-timeout'
  gem 'rails_12factor'
end
