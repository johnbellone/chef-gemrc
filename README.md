# blp-gemrc cookbook

[![Build Status](https://img.shields.io/travis/johnbellone/blp-gemrc-cookbook.svg)](https://travis-ci.org/johnbellone/blp-gemrc-cookbook)
[![Code Quality](https://img.shields.io/codeclimate/github/johnbellone/blp-gemrc-cookbook.svg)](https://codeclimate.com/github/johnbellone/blp-gemrc-cookbook)
[![Test Coverage](https://codeclimate.com/github/johnbellone/blp-gemrc-cookbook/badges/coverage.svg)](https://codeclimate.com/github/johnbellone/blp-gemrc-cookbook/coverage)
[![Cookbook Version](https://img.shields.io/cookbook/v/blp-gemrc.svg)](https://supermarket.chef.io/cookbooks/blp-gemrc)
[![License](https://img.shields.io/github/license/johnbellone/blp-gemrc-cookbook.svg?maxAge=2592000)](http://www.apache.org/licenses/LICENSE-2.0)

Library cookbook which manages a [RubyGems configuration file][0].

## Basic Usage
The default recipe configures the [gem environment][1] to disable the
installation of documentation when gems are installed. A common use
case for this cookbook is to configure the Chef Client's gem
environment to an internal mirror if behind the veil of the corporate
firewall.

Here is an example of how to use an internal [Artifactory instance][2]
to [mirror the RubyGems.org repository][3].

``` ruby
node.default['gemrc']['path'] = Gem::ConfigFile::SYSTEM_WIDE_CONFIG_FILE
node.default['gemrc']['reload'] = true
node.default['gemrc']['config']['sources'] = ['http://artifactory.corporate.com/artifactory/api/gems/ruby-gems/']
include_recipe 'blp-gemrc::default'
```

[0]: http://docs.ruby-lang.org/en/2.1.0/Gem/ConfigFile.html
[1]: http://guides.rubygems.org/command-reference/#gem_environment
[2]: https://www.jfrog.com/artifactory/
[3]: https://www.jfrog.com/confluence/display/RTF/RubyGems+Repositories
