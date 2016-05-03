# Deploy all the things!

This is an example app to have something for deployment.

## Setup

There is `Vagrant`-file provided to provide you with a working environment for the app itself. Start the Vagrant box:

```
vagrant up
```

After the box has booted connect to it via SSH:

```
vagrant ssh
```

The project can be found under `/home/vagrant/project`:

```
cd project
```

The project is a simple Rails application. To install all dependencies run:

```
bundle install
```

Next step is to setup your **local** database:

```
bundle exec rails db:setup
```
