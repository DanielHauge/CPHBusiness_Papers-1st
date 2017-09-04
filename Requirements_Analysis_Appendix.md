Requirements Analysis Appendix
============================
This is a Requirements Analysis Appendix by studentgroup: Emmely, Kristian, Daniel.

Requirements Analysis Document can be found here: [Link to document](Requirements_Analysis_Document.md)


## Usecases
#### UC1
Use case name: Create New Account.

Participating actors: HN User - System.

Flow of events.

1. User selects Login in the menu.
2. The system presents a form for creating a new account.
3. The user completes the form by filling in username and password. The user then submits the form.

Pre-conditions: The user is not allready logged into an account.

Post-conditions:
- A: The system responds by going back to the previous page the user was on. A link with the user name and number of karma points shows up in the menu. A links with the title welcome and threads also shows up in the menu.
- B: User is prompted that the user name has been taken.

----------------------------
#### UC2
Use case name: Login.

Participating actors: HN User -> System.

Flow of events:
1. User selects Login
2. The system presents a form for login.
3. The user completes the form by filling in username and password. The user then submits the form.
4.The system responds by going back to the previous page the user was on. New links is added to the menu, links for introduction to HN, threads and edit profile information.

Precondition: The user has an account, and is not allready logged in to an account.

Exit condition:
- A: 4.The system responds by going back to the previous page the user was on. New links is added to the menu, links for introduction to HN, threads and edit profile information.
- B: User is prompted that the user name or password was incorrect.

--------------------------------
#### UC3
Use case name: UPDATE USER INFORMATION.

Participating actors: HN User -> System.

Flow of events:
1. Users selects link to user information.
2. The system responds by presenting a form to the HN User, with the editable fields About, Email, Showdead, Npprocast, Maxvisit, minaway, delay.  and non editable information about the HN User.
3. The HN User make changes and submits the form.

Pre-conditions: The users is logged in.

Post-conditions: 
- A: The system responds by presenting the form with the updated information.
- B: The system present to the user that something went wrong.

--------------------------------
#### UC4
Use case name: Submit a thread.

Participating actors: HN User -> System.

Flow of events:
1. The user selects the link submit in the main menu.
2. The system responds with a submit form.
3. The user fill in the form giving a Title and URL linking to the news article. Leave url blank to submit a question for discussion. If there is no url, the text (if any) will appear at the top of the thread. Titles beginning with "Show HN" will appear under show.

Pre-condition: The users is logged in.

Post-condition:
- A: The system responds with a thread successfully submitted message
- B: The system present to the user that something went wrong.

-------------------------------
#### UC5
Use cast name: Comment on a thread.

Participating actors: HN User -> System.

Flow of events:
1. The user selects to comment on a specific a thread in the display of stories.
2. The system responds with a form and details about the thread, and previous comments. The thread information is made up by the title, number of points, creator of the thread, days since threaded, number of comments. The comments are presented with username of comment submitter, days since threaded, the comments and a link to reply.
3. The user fill in the comment in the form and submits it.

Pre-condition: The users is logged in.

Post-condition:
- A: The system responds with sowing the page of the comments.
- B: The system present to the user that something went wrong.

-----------------------------------------
#### UC6
Use case name: Reply to a thread comment.

Participating actors: HN User -> System.

Flow of events:
1. The user selects the comment section of a thread.
2. The system responds with a form and details about the thread and previous comments. The thread information is made up by the title, number of points, creator of the thread, days since threaded, number of comments. The comments are presented in a hierarchy 
3. The user selects reply to a comment.with username of comment submitter, days since threaded, the comments and a link to reply.
4. The system responds with a form the title of the thread and the parent comment to reply to.
5. The HN user writes the reply by filling in the form and submitting. 

Pre-condition: The users is logged in.

Post-condition:
- A: The system responds with a comment successfully submitted message and displaying the page of the comments.
- B: The system present to the user that something went wrong.
