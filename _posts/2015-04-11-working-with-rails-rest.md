---
layout: post
title: "Working with Rails and Travis CI"
description: ""
category: 
tags: []
---
{% include JB/setup %}

###Create the GitHub repository.

I'm still working on it.

###Create the Rails application.

I'm still working on it.

###Deploy the application to Heroku.

I'm still working on it.

We need to install the Heroku toolbelt first in order to be able to interact with Heroku from our system. Once installed, just a few steps to create the application in Heroku:

	heroku login
	#prompts for username/password
	heroku create

Now we can publish our Heroku application with `git push heroku master` and what we will see is the deployment almost instantly.

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

This will launch an interactive scripts to setup the ` .travis.yml` file.

Now all we need to do is push the repository to GitHub and voila! the deployment process starts. We can check the results of the build in Travis CI and Heroku activity log
