Xem lai elastic map reduce, cloudformation

SQS NOT keep track log event app
SWF thì có

Typical database block sizes range from 2 KB to 32 KB. Amazon Redshift uses a block size of 1 MB

For all new AWS accounts there is a soft limit of 20 EC2 instances per region.

Q. You have a high performance compute application and you need to minimize network latency between EC2 instances as much as possible. What can you do to achieve this?

Create a placement group within an Availability Zone and place the EC2 instances within that placement group.

Q. You work for a cosmetic company which has their production website on AWS. The site itself is in a two-tier configuration with web servers in the front end and database servers at the back end. The site uses using Elastic Load Balancing and Auto Scaling. The databases maintain consistency by replicating changes to each other as and when they occur. This requires the databases to have extremely low latency. Your website needs to be highly redundant and must be designed so that if one availability zone goes offline and Auto Scaling cannot launch new instances in the remaining Availability Zones the site will not go offline. How can the current architecture be enhanced to ensure this?
Correct. In this scenario if you lost an availability zone, you would still have 2 other Availability Zones available each that is configured to handle 50% peak load per zone. 50% + 50% = 100%.

Q. Which of the following metrics do you need to design a custom cloud watch metric for, when monitoring the health of your EC2 instances?

Memory usage

Q. You work for a toy company that has a busy online store. As you are approaching Christmas, you find that your store is getting more and more traffic. Your web tier is behind an Auto Scaling group, but you notice that is is frequently scaling, sometimes multiple times in an hour, only to scale back down after peak usage. You need to keep Auto Scaling from scaling up and down so rapidly. Which of the following options would help you to achieve this?

Modify the Auto Scaling group cool-down timers & modify the Amazon CloudWatch alarm period that triggers your Auto Scaling scale down policy.

Q. You are a solutions architect who has been asked to do some consulting for a US company that produces re-useable rocket parts. They have a new web application that needs to be built and this application must be stateless. Which three services could you use to achieve this?

RDS, DynamoDB & Elasticache.

## de thi so 1
Q. Which is a correct example of a synchronous data replication?

Q. What is the AWS Lambda resource limit for the amount of ephemeral disk capacity allocated per invocation?

## Last exam in Udemy

Q. In regards to EC2 which of the following is not a customers responsibility under the shared responsibility model?

Q. You are designing an AWS solution for a new customer and they want to use their active directory credentials in order to sign in to the AWS management console. What kind of authentication response is required in order for users to authenticate with the AWS security token service (STS).

Q. You are designing a web application for a new social media start up and have recommended using DynamoDB for the database due to its superior performance. You need to ensure that your database has redundancy. What additional steps should you do?

Q. You are a solutions architect working for a large cell phone company in the US. Your CSO has engaged a third party security company to conduct a security audit of your company to make sure it is not liable to hacking. The third party security company would like to conduct a penetration test on your AWS estate. Would this be allowed by AWS?

Q. AWS help provide protection against some forms of traditional network attacks. Which of the following is not protected against by AWS?

Q. You have been monitoring a sensitive autoscaling group, and you expect it to scale-in as you enter a period of holiday downtime. The auto scaling group is distributed over three AZs ( AZ - A & -B have two instances each, and AZ -C has three instances). All instances have different CPU and Memory utilization, and all instances have been running for a different number of days. All instances come from different versions of a root AMI, and all instances have different numbers of sessions connected. Which instance will be the 1st to shut down?

Q. Auto Scaling is a tool used to create fault-tolerant and cost-effective architectures.

Q. What is the maximum VisibilityTimeout of an SQS message in a FIFO queue?

Q. A client who is using EC2 believes that someone other than approved administrators is trying to gain access to her Linux web app instances, and she asks what sort of network access logging can be added to the system. Which of the following might you recommend?

Q. You have a MySQl database running on an EC2 instance in a private subnet. You can connect via SSH, but you are unable to apply updates to the database server via the NAT instance. What might you do to remedy this problem?


Q. Your company provides an online image recognition service and uses SQS to decouple system components. Your EC2 instances poll the image queue as often as possible to keep end-to-end throughput as high as possible, but you realize that all this polling is resulting in both a large number of CPU cycles and skyrocketing costs. How can you reduce cost without compromising service?

Q. You work for a popular media outlet about to release a story that is expected to go viral. During load testing on the website, you discover that there is read contention on the database tier of your application. Your RDS instance consists of a MySQL database on an extra large instance. Which two of the following approaches would be best to further scale this instance to meet the anticipated increase in traffic your viral story will generate?

Q. Following advice from your consultant, you have configured your VPC to use Dedicated hosting tenancy. A subsequent change to your application has rendered the performance gains from dedicated tenancy superfluous, and you would now like to recoup some of these greater costs. How do you revert to Default hosting tenancy?

Q. You are developing a web application, and you are maintaining separate sets of resources for your alpha, beta, and release environments. Each version runs on Amazon EC2 with an EBS volume. You use Elastic Load Balancing to manage traffic and Amazon Route 53 to manage your domain. What's the best way to check the health and status of all three groups of services simultaneously?

Q. You're building out a single-region application in us-west-2. However, disaster recovery is a strong consideration, and you need to build the application so that if us-west-2 becomes unavailable, you can fail-over to us-west-1. Your application relies exclusively on pre-built AMI's. In order to share those AMI's with the region you're using as a backup, which process would you follow?