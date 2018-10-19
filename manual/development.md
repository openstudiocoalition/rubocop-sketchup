# Building

## Development Requirements

Building this gem requires [bundler](http://bundler.io/).

```bash
gem install bundler
```

## Initialize Developer Environment

From the folder where you [cloned](https://help.github.com/articles/cloning-a-repository/) the repository:

```bash
bundle install
```

This will install all the developer dependencies to build the gem.

## Build

```bash
bundle exec rake install
```

After running this command `rubocop-sketchup` should be available on your system.

## Test

Running all tests:

```bash
bundle exec rake
```

Running single spec:

```bash
bundle exec rake spec SPEC=spec/rubocop/sketchup/requirements/global_methods_spec.rb
```


# Add a new cop

Use a rake task to generate a cop template.

```sh
$ bundle exec rake new_cop[Department/Name]
Files created:
  - lib/rubocop-sketchup/sketchup/cop/department/name.rb
  - spec/rubocop-sketchup/sketchup/cop/department/name_spec.rb
File modified:
  - A configuration for the cop is added into config/default.yml
    - If you want to disable the cop by default, set `Enabled` option to false.

Do 1 steps:
  1. Modify the description of Department/Name in config/default.yml
  2. Implement your new cop in the generated file!
```


## Implementing the cop

See [RuboCop's own documentation](https://github.com/rubocop-hq/rubocop/blob/master/manual/development.md) for details.


# Release

To release a new version (Done by SketchUp Team), update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

http://guides.rubygems.org/publishing/

You need the API key for an account that have ownership of the gem to push a new version. Make sure the API key is set up in `~/.gem/credentials` before running `bundle exec rake release`.

#### HTTPS GitHub Credentials under Windows

> As of 22 Feb 2018, GitHub has disabled support for weak encryption which means many users will suddenly find themselves unable to authenticate using a Git for Windows which (impacts versions older than v2.16.0). DO NOT PANIC, there's a fix. Update Git for Windows to the latest (or at least v2.16.0).

https://github.com/Microsoft/Git-Credential-Manager-for-Windows