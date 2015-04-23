---
layout: post
title: "Working with Rails and Travis CI"
description: ""
category: 
tags: []
---
{% include JB/setup %}

###Create the GitHub repository.

If you already have a GitHub repository

###Create the Rails application.

I won't explain details about how to get started with Rails. There's plenty of documentation on the web (personally I recommend gorails approach). Having said that, let's create a simple rails application:

	$ rails new testapp

That instruction is enough to create a blank application inside `testapp` directory. Now you can navigate into it and test your brand new app:
	
	$ cd testapp
	$ rails server
	=> Booting WEBrick
	=> Rails 4.2.0 application starting in development on http://localhost:3000
	=> Run `rails server -h` for more startup options
	=> Ctrl-C to shutdown server
	[2015-04-23 10:17:21] INFO  WEBrick 1.3.1
	[2015-04-23 10:17:21] INFO  ruby 2.0.0 (2014-11-13) [i686-linux]
	[2015-04-23 10:17:21] INFO  WEBrick::HTTPServer#start: pid=2562 port=3000

That created a web server instance in `testapp` directory. Navigating to `http://localhost:3000` will display a simple welcome message from Rails.

Now let's add some structure. To do that, the Rails framework offers scaffolding. Let's see how it works:

	$ rails generate scaffolding Ticket name:string description:string active:boolean

After all scaffolding process finishes, we run a migration to create the tables needed to store the ticket information.

	$rake db:migrate


###Deploy the application to Heroku.

We need to install the Heroku toolbelt first in order to be able to interact with Heroku from our system. Once installed, just a few steps to create the application in Heroku:

	heroku login
	#prompts for username/password
	heroku create

Now we can publish our Heroku application with `git push heroku master` and what we will see is the deployment almost instantly. Please follow this well explained post from Heroku on how to push Rails apps.



But what had just happened? heroku received an update on the repository so it deploys the application automatically. This could be good if we want to just push changes directly to Heroku, but our GitHub repository now is outdated. Do we need to do the `git push` to both GitHub and Heroku every time we make a significant change in our application? Hell no! That's not a good sign at all! That could cause some trouble in the future as our repository grows in participants. That is why an automated deployment workflow is a good and healthy choice to go, and Travis CI is a great tool to achieve this.

###Travis CI

Travis CI is a Continuous Integration system, that means it automates the tasks needed to deploy an application and run tests. In other words, it puts it seal of aproval, so now every push made to our repository has to _compile_. We can sign up directly with GitHub and sync a repository.
To get started we need to define a `.travis.yml` file. This will tell Travis what kind of application is and what to do with it.


First of all, we need to tell Heroku that we have a public repository wich contains the application code to be deployed. To do this, we select the application from the dashboard, and select the Deploy option on the menu bar. Now we have to authorize Heroku to inspect our repository through GitHub.


###Integrate with Travis CI

But how do we integrate this deployment workflow into a Heroku application (or how to enable automatic deploys on Heroku). Actually it's pretty simple with the travis command line tool. Just install the gem with:

	gem install travis

And use it to engage your GitHub app with Heroku:

	travis setup heroku

This will launch an interactive scripts to setup the `.travis.yml` file.

Now all we need to do is push the repository to GitHub and voila! the deployment process starts. We can check the results of the build in Travis CI and Heroku activity log
