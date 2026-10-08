---
title: AWS Interview Questions
date: 2023-11-12 09:41:26
tags: [AWS, interview, codetest]
categories: work
---
## English Version

1. EBS vs. instance store (instance-local storage)
   - EBS
     - EBS volumes are persistent. EBS is suitable for databases, file systems, and any critical data that must be quickly accessible and durable.
     - It offers consistent and predictable performance.
     - The lifetime of an EBS volume is independent of the lifetime of the EC2 instance to which it may be attached.
   - Instance store
     - Volumes are ephemeral. Data on an instance store volume is lost if the instance is stopped, terminated, or fails.
     - It provides higher throughput and lower latency than EBS.
     - It is best suited for the temporary storage of frequently changing information, such as buffers and caches.
     - Cost: There is no additional cost for instance store volumes because they are included in the price of the instance itself.
     - It is available only for certain EC2 instance types and sizes.
2.

---

## 中文版

1. EBS 与 instance store（实例本地存储）的对比
   - EBS
     - EBS 卷是持久化的。EBS 适用于数据库、文件系统，以及任何需要快速访问和持久保存的关键数据。
     - 它提供稳定且可预测的性能。
     - EBS 卷的生命周期独立于其所挂载的 EC2 实例的生命周期。
   - Instance store
     - 卷是临时的。如果实例停止、终止或发生故障，instance store 卷上的数据会丢失。
     - 与 EBS 相比，它提供更高的吞吐量和更低的延迟。
     - 它最适合临时存储频繁变化的信息，例如缓冲区和缓存。
     - 成本：使用 instance store 卷无需额外付费，因为其费用已包含在实例本身的价格中。
     - 它仅适用于特定的 EC2 实例类型和大小。
2.