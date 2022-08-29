# Design a Production Ready Kubernetes Cluster in AWS


Approach is to build the eks cluster on a jenkins server to enable CI/CD

### Installation of jenkins server for CI/CD
- Create an EC2 instance
- Select any os and instance type
- Create a keypair && download the pem.file
- Grant permission `chmod 400 name.pem`
- SSH into the server
- Switch to the root user to allow installation `sudo su -`

### Install Java
We will be using open java for our demo, Get latest version from http://openjdk.java.net/install/
- `yum install java-1.8*`
- Confirm Java Version `java -version`
- Find your java home path `find /usr/lib/jvm/java-1.8* | head -n 3`
- ```export JAVA_HOME```
  ```PATH=$PATH:$JAVA_HOME```
- Update your .bash_profile `source ~/.bash_profile`
- Check java version again to be sure installation was complete `java -version`

### Install Jenkins
You can install jenkins using the rpm or by setting up the repo. We will setup the repo so that we can update it easily in future. Get latest version of jenkins from https://pkg.jenkins.io/redhat-stable/
- ```yum -y install wget
      wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
      rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
      yum -y install jenkins```
      
 ### Start Jenkins
 -  Start jenkins service `systemctl start jenkins`
 -  Setup Jenkins to start at boot, `systemctl enable jenkins`
 #### Accessing Jenkins
 -  Visit `http://YOUR-SERVER-PUBLIC-IP:8080` since jenkins runs on port:`8080`
 -  use this to get your admin password `cat /var/lib/jenkins/secrets/initialAdminPassword`
 

 
