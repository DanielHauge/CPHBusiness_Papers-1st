Group 8: Continues Delivery Setup Chain Documentation
==============================================================
## Link Minimal Viable Prototype
[Minimal Viable Prototype](https://#)
TO DO In the top of the document, you provide a link to your MVP application serving at least a static HTML page.

## A Brief Description of the Continues Delivery Technology

#### Overview of the Setup

Our setup consists of the following components

- GitHub repository. Repository of the Web Application ( our Minimal Viable Prototype ) and where new changes to the application are being pushed.
- DockerHub repository. The repository where the docker image is being hosted. 
- Remote Machine on DigitalOcean with Jenkins Server. This server runs the build and delivery jobs. [Link to the server here](http://165.227.168.19:8080/login?from=%2F).
- The remote machine on DigitalOcean with the Static Web Server. Where the Web Application is being deployed and hosted.

#### Overview of the Build and Delivery Jobs
The Jenkins server is set up to check for changes in the GitHub repository.
If the Jenkins Server detects any changes in the GitHub repository it runs the build and deploys jobs.
The following is a description of the processes in each job:
##### The Build Job
The Jenkins Server builds a docker image from GitHub project repository. 
It then pushes the docker image up to the DockerHub repository.
##### The Deploy Job Process
The end of docker-build job then deploys the docker image that is hosted on the DockerHub to the Static Web Server. When this process is finished it logs onto the web server and initiate the setup image to start the server.

It then deploys the docker image that is hosted on the DockerHub to the Static Web Server. It logs in to When this process is finished it checks the status of the Web Application as a final step.


## Manual How to Setup The Continues Deliver and Integration Technology of Our Choice

- The pre recusite for this is that you have an account at Digital Ocean (https://www.digitalocean.com)
- Setup the public and private keys on your locale machine. [Guide here](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)
- Install Vagrant (https://www.vagrantup.com/docs/installation/) and VirtualBox (https://www.virtualbox.org/wiki/Downloads) to the remote machine
- Install Digital Ocean Vagrant plugin. [Guide here](vagrant up --provider=digital_ocean)

Further down there we will set up two remote machines on digital Ocean with Vagrant scripts.


The vagrant scripts will create two new Ubuntu 16.04.3 x64 droplets (smallest machines)




### Prepare The Remote Jenkins Server - Setup Jenkins




- Navigate to the Jenskins server directory in the project where the Vagrant file is contained.
- Open the vagrantfile and put in your own information where these signs are present <your_info>.
- `vagrant up --provider=digital_ocean`
- After starting the Jenkins should be up and running. You can access it via [Jenkins server droplet IP]:8080. 


#### Configuring Jenkins
Access the Jenkins Server by going to [Jenkins server droplet IP]:8080.
Now that Jenkins is running you have to configure it. On the first time use it will present you the following page.
![CI Setup](images/jenkins_fst_login.png)

Here you have to insert the key that you get either from the output of the provision script or via:

`vagrant ssh`

`sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

Subsequently, choose to Install suggested plugins.
Afterwards, create a first admin user on Jenkins. For this example, we will call it builder too.

##### Adding Credentials to Jenkins

To allow for the later use of DockerHub as the registry for the container with the final web application you need to be registered at https://hub.docker.com.
After you have created a user at DockerHub, in Jenkins navigate to Credentials -> (global) -> Add Credentials (which corresponds to navigating to the following URL: [Jenkins server IP]:8080/credentials/store/system/domain/_/ ).
There add a Secret text, where the secret is our password to our DockerHub account.
![CI Setup](images/jenkins_secret_text.png)




##### Creating Our Build Jobs

In total we will create two build jobs both Freestyle build job. 
We will use them to execute shell commands to build and deploy our docker containers.
The build jobs are the following:
Build-Docker (Maven project build job, red in image)
Deploy-Docker (Maven project build job, green in image)
The dependencies of the build jobs is given by their sequence above.

###### A Freestyle Build Job for Build-Docker

This job will, with the help of git repo build a Docker image on DockerHub. 
The built code will be consumed by the subsequent freestyle Docker build job.
The build job consists of two build steps. One for building the Docker container and distributing it to the DockerHub
Navigate to New Item, select Freestyle project, and give it the name Build-Docker. Subsequently, under Source Code Management choose Git and point it to the corresponding repository on GitHub [TODO add repo here].
Now, under Build -> Add build step choose Execute shell. Paste the following shell script into the Command field.

[TODO add shell script here]

###### A Freestyle Project Build Job for Deploy-Docker

This job deploys the web application/REST API - from a Docker container registered at the DockerHub. 
This build script deploys the container to the remote machine by executing a sequence of shell commands.
Navigate to New Item, select Freestyle project, and give it the name Deploy-Docker. 
Subsequently, under Source Code Management choose Git and point it to the repository on GitHub containing the Dockerfile [TODO add repo here].
Now, under Build -> Add build step choose Execute shell. Paste the following shell script into the Command field.

### Prepare The Remote Static Web Server

[TODO]

## We are Done!

That is it! After creating and running the above four build jobs you should have the web application up and run on our remote machine. Try to point our browser to http://

This guide is base on The lecture notes [05-Continuous Integration and Delivery](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/lecture_notes/05-Continuous%20Integration%20and%20Delivery.ipynb)
