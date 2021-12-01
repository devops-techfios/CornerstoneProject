# Write a Jenkinsfile to deploy on Tomcat server

### Pre-requisites
1. Maven plugin should be installed in Jenkins. By default maven plugin will be installed in Jenkins
2. Configure specific version of maven in Jenkins Global Tool Configuration

### References
How to install plugins in Jenkins [https://devopspilot.com/content/jenkins/tutorials/common/02-how-to-install-plugins]
How to configure maven in Global Tool Configuration [https://devopspilot.com/content/jenkins/tutorials/common/03-global-tool-configurations]
How to create pipeline job in Jenkins [https://devopspilot.com/content/jenkins/tutorials/pipeline/01-how-to-create-pipeline-job]
How to install Tomcat [https://devopspilot.com/content/tomcat/tutorials/installation]
How to manually deploy the java application to Tomcat [https://devopspilot.com/content/tomcat/tutorials/how-to-manually-deploy-java-application-to-tomcat]
How to deploy the java application to Tomcat 9 webserver using maven [https://vigneshsweekaran.github.io/content/tomcat/tutorials/how-to-deploy-java-application-to-tomcat-using-maven]

## Instructions for creating Jenkinsfile

1. Fork project hello-world and update the required feilds in the Jenkinsfile
2. In Jenkinsfile create tools block use maven definition to refer the maven installation "maven-3.6.3" configured in Jenkins Global tool configuration.
3. In Jenkinsfile, create stage for Build, execute  mvn clean package command to compile and package the java application.
4.  In Jenkinsfile, create Deploy stage to use "Deploy to container" plugin for deploying "hello-world.war" file to tomcat webserver.
5. Parameters passed to Deploy to container plugin definition.

credentialsId: ‘tomcat_credential’ –> Store the tomcat username and password in Jenkins credentials and pass the tomcat credential id here. I have stored the tomcat credentals in Jenkins and created the id as tomcat_credential

Before storing the credentials in jenkins, create a user in Tomcat with manager-script role.

To create users in Tomcat, open the file /var/lib/tomcat9/conf/tomcat-users.xml

```
sudo vi /var/lib/tomcat9/conf/tomcat-users.xml

```
Go to end of the file and paste the following lines inside tomcat-users block and save it.

  ```
  <role rolename="manager-script"/>
  <user username="deployer" password="deployer" roles="manager-script"/>

  ```


Here we have defined one role manager-script and created one user deployer and assigned the manager-script role to the deployer user.

Then restart the tomcat9

```
sudo systemctl restart tomcat9

```
url: ‘http://152.70.71.239:8080/’ –> Your tomcat url
contextPath: ‘/pipeline’ –> Context path to deploy in Tomcat
onFailure: false –> Flag used to control the deployment, I dont want to deploy If my pipeline JOb fails, thatswhy I am setting onFailure flag to false
war: ‘target/*.war’ –> Your war file name

   ```