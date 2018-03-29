# aws note
1. Accessing a Bucket
  * In a virtual-hosted–style URL, the bucket name is part of the domain name in the URL. For example:
http://bucket.s3.amazonaws.com
http://bucket.s3-aws-region.amazonaws.com.

  * In a virtual-hosted–style URL, you can use either of these endpoints. If you make a request to the http://bucket.s3.amazonaws.com endpoint, the DNS has sufficient information to route your request directly to the Region where your bucket resides.
For more information, see Virtual Hosting of Buckets.

2. When you stop EC2 instance, the following happens:

-The instance performs a normal shutdown and stops running; its status changes to stopping and then stopped.
-Any Amazon EBS volumes remain attached to the instance, and their data persists.
-Any data stored in the RAM of the host computer or the instance store volumes of the host computer are gone.
-In most cases, the instance is migrated to a new underlying host computer when it's started.
-EC2-Classic: AWS releases the public and private IPv4 addresses for the instance when you stop the instance, and assign new ones when you restart it.
-EC2-VPC: The instance retains its private IPv4 addresses and any IPv6 addresses when stopped and restarted. AWS releases the public IPv4 address and assign a new one when you restart it.
-EC2-Classic: AWS disassociates any Elastic IP address that's associated with the instance. You're charged for Elastic IP addresses that aren't associated with an instance. When you restart the instance, you must associate the Elastic IP address with the instance; AWS doesn't do this automatically.
-EC2-VPC: The instance retains its associated Elastic IP addresses. You're charged for any Elastic IP addresses associated with a stopped instance

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
-When you create an EBS volume in an Availability Zone, it is automatically replicated within that zone to prevent data loss due to failure of any single hardware component.
-An EBS volume can only be attached to one EC2 instance at a time.
-After you create a volume, you can attach it to any EC2 instance in the same Availability Zone
-An EBS volume is off-instance storage that can persist independently from the life of an instance.
-EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.
Cách tính IOPS, through put, latency
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html
IOPS là số lần đọc ghi / giây
throughput là số MB đọc ghi / giây

Chú ý usecase cho Provisioned IOPS SSD (io1)
Critical business applications that require sustained IOPS performance, or more than 10,000 IOPS or 160 MiB/s of throughput per volume
Large database workloads, such as:
MongoDB
Cassandra
Microsoft SQL Server
MySQL
PostgreSQL
Oracle

7. An elastic network interface (ENI) is a logical networking component in a VPC that represents a virtual network card. You can attach a network interface to an EC2 instance in the following ways:

When it's running (hot attach)
When it's stopped (warm attach)
When the instance is being launched (cold attach).

8. Cloud Formation
Dùng để tạo infrastructure từ template (JSON)
Không tính tiền cloud formation, chỉ tính tiền các dịch vụ đc tạo ra
Cloud Formation > Elastic Beanstalk

9. AWS Elastic Beanstalk
Provides an environment to easily deploy and run applications in the cloud. It is integrated with developer tools and provides a one-stop experience for you to manage the lifecycle of your applications.

10. Elastic Map Reduce (EMR)
https://kipalog.com/posts/Tong-quan-mo-hinh-lap-trinh-MapReduce
Mapreduce là một mô hình lập trình, thực hiện quá tình xử lý tập dữ liệu lớn. Mapreduce gồm 2 pha : map và reduce.
Hàm Map : Các xử lý một cặp (key, value) để sinh ra một cặp (keyI, valueI) - key và value trung gian. Dữ liệu này input vào hàm Reduce.
Hàm Reduce : Tiếp nhận các (keyI, valueI) và trộn các cặp (keyI, valueI) trung gian , lấy ra các valueI có cùng keyI.

Việc của lập trình viên là quan tâm tới 2 hàm Map và Reduce. Còn các vấn đề khác như : phân chia các dữ liệu đầu vào, lịch trình thực thi các machines, handling các machines failure, quản lý việc giao tiếp giữa các machines là việc của hệ thống run-time.
=> Lập trình viên có thể không có kinh nghiệm về hệ thống song song và phân tán vẫn dễ dàng vận hành một hệ thống phân tán lớn.
Áp dụng mô hình MapReduce chạy trên lượng lớn các machine cỡ hàng ngàn machine và data lên đến mức Terabytes.

Các job sau dễ dàng sử dụng Mapreduce:

Thống kê số từ khóa xuất hiện trong các documents.
Thống kê số documents có chứa từ khóa.
Thống kê số câu match với pattern trong các documents.
Thống kê số URLs xuất hiện trong các web pages.
Thống kê số lượt truy cập các URLs.
Thống kê số từ khóa trên các hostnames.
Distributed Sort.

11. AWS Global, Regional, AZ resource Availability
http://jayendrapatil.com/aws-global-vs-regional-vs-az-resources/
![alt text](https://user-images.githubusercontent.com/5670932/38067205-940107ca-3335-11e8-95ad-8dbd4a873bd9.png "")

IAM
Users, Groups, Roles, Accounts – Global
Same AWS accounts, users, groups and roles can be used in all regions
Key Pairs – Global or Regional
Amazon EC2 created key pairs are specific to the region
RSA key pair can be created and uploaded that can be used in all regions
Virtual Private Cloud
VPC – Regional
VPC are created within a region
Subnet – Availability Zone
Subnet can span only a single Availability Zone
Security groups – Regional
A security group is tied to a region and can be assigned only to instances in the same region.
VPC Endpoints – Regional
You cannot create an endpoint between a VPC and an AWS service in a different region.
VPC Peering – Regional
VPC Peering can be performed across VPC in the same account of different AWS accounts but only within the same region. They cannot span across regions
Elastic IP Address – Regional
Elastic IP address created within the region can be assigned to instances within the region only
EC2
Resource Identifiers – Regional
Each resource identifier, such as an AMI ID, instance ID, EBS volume ID, or EBS snapshot ID, is tied to its region and can be used only in the region where you created the resource.
Instances – Availability Zone
An instance is tied to the Availability Zones in which you launched it. However, note that its instance ID is tied to the region.
EBS Volumes – Availability Zone
Amazon EBS volume is tied to its Availability Zone and can be attached only to instances in the same Availability Zone.
EBS Snapshot – Regional
An EBS snapshot is tied to its region and can only be used to create volumes in the same region and has to be copied from One region to other if needed
AMIs – Regional
AMI provides templates to launch EC2 instances
AMI is tied to the Region where its files are located with Amazon S3. For using AMI in different regions, the AMI can be copied to other regions
Auto Scaling – Regional
Auto Scaling spans across multiple Availability Zones within the same region but cannot span across regions
Elastic Load Balancer – Regional
Elastic Load Balancer distributes traffic across instances in multiple Availability Zones in the same region
Placement Groups – Availability Zone
Placement groups can be span across Instances within the same Availability Zones
S3 – Global but Data is Regional
S3 buckets are created within the selected region
Objects stored are replicated across Availability Zones to provide high durability but are not cross region replicated unless done explicitly
Route53 – Global
Route53 services are offered at AWS edge locations and are global
DynamoDb – Regional
All data objects are stored within the same region and replicated across multiple Availability Zones in the same region
Data objects can be explicitly replicated across regions using cross-region replication
WAF – Global
Web Application Firewall (WAF) services protects web applications from common web exploits are offered at AWS edge locations and are global
CloudFront – Global
CloudFront is the global content delivery network (CDN) services are offered at AWS edge locations
Storage Gateway – Regional
AWS Storage Gateway stores volume, snapshot, and tape data in the AWS region in which the gateway is activated

