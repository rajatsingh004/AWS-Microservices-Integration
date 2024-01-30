# Web-App
![image](https://github.com/rajatsingh004/AWS-Microservices-Integration/assets/32368968/296e9c1c-44c8-402f-86ef-22a6f46ef332)

It is a sample microservice application you can use as a sandbox to test and learn the process of the deployment of a website using various AWS services.
Route 53
CloudFront
Amazon Cognito
Elastic Load Balancer
Auto Scaling Group
Amazon RDS
ElastiCache

## AWS Route53
Configured the required domain name fo your web-app and when the user hits it in the browser, Route 53 also resolves the domain name to the CloudFront distribution.

## AWS CloudFront
CloudFront serves as the content delivery network, retrieving and delivering the initial content of the web-app. It points to an S3 bucket where the custom login page is hosted.

## AWS Cognito
The custom login page interacts with Amazon Cognito for user authentication. Upon entering their credentials, users authenticate through the Cognito hosted UI. After successful authentication, Cognito redirects the user back to the specified callback URL, which is the endpoint of the load balancer. This ensures users are directed back to the application running on EC2 instances.

## ELB
The load balancer receives the redirected request from Cognito and forwards it to the EC2 instances. EC2 instances behind the load balancer generate and serve the content of the web-app.

## ASG
EC2 instances are managed by an Auto Scaling Group (ASG), which automatically adjusts the number of instances based on demand. When there is high traffic, the ASG may increase the number of instances to handle the load.

## Databases

### RDS
Amazon RDS with Replica: Used for storing and managing relational data across microservices.

### ELasticache
Multi-AZ ElastiCache for Caching: Used to improve performance by caching frequently accessed data.

