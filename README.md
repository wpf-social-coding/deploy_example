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
bundle exec rake db:setup
```

## Running the application

To run the application locally run the following command inside `/home/vagrant/project`:

```
bundle exec rails s -b 0.0.0.0
```

You can now access the website **on your** computer under <http://localhost:3030/>.

On this page you can manage your todo items. Go ahead and create some items.


## Deploy the application

(For more details see the [official Heroku guide for Rails 4 apps](https://devcenter.heroku.com/articles/getting-started-with-rails4))

Head over to [Heroku](http://heroku.com/) and create an account. After that login to your account inside
the box (if you don't run this inside the VM install the [Heroku Toolbelt](https://toolbelt.heroku.com/)):

```
heroku login
```

Now you need to create an app on Heroku:

```
heroku create
```

Now you can push your repo to Heroku:

```
git push heroku master
```

Last step is to migrate the database:

```
heroku run rake db:migrate
```

Congratulations! You just deployed to Heroku. Visit your app under your generated domain. Find out that domain by running:

```
heroku open
```
