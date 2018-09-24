---
layout: post
title:      "Moving Front to Back: React and Rails"
date:       2018-09-24 19:18:31 +0000
permalink:  moving_front_to_back_react_and_rails
---


Recently I completed a project combining a React driven front end and a Rails powered back end. The app is a community driven message board that can flesh out various discussions inside the broad topic of classical music.  The process was illuminating, and I’d like to break down the three distinct phases: building React, constructing Rails API, and merging the two together.
## React App
Running a simple command “npx create-react-app my-app” in BASH terminal yields a very satisfactory initial setup for a react application with a lot of dependencies and minimum constructs in place.  

* src directory with initial builds for index.js and app.js  
* Basic CSS elements
* Component and Container directories ready to be populated.

Entering a simple command to begin building my custom components for the classical forum message board felt very nice. In my app, I decided to go heavy on <Link /> components to route into my various tiers of containers and components.  While this made navigating between sections of the app simple, it added a challenge regarding passing data down to the component levels. I had to rely entirely on params to ferry data into components.  Since I wasn’t calling components directly, I couldn’t pass props down to them like I have in the past.

I created a dummy database in a file called data.js.  Knowing that I would eventually call to a stronger database using a Rails API, I knew this would eventually be deprecated, but stubbing data in this area helped simulate how my components would talk to a dataset without having those destinations in place.  However, I knew because calls to my data file didn’t involve asynchronous actions, I wouldn’t be able to truly test pieces of my Redux setup until connecting to my data with an API.  So, I shifted from front end to back end and created my rails framework.
## Rails API
The next step in my project required connecting my React App to a functioning database.  Time for Rails!  Most of the setup felt very familiar.

*Generate a new rails app using “rails new classical-music-forum --api”
*Generate table rows for each object in the database
*Translate data from data.js into a seed file data.rb.
*Move React App into a folder called “client” in rails framework.

With this setup, API calls from React still wouldn’t talk to the Rails database because my front end and back end were hosted on different server ports (localhost:3000, and localhost:3001).  I needed to establish a proxy in client/package.json.  

* “proxy”: http://localhost:3001/

That allowed my React App to make calls to my Rails Server.  Even though there was new ground to cover, creating and connecting a Rails API framework to my functioning React App was a breeze.
## Fetching Data
Now that the database had been initialized and API endpoints created, the final element was building the various fetch actions.  Thanks to Redux-Thunk, I could build actions that return functions. These functions fetched data from my Rails API and in a promise chain, dispatched an action using the fetched JSON data.  In my initial scope for the app, I decided to only work with GET and POST methods in fetch.  The first grabbed all forum data from the database, and the latter pushed a new object into the database using a create method in the associated controller.  
## Conclusion
The process of connecting the React and Rails independent frameworks did feel a little like assembling Frankenstein’s monster.  However, the result was worthwhile.  I had full utility and flexibility to design solutions from top to bottom.  With a little extra effort in configuration, I felt at home both with the elegant and powerful tools native to React, along with the strong customization enabled by Rails routing and controller setup.




