# aws note
1. Accessing a Bucket
  * In a virtual-hosted–style URL, the bucket name is part of the domain name in the URL. For example:
http://bucket.s3.amazonaws.com
http://bucket.s3-aws-region.amazonaws.com.

  * In a virtual-hosted–style URL, you can use either of these endpoints. If you make a request to the http://bucket.s3.amazonaws.com endpoint, the DNS has sufficient information to route your request directly to the Region where your bucket resides.
For more information, see Virtual Hosting of Buckets.

2. When you stop EC2 instance, the following happens:

* The instance performs a normal shutdown and stops running; its status changes to stopping and then stopped.
* Any Amazon EBS volumes remain attached to the instance, and their data persists.
* Any data stored in the RAM of the host computer or the instance store volumes of the host computer are gone.
* In most cases, the instance is migrated to a new underlying host computer when it's started.
* EC2-Classic: AWS releases the public and private IPv4 addresses for the instance when you stop the instance, and assign new ones when you restart it.
* EC2-VPC: The instance retains its private IPv4 addresses and any IPv6 addresses when stopped and restarted. AWS releases the public IPv4 address and assign a new one when you restart it.
* EC2-Classic: AWS disassociates any Elastic IP address that's associated with the instance. You're charged for Elastic IP addresses that aren't associated with an instance. When you restart the instance, you must associate the Elastic IP address with the instance; AWS doesn't do this automatically.
* EC2-VPC: The instance retains its associated Elastic IP addresses. You're charged for any Elastic IP addresses associated with a stopped instance

3. Which service can help you manage the budgets for all your AWS resources?
AWS budgets

4.  SQS Message Lifecycle:

 4.1 Component 1 sends Message A to a queue, and the message is distributed across the Amazon SQS servers redundantly.
 4.2 When Component 2 is ready to process a message, it consumes messages from the queue, and Message A is returned. While Message A is being processed, it remains in the queue and isn't returned to subsequent receive requests for the duration of the visibility timeout.
 4.3 Component 2 deletes Message A from the queue to prevent the message from being received and processed again once the visibility timeout expires.

5. How many types of block devices does Amazon Elastic Compute Cloud service support?
Instance store volumes (virtual devices whose underlying hardware is physically attached to the host computer for the instance)
EBS volumes (remote storage devices)

6. EBS
* When you create an EBS volume in an Availability Zone, it is automatically replicated within that zone to prevent data loss due to failure of any single hardware component.
* An EBS volume can only be attached to one EC2 instance at a time.
* After you create a volume, you can attach it to any EC2 instance in the same Availability Zone
* An EBS volume is off-instance storage that can persist independently from the life of an instance.
* EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.

Cách tính IOPS, through put, latency
* https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html
* IOPS là số lần đọc ghi / giây
* throughput là số MB đọc ghi / giây

Chú ý usecase cho Provisioned IOPS SSD (io1)
* Critical business applications that require sustained IOPS performance, or more than 10,000 IOPS or 160 MiB/s of throughput per volume
* Large database workloads, such as:
* MongoDB
* Cassandra
* Microsoft SQL Server
* MySQL
* PostgreSQL
* Oracle

7. An elastic network interface (ENI) is a logical networking component in a VPC that represents a virtual network card. You can attach a network interface to an EC2 instance in the following ways:

* When it's running (hot attach)
* When it's stopped (warm attach)
* When the instance is being launched (cold attach).

8. Cloud Formation
* Dùng để tạo infrastructure từ template (JSON)
Không tính tiền cloud formation, chỉ tính tiền các dịch vụ đc tạo ra
Cloud Formation > Elastic Beanstalk

9. AWS Elastic Beanstalk

* Simply upload your code, Elastic Beanstalk handles  the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. You have full control over the AWS resources. 
* Provides an environment to easily deploy and run applications in the cloud. It is integrated with developer tools and provides a one-stop experience for you to manage the lifecycle of your applications.
* There is no additional charge for Elastic Beanstalk - you pay only for the AWS resources you use

10. Elastic Map Reduce (EMR)
* https://kipalog.com/posts/Tong-quan-mo-hinh-lap-trinh-MapReduce
* Mapreduce là một mô hình lập trình, thực hiện quá tình xử lý tập dữ liệu lớn. Mapreduce gồm 2 pha : map và reduce.
* Hàm Map : Các xử lý một cặp (key, value) để sinh ra một cặp (keyI, valueI) - key và value trung gian. Dữ liệu này input vào hàm Reduce.
* Hàm Reduce : Tiếp nhận các (keyI, valueI) và trộn các cặp (keyI, valueI) trung gian , lấy ra các valueI có cùng keyI.

Việc của lập trình viên là quan tâm tới 2 hàm Map và Reduce. Còn các vấn đề khác như : phân chia các dữ liệu đầu vào, lịch trình thực thi các machines, handling các machines failure, quản lý việc giao tiếp giữa các machines là việc của hệ thống run-time.
=> Lập trình viên có thể không có kinh nghiệm về hệ thống song song và phân tán vẫn dễ dàng vận hành một hệ thống phân tán lớn.
Áp dụng mô hình MapReduce chạy trên lượng lớn các machine cỡ hàng ngàn machine và data lên đến mức Terabytes.

Các job sau dễ dàng sử dụng Mapreduce:

* Thống kê số từ khóa xuất hiện trong các documents.
* Thống kê số documents có chứa từ khóa.
* Thống kê số câu match với pattern trong các documents.
* Thống kê số URLs xuất hiện trong các web pages.
* Thống kê số lượt truy cập các URLs.
* Thống kê số từ khóa trên các hostnames.
* Distributed Sort.

11. AWS Global, Regional, AZ resource Availability
http://jayendrapatil.com/aws-global-vs-regional-vs-az-resources/
![alt text](https://user-images.githubusercontent.com/5670932/38067205-940107ca-3335-11e8-95ad-8dbd4a873bd9.png "")

EBS Volumes – Availability Zone

EBS Snapshot – Regional

Auto Scaling – Regional
  * Auto Scaling spans across multiple Availability Zones within the same region but cannot span across regions

Elastic Load Balancer – Regional
  * Elastic Load Balancer distributes traffic across instances in multiple Availability Zones in the same region

Placement Groups – Availability Zone
  * Placement groups can be span across Instances within the same Availability Zones

DynamoDb – Regional
  * All data objects are stored within the same region and replicated across multiple Availability Zones in the same region
  * Data objects can be explicitly replicated across regions using cross-region replication

CloudFront – Global
  * CloudFront is the global content delivery network (CDN) services are offered at AWS edge locations

Storage Gateway – Regional
  * AWS Storage Gateway stores volume, snapshot, and tape data in the AWS region in which the gateway is activated

12. How is Amazon SWF different from Amazon SQS?

* Amazon SWF API actions are task-oriented. Amazon SQS API actions are message-oriented.
* Amazon SWF keeps track of all tasks and events in an application. Amazon SQS requires you to implement your own application-level tracking, especially if your application uses multiple queues.
* The Amazon SWF Console and visibility APIs provide an application-centric view that lets you search for executions, drill down into an execution’s details, and administer executions. Amazon SQS requires implementing such additional functionality.
* Amazon SWF offers several features that facilitate application development, such as passing data between tasks, signaling, and flexibility in distributing tasks. Amazon SQS requires you to implement some application-level functionality.
* In addition to a core SDK that calls service APIs, Amazon SWF provides the AWS Flow Framework with which you can write distributed applications using programming constructs that structure asynchronous interactions.

13. What are some use cases that can be solved with Amazon SWF? 

* Use case #1: Video encoding using Amazon S3 and Amazon EC2
* Use case #2: Processing large product catalogs using Amazon Mechanical Turk. 
* Use case #3: Migrating components from the datacenter to the cloud. Business critical operations are hosted in a private datacenter but need to be moved entirely to the cloud without causing disruptions.

14. RDS Best Practices
* http://jayendrapatil.com/aws-certification-rds-best-practices/
* On a MySQL DB instance
  * Do not create more than 10,000 tables using Provisioned IOPS or 1000 tables using standard storage. Large numbers of tables will significantly increase database recovery time after a failover or database crash. If you need to create more tables than recommended, set the innodb_file_per_table parameter to 0.
  * Avoid tables in the database growing too large. Provisioned storage limits restrict the maximum size of a MySQL table file to 6 TB. Instead, partition the large tables so that file sizes are well under the 6 TB limit. This can also improve performance and recovery time.

* Performance
  * If the database workload requires more I/O than provisioned, recovery after a failover or database failure will be slow.
  * To increase the I/O capacity of a DB instance,
    * Migrate to a DB instance class with High I/O capacity.
    * Convert from standard storage to Provisioned IOPS storage, and use a DB instance class that is optimized for Provisioned IOPS.
    * if using Provisioned IOPS storage, provision additional throughput capacity.

* Multi-AZ & Failover
  * Deploy applications in all Availability Zones, so if an AZ goes down, applications in other AZs will still be available.
  * Use Amazon RDS DB events to monitor failovers.
  * Set a TTL of less than 30 seconds, if the client application is caching the DNS data of the DB instances. As the underlying IP address of a DB instance can change after a failover, caching the DNS data for an extended time can lead to connection failures if the application tries to connect to an IP address that no longer is in service.
  * Multi-AZ requires transaction logging feature to be enabled. Do not use features like Simple recover mode, offline mode or Read-only mode which turn of transaction logging.
  * To shorten failover time
  * Ensure that sufficient Provisioned IOPS allocated for your workload. Inadequate I/O can lengthen failover times. Database recovery requires I/O.
  * Use smaller transactions. Database recovery relies on transactions, so break up large transactions into multiple smaller transactions to shorten failover time
  * Test failover for your DB instance to understand how long the process takes for your use case and to ensure that the application that accesses your DB instance can automatically connect to the new DB instance after failover.