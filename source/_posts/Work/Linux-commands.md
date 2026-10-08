---
title: Essential Linux Commands
date: 2023-11-12 09:41:07
tags: [Linux, interview, codetest]
categories: work
---
## English Version

1. How do you use the `tar` command to archive three files into `test.tar`?
   - `tar -cvf test.tar file1.txt file2.txt file3.txt`
   - `-c`: This option stands for “create,” indicating that you are creating a new archive.
   - `-v`: This stands for “verbose.” It is optional; when used, it tells `tar` to list the files being archived. It is useful for seeing what the archive includes.
   - `-f`: This option lets you specify the archive's name. In this case, `test.tar` is the name of the archive being created.
2. Linux disk commands:
   - `dmesg` (Display Message): This command examines or controls the kernel ring buffer. It prints the kernel's message buffer, including information about hardware devices detected during boot and any drivers attached to them.
     - After booting, use `dmesg` to see messages related to hardware devices, including HDDs.
     - Running `dmesg | grep sda`, assuming `sda` is your HDD, can help you see messages related to its detection.
   - `dd` (Data Duplicator): This command copies and converts data. It can perform operations such as backing up a disk's contents or copying data between different media. It is not used to detect or list hardware.
   - `du` (Disk Usage): This command reports the disk space used by files and directories. It is useful for monitoring disk usage but does not provide hardware-detection information.
   - `dc` (Desk Calculator): This reverse-Polish notation calculator supports arbitrary-precision arithmetic. It is unrelated to hardware or disk management.
3. `iptables` is a tool for configuring the Linux kernel's netfilter firewall.
   - Filter Table: The default table when no other table is specified. It controls the authorization of data packets to and from the system. Its standard chains are INPUT, FORWARD, and OUTPUT.
   - NAT Table: This table performs network address translation (NAT). It alters packets' source and destination addresses as they pass through. Its typical chains are PREROUTING, POSTROUTING, and OUTPUT.
   - Mangle Table: Used for specialized packet alteration. It can modify packet headers in various ways, such as adjusting TTL values. Its chains include PREROUTING, INPUT, FORWARD, OUTPUT, and POSTROUTING.
   - Raw Table: Used mainly to configure exemptions from connection tracking. Its chains are PREROUTING and OUTPUT.
   - Security Table: Used for Mandatory Access Control (MAC) networking rules, such as those enabled by SELinux. Its chains are INPUT, OUTPUT, and FORWARD.
4. Disk commands:
   - `du`: Stands for disk usage. It estimates file-space usage.
   - `df`: Stands for disk free. It shows the amount of free disk space on file systems.
   - `dc`: Stands for desktop calculator. It is an arbitrary-precision calculator.

---

## 中文版

1. 如何使用 `tar` 命令将三个文件归档到 `test.tar`？
   - `tar -cvf test.tar file1.txt file2.txt file3.txt`
   - `-c`：此选项代表“create”，表示创建一个新的归档文件。
   - `-v`：此选项代表“verbose”。它是可选的；使用后，`tar` 会列出正在归档的文件，便于查看归档中包含哪些内容。
   - `-f`：此选项用于指定归档文件的名称。在本例中，`test.tar` 是正在创建的归档文件名。
2. Linux 磁盘命令：
   - `dmesg`（Display Message）：此命令用于检查或控制内核环形缓冲区。它会输出内核的消息缓冲区，其中包括内核在启动期间检测到的硬件设备信息，以及连接到这些设备的驱动程序。
     - 启动后，可以使用 `dmesg` 查看与硬件设备（包括 HDD）相关的消息。
     - 假设 `sda` 是你的 HDD，运行 `dmesg | grep sda` 可以帮助你查看与该 HDD 检测有关的消息。
   - `dd`（Data Duplicator）：此命令用于复制和转换数据。它可以执行备份磁盘内容或在不同介质之间复制数据等操作。它不用于检测或列出硬件。
   - `du`（Disk Usage）：此命令报告文件和目录占用的磁盘空间。它适合监控磁盘使用情况，但不提供硬件检测信息。
   - `dc`（Desk Calculator）：这是一个支持任意精度算术的逆波兰表示法计算器，与硬件或磁盘管理完全无关。
3. `iptables` 是用于配置 Linux 内核 netfilter 防火墙的工具。
   - Filter Table：未指定其他表时使用的默认表。它用于控制进出系统的数据包授权。其标准链为 INPUT、FORWARD 和 OUTPUT。
   - NAT Table：此表用于网络地址转换（NAT）。数据包经过时，它会更改数据包的源地址和目标地址。其典型链为 PREROUTING、POSTROUTING 和 OUTPUT。
   - Mangle Table：用于特殊的数据包修改。此表可以用多种方式修改数据包头，例如调整 TTL 值。其链包括 PREROUTING、INPUT、FORWARD、OUTPUT 和 POSTROUTING。
   - Raw Table：主要用于配置连接跟踪的豁免。其链为 PREROUTING 和 OUTPUT。
   - Security Table：用于强制访问控制（MAC）网络规则，例如由 SELinux 启用的规则。其链为 INPUT、OUTPUT 和 FORWARD。
4. 磁盘命令：
   - `du`：代表 disk usage，用于估算文件空间使用量。
   - `df`：代表 disk free，用于显示文件系统上的可用磁盘空间。
   - `dc`：代表 desktop calculator，是一个任意精度计算器。

