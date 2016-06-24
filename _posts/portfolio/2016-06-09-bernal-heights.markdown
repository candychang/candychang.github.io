---
layout: media
title: Bernal Heights App
modified:
categories: portfolio
excerpt: Web Design and Development
tags: []
image:
  feature: bhnc_room.jpg
  teaser: bhnc_logo_notxt.png
  thumb:
ads: false
date: 2016-06-09T20:52:01+00:00
timeframe: Spring 2016
company: CS169 Software Engineering
---

<a class="btn" href="http://bernal-heights.herokuapp.com/">Check out the project</a>
<a class="btn-secondary" href="https://github.com/candychang/bernal-heights">Github repo</a>
<a class="btn-secondary" href="https://www.pivotaltracker.com/n/projects/1543993">Pivotal Tracker</a>

<img src="{{ site.url }}/images/homepage.png" alt="bhnc app homepage" itemprop="image">

## Overview

I worked on a team of five computer science/EECS students during the Spring 2016
semester to create a web application promoting community engagement and safety 
in Bernal Heights, San Francisco. Our client was the 
[Bernal Heights Neighborhood Center](https://donatenow.networkforgood.org/BHNC?code=Website+button "BHNC Link") (BHNC),
a small non-profit that provides social programs for seniors and youth, 
and fosters neighborhood activism to solve local problems. We made this as part
of CS169, Software Engineering as a Service.

### Involvement
Everyone on the team contributed to both design and implementation, which was 
a really great experience after group projects with mostly distributed roles. As
one of the two team members with some prior Rails experience, I was heavily involved
in implementation and learning how to manage testing and deployment.

* Full-stack, agile, TDD and BDD development on Ruby on Rails, following MVC and RESTful practices
* Design and implementation of the admin-side workflow for  staff accounts, hotspots and events
* Managed Git repo, continuous integration and deployment 
* Low-fi mockups, including the hotspot form experience on mobile devices
* In-person interviews and persona generation

### Tools

_Design_: Pencil and paper, whiteboard, POP, Adobe Illustrator, browser prototyping

_Development_: Ruby on Rails, Haml, Sass, Javascript, Pivotal Tracker, Travis CI, 
CodeClimate, Cucumber, Rspec, Heroku

## Process

### Team Workflow

This project was very much about learning by doing --- not only Rails and its
various gems, but also the agile workflow. We had daily standups in Slack,
wrote, pointed and assigned user stories and features in Pivotal Tracker,
and practiced test-driven development with continuous integration and deployment.

* Week one: Client meeting, create user stories/mockups for the features this 
            iteration, write Cucumber/Rspec tests, meet with instructors for mini-review
* Week two: Work on our stories until all tests pass green, deploy for user testing

I was in charge of managing our repo, as well as continuous integration and deployment. 
We also had a PM who looked after Pivotal Tracker and made sure our standups got done,
and a point person for contacting our client and submitting progress reports to our 
instructors.

### Customer Needs

We worked with Ailed and Esme, BHNC chairs of community engagement and public
safety, for the majority of the project.

One of the most successful programs Ailed and Esme manage at BHNC is the hotspot 
walk. Residents submit hotspot forms about problems in the neighborhood that 
affect public safety, and BHNC staff aggregate the information. Then, they
invite the police and relevant city departments to walk with BHNC staff and neighbors 
around the neighborhood to see the problems in person. This is often a more effective
way of getting problems fixed than relying on individual requests from residents.

<img class="centered-img" src="{{ site.url }}/images/sample_hotspot_redacted.png" alt="sample hotspot form" itemprop="image">
<figcaption>Example of submitted hotspot form, contact information redacted</figcaption>

Up until now, staff had to process over 200 of these forms per walk. One dedicated neighbor 
was inputting all the information by hand into Google Maps in order to get a 
visualization of problem spots.

Ailed also wanted to get residents more involved in resolving their own problems.
Besides hotspot walks, there are also community meetings, park cleanups, and other
events that Ailed wanted to easily share with residents. She had tried using Nextdoor
but found it too time-consuming to manage and too cluttered with other topics
to get her information across.

Based on these conversations with Ailed and Esme, we established three
main functionalities of the requested web app:

* Gather, manage and share hotspot form information
* Provide a centralized calendar for BHNC and resident-created events
* Share useful resources with residents in one accessible location

### Design Process

<img src="{{ site.url }}/images/bh_flow.jpg" alt="admin flow" itemprop="image">

We started out with a broad brainstorming session for how the app
would be put together. Each iteration, if needed, we would sketch out how the
new features would fit into the current plan and run those by Ailed and Esme.
Within our team, we often tried to do group design on the whiteboard,
and shared our sketches over Slack when meeting up wasn't possible.

For most of our big questions, we made low-fi prototypes in POP and travelled in person 
to SF to have Ailed, Esme and Bernal residents do some user testing. I was in charge of 
making a wizard version of the hotspot form to compare against the single-page version.

<a class="btn-secondary" href="https://popapp.in/w/projects/56eb0d6243b167426a24622f/mockups">POP prototype of hotspot form</a>

<img src="{{ site.url }}/images/bh_hotspot_popapp.png" alt="sketches for POP" itemprop="image">
<figcaption>A few screens from the POP prototype</figcaption>

### Design Decisions

From the testing feedback, we made three big changes to our implementation.

**Sign-in**

Initially, we planned to use sign-in and 3rd party authentication to eliminate the need for filling
in name and contact information on every submitted form. This seemed like a time-saving feature
that would encourage more people to submit. After user testing, however, we eliminated sign-in
for residents. Testers said requiring a user name and password made the application feel unwelcoming; 
the sign-in page was more of a barrier to them than filling out their information.

**Hotspot Form Wizard**

We ended up implementing a wizard to walk through the required information for hotspot
forms, since most testers reported feeling more overwhelmed by the single-page prototype,
and visibily enjoyed using the wizard version more.

**Location Search**

Testers assumed that the first step to submitting a hotspot form was specifying a location. 
Many attempted to "drop a pin" on to the map. We initially had location come after specifying 
the type of issue being reported. Seeing testers' reactions, however, we went back to the 
drawing board. Although dropping a pin was a natural reaction for users, we felt that in 
reality being able to do that accurately, especially if on a mobile browser, would be difficult. 
Instead, we added a search bar to the map; searching for a location would drop a pin and pop 
up a link to fill out the rest of the hotspot form.

<img src="{{ site.url }}/images/hotspot_location.png" alt="hotspot location" itemprop="image">
<figcaption>Hotspot with location search</figcaption>

**Admin Workflow**

Since I ended up taking on many of the admin-side user stories, I thought a lot about
Ailed's personality and the contexts in which she'd be using this app. Working
in a small non-profit already meant being strapped for time and resources; in addition,
Ailed was a new mother. When we visited, she was always on the move, even within the 
neighborhood center. She also mentioned that she did a lot of her work on her phone,
since she rarely had time to sit down at her desk.

I decided to create a homepage that would prompt Ailed if anything needed her 
attention --- for example, if any new events had been submitted and needed approval ---
and would provide immediate access to her most common tasks.

<img src="{{ site.url }}/images/admin_homepage.png" alt="admin homepage" itemprop="image">
<figcaption>Final admin homepage</figcaption>

Some other small details worked in by the last iteration: if signed in, the admin doesn't 
need to fill out name, contact info or organization name on any of the forms. The events 
calendar has a reminder about the number of unapproved events. Clicking on a pin in the 
admin hotspot map will show a link to the entire form submission; earlier iterations,
the only way to view that information was going through the list of hotspots below the map.

<img src="{{ site.url }}/images/hotspot_admin_1024.png" alt="bhnc calendar" itemprop="image">
<figcaption>Admin hotspots page</figcaption>

### Final Thoughts

<img src="{{ site.url }}/images/bh_visit.jpg" alt="me at bhnc" itemprop="image">
<figcaption>At in-person meeting with Ailed and Esme</figcaption>

It was extremely rewarding working with a non-profit for the semester,
especially because I know firsthand how difficult it is to get projects like
these off the ground without outside help. 

Outside of software development, we learned a lot about how to communicate 
effectively. While Ailed had a general idea of what she wanted, she didn't have 
a clear picture of the possibilities or limitations of a web application. 
We found that having visual representations ready while discussing features
was the best way to elicit useful feedback, absent opportunities to speak face to face. 
We did manage to make two trips to BHNC in person, and those meetings were the most
fruitful. Not only did we clarify many questions, but we also got a feel for the
characteristics of Bernal Heights, BHNC, and some of its residents.

Agile development was a first for most of us, and the test-driven process
was especially taxing at first. In addition, we had to keep on revising our back-end
relationship models as user stories and features were added or discarded.
At the same time, our workflow had everyone involved in discussing both UX
and implementation, and I enjoyed that immensely. I also liked learning how to
test with Cucumber, which made it easier to focus discussion about app
features on user needs instead of specific technologies or implementation.

Going forward, one of my teammates and I have committed 
to staying in touch with Ailed and maintaining the app post-graduation.

Some of our plans:

- make UX better for certain groups of neighbors - those who would like to print
  records out or want confirmation of their submissions
- add the attach photo functionality to hotspot forms
- cluster hotspots that are about the same location
- unify visual design, and also match look and feel of app better to the characteristics of BHNC

Although we won't all be continuing to work on this app, I couldn't have asked 
for a better group of people to work with during the semester.
I'll miss getting their Slack notifications :)

<img src="{{ site.url }}/images/bh_group_pic.jpg" alt="team picture" itemprop="image">
<figcaption>Our amazing team!</figcaption>




