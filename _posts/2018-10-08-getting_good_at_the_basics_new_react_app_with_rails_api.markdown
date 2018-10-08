---
layout: post
title:      "Getting Good at the Basics: New React App with Rails API"
date:       2018-10-08 19:49:46 +0000
permalink:  getting_good_at_the_basics_new_react_app_with_rails_api
---


As a web developer, establishing repeatable routines can save a great deal of thought and energy on a project. In fact, identifying work that can be automated and abstracted is central to coding anyway.  So, we should embrace opportunities to set up simple and repeatable tasks for ourselves.  This blog post is a guide to quickly and reliably create a react app with access to a database through a Rails API.

## Given:

This guide assumes your coding environment is running
* Rails 5.1.6
* npm 6.4.1

You can check your versions respectively by typing the following into your terminal:
```
$ rails -v
$ npm -v
```
## Objective:

To connect a React Front End Application to a Rails API, you need a Rails framework that houses a React application therein.  Once built, you’ll code in a time saver that allows you to launch both the Rails and React servers with a single command, by way of the Foreman ruby gem.

## Process:

Open your favorite text editor and a coding terminal.  Change directories to the location you want to house your project.

`$ cd code/projects`

Then we'll create a Rails app intended for API use.

`$ rails new my-rails-app --api`

Once the directory is created, navigate inside to create our React app.
```
$ cd my-rails-app
$ npx create-react-app client
``` 
(npx is included with npm 5.2.0 and higher.)

After the React app creation (which may take a bit), you’ll have hit a milestone.  you have two applications, Rails and React, who are ready to launch on individual servers.  Hurray!

The final step is to build a launching bridge that can tell both apps to launch with a single command. 
In your Gemfile, we are going to add

`gem 'foreman', '~> 0.82.0'`

As of the penning of this blog post, Foreman will default to version 0.64.0 if none is specified.  This does not support some of the syntax used up ahead.  Therefore, specifying a version of at least 0.82.0 is required for these instructions to hold true.

Then in terminal run:

`$ bundle update`

navigate to your lib/tasks folder and create a file called start.rake.

`$ cd lib/tasks`

In start.rake, add the following code:
```
task :start do
  exec 'foreman start -p 3000'
end
```
This allows you to launch your React and Rails servers with the single command:

`$ rake start`

HOWEVER, there is one final piece missing.  We need to create a Procfile in our project's root directory.  In Procfile, add:
```
web: cd client && npm start
api: bundle exec rails s -p 3001
```
Now when you run rake start, you should see both your Rails and React servers launch simultaneously on ports 3000 and 3001.

## Conclusion:

This process is stable and repeatable for each new project using Rails and React.  The purpose is to save a developer’s energy and time for the work that is specific to the project.  For instance, this guide does cover any of the specifics about structures that may exist in their React app, or what objects may be called upon from the database via Rails API.  Simply, with these steps a developer can create their project framework and get to the real work with fresh wits and optimized time.

