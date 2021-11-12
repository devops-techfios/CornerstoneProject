# Draw AWS architecture diagram for below project.

Draw an architecture diagram for Project Tech FiOS. Application under discussion is a classic three tier application built with auto scaling, load balancing and secured inside a isolated cloud environment. Traffic to www.projecttechfios.com is routed via Amazon provided DNS service.


### Pre-requisites
1. Use online drawing tools like draw.io or lucidchart



## Steps for diagram

1. Draw a user - User accounts for development team with access to core AWS services 
2. Draw Route 53 - Configure a web domain
3. Draw a container for VPC - Traffic routing into and out of our Private Cloud
4. Draw Load Balancers to send traffic to ASG containing EC2 instances - Distribute traffic evenly across resources
5. Draw ASG attached to EC2 instance - Auto scale resources
6. Draw EC2 instances for app and web layer  - Servers to host project
7. Location for bulk storage - Draw S3 bucket connected to App layer
8. A database to store and catalog data - Draw RDS showing connection from app layer
9. Send notifications from app layer - Draw SNS topic from app layer