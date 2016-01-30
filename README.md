# Heroku Buildpack Ruby Version

This buildpack will read the ruby version from the project's `.ruby-version` file and inject that version into the `Gemfile` as an argument for the `ruby` method. This way the ruby binaries installations are delegated to the **heroku-buildpack-ruby**.

It also revolve ruby versions without the patch version or aliases. For example:

```shell
#.ruby-version
2.2
```

The buildpack will inject a full version into the `Gemfile`.

```shell
# Buildpack output
-----> Getting ruby version from .ruby-version file
-----> Found Ruby version: 2.2
-----> Adding Ruby version to Gemfile: 2.2.4
```

## Usage

Use this buildpack with [heroku-buildpack-ruby](https://github.com/heroku/herok-buildpack-ruby) using buildpack layering with [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi).

Point the buildpack to ddollar's [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi):

    $ heroku buildpacks:set https://github.com/ddollar/heroku-buildpack-multi.git

Add this repository to your `.buildpacks` file:

    https://github.com/platanus/heroku-buildpack-ruby-version.git
    https://github.com/heroku/heroku-buildpack-ruby.git

## Requirements

This buildpack `detect` scripts checks the following:

- The presence of a `.ruby-version`
- The presence of a `Gemfile`
- That you are NOT using the `ruby` method in your `Gemfile`

## Credits

Thank you [contributors](https://github.com/platanus/heroku-buildpack-ruby-version/graphs/contributors)!

<img src="http://platan.us/gravatar_with_text.png" alt="Platanus" width="250"/>

heroku-buildpack-ruby-version is maintained by [platanus](http://platan.us).

## License

Potassium is © 2016 platanus, spa. It is free software and may be redistributed under the terms specified in the LICENSE file.
