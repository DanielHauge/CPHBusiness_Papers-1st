Group 8: Continues Deliery Setup Chain and How to Replicate it
==============================================================
## The Architecture of Continues Deliver and Integration 

Our setup consist of the following components

- GitHub repository. Repository of the Web Application and where new changes to the application is being pushed.
- DockerHub repository. Repository where the docker image is being hosted. 
- Remote Machine on DigitalOcean with Jenkins Server. This server runs the build and delivery jobs.
- Remote machine on DigitalOcean with the Static Web Server. Where the Web Application is being deployed and hosted.
- Remote machine on DigitalOcean with Database Server. This database server is used by the Web Application.   

#### Overview of the Build and Delivery Jobs
The Jenkins server is set up to check for changes in the GitHub repository with a interval (checks every 5 min in our setup).
If the Jenkins Server detects any changes in the GitHub repository it runs the build and deploy jobs.
The following is a description of the the processes in each job:
##### The Build Job
The Jenkins Server builds a docker image from the Web Application hosted on the GitHub repository. 
It then pushes the docker image up to the DockerHub repository.
##### The Deploy Job Process
When the build job is finished the deploys job starts.
The deploy job starts by preparing the server
- [TODO]
- [TODO]
- [TODO]
It then deploys the docker image that is hosted on the DockerHub to the Static Web Server. When this process is finished it checks the status of the Web Application as a final step.
Setup Our Remote Machines for Jenkins and The Static Server with Vagrant
[TODo write the command for starting Vagrant]

## Manual How to Setup The Architecture of Continues Deliver and Integration 

### Set Up a Droplet on Digital Ocean
The pre recusite for this is that you have an account at Digital Ocean (https://www.digitalocean.com)

The vagrant script will create two new Ubuntu 16.04.3 x64 droplets (second smallest machine, 0.015USD per hour/ 10USD per month)

Now you have a two remote machine up and running.

## Prepare The Remote Static Web Server

[TODO]

## Prepare The Remote Jenkins Server - Setup Jenkins

- Install Vagrant (https://www.vagrantup.com/docs/installation/) and VirtualBox (https://www.virtualbox.org/wiki/Downloads) to the remote machine
- cd to the directory with the Vagrantfile and startup the VM. When started up for the first time vagrant up will automatically run the provision script (provision.sh). Note in case you want to allow our group members to log onto the Jenkins build server on this machine uncomment the line # config.vm.network "public_network" in the Vagrantfile.
- `cd /vm` #[comment]: <> (TODO)`
- `vagrant up`
- You can ssh into this VM via `vagrant ssh`
- After starting the VM Jenkins should be up and running. You can access it via [our droplet IP]:8080

### Configuring Jenkins

Now that Jenkins is running you have to configure it. On first time use it will present you the following page.
[pic]

Here you have to insert the key that you get either from the output of the provision script or via:

`vagrant ssh`

`sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

Subsequently, choose to Install suggested plugins. we will install the other required plugins later manually.
Afterwards, create a first admin user on Jenkins. For this example we will call it builder too.

#### Adding Credentials to Jenkins

To allow for the later use of DockerHub as registry for the container with the final web application you need to be registered at https://hub.docker.com.
After you have created a user at DockerHub, navigate to Credentials -> (global) -> Add Credentials (which corresponds to navigating to the following URL: [Jenkins server IP]:8080/credentials/store/system/domain/_/ ).
There add a Secret text, where the secret is our password to our DockerHub account.

[pic]

#### Allow Jenkins User to Execute Deployment Script Remotely
To allow for a login from a non-interactive shell to the remote machine we have to create a pair of SSH keys for the jenkins user, i.e., the Linux user executing the shell scripts in Freestyle jobs.
You enable non-interactive login to the remote machine by logging to the VM, switching to the jenkins user, creating a pass-phrase-less key pair and moving them to the remote machine.

`vagrant ssh`

`sudo su jenkins`

`ssh-keygen -t rsa -b 2048`

`cat /var/lib/jenkins/.ssh/id_rsa.pub`

Copy the output of the cat command, i.e., the jenkins users' public key into you clipboard. From another terminal session connect to your remote server at DigitalOcean and register yet another public key.

`ssh builder@[remote server IP]`

`echo "<our_public_jenkins_key>" >> ~/.ssh/authorized_keys`

`exit`

To verify that the remote login based on the keys is working, ssh to the machine from the jenkins user in our Vagrant VM:

`ssh builder@<our_ip>`

Afterwards, to exit from the remote machine, from the jenkins user, and from the VM type:

`exit`

`exit`

`exit`

### Creating Our Build Jobs

In total we will create two build jobs both Freestyle build job. 
We will use them to execute shell commands to build and deploy our docker containers.
The build jobs are the following:
Build-Docker (Maven project build job, red in image)
Deploy-Docker (Maven project build job, green in image)
The dependencies of the build jobs is given by their sequence above.

#### A Freestyle Build Job for Build-Docker

This job will, with the help of git repo build a docker image on DockerHub. 
The built code will be consumed by the subsequent freestyle Docker build job.
The build job consists of two build steps. One for building the Docker container and distributing it to the DockerHub
Navigate to New Item, select Freestyle project, and give it the name Build-Docker. Subsequently, under Source Code Management choose Git and point it to corresponding repository on GitHub [TODO add repo here].
Now, under Build -> Add build step choose Execute shell. Paste the following shell script into the Command field.

[TODO add shell script here]

### A Freestyle Project Build Job for Deploy-Docker

This job deploys the web application/REST API - from a Docker container registered at the DockerHub. 
This build script deplys the container to the remote machine by executing a sequence of shell commands.
Navigate to New Item, select Freestyle project, and give it the name Deploy-Docker. 
Subsequently, under Source Code Management choose Git and point it to the repository on GitHub containing the Dockerfile [TODO add repo here].
Now, under Build -> Add build step choose Execute shell. Paste the following shell script into the Command field.



## We are Done!

That is it! After creating and running the above four build jobs you should have the web application up and running on our remote machine. Try to point our browser to http://

This guide is base on The lecture notes [05-Continuous Integration and Delivery](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/lecture_notes/05-Continuous%20Integration%20and%20Delivery.ipynb)


