# dotfiles
Public configuration files used by ruby apps

Rubocop configuration: 
We're using rubocop as linter to keep our ruby code with the same format.
```
rubocop.yml
```
Usage:
In your repo's .rubocop.yml add:

```
inherit_from:
  - https://raw.githubusercontent.com/devforce/dotfiles/master/rubocop.yml
```

And add the following to your Gemfile:
        
        gem 'rubocop-airbnb'
    
Along with any Cop overides. For example:
    
    Metrics/LineLength:
      Max: 150
