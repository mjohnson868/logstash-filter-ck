# Logstash CK Filter Plugin

This is a ChainKit filter plugin for [Logstash](https://github.com/elastic/logstash).

This open source software is governed by the MIT license. 

### 1. Installation Instructions

#### Prerequisites
- To get started, you'll need JRuby with the Bundler gem installed.

- Clone this code and logstash code

- Install dependencies
```sh
bundle install
```

#### Test

- Install your dependencies

```sh
bundle install
```

- Run tests

```sh
export CKUSER=user
export CKPASS=changeMe
bundle exec rspec
```

### 2. Running your unpublished Plugin in Logstash

#### 2.1 Run in a local Logstash clone

- Edit Logstash `Gemfile` and add the local plugin path, for example:
```ruby
gem "logstash-filter-ck", :path => "/your-workspace/logstash-filter-ck"
```
- Install plugin
```sh
# Logstash 2.3 and higher
bin/logstash-plugin install --no-verify

# Prior to Logstash 2.3
bin/plugin install --no-verify

```
- Run Logstash with this plugin
```sh
bin/logstash -e \
'filter { ck { username => "user", password => "changeMe" } ckverify { username => "user", password => "changeMe" } }'
```
At this point any modifications to the plugin code will be applied to this local
Logstash setup. After modifying the plugin, simply rerun Logstash.

#### 2.2 Run in an installed Logstash

You can use the same **2.1** method to run your plugin in an installed Logstash by editing its
`Gemfile` and pointing the `:path` to your local plugin development directory or you can build
the gem and install it using:

- Build your plugin gem
```sh
gem build logstash-filter-ck.gemspec
```
- Install the plugin from the Logstash home
```sh
# Logstash 2.3 and higher
bin/logstash-plugin install --no-verify

# Prior to Logstash 2.3
bin/plugin install --no-verify

```
- Start Logstash and proceed to test the plugin

## Contributing

All contributions and fixes are welcome. Contact info@chainkit.com
