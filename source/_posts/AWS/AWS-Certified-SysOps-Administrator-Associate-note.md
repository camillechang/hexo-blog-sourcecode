---
layout: aws
title: AWS Certified SysOps Administrator Associate note
date: 2022-07-23 16:11:49
tags: [AWS, Certification]
categories: AWS
---

### Route53

1. A record - root domain, forward domain/sub domain to IPv4 address
2. Alias - route traffic to AWS resources, such as CloudFront, S3.
3. CNAME - map one domain to another, but not root domaian.
4. AAAA - IPv6

### CloudFormation

- StackSets - can deploy to multiple accounts/regions with single operation
- Changeset - upcoming changes
- Nested stacks - reuse

### encryption
- SSE-S3, s3 managed keys + AES 256
- SSE-KMS, key can be customer generated and KMS mannaged
- SSE-C, server side encryption + client manage keys + key does not store on AWS
- Client side encryption

### Volume and Storage
- Volume gateway
		1. Stored volumes, asynchronise copy ->s3, full volume to local gateway
		2. Cached Volumes, full volume ->s3, part volume to local cache.
- SSD
		1. General purpose, gp3, gp2
		2. Provisioned IOPS, io2(block express), io1
- HDD(cannot use as boot volume and multi attach)
		1. Throughout optimized, st1
		2. Cold HDD, sc1
- RDS
		1. Enhaced monitoring, metrics, cpu, memory, cheaper visibilty
		2. Proxy pool share DB connections, improve performace.
		3. Multi-AZ, high avaiblity.
- S3
		1. RTC(Replication time control), event notification <15mins
		2. WORM, valut lock policy
		3. Inventory report, audit/report replicaiton/encryption status of objects.
		vs System manager inventory, collect metadata from EC2 and on prem.
- Data Lifecycle Manager
		1. automate the creation, retention, and deletion of Amazon Elastic Block Store (Amazon EBS) snapshots.
		2. create a lifecycle policy that includes specific tags to back up EBS volumes on a specified schedule and for a specified retention period.
### AD
- AWS AD, windows, VPN/ dircect connect
- AD connector, trust relationship, AD->AWS
- Simple AD, LDAP

### AMI
- Linux paravitural AMI, are not supported in all AWS regions.
- Hareware VM(HVM)

### ElasticCache
- Redis, add shards, scales horizontally, support data types
	1. cluster mode enabled, means that your data and read/write access to that data is spread across multiple Redis nodes.

- Memcached, mutithread, add nodes, scaled vertically
	1. scale up (use a node that has a larger memory footprint)
	2. scale out (add additional nodes to the cluster) to accommodate the additional data.
### Some security and other services
- WAF, SQL Injection/ Cross site scripting, filter web traffic based on IP addresses, HTTP body/headers, custom URIs
- OpsHubs, manage snow family, devices and local aws services
- Control tower,landing zone
- Artifact, report of ISO certificates and PCI.
- cloudHSM, hardware security module, 3rd party support, generated encrtyption keys
- Config,
- Shield, DDOS
- Shield Advanced: DDOS protecting for scaling, layer3,4 and 7
- Inspector, automate improve secrity assessment
- GuardDuty, Intelligent threat detection.
- Cloudtrail, who to blame, log API activity, data events and file intergrity validation.
- X-Ray, debug apps
- Macie, machine learning to discover, monitor and protect s3. API keys, regulatory documents.
- Glue, extract, transform, load (ETL) service, work with data lakes,redshift,RDS,crawer to populate glue catalog with tables.
- Trust Advisor, check service  usage>80%, real time guidance, cost
- AWS inventory, collect metedata from EC2 and on-prme

### VPC and Network
- Direct connect + VPN = IPSec-encrypted private connection
- Site to site VPN = on prem + amazon VPC