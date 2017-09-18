Setup Your Remote Machines for Jenkins and the static server
============================================================
For this we rent the cheapest possible cloud machine at Digital Ocean -which they call "droplet". 

### Option 1: The manual way to create a drolet on Digital Ocean
The descriptions and the provided setup script should be valid for any Debian-based Linux.

- Create an account at Digital Ocean (https://www.digitalocean.com)
- Create a new Ubuntu 16.04.3 x64 droplet (second smallest machine, 0.015USD per hour/ 10USD per month)
- Register your public SSH key while creating a droplet. 
- If you do not have a pair of keys read on how to do that. (https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)
- SSH to your new machine and create a new user, which we will call builder. You can copy the IP <your_ip> from your droplet configuration page.

`ssh root@<your_ip>

adduser builder

usermod -aG sudo builder

exit`

-Enable public key authentication for your new user. The following assumes that you have a keypair readily available.

`ssh root@<your_ip>
su - builder
mkdir ~/.ssh
chmod 700 ~/.ssh
echo "<your_public_key>" > ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys`

In case you have issues with this step make sure to read the guide on initial Ubuntu server setup, especially the section "Step Four — Add Public Key Authentication"!

-Copy the setup script to the remote machine, log onto it, make the file executable, and run it.

`scp /path/to/remote/setup.sh builder@<your_ip>:/home/builder
ssh builder@<your_ip>
chmod u+x ./setup.sh
./setup.sh
exit`

Now you have a remote machine up and running.

### Option 2: Setup Your Remote Machines for Jenkins and The Static Server with Vagrant

## Setup Jenkins on Your Remote Machine

-Install Vagrant (https://www.vagrantup.com/docs/installation/) and VirtualBox (https://www.virtualbox.org/wiki/Downloads) to your local machine
-cd to the directory with the Vagrantfile and startup the VM. When started up for the first time vagrant up will automatically run the provision script (provision.sh). Note in case you want to allow your group members to log onto the Jenkins build server on this machine uncomment the line # config.vm.network "public_network" in the Vagrantfile.
-`cd /vm` #[comment]: <> (TODO)
-`vagrant up`
-You can ssh into this VM via `vagrant ssh`
-After starting the VM Jenkins should be up and running. You can access it via [your droplet IP]:8080

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
There add a Secret text, where the secret is your password to your DockerHub account.

[pic]

#### Allow Jenkins User to Execute Deployment Script Remotely
To allow for a login from a non-interactive shell to the remote machine we have to create a pair of SSH keys for the jenkins user, i.e., the Linux user executing the shell scripts in Freestyle jobs.
You enable non-interactive login to the remote machine by logging to the VM, switching to the jenkins user, creating a pass-phrase-less key pair and moving them to the remote machine.

`vagrant ssh
sudo su jenkins
ssh-keygen -t rsa -b 2048
cat /var/lib/jenkins/.ssh/id_rsa.pub`
Copy the output of the cat command, i.e., the jenkins users' public key into you clipboard. From another terminal session connect to your remote server at DigitalOcean and register yet another public key.
`ssh builder@[remote server IP]
echo "<your_public_jenkins_key>" >> ~/.ssh/authorized_keys
exit`

To verify that the remote login based on the keys is working, ssh to the machine from the jenkins user in your Vagrant VM:

`ssh builder@<your_ip>`

Afterwards, to exit from the remote machine, from the jenkins user, and from the VM type:

`exit
exit
exit`

### Creating Your Build Jobs

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

That is it! After creating and running the above four build jobs you should have the web application up and running on your remote machine. Try to point your browser to http://



