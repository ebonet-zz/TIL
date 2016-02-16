### Expanding custom config files in Rails
_02/15/2016_


I had to access an API from my rails API, where I can run it on localhost and
a staging scenario for testing. I needed a place to properly store the credentials,
and a `YAML` is an elegant solution. Digging around, I found a solution that works
really well:

* `configs/custom_config.yml` :

``` YML

development:
  API_PATH: devPath
  API_KEY: abcdefdg

staging:
  API_PATH: hmgPath
  API_KEY: abcdefdg

production:
  API_PATH: prodPath
  API_KEY: abcdefdg

```

* `configs/initializers/custom_config.rb` :

``` ruby
CUSTOM_CONFIG = YAML.load_file(Rails.root.join('./config/custom_config.yml'))[Rails.env]
```

* And in the code :

``` ruby
@basePath = CUSTOM_CONFIG["API_PATH"]
```
