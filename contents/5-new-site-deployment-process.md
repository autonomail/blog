{{{ "title": "New site deployment process", "tags": ["server"], "category": "server", "date": "05-27-2014" }}}

We have shifted over to using [Digital Ocean](https://www.digitalocean.com/?refcode=98d0e3d7eb67) for hosting [autonomail.com](https://autonomail.com). This website is not involved in the actual email part of our service. Nor will it have user login facilities. It is simply a place for introducing us and keeping you up-to-date with what we're upto.

We're running the site within a [Docker](docker.io) container, built on the [phusion](https://github.com/phusion/baseimage-docker) base image. Docker is now the preferred mechanism of deploying sites for us (and many other folks). The phusion base image is the perfect foundation upon which to build a Docker container as it makes it easy to run daemons and also provides a number of useful utilities such as [runsv](http://smarden.org/runit/runsv.8.html) and [syslog-ng](http://www.balabit.com/network-security/syslog-ng) both of which we use.

Logging gets sent to [Loggly](https://www.loggly.com/). This will allow us to perform post-mortem analysis of problems even if we are unable to connect to our server.

The server itself is setup using an [Ansible](http://ansible.com/) playbook, making it easy for us to setup new servers and deploy the site to them. We re-deploy the site whenever a successful build completes within [Shippable](https://www.shippable.com/), our build platform. Right now, we're looking to automate this deployment process so that we can have true "continuous deployment".

We aim to write a more detailed blog soon about our setup so that you too can setup something similar for your sites.
