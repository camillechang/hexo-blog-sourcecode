---
title: Docker Basics — Notes from Nana's Course (Unfinished)
date: 2022-08-06 20:31:15
tags: [DevOps, Docker]
categories: DevOps
---
### 1. Docker vs VM (virtualization tools)

|   |  Docker |  VM |
|---|---|---|
|  Architecture |  Virtualized application layer | Virtualized application layer + OS kernel |
|  Size |  Smaller | |
|  Speed |  Faster | |
|  Compatibility |   |  A VM with its own OS can run on any host OS |

### 2. Docker Compose

Docker Compose runs multiple services.

### 3. Volume types

1. Host volume
2. Anonymous volume
3. Named volume
   - You can reference the volume by name.
   - Named volumes should be used in production.

- Link: https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana

---

## 中文版

### 1. Docker 与 VM（虚拟化工具）

|   |  Docker |  VM |
|---|---|---|
|  架构 |  虚拟化应用层 | 虚拟化应用层 + 操作系统内核 |
|  大小 |  更小 | |
|  速度 |  更快 | |
|  兼容性 |   |  带有自身操作系统的 VM 可以在任何宿主操作系统上运行 |

### 2. Docker Compose

Docker Compose 用于运行多个服务。

### 3. Volume 类型

1. Host volume
2. Anonymous volume
3. Named volume
   - 可以通过名称引用该 volume。
   - 生产环境中应使用 named volume。

- 链接：https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana