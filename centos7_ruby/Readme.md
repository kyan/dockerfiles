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
