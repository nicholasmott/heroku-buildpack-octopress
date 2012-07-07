Heroku Buildpack Octopress
==============================

A fork of the [official Ruby Buildpack][1] with support for generating an [Octopress][2] static site during the build/deploy stage.

Inspired by the [heroku-buildpack-ruby-octopress][3] from Jason Garber but updated to work with the new Heroku Bundler method of [specifying a Ruby version][4].

Installation
------------
To use this build pack prepare your Octopress install according to the [original instructions][5] from Jason Garber.

When creating the Heroku application substitute this buildpack.

```
heroku create --buildpack https://github.com/nicholasmott/heroku-buildpack-octopress
```
or add this buildpack to your current app
```
heroku config:add BUILDPACK_URL=https://github.com/nicholasmott/heroku-buildpack-octopress
```

Flow
----
The buildpack adds the octopress `generate` task after `rake assets:precompile` task in the Ruby language pack.

The Rack language pack is then invoked by the `config.ru` file which runs the Sinatra Static Server to serve the generated files.

Rails 2/3 detection remains in place but will be ignored.

[1]: https://github.com/heroku/heroku-buildpack-ruby
[2]: http://octopress.org/
[3]: https://github.com/jgarber/heroku-buildpack-ruby-octopress
[4]: https://devcenter.heroku.com/articles/ruby-versions
[5]: http://jasongarber.com/blog/2012/01/10/deploying-octopress-to-heroku-with-a-custom-buildpack/