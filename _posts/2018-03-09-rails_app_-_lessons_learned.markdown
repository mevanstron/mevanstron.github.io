---
layout: post
title:      "Rails App - Lessons Learned"
date:       2018-03-09 16:22:43 -0500
permalink:  rails_app_-_lessons_learned
---


My first Rails project is a video game community hub.  Users can create accounts, add video games to their collection, and create a review for each title.  As this project unfolded over the past two weeks, I discovered elements of the design process that both challenged and enhanced my creative output as a web developer.
### Scope
As with other projects, I knew that scope needed to be defined and redefined as the it moved forward.  I knew that I needed mechanisms to allow:
1.	users to create and sign into accounts
2.	video games to be created and assigned to a user’s collection
3.	tags to be added and assigned to individual video games
4.	reviews to be written for a specific game and associated with an author (user).

Midway into working on the project, I realized that it would be neat if consoles could be defined that individual games belonged to.  Users could see a list of games for each console and organize their collection in this manner.  Though this would be a valuable feature, because it was not defined in my initial scope, I tabled it for a future release.  Because of this, I was able to complete my project in the time allotted.
### Red/Green/Refactor
Start with broken code: RED, make the code do what it needs to do: GREEN, then REFACTOR.
As I continued to build the Video Game Community Hub (the flashy name I’ve given this app), I often felt an urge to ‘pretty up’ code right after it had been written.  While it was important that my final code would be scrutinized under a refactoring lens, there is a time and a place for all things.  Out of scope feature development can lead down rabbit holes of project delay, and so can hap hazard refactoring.

While I was creating the new and edit forms for a video game, I remembered that If I could get my code identical between the two, I could use a partial to represent both forms, DRYing up my code considerably.  Instead of moving on to the next view that I was ready to work on, I began looking up the syntax for calling partials and switched gears entirely from writing original code and building in functionality to DRYing up my code and refactoring.  

This caused a loss of focus and a change in my mental gears, which ultimately slowed down the project.  When I realized this, I made a note that I would implement partials in a later refactoring session and moved on.  Though, I wasn’t working in a traditional Test-Driven Development environment, I quickly felt the value of Red/Green/Refactor. 
### Conclusion
Now that I have completed the project, it’s clear to me that there were times when following self-imposed protocols fueled my productivity and success.  It’s also clear, that my productivity lagged when I went off script following my primal coding instinct that chased after code smells as they wafted past.  “A disciplined mind leads to happiness, and an undisciplined mind leads to suffering.” – Dalai Lama XIV

