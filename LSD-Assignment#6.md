LSD Assigment #6
===============================
This is the LSD-assignment number #6.

Credit: Emmely, Kristian, Daniel.

## 1. Subsystems
![subsystems][subsystems].

## 2. Logical Datamodel.
![logicaldata][data]

## 3. 
- A complete use case diagram.

![Use Cse Diagram][usecasediagram]

Use Cases
==================

#### b. Use case model

###### UC1
Use case name: Create New Account.

Participating actors: HN User - System.

Flow of events.

1. User selects Login in the menu.
2. The system presents a form for creating a new account.
3. The user completes the form by filling in username and password. The user then submits the form.

Pre-conditions: The user is not already logged into an account.

Post-conditions:
- A: The system responds by going back to the previous page the user was on. A link with the user name and number of karma points shows up in the menu. Links with the title welcome and threads also shows up in the menu.
- B: User is prompted that the user name has been taken.
- C: Invalid username or password

----------------------------
###### UC2
Use case name: Login.

Participating actors: HN User -> System.

Flow of events:
1. User selects Login
2. The system presents a form for login.
3. The user completes the form by filling in username and password. The user then submits the form.

Precondition: The user has an account, and is not already logged in to an account.

Exit condition:
- A: The system responds by going back to the previous page the user was on. New links are added to the menu, links for an introduction to HN, threads and edit profile information.
- B: User is prompted that the user name or password was incorrect.

--------------------------------
###### UC3
Use case name: Update User Information.

Participating actors: HN User -> System.

Flow of events:
1. Users select the link to user information.
2. The system responds by presenting a form to the HN User, with the editable fields for the accounts information.  and noneditable information about the HN User.
3. The HN User make changes and submits the form.

Pre-conditions: The users are logged in.

Post-conditions: 
- A: The system responds by presenting the form with the updated information.
- B: The system present to the user that something went wrong.

--------------------------------
###### UC4
Use case name: Submit a thread.

Participating actors: HN User -> System.

Flow of events:
1. The user selects the link to submit in the main menu.
2. The system responds with a submit form.
3. The user fills in the form giving a Title and URL linking to the news article. Leave URL blank to submit a question for discussion. If there is no URL, the text (if any) will appear at the top of the thread. Titles beginning with "Show HN" will appear under show.

Pre-condition: The users are logged in.

Post-condition:
- A: The system responds with a thread successfully submitted message
- B: The system present to the user that something went wrong.

-------------------------------
###### UC5
Use cast name: Comment on a thread.

Participating actors: HN User -> System.

Flow of events:
1. The user selects to comment on a specific a thread in the display of stories.
2. The system responds with a form and details about the thread, and previous comments. The thread information is made up by the title, the number of points, creator of the thread, days since threaded, number of comments. The comments are presented with the username of comment submitter, days since threaded, the comments and a link to reply.
3. The user fills in the comment in the form and submits it.

Pre-condition: The users are logged in.

Post-condition:
- A: The system responds with showing the page of the comments.
- B: The system present to the user that something went wrong.

-----------------------------------------
###### UC6
Use cast name: View thread.

Participating actors: HN User -> System.

Flow of events:
1. The user selects a specific story to open.
2. The system responds with a form and details from the thread, and all comments. The thread information is made up by the title, the number of points, creator of the thread, days since thread creation, number of comments. The comments are presented with the username of comment submitter, days since threaded, the comments and a link to reply.

Pre-condition: None

Post-condition:
- A: The system responds with showing the page of the comments.
- B: The system present to the user that something went wrong.

-----------------------------------------
###### UC7
Use case name: Create Thread.

Participating actors: Simulator Program -> System.

Flow of events:
1. The user submits a post to the system API. The post consists of a Title, Text or URL.

Pre-condition: none

Post-condition:
- A: The system API responds with a successful response and details about the created post.
- B: The system API responds with error and details about the error.
- C: The system API responds with status: System is unreachable, most likely offline.

--------------------------------
###### UC8
Use case name: Comment on a thread.

Participating actors: Simulator Program -> System.

Flow of events:
1. The user submits a post to the system API. The post consists of a Title, Text or URL.

Pre-condition: none

Post-condition:
- A: The system API responds with a successful response and details about the created post.
- B: The system API responds with error and details about the error.
- C: The system API responds with status: System is unreachable, most likely offline.

--------------------------------
###### UC9
Use case name: Query system status.

Participating actors: Simulator Program -> System.

Flow of events:
1. The user requests the systems API for the current status.

Precondition: None

Post-condition:
- A: The system API responds with status: system is operational
- B: The system API responds with status: System is upgrading
- C: The system API responds with status: System is unreachable, most likely offline.
------------------------------
###### UC10

Use case name:  Query system latest.

Participating actors: Simulator Program -> System.

Flow of events:

1. The user requests the systems API for the latest ingested thread or comment.

Pre-condition: None

Post-condition:

- A: The system API responds with a thread or comment
- B: The system API responds with status: System is upgrading
- C: The system API responds with status: System is unreachable, most likely offline.

Actor Responsibility
==================

###### HN User
This Actor is the web user that can interact with the hackernews server with the use of the website GUI, the HN users responsibility is to correctly navigate the GUI and use it's function in the presented forms and functions.

###### Simulated User
This actor is a outside user created autonomous program user, that post storys and comments to the system and ask for the latest ingest story or comment, using the servers API system.

Sub-system sequence diagram
==================
![UC1][UC1].
![UC2][UC2].
![UC3][UC3].
![UC4][UC4].
![UC5][UC5].
![UC6][UC6].
![UC7][UC7].
![UC8][UC8].
![UC9][UC9].
![UC10][UC10].

- A fully dressed use case description for all use-cases indentified above.
/// write a fully dressed use case description for the most important use-cases
- A brief use case description for all other users.
/// Put use-cases from rad here, and maybe fix errors in it. (requirements have most likely changed)
- A description of all actors, including responsability
/// Write 2 lines about actors and their responsability
- A Sub-system sequence diagram for all identified scenarios in the use-cases
/// Put in pictures of the most important sub-system sequence diagram sub-systems.


[data]: https://github.com/DanielHauge/CPHBusiness_Papers/blob/master/images/LogicalDataModel.png
[subsystems]: https://github.com/DanielHauge/CPHBusiness_Papers/blob/master/images/SubSystems.png
[usecasediagram]: https://github.com/DanielHauge/CPHBusiness_Papers/blob/master/images/usecasediagram.png
