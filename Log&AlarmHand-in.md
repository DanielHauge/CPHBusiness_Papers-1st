#Hand-in for LSD
==============
Logging, Alarms, post mortem report.

### Logging
We have setup logging, see Logging (Elk stack) on our [HackerNews Github Wiki](https://github.com/DanielHauge/HackerNews-Grp8/wiki/ELK-Stack)

### Alarms
We have setup an alarm on the ammount of messages in RabbitMQ channel, if it get to big, that means the database inserters cannot follow the rate at which they come in. Also if no data is available, that means the server is down and needs to get up as fast as possible.

### Chrashing the system
We intentionally chrashed our system, with to many requests to see comments on a thread with alot of comments. This will chrash the Webapi if being done in very quick succesion. 17:20 - 11/13

Our operators discovered the outage X hours later.

### Post-mortem report

#### Summary
GoWebApi chrashed and wasn't up for use.
- Affected users: Website user
- outage time: From 17:20 - 11/13 to XX:XX - XX/XX (XX hours)
#### Detailed description
As per 17:20 - 11/13 the GoWebApi docker container exited with a exitcode of 2. This means, the website can no longer contact the GoWebApi to fetch data, login, create user, submit posts or practicly anything.
- be brutally honest, what happened, what happened, what is the error, what does that error mean.

#### Root cause
The GoWebApi chrashed because of a big amount of requests to see comments on a thread with alot of comments, this means that the goapi needs to query the database for alot of information for every request to be displayed to the user. This information can take a fair bit of time to query for. This means, that it was starting up alot requests for alot of data many times, so many times the database threw an error saying there was to many connections to the database. Because it couldn't finish fetching all the data fast enough. This meant the gowebapi chrashed.

#### The fix
We started up the docker container again.

#### Lessons learned
To never intentionally stop a docker container which needs to run for the system to be functional.
