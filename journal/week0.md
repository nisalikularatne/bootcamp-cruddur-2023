# Things to install and set up for running the Cruddur application

In order to proceed with building the Cruddur application for the bootcamp one will have to register with the services mentioned below:
* Create a github account. Make a repository using ExamProCo/aws-bootcamp-cruddur-2023 template.
* Create a gitpod account. Install the chrome/firefox extension and set up your prefered IDE to work with.
* Create an AWS account and configure your IAM user with MFA enabled
* Create a HoneyComb.io account for observability across distributed services
* Register a momento account through CLI for utilizing the Momento Serverless Caching service
* Create an account on Lucidchart which will allow you to create chart/diagrams
* Create a Rollbar account for error logging and tracking services

# Week 0 — Billing and Architecture

One of the prime concepts learned in week 0 about AWS billing was the triad of cost, time and scope. And how we need to keep all these 3 factors while architecting a solution according to an organisations business use case.

## Billing Alerts
In this section I learned 2 ways in which billing alerts can be set up.
* CloudWatchAlarm - We can create a billing alert using cloudwatch alarm in the us-east-1 region
* Budgets - We can utilize AWS Budgets to help us identify resources which are over or under utilized

## Cost Explorer
In week0, there was a demo on how cost explorer service can be utilized to track and visualize AWS costs and it also helps get a forecasted cost for upcoming months.

## Cost Allocation Tags
Cost Allocation Tags are extremely helpful when you want to organize costs across multiple services. A tag is a label that you or AWS assigns to an AWS resource therefore we have user defined and AWS defined tags. Each tag consists of a key and a value. For each resource, 
each tag key must be unique, and each tag key can have only one value. All tags need to be activated.

## AWS Pricing Calculator
AWS Pricing Calculator helps estimate the cost for an architecture solution. It calculates the estimates based on 730 hours

## AWS Credits
AWS Credits is a coupon or tag which can be obtained at an event or on completion of an AWS certification which can then be used in your AWS account. It does however come with an expiration date

## Free Tier
In this section, week0 demonstrates all the services which are free for 12 months. Post 12 months certain services are still free
and trial services are for limited days.

# Week0 - Architectural Diagram

In order to build the Crudder Architecture we would require the below mentioned components:
* Frontend and Backend Applications hosted within a container in ECS cluster.
* Route53 for DNS 
* AWS Cognito for Authentication
* AWS RDS and DynamoDB databases
* Momento as a third party serverless caching solution
* In this diagram we have tried to keep cost minimal and make use of the AWS free tier as much as possible.
![alt text](img/Crudder%20Logical%20Diagram.png)

# Week0 - Security in and of the Cloud

Cloud Security is important as it helps reduce impact of breaches. Helps protect networks, applications, services in cloud environments against malicious data theft. It also helps reduce human error responsible for data leaks.  
## Adding MFA to root account
Enable either a virtual or hardware MFA for root account as this account is has all the AWS privileges attached to it. In case it is compromised,
attackers can run malicious scripts on your AWS account and do bitcoin mining. In my case I used a virtual MFA using google authenticator app on my phone.

## AWS Organisations
Using AWS Organisations we can create multiple AWS accounts using the management account. In this exercise, I created
Business Units (Engineering, HR, Cloud) and also Active and Standby Accounts. Moreover I went through the best practices of setting up SCP (Service Control Policies) which can be used to manage permissions in a new organisation created by AWS

## AWS CloudTrail
Using AWS CloudTrail we can audit all of the API calls to services in that particular region. Since this service is not free and costs a few dollars, I havent set it up on my account.

## IAM
IAM topic was extensively discussed in the week-0 content of the bootcamp. The IAM service is a free service provided by AWS to provide privileges to users and set up permissions and restrictions on service access. 
I'm listing some of the key takeaways from my learnings on IAM
* It is best practice to assign least privileges to a user.
* We can have a username and password for a user to access AWS. Another mechanism of providing access to the users is through access key and secret access key.
  It is best practice to store these values in environment files and not to expose them hardcoded in github repositories.
* Policies are attached to a role, group or IAM user specifying the actions the user can or cannot perform.
* Best practice to user IAM instead of root account for AWS. Use the root account only for billing and managing AWS organisations.

## AWS Organization SCP's
In this section I create a SCP which prevents a user to leave the organization. 

## Security Best Practices
* Data Protection and Residency in accordance to Security Policy
* IAM with least privileges
* Governance and compliance of AWS Services being used
* Shared Responsiblity of Thread Detection
* Incidence Response Plans to include Cloud
