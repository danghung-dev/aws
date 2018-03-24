# Well-Architected Framework
## Security
### Defination
* Identity and Access Management
Privilege management
    * Question
        * How are you protecting access to and use of the AWS root account credentials?
        * How are you defining roles and responsibilities of system users to control human access to the AWS Management Console and API?
            * VD chia quyền theo root, có thể chia theo deparment ...
        * How are you limiting automated access to AWS resources (for
example, applications, scripts, and/or third-party tools or services)?
            * VD chỉ cho EC2 access vào DB
* Detective control
    * Questions
        * How are you capturing and analyzing logs?
* Infrastructure protection
    * Questions
        * How are you enforcing network and host-level boundary
protection?
        * How are you leveraging AWS service-level security features?
        * How are you protecting the integrity of the operating system?
* Data protection
        data nào available cho user nào. cái nào public, cái nào private. ai đc access vào data nào. must encrypt everything where posible
    * Question
        * How are you encrypting and protecting your data at rest?
        * How are you classifying your data?
        * How are you managing keys?
        * How are you encrypting and protecting your data in transit? (SSL)
* Incident Response
    * Questions
        * How do you ensure that you have the appropriate incident
response?

## Reliability
### Defination
* Foundations
    * REL 1: How are you managing AWS service limits for your accounts?
    * REL 2: How are you planning your network topology on AWS?
* Change Management
    * REL 3: How does your system adapt to changes in demand?
    * REL 4: How are you monitoring AWS resources?
    * REL 5: How are you executing change?
* Failure Management
    * REL 6: How are you backing up your data?
    * REL 7: How does your system withstand component failures?
    * REL 8: How are you testing your resiliency?
    * REL 9: How are you planning for disaster recovery?
## Performance Efficiency
### Defination
* Selection
    * PERF 1: How do you select the best performing architecture?
    * PERF 2: How did you select your compute solution?
    * PERF 3: How do you select your storage solution?
    * PERF 4: How do you select your database solution?
    * PERF 5: How do you configure your networking solution
* Review
    * PERF 6: How do you ensure that you continue to have the most appropriate resource type as new resource types and features are introduced?
* Monitoring
    * PERF 7: How do you monitor your resources post-launch to ensure they are performing as expected?
* Tradeoffs
    * PERF 8: How do you use tradeoffs to improve performance
## Cost Optimization
### Defination
* Cost-Effective Resources
    * COST 1: Are you considering cost when you select AWS services for your solution?
    * COST 2: Have you sized your resources to meet your cost targets?
    * COST 3: Have you selected the appropriate pricing model to meet your cost targets?
* Matching Supply and Demand
    * COST 4: How do you make sure your capacity matches but does not substantially exceed what you need?
* Expenditure Awareness
    * COST 5: Do you consider data-transfer charges when designing your architecture?
    * COST 6: How are you monitoring usage and spending?
    * COST 7: Do you decommission resources that you no longer need or stop resources that are temporarily not needed?
    * COST 8: What access controls and procedures do you have in place to govern AWS usage?
* Optimizing Over Time
    * COST 9: How do you manage and/or consider the adoption of new services?
## Operational Excellence
### Defination
* Prepare
    * OPS 1: What factors drive your operational priorities?
    * OPS 2: How do you design your workload to enable operability?
    * OPS 3: How do you know that you are ready to support a workload?
* Operate
    * OPS 4: What factors drive your understanding of operational health?
    * OPS 5: How do you manage operational events?
* Evolve
    * OPS 6: How do you evolve operation
