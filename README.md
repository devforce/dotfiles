# dotfiles
Public configuration files used by ruby apps

### Rubocop configuration:
We're using rubocop as linter to keep our ruby code with the same format.

### Usage:
##### In your repo's Gemfile add this to the development section:
```
  gem 'rubocop-rails_config', '~> 0.2'
  gem 'rubocop-rspec'
```

##### In your repo's .gitignore add:
```
# Rubocop temporary files
.rubocop-https---*
```

##### In your repo's .codeclimate.yml add:
```
prepare:
  fetch:
    - url: 'https://raw.githubusercontent.com/airbnb/ruby/master/rubocop-airbnb/config/rubocop-style.yml'
      path: '.rubocop_airbnb.yml'
    - url: 'https://raw.githubusercontent.com/devforce/dotfiles/master/rubocop/rubocop_trailhead.yml'
      path: '.rubocop_trailhead.yml'
```
Code Climate configuration looks like this because rubocop is not allowed to follow links, so we download the file beforehand using the above.

##### In your repo's `.rubocop.yml` add:
```
inherit_from:
  - .rubocop_airbnb.yml
  - .rubocop_trailhead.yml
```
We inherit from a local file instead of directly from the remote so Codeclimate can read the file.

##### Add any Cop overides into your `.rubocop.yml`.
    Metrics/LineLength:
      Max: 42

##### In your repo add `.rubocop_airbnb.yml` with this content:
```
inherit_from:
  - https://raw.githubusercontent.com/airbnb/ruby/master/rubocop-airbnb/config/rubocop-style.yml
```

##### In your repo add `.rubocop_trailhead.yml` with this content:
```
inherit_from:
  - https://raw.githubusercontent.com/devforce/dotfiles/master/rubocop/rubocop_trailhead.yml
```
##### In your repo you can run rubocop on just your changed files:
```bash
git status --porcelain | grep M | xargs bundle exec rubocop
```
Or for just rb files:
```bash
git status --porcelain | grep M | grep '\.rb' | xargs bundle exec rubocop
```
