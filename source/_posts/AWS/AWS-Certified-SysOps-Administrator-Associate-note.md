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

- StackSets - can deploy to ultiple accounts/regions with single operation
- Changeset - upcoming changes
- Nested stacks - reuse

### encryption
- SSE-S3, s3 managed keys + AES 256
- SSE-KMS, key can be customer generated and KMS mannaged
- SSE-C, server side encryption + client manage keys + key isnot stored on AWS
- Client side encryption
### Some key services
- WAF, SQL Injection/ Cross site scripting
- OpsHubs, manage snow family, devices and local aws services
- Artifact, report of ISO certificates and PCI.
- cloudHSM, generated encrtyption keys
- Config,
- Shield, DDOS
- Shield Advanced: DDOS protecting for scaling, layer3,4 and 7
- Inspector, automate improve secrity assessment