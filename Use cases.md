Requirements Analysis Document (RAD)
==================

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
Use case name: Reply to a thread comment.

Participating actors: HN User -> System.

Flow of events:
1. The user selects the comment section of a thread.
2. The system responds with a form and details about the thread and previous comments. The thread information is made up by the title, the number of points, creator of the thread, days since threaded, number of comments. The comments are presented in a hierarchy 
3. The user selects reply to a comment.with the username of comment submitter, days since threaded, the comments and a link to reply.
4. The system responds with a form the title of the thread and the parent comment to reply to.
5. The HN user writes the reply by filling in the form and submitting. 

Pre-condition: The users are logged in.

Post-condition:
- A: The system responds with showing the page of the comment.
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
Use case name: Query system.

Participating actors: Simulator Program -> System.

Flow of events:
1. The user requests the systems API for the latest ingested thread or comment.

Precondition: None

Post-condition:
- A: The system API responds with a thread or comment
- B: The system API responds with status: System is upgrading
- C: The system API responds with status: System is unreachable, most likely offline.
------------------------------
###### UC9

Use case name: API Create Comment.

Participating actors: Simulator Program -> System.

Flow of events:

1. The user submits a comment with a designated thread.

Pre-condition: 

1. An existing thread for the comment to be added too.

Post-condition:

- A: The system API responds with a successful response and details about the created post.
- B: The system API responds with error and details about the error.
- C: The system API responds with status: System is unreachable, most likely offline.


4: Glossary
-------------------
