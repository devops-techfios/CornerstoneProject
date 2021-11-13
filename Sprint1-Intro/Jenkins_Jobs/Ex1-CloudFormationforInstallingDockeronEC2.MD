# Create Cloud formation template for Installing Docker on Amazon Linux server.

Below is the manual instructions. Add custom automations using user data script within Cloud formation template.Reference material here

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/deploying.applications.html


### Pre-requisites
1. Amazon Linux EC2 Instance

Copy a suitable cloud formation template from reference material and add the below steps under UserData section. UserData section is used to execute custom shell scripts after a new server is built

## Installation Steps

1. Install docker and start docker services
   ```sh 
   yum install docker -y
   docker --version 
   
   # start docker services
   service docker start
   service docker status
   ```
1. Create a user called dockeradmin
   ```sh
   useradd dockeradmin
   passwd dockeradmin
   ```
1. add a user to docker group to manage docker 
   ```
   usermod -aG docker dockeradmin
   ```
### Validation test to confirm after installation. Not required for automation
1. Create a tomcat docker container by pulling a docker image from the public docker registry
   ```sh
   docker run -d --name test-tomcat-server -p 8090:8080 tomcat:latest
   ```