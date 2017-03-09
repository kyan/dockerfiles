# Supported tags and respective `Dockerfile` links

-	[`2.4.0`, `2.4`, `latest` (*2.4/Dockerfile*)](https://github.com/docker-library/ruby/blob/1c70fd4133287f2273a0cd890a21c91d8da98094/2.4/Dockerfile)

# What is Ruby?

Ruby is a dynamic, reflective, object-oriented, general-purpose, open-source programming language. According to its authors, Ruby was influenced by Perl, Smalltalk, Eiffel, Ada, and Lisp. It supports multiple programming paradigms, including functional, object-oriented, and imperative. It also has a dynamic type system and automatic memory management.

> [wikipedia.org/wiki/Ruby_(programming_language)](https://en.wikipedia.org/wiki/Ruby_%28programming_language%29)

![logo](https://raw.githubusercontent.com/docker-library/docs/01c12653951b2fe592c1f93a13b4e289ada0e3a1/ruby/logo.png)

# How to use this image

## Run a single Ruby script

For many simple, single file projects, you may find it inconvenient to write a complete `Dockerfile`. In such cases, you can run a Ruby script by using the Ruby Docker image directly:

```console
$ docker run -it --rm --name my-running-script -v "$PWD":/usr/src/myapp -w /usr/src/myapp ruby:2.1 ruby your-daemon-or-script.rb
```

## Encoding

By default, Ruby inherits the locale of the environment in which it is run. For most users running Ruby on their desktop systems, that means it's likely using some variation of `*.UTF-8` (`en_US.UTF-8`, etc). In Docker however, the default locale is `C`, which can have unexpected results. If your application needs to interact with UTF-8, it is recommended that you explicitly adjust the locale of your image/container via `-e LANG=C.UTF-8` or `ENV LANG C.UTF-8`.

# Image Variants

The `ruby` images come in many flavors, each designed for a specific use case.

## `ruby:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of. This tag is based off of [`buildpack-deps`](https://registry.hub.docker.com/_/buildpack-deps/). `buildpack-deps` is designed for the average user of docker who has many images on their system. It, by design, has a large number of extremely common Debian packages. This reduces the number of packages that images that derive from it need to install, thus reducing the overall size of all images on your system.

# Supported Docker versions

This image is officially supported on Docker version 17.03.0-ce.

Support for older versions (down to 1.6) is provided on a best-effort basis.

Please see [the Docker installation documentation](https://docs.docker.com/installation/) for details on how to upgrade your Docker daemon.

# Documentation

Documentation for this image is stored in the [`ruby/` directory](https://github.com/docker-library/docs/tree/master/ruby) of the [`docker-library/docs` GitHub repo](https://github.com/docker-library/docs). Be sure to familiarize yourself with the [repository's `README.md` file](https://github.com/docker-library/docs/blob/master/README.md) before attempting a pull request.




# Docker installation of Ruby on Centos7

https://hub.docker.com/r/kyan/centos7_ruby

Also includes:

- wkhtmltopdf
- Forego
- Node 7
- PhantomJS

## Build a new image for Kyan Docker Hub

Use the next available version number and build the image via:

    $ docker build -t kyan/centos7_ruby:vX .

Ensure you are part of the 'owners' group for the Kyan Docker Hub account

Login to docker hub (use your own docker hub details):

    $ docker login
    $ docker push kyan/centos7_ruby:vX

## Use this image

At the top of the Dockerfile in your project:

    FROM kyan/centos7_ruby:vX
