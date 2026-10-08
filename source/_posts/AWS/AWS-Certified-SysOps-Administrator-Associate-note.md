---
layout: aws
title: AWS Certified SysOps Administrator – Associate Notes
date: 2022-07-23 16:11:49
tags: [AWS, Certification]
categories: AWS
---

### Route 53

1. A record - root domain, forward domain/sub domain to IPv4 address
2. Alias - route traffic to AWS resources, such as CloudFront, S3.
3. CNAME - map one domain to another, but not root domain.
4. AAAA - IPv6

### CloudFormation

- StackSets - can deploy to multiple accounts/regions with single operation
- Changeset - upcoming changes
- Nested stacks - reuse

### encryption
- SSE-S3, s3 managed keys + AES 256
- SSE-KMS, key can be customer generated and KMS managed
- SSE-C, server side encryption + client manage keys + key does not store on AWS
- Client side encryption

### Volume and Storage
- Volume gateway
		1. Stored volumes, synchronize copy ->s3, full volume to local gateway
		2. Cached Volumes, full volume ->s3, part volume to local cache.
- File Gateway(NFS, SMB)
- SSD
		1. General purpose, gp3, gp2
		2. Provisioned IOPS, io2(block express), io1
- HDD(cannot use as boot volume and multi attach)
		1. Throughout optimized, st1
		2. Cold HDD, sc1
- RDS
		1. Enhanced monitoring, metrics, cpu, memory, cheaper visibility
		2. Proxy pool share DB connections, improve performance.
		3. Multi-AZ, high availability.
- S3
		1. RTC(Replication time control), event notification <15mins
		2. WORM, vault lock policy
		3. Inventory report, audit/report replication/encryption status of objects.
		vs System manager inventory, collect metadata from EC2 and on prem.
		4. Transfer Acceleration is a bucket-level feature that enables fast, easy, and secure transfers of files over long distances between your client and an S3 bucket.
		5. Global Accelerator service does not work with S3. It only supports endpoints like application load balancers, network load balancers, EC2 instances, or elastic IP addresses.
- Data Lifecycle Manager
		1. automate the creation, retention, and deletion of Amazon Elastic Block Store (Amazon EBS) snapshots.
		2. create a lifecycle policy that includes specific tags to back up EBS volumes on a specified schedule and for a specified retention period.
- Aurora DB cluster,
		- consists of one or more DB instances and a cluster volume that manages the data for those DB instances
		-  cluster volume is a virtual database storage volume that spans multiple Availability Zones, with each Availability Zone having a copy of the DB cluster data.
	![AuroraDBCluster](../../imgs/AuroraDBCluster.png)
		Link https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html
		- backtracking an Aurora DB cluster,"rewinds" the DB cluster to the time you specify
		- the Performance Insights feature in the Amazon Aurora Serverless database which will automatically connect to a new Aurora database instance while preserving application connections.
### AD
- AWS AD, windows, VPN/ direct connect
- AD connector, trust relationship, AD->AWS
- Simple AD, LDAP

### AMI
- Linux parasitical AMI, are not supported in all AWS regions.
- Hardware VM(HVM)

### ElasticCache(in-memory data store)
- Redis, add shards, scales horizontally, support data types
	1. cluster mode enabled, means that your data and read/write access to that data is spread across multiple Redis nodes.
	2. richer data types and operations, great for leaderboard, geospatial data

- Memcached, multithread, add nodes, scaled vertically
	- key/value store faster than Redis
  1. Scaling HORIZONTALLY:
		1.1. scale out (Add Nodes to a Cluster)
		1.2. scale in (Remove Nodes from a Cluster)
  2. Scaling VERTICALLY
		2.1  scale out (create a new cluster and using a higher EC2 type)
		2.1  scale in (create a new cluster and using a lower EC2 type)
	3. does not support Multi-AZ for high availability.
	![Memcached](../../imgs/Memcached.png)
	From link https://portal.tutorialsdojo.com/courses/aws-certified-sysops-administrator-associate-practice-exams/
### Some security and other services
- WAF, SQL Injection/ Cross site scripting, filter web traffic based on IP addresses, HTTP body/headers, custom URIs
- OpsHubs, manage snow family, devices and local aws services
- OpsWorks, chef and puppet
- Control tower,create accounts via account factory, enroll account, landing zone's managment accounts.
- Artifact, report of ISO certificates and PCI.
- cloudHSM, hardware security module, 3rd party support, generated encryption keys
- Config,
- Shield, DDOS
- Shield Advanced: DDOS protecting for scaling, layer3,4 and 7
- Inspector, automated vulnerability management service that continually scans workloads for software vulnerabilities and unintended network exposure.
- GuardDuty, Intelligent threat detection.
- Cloudtrail, who to blame, log API activity, data events and file integrity validation.
- X-Ray, debug apps
- Macie, machine learning to discover, monitor and protect s3. API keys, regulatory documents.
- Glue, extract, transform, load (ETL) service, work with data lakes,redshift,RDS,crawler to populate glue catalog with tables.
- Trust Advisor, check service  usage>80%, real time guidance, cost
- Cost Explorer, view costs, usage and forecast.

### VPC and Network
- Direct connect + VPN = IPSec-encrypted private connection
- Site to site VPN = on prem + amazon VPC
- Route table and NACLs, stateless - VPC level
- Security group-> stateful, subnet level

## Others never remembered
- Enhanced Networking, provides higher bandwidth, higher packet per second (PPS) performance, and consistently lower inter-instance latencies
- Virtual Private Gateway,VPN endpoint
 ![VPG](../../imgs/VPG.png)
- CloudFront Origin Shield, an additional layer in the CloudFront caching infrastructure that helps to minimize your origin’s load, improve its availability, and reduce its operating costs. Benefits include a better cache hit ratio, better network performance, and reduced origin load.
- warm pool is a pool of pre-initialized EC2 instances that sits alongside an Auto Scaling group

## System manager
- Inventory, collects information about your instances and the software installed on them, helping you to understand your system configurations and installed applications.
- Automation, automate common and repetitive IT operations and management tasks
- Run Command, provides you safe, secure remote management of your instances at scale without logging into your servers, replacing the need for bastion hosts, SSH, or remote PowerShell


## Cloudfront
- Edge locations and local zones
- Cache statistics,
- Popular objects, what objects are frequently being accessed, and get statistics on those objects.
- Top referrers
- Usage report, the number of HTTP and HTTPS requests that CloudFront responds to from edge locations in selected regions.
- Viewers, the physical devices (desktop computers, mobile devices) and about the viewers (typically web browsers)

## Little
- By default, the enableDnsHostNames is set to false for VPCs created using the AWS CLI
- AWS Resource Access Manager (RAM) helps you securely share your resources across AWS accounts
- Step Function, provides serverless orchestration for modern applications.
- SWF,fully-managed state tracker and task coordinator service
## ALB
- Connection draining, Auto Scaling will wait for outstanding requests to complete before terminating instances.
- ASG lifecycle hook, can be used  to the auto-scaling group to pause an instance before it’s terminated.  perform custom actions during ec2 instances scale-out or scale-in.
- EC2Rescue,a troubleshooting tool that you can run on your Amazon EC2 Windows Server instances.
## IAM
- Identity based policy, attached to Identity(role, user and group)
- resource based policy, attached to resources and additional principal

---

## 中文版

### Route 53

1. A 记录——用于根域名，将域名/子域名指向 IPv4 地址
2. Alias——将流量路由到 AWS 资源，例如 CloudFront、S3
3. CNAME——将一个域名映射到另一个域名，但不能用于根域名
4. AAAA——IPv6

### CloudFormation

- StackSets——可通过单次操作部署到多个账户/区域
- Change set——即将发生的变更
- 嵌套堆栈——复用

### 加密

- SSE-S3：S3 托管密钥 + AES 256
- SSE-KMS：密钥可以由客户生成并由 KMS 管理
- SSE-C：服务器端加密 + 客户端管理密钥 + 密钥不存储在 AWS 上
- 客户端加密

### 卷与存储

- Volume Gateway
  1. Stored Volumes：将副本同步到 S3，完整卷保留在本地网关
  2. Cached Volumes：完整卷存储在 S3，部分卷保留在本地缓存
- File Gateway（NFS、SMB）
- SSD
  1. 通用型：gp3、gp2
  2. 预置 IOPS：io2（Block Express）、io1
- HDD（不能用作启动卷，也不能多重挂载）
  1. 吞吐优化型：st1
  2. Cold HDD：sc1
- RDS
  1. Enhanced Monitoring：提供指标、CPU 和内存信息，以较低成本提高可见性
  2. Proxy：池化并共享数据库连接，以提升性能
  3. Multi-AZ：高可用性
- S3
  1. RTC（Replication Time Control）：事件通知少于 15 分钟
  2. WORM、Vault Lock 策略
  3. Inventory Report：审计/报告对象的复制和加密状态；相比之下，Systems Manager Inventory 从 EC2 和本地环境收集元数据
  4. Transfer Acceleration 是存储桶级功能，可在客户端与 S3 存储桶之间进行快速、简便且安全的远距离文件传输
  5. Global Accelerator 不适用于 S3。它只支持 Application Load Balancer、Network Load Balancer、EC2 实例或 Elastic IP 地址等端点
- Data Lifecycle Manager
  1. 自动创建、保留和删除 Amazon Elastic Block Store（Amazon EBS）快照
  2. 创建生命周期策略，根据指定标签，按指定计划和保留期备份 EBS 卷
- Aurora DB 集群
  - 由一个或多个 DB 实例以及管理这些实例数据的集群卷组成
  - 集群卷是一种跨多个 Availability Zone 的虚拟数据库存储卷，每个 Availability Zone 都有一份 DB 集群数据副本
  ![AuroraDBCluster](../../imgs/AuroraDBCluster.png)
  链接：https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html
  - 对 Aurora DB 集群执行 backtracking，会将 DB 集群“倒回”到指定时间
  - Amazon Aurora Serverless 数据库中的 Performance Insights 功能会自动连接到新的 Aurora 数据库实例，同时保留应用程序连接

### AD

- AWS AD：Windows、VPN/Direct Connect
- AD Connector：信任关系，AD → AWS
- Simple AD：LDAP

### AMI

- Linux 半虚拟化 AMI 并非所有 AWS 区域都支持
- Hardware VM（HVM）

### ElastiCache（内存数据存储）

- Redis：增加分片、横向扩展、支持多种数据类型
  1. 启用集群模式意味着数据以及对数据的读写访问会分布到多个 Redis 节点
  2. 提供更丰富的数据类型和操作，非常适合排行榜和地理空间数据
- Memcached：多线程、增加节点、纵向扩展
  - 键值存储，比 Redis 更快
  1. 横向扩展：
     1.1. 扩出（向集群添加节点）
     1.2. 缩入（从集群移除节点）
  2. 纵向扩展：
     2.1. 扩大（新建集群并使用更高规格的 EC2 类型）
     2.2. 缩小（新建集群并使用更低规格的 EC2 类型）
  3. 不支持使用 Multi-AZ 实现高可用
  ![Memcached](../../imgs/Memcached.png)
  来源：https://portal.tutorialsdojo.com/courses/aws-certified-sysops-administrator-associate-practice-exams/

### 一些安全及其他服务

- WAF：SQL Injection/Cross-Site Scripting；根据 IP 地址、HTTP 正文/标头和自定义 URI 筛选 Web 流量
- OpsHub：管理 Snow Family、设备和本地 AWS 服务
- OpsWorks：Chef 和 Puppet
- Control Tower：通过 Account Factory 创建账户、注册账户以及管理 Landing Zone 的管理账户
- Artifact：ISO 证书和 PCI 报告
- CloudHSM：硬件安全模块、第三方支持、生成加密密钥
- Config
- Shield：DDoS
- Shield Advanced：用于扩展的 DDoS 防护，覆盖第 3、4 和 7 层
- Inspector：自动化漏洞管理服务，持续扫描工作负载中的软件漏洞和意外网络暴露
- GuardDuty：智能威胁检测
- CloudTrail：追踪责任方、记录 API 活动、数据事件和文件完整性验证
- X-Ray：调试应用程序
- Macie：使用机器学习发现、监控和保护 S3 中的 API 密钥及监管文档
- Glue：提取、转换和加载（ETL）服务；处理 Data Lake、Redshift 和 RDS；使用爬网程序在 Glue Catalog 中填充表
- Trusted Advisor：检查服务使用率是否超过 80%，提供实时指导和成本建议
- Cost Explorer：查看成本、使用量和预测

### VPC 与网络

- Direct Connect + VPN = 采用 IPsec 加密的私有连接
- Site-to-Site VPN = 本地环境 + Amazon VPC
- Route Table 和 NACL：无状态，VPC 级别
- Security Group：有状态，子网级别

## 其他总是记不住的内容

- Enhanced Networking：提供更高带宽、更高的每秒数据包（PPS）性能，以及持续更低的实例间延迟
- Virtual Private Gateway：VPN 端点
  ![VPG](../../imgs/VPG.png)
- CloudFront Origin Shield：CloudFront 缓存基础设施中的附加层，有助于降低源站负载、提高可用性并减少运营成本；其优势包括更高的缓存命中率、更好的网络性能和更低的源站负载
- Warm Pool：位于 Auto Scaling Group 旁的一组预初始化 EC2 实例

## Systems Manager

- Inventory：收集实例及其已安装软件的信息，帮助了解系统配置和已安装的应用程序
- Automation：自动执行常见、重复的 IT 运维和管理任务
- Run Command：无需登录服务器，即可安全地大规模远程管理实例，可替代 Bastion Host、SSH 或远程 PowerShell

## CloudFront

- Edge Location 和 Local Zone
- 缓存统计
- Popular Objects：了解哪些对象被频繁访问，并获取这些对象的统计信息
- Top Referrers
- Usage Report：CloudFront 从所选区域的 Edge Location 响应的 HTTP 和 HTTPS 请求数量
- Viewers：物理设备（台式电脑、移动设备）以及查看器（通常是 Web 浏览器）

## 零散知识

- 默认情况下，通过 AWS CLI 创建的 VPC，其 `enableDnsHostNames` 设置为 `false`
- AWS Resource Access Manager（RAM）帮助你跨 AWS 账户安全地共享资源
- Step Functions：为现代应用程序提供无服务器编排
- SWF：完全托管的状态跟踪器和任务协调服务

## ALB

- Connection Draining：Auto Scaling 会等待未完成的请求处理完毕，再终止实例
- ASG Lifecycle Hook：可让 Auto Scaling Group 在终止实例前暂停该实例，并在 EC2 实例扩出或缩入期间执行自定义操作
- EC2Rescue：可在 Amazon EC2 Windows Server 实例上运行的故障排除工具

## IAM

- 基于身份的策略：附加到身份（角色、用户和组）
- 基于资源的策略：附加到资源，并包含额外的 Principal
