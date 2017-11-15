Hand-in for LSD
==============
Logging, Alarms, post mortem report.

### Logging
We have setup logging, see Logging [Elk stack](139.59.157.29:5601) on our [HackerNews Github Wiki](https://github.com/DanielHauge/HackerNews-Grp8/wiki/ELK-Stack)

### Alarms
In our [Grafana](http://207.154.213.133:3000) we have set up an alarm on the number of messages in RabbitMQ channel, if it gets too big, that means the database inserters cannot follow the rate at which they come in. Also if no data is available, that means the server is down and needs to get up as fast as possible.
we have implemented a LINE alarm that alarms us through a phone app. We also have a general alarm set up for Slack, that post all alarm states to that channel.

*Screen shots of the alarms in Grafana:*
[![https://gyazo.com/88443bb6a289f5419c69e47ab64159bf](https://i.gyazo.com/88443bb6a289f5419c69e47ab64159bf.png)](https://gyazo.com/88443bb6a289f5419c69e47ab64159bf)

*Screen shots of SMS alarms we received from Grafana:*
[![alarm](https://cdn.discordapp.com/attachments/352040342327132163/380309387551440896/image.png)](https://cdn.discordapp.com/attachments/352040342327132163/380309387551440896/image.png)

### Crashing the system
We intentionally crashed our system, with too many requests to see comments on a thread with alot of comments. This will crash the Web API (gowebapi) if being done in very quick succession. 17:20 - 11/13

Our operators discovered the outage X hours later.

### Post-mortem report

#### Summary
GoWebApi crashed and wasn't up for use.
- Affected users: Website user
- outage time: From 17:20 - 11/13 to XX:XX - XX/XX (XX hours)
#### Detailed description
As per 17:20 - 11/13 the GoWebApi docker container exited with an exit code of 2. This means the website can no longer contact the GoWebApi to fetch data, login, create a user, submit posts or practically anything.
- be brutally honest, what happened, what happened, what is the error, what does that error mean.

#### Root cause
The GoWebApi crashed because of a big amount of requests to see comments on a thread with a lot of comments, this means that the goapi needs to query the database for a lot of information for every request to be displayed to the user. This information can take a fair bit of time to query for. This means, that it was starting up a lot requests for a lot of data many times, so many times the database threw an error saying there were too many connections to the database. Because it couldn't finish fetching all the data fast enough. This meant the gowebapi crashed.

#### The fix
We started up the docker container again.

#### Lessons learned
To never intentionally stop a docker container which needs to run for the system to be functional.
