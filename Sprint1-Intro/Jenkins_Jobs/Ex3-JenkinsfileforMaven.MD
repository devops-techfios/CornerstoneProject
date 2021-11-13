# Write a Jenkinsfile to build a Maven Project

### Pre-requisites
1. Maven plugin should be installed in Jenkins. By default maven plugin will be installed in Jenkins
2. Configure specific version of maven in Jenkins Global Tool Configuration

### References
How to install plugins in Jenkins [https://devopspilot.com/content/jenkins/tutorials/common/02-how-to-install-plugins]
How to configure maven in Global Tool Configuration [https://devopspilot.com/content/jenkins/tutorials/common/03-global-tool-configurations]
How to create pipeline job in Jenkins [https://devopspilot.com/content/jenkins/tutorials/pipeline/01-how-to-create-pipeline-job]

## Instructions for creating Jenkinsfile

1. Fork project hello-world and update the required feilds in the Jenkinsfile
2. In Jenkinsfile create tools block use maven definition to refer the maven installation "maven-3.6.3" configured in Jenkins Global tool configuration.
3. In Jenkinsfile, create stage for Build, execute  mvn clean package command to compile and package the java application.

   ```