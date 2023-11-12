---
title: AWS Interview questions
date: 2023-11-12 09:41:26
tags: [AWS, interview, codetest]
categories: work
---
1. EBS vs instance store(instance local store)
- EBS
  - EBS volumes are persistent, EBS is suitable for databases, file systems, and storing any critical data that needs to be quickly accessible and requires durability.
  - Offers consistent and predictable performance.
  - the lifetime of a EBS volume is independent of the lifetime of an EC2 instance to which it may be attached.
- Instance store
  - Volumes are ephemeral. Data on an instance store volume is lost if the instance is stopped, terminated, or if it fails.
  - Provides higher throughput and lower latency compared to EBS
  - Best suited for temporary storage of information that changes frequently, such as buffers, caches
  - Cost: there is no additional cost for using instance store volumes as they are included in the price of the instance itself.
  - Only available for certain EC2 instance types and sizes.
2.