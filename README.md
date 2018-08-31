# dotfiles
Public configuration files used by ruby apps

### Rubocop configuration: 
We're using rubocop as linter to keep our ruby code with the same format.

### Usage:
##### In your repo's .codeclimate.yml add:
```
prepare:
  fetch:
    - url: 'https://raw.githubusercontent.com/airbnb/ruby/master/rubocop-airbnb/config/rubocop-style.yml'
      path: '.rubocop_airbnb.yml'
    - url: 'https://raw.githubusercontent.com/devforce/dotfiles/master/trailhead_rubocop.yml'
      path: '.rubocop_trailhead.yml'
```
This provides a way for Codeclimate to fetch the files and silently replace those 2 files.

##### In your repo's `.rubocop.yml` add:
```
inherit_from:
  - .rubocop_airbnb.yml
  - .rubocop_trailhead.yml
```
We inherit from a local file instead of directly from the remote so Codeclimate can read the file.

##### Add any Cop overides into your `.rubocop.yml`.
   
    Metrics/LineLength:
      Max: 150

##### In your repo add `.rubocop_airbnb.yml` with this content:
```
inherit_from:
  - https://raw.githubusercontent.com/airbnb/ruby/master/rubocop-airbnb/config/rubocop-style.yml
```

##### In your repo add `.rubocop_trailhead.yml` with this content:
```
inherit_from:
  - https://raw.githubusercontent.com/devforce/dotfiles/master/trailhead_rubocop.yml
```
