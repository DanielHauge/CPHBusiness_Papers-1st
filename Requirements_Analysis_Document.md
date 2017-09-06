Requirements Analysis Document (RAD)
==================
This is a Requirements Analysis Document by studentgroup: Emmely, Kristian, Daniel.
The analysis is for a clone of Hacker News. Assignments description: [Here][1].
This document come with an appendix, which is included in this repository. It can be found here: [Appendix](Requirements_Analysis_Appendix.md). The appendix has all the usecases.
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
Our system is ment to showcase our ability to analyse and replicate a pre existing system, while also maintaining said replica. also implement repairs on the system from feedback that we'll be given over the duration of this semester.

### B. Scope of the system
____________
The system needs to allow multiple users to interact with the server through a web browser and make their account which enables them to post stories and comments, and also enable them to give or take karma and report stories.
The system will also include an API that can be used as an interface to interacting with the system.

### C. Objectives and success criteria of the project
____________
The project must be able to handle multiple users posting stories and comments at the same time, while also having a minimum 95% uptime even while part of the system is down for upgrading. The project needs to allows users to make a program that can simulate user interaction that creates stories and comments using a REST API, likewise the users should also be able to do these actions using a web browser as well.

### D. Definitions, acronyms, and abbreviations
____________
The term stories are used when we talk about the concept of posting news stories to the system. When we go into more technical details of the functionality of the system we use the term threads, but stories and threads are essentially the same thing.

we will use HN User for Hacker news user.

When we mention the system, we mean the broad concept of the whole system, which will include server and database and any other component that will effect the application.

### E. References
____________
- Hacker News: https://news.ycombinator.com/newest.
- Reddit: https://www.reddit.com/

### F. Overview
____________
The product will be a student project focused on making a copy of Hacker News from the ground up, while keeping it maintained over the duration of this semester. Around halfway through we will hand over testing to another group, who will send feedback on errors that we will have to repair while they are testing. In this period we'll test another groups project at the same time, and send them feedback on errors we encounter. This is to showcase our proficiency in building and maintaining a web based system as well as testing a foreign system and giving feedback that's useful to the owners of the system.



----------


2: Current system
-------------------
The system Hacker News is an online web forum news site, which shares many similarities with the popular site Reddit. it allows users of the website to register themselves with an account and share stories and comment on other users stories. additionaly users can give or take karma from stories and comments that increase or decreases their priority on the site. This allows the users to show what content that contributes to the discussion they have interest in. In the case of Hacker News it's any discussion on hacking, programming or news regarding these activities in general, while taking away focus from disruptive or unwanted discussion.


----------


3: Proposed system
-------------------
### A. Overview
____________
The proposed system would be a both a REST API server, that handles the multiple users, and a Database that contains all the content of the system, which the user generated.
### B. Functional requirements

##### API User Functional requirements
- The user must be able to submit thread via an API - UC7.
- The user must be able to Comment on a thread via an API - UC9.
- The user must be able to query the latest ingested comment or thread - UC8.


------------------------------------------
##### Human(Browser) User Functional requirements
Account
- The users must be able to create a new account - UC1.
- The users must be able to log in - UC 2.
- The users must be able to change the password.
- The users must be able to edit their user information - UC3.
- The users must be able to see their user information.

Posts
- The users must be able to create a post thread - UC4.
- The users must be able to flag posts.
- The user must be able to search for posts
- The user must be able to filter for posts on news, show, jobs and ask.
- The users must be able to see his own submissions.

Comments
- The users must be able to comment on posts - UC5.
- The users must be able to reply to comments - UC6
- The users must be able to see all comments.
- The users must be able to see his own comments.

Karma points
- The users must be able to upvote posts
- The users must be able to downvote posts, but only when user has above 500 karma points
- The users must be able to see his her points.
- The users should automatically be upgraded to vote when received 500 points or more.

### C. Nonfunctional requirements
____________
#### a. Usability
- We will not put too much effort into the usability of the system since the main purpose, is that the system should be used via the API / Simulation program. Therefore the use of the web application will not be required to be exactly the same as hacker news.
#### b. Reliability
- The web application needs to have 95% uptime.
- The system cannot lose any information which has been sent from the simulation program or web users.
#### c. Performance
- The user needs to be notified latest 10 seconds after the action which will give a response. This is to ensure good quality throughout the application.
- The system needs to be able to handle multiple users at one time.
#### d. Supportability
- The system needs to work on popular browsers such as Google Chrome, Mozilla Firefox, Safari, Internet Explorer 9.
- The system needs to have a mechanism so that when users post content and the system is down, the content will be published to the system when it's operational again.
#### e. Implementation
- The system needs to have a REST API for the simulation program to simulate user activity.
#### f. Interface
- The system needs to interact with a database for storage of user information and content.
- The system needs to interact with a REST API for the simulation program and other users.
#### g. Packing
- No Packing(physical) requirements.
#### h. Legal
- The system needs to remove illegal content from the system. (By user input: Mark as spam)

### D. Systemmodels
____________
#### a. Scenarios

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

Participating actor instances: **Tester:HN User & HackerNewsClone:System.**

Flow of events:
1. Tester selects Login
2. HackerNewsClone presents a form for login
3. Tester completes the form by inputting username and password and then submits.
4. (A) HackerNewsClone responds by going back to the previous page Tester was on. New links are added to the menu, links for an introduction to HN, threads and edit profile information.

##### Scenario 3
Scenario Name: Submit Thread - UC4.

Participating actor instances: **Tester:HN User & HackerNewsClone:System.**

Flow of events:
1. Tester selects submit
2. HackerNewsClone responds with a submit form
3. Tester fill in the form giving a Title and URL linking to the news article and submits
4. (A) HackerNewsClone responds with a thread successfully submitted message

##### Scenario 4
Scenario Name: API-Query - UC8.

Participating actor instances: **Helge's Program:Simulator program & HackerNewsClone:System.**

Flow of events:
1. Helge's Program requests the HackerNewsClone's API for the latest ingested thread or comment.
2. (C) HackerNewsClone's API responds with status: System is unreachable or offline.

##### Scenario 5
Scenario Name: Story Discussion - UC2, UC5, UC6.

Participating actor instances: **Anders:HN User, Anna:HN User & HackerNewsClone:System.**

Flow of events:
1. Anders logs into Hacker News on his break at work. He sees Anna's story about a subject he is very passionate about. Since he is already logged in he opens up the story to view the discussion.
2. The system presents Anders with details of the story, view of the story discussion and a form to make a comment.
3. Anders fills in a comment and submits it.
4. Later that evening Anna sits in front of the TV she picks up her smart phone and open Hacker News. She can see that more comments have been added to her story. She clicks on the story to view more details.
5. The system presents Anna with details of the story, and view of the discussion and a form to make a comment. Anna sees Anders comment, she chooses to answer by clicking reply on the comment.
6. Because Anna is not yet logged in, the system presents the Anna with a form to log in or create a new account.
7. Anna fills in her user name and password to log in.
8. The system presents the story details, and a form to reply. 
9. Anna fills in an answer and submits.
10. The system presents the Anna with the page of the story of the discussion she replied to.


#### b. Use case model
[Usecases](Requirements_Analysis_Appendix.md)

4: Glossary
-------------------

[1]:https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/01-HN%20Clone%20Task%20Description.ipynb
