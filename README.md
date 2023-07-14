This project is related to this project: https://github.com/marviigrey/NFS-WEB-DB-APP

Moving forward with the project we will add automation by introducing CICD with JENKINS:

==================================================================================================================================================
Installing Jenkins:
1. spin an Ubuntu ec2-instance.
2. Ensure port 8080 under TCP protocol is open for your ec2 instance.
3. SSH into the server and install the pre-requisite of Jenkins which is Java:
4. sudo apt update
   sudo apt install default-jdk-headless
5. Install Jenkins:
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt-get install Jenkins
6. confirm jenkins is running:
      sudo systemctl status jenkins
7. Great!, now login to jenkins dashboard by using the Public ip and port 8080:
     <public-ip>:8080
8. perform the setup and create a user profile.
----------------------------------------------------------------------------------------------------
We are going to continue the project by configuring Jenkins to pull code changes automatically from our source code repository.
We will give Jenkins permission to our GitHub repo of the tooling app to check for updates on our source code and pull the changes to create a build.
after building, we then tell Jenkins to retain build artifacts into our NFS server:

1. enable webhook to the GitHub repo and include the jenkins URL.
2. create a freestyle project on jenkins and add the repo to Jenkins as our source code.
3. install the plugin called "publish over ssh" on the NFS server and add the key file of our NFS server, also include the hostname, IP, and username.
4. this should be done on the Post-build-action on your project.
5. To confirm,change anything on the readme file or add another file and watch it appear on the nfs server.
   
