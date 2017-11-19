## 1)
Docker swarm is a way to make machines talk together to work as a single unit. We want it because with docker swarm it is easy to scale up, we can add a new machine to the swarm and increase strengh. We can easily scale up to run multiple containers to increase capacity. By scaling horizontally in any area that needs it will help eliminate bottlenecks. 
Docker swarm provides great scaling possibilities to eliminate Congestion, it provides possibility for redundancy to eliminate single point of failure, and also be possible to setup content delivery network by making the DNS route our traffic to the different nodes(machines) to eliminate single point of entry. All in all, it provides an answer to problems with bottlenecks.

## 2)

```
root@HQ:~# docker node ls
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS
5wtwvhnmrbyotczntmkyxmiy7 *   HQ                  Ready               Active              Leader
9o4xu9nu4gelyu1u84kgkf68j     HackerNewsSite      Ready               Active              Reachable
znbkp4eyzgjfopyetrp0kl7qo     RabbitMQ            Ready               Active
wd0kccpvmphbcwsgonevbug65     slave1              Ready               Active
vilw315d7jpiaspyhvd1st018     slave2              Ready               Active
```

```
root@HQ:~# docker service ls
ID                  NAME                MODE                REPLICAS            IMAGE                           PORTS
bfcj156gl3s5        Database-Insert     replicated          1/1                 danielhauge/goinserter:latest
id6c1g2p8bo0        core                replicated          3/3                 danielhauge/goapi:latest        *:8787->8787/tcp
sm385kmg65ex        docker-exporter     global              5/5                 basi/socat:v0.1.0               *:30002->4999/tcp
y4btd9dtwc2i        grafana             replicated          1/1                 grafana/grafana:4.5.2           *:3000->3000/tcp
3d4dix4y4vhx        prometheus          replicated          1/1                 prom/prometheus:latest          *:9090->9090/tcp
3ybergq71wdr        webapi              replicated          5/5                 danielhauge/gowebapi:latest     *:9191->9191/tcp
4i0d8hn5hhqh        website             replicated          5/5                 danielhauge/hnwebsite:latest    *:8080->80/tcp
```
New Grafana Dashboard with service discovery implemented: [Here](http://165.227.151.217:3000/dashboard/db/go-core?refresh=5s&orgId=1)
admin - admin
