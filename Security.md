## 1) Assests

A definition of our assests and a thread model of our system.

#### Asserts:
- Data
```
This is our data on a MySQL server that consists of user information, comments and stories.
```
- Machines
```
This is our physical machines hosted by Digital Ocean
```
- Software
```
This is our software code that runs our service
```
- Reputation
```
This is our good reputation for having 99%<uptime
```

#### Threats:
- Illegal content
- User data gets sniffed / data theft
- To not have atleast 95% availability
- That digital ocean is going down

#### Vulnerabilities:
- Communication is not secure over HTTP protocol
- We do not restrict what content gets posted to our service
- We do not have limitations or enforce strong user passwords
- HTTP Security Header is missing
..* X-Frame-Options - Protects against Clickjacking attacks	
..* X-XSS-Protection - Mitigates Cross-Site Scripting (XSS) attacks	
..* X-Content-Type-Options - Prevents possible phishing or XSS attacks		
- No moderation of posts / no feature to report posts
- DB backup not automated
- Our code is public on GitHub
- We host our service on Digital Ocean.

## 2) Risk Matrix

| Risk No    | Risk                        | Severity | Likelyhood | Impact |
| :--------:| --------------------------- | -------- | ---------- | ----------- |
| 0 | Meteors falling down and killing everyone | Catastrophic | >Rare | Moderate |
| 1 | Data theft because of insecure communication or brute force hacking | Moderate | likely | Low |
| 2 | Someone post illegal content | Moderate | likely | Moderate |
| 3 | Someone finds vulnerabilities in our (publicly available) source code and uses it to hack our system and bring it down | Moderate | possible | Moderate |
| 4 | Digital Ocean goes down and with it our service | Catastrophic | Rare | Moderate |

## OWTF Report
We followed the guide of top 10 security risk defined here https://www.owasp.org/images/7/72/OWASP_Top_10-2017_%28en%29.pdf.pdf  
mostly due to our inexperience with the OWTF we found it hard to specify what test to run specifically, so we did broad sweeps on   several ips and sub domains, and it was only the skipfish method that brought up any kind of "errors" but was marked as only information level issue.  
We did see a performance spike on thier grafana when we did the skipfish sweep as shown below  
![https://i.gyazo.com/a72d917771963da2033e280bf1eb1f2c.png](https://i.gyazo.com/a72d917771963da2033e280bf1eb1f2c.png)  
it should be noted that normally their cpu usage is around 0-5% while our test capped out at 59% usage.  

Since we couldn't get any malicious messages through thier system we couldn't find anything in their logs.  

We did however through the use of skipfish find out that they don't have thier MIME (Multipurpose Internet Mail Extensions) setup which is probably the reason why one of our members antivirus blocks traffic to the hackernews clone site unless they exclude the ip from the protection as having no MIME type results in browsers doing "MIME Sniffing" which makes the browser determine the content of the site, this has malcious use as if the content is a executable the browser will run it automatically.  
![https://i.gyazo.com/5586105d7a3f6603c7978656e1ddf67e.png](https://i.gyazo.com/5586105d7a3f6603c7978656e1ddf67e.png)
