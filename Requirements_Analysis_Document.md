Requirements Analysis Document (RAD)
==================
This is a Requirements Analysis Document by studentgroup: Emmely, Kristian, Daniel.
The analysis is for a clone of Hacker News. Assignments description: [Here][1].
This document come with an appendix, which is included in this repository. It can be found here: [Appendix](Requirements_Analysis_Appendix.md)
> **Content:**
> -  1: [Introduction](#1-introduction)
>> - A. [Purpose of the system](#a-purpose-of-the-system)
>> - B. [Scope of the system](#b-scope-of-the-system)
>> - C. [Objectives and success criteria of the project](#c-objectives-and-success-criteria-of-the-project)
>> - D. [Definitions, acronyms, and abbreviations](#d-definitions-acronyms-and-abbreviations)
>> - E. [References](#e-references)
>> - F. [Overview](#f-overview)
> - 2: [Current system](#2-current-system)
> - 3: [Proposed system](#3-proposed-system)
>> - A. [Overview](#a-overview)
>> - B. [Functional requirements](#b-functional-requirements)
>> - C. [Nonfunctional requirements](#c-nonfunctional-requirements)
>> - D. [Systemmodels](#d-systemmodels)
> - 4: [Glossary](#4-glossary)

----------


1: Introduction
-------------------

### A. Purpose of the system
____________
The system Hacker News is a online web forum news site, which share many simularities with the popular site Reddit. it allows users of the website to register themself as a account and share stories and comment on other users stories, aswell as give or take karma from stories and comments that increase or decreases their priority on the site, this allows the users to show what content that contribute to the discussion they have interest in, in the case of Hacker News it's any discussion on hacking, programming or news regarding these activities in general, while taking away focus from disruptive or unwanted discussion.

### B. Scope of the system
____________
The system needs to allow multiple users to interact with the server through a web browser, and make their account which enables them to post stories and comment, and also enable them to give or take karma and report stories.

### C. Objectives and success criteria of the project
____________
The project must be able to handle multiple a users posting stories and comments and the same time, while also having a minimum 95% uptime even while the database is down for upgrading. The project needs to allows users to make a Program that can simulate user interaction that create stories and comments on stories using a REST api, likewise the users should also be able to do these actions using a web browser aswell.

### D. Definitions, acronyms, and abbreviations
____________
The term stories is used when we talk about the concept of posting news stories to the system. When we go into more technical detials of the functionallity of the system we use the term threads, but stories and threads is essentially the same thing.

### E. References
____________
- Hacker News: https://news.ycombinator.com/newest.
- Reddit: https://www.reddit.com/

### F. Overview
____________
The product will be a student project focused on making a copy of Hacker News from the ground up, while keeping it maintained over the duration of this semester, around halfway through we will hand over testing to another group, who will send feedback on errors that we will have to execute while they are testing, in this period we'll test another groups project at the same time, and send them feedback on errors we encounter. This is to showcase our proficiency in building and maintaining a web based system aswell as testing a forign system and giving feedback that's useful to the owners of the system.



----------


2: Current system
-------------------
There is no system currently but we wish to create a web based system that handles similar to the Hacker News web site.


----------


3: Proposed system
-------------------
### A. Overview
____________
The proposed system would be a both a REST api server, that handles the multiple users, and a Database that contains all the content of system.
### B. Functional requirements
____________
Account
- The users must be able to create new account - UC1.
- The users must be able to login - UC 2.
- The users must be able to change password.
- The users must be able to edit their user information - UC3.
- The users must be able to see their user information.

Posts
- The users must be able to create a post thread - UC4.
- The users must be able flag posts.
- The user must be able to search for posts
- The user must be able to filter for posts on news, show, jobs and ask.
- The users must be able to see his own submissions.

Comments
- The users must be able to comment on posts - UC5.
- The users must be able to reply to comments - UC6
- The users must be able to see all comments.
- The users must be able to see his own comments.

Points
- The users must be able upvote posts
- The users must be able downvote posts
- The users must be able to see his her points.
- The users should automatically be upgraded to vote when received 50 points or more.

### C. Nonfunctional requirements
____________
#### a. Usability
- We will not put to much effort into usabillity of the scope of the system since the main purpose is that the system should be used via the API / Simulation program. Therefore the use of the webapplication will be required to be exactly the same as hacker news.
#### b. Reliability
- The webbapplication needs to have 95% uptime.
- The system cannot loose any information which has been sent from the simulation program.
#### c. Performance
- The user needs to be notified earliest 10 seconds after action which will give response. This is to ensure good quality throughtout the application.
- The system needs to be able to handle more throughtput than the simulation programs specifications.
#### d. Supportability
- The system needs to work on popular browsers such as: Google chrome, Mozilla firefox, Safari, Internet explorer 9.
- The system needs to have a mechanism so that when users post content and the system is down, the content will be published to the system when it's operational again.
- #Installability(CI?), Scalability(Load balacing?), Maintainability(Able to upgrade system live?)
#### e. Implementation
- The system needs to have a REST API for the simulation program to simulate users.
#### f. Interface
- The system needs to interact with a database for storage of userinformation and content.
- The system needs to interact with a REST API for the simulation program and other users.
#### g. Packing
- No Packing(physical) requirements.
#### h. Legal
- The system needs to remove ilegal content from the system. (By user input: Mark as spam)

### D. Systemmodels
____________
#### a. Scenarios
**__Insert 2 Scenarios. one with Login and one with submit a thread__**

##### Scenario 1
Scenario Name: Account Creation - UC1.

Participating actor instances: **Tester:HN User & HackerNewsClone:System.**

Flow of events:
1. Tester selects login in the menu
2. HackerNewsClone presents a form for creating a new account
3. Tester completes filling in the form and then submits.
4. (B) Tester is prompted that the user name has been taken.

##### Scenario 2
Scenario Name: Login - UC2.

Participating actor instances: **Simulation:HN User & HackerNewsClone:System.**

Flow of events:
1. Simulation selects Login
2. HackerNewsClone presents a form for login
3. Simulation completes the form by inputting username and password and then submits.
4. (A) HackerNewsClone responds by going back to the previous page Simulation was on. New links is added to the menu, links for introduction to HN, threads and edit profile information.

##### Scenario 3
Scenario Name: Submit Thread - UC4.

Participating actor instances: **Simulation:HN User & HackerNewsClone:System.**

Flow of events:
1. Simulation selects submit
2. HackerNewsClone responds with a submit form
3. Simulation fill in the form giving a Title and URL linking to the news article and submits
4. (A) HackerNewsClone responds with a thread succesfully submitted message

#### b. Use case model
**__Insert use case model with all use-cases__**

4: Glossary
-------------------

[1]:https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/01-HN%20Clone%20Task%20Description.ipynb
