Xem lai elastic map reduce, cloudformation

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