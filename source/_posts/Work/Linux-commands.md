---
title: Linux commands
date: 2023-11-12 09:41:07
tags: [Linux, interview, codetest]
categories: work
---
1. tar command to archive three files to a file test.tar?
- `tar -cvf test.tar file1.txt file2.txt file3.txt
`
- -c: This option stands for "create", indicating that you're creating a new archive.
- -v: This stands for "verbose". It's optional and when used, it tells tar to list the files it's archiving. It's useful for seeing what's being included in the archive.
- -f: This option allows you to specify the name of the archive. In this case, test.tar is the name of the archive you're creating.
2. linux disk command
- -dmesg (Display Message): This command is used to examine or control the kernel ring buffer. It prints the message buffer of the kernel, which includes information about hardware devices that the kernel detects during boot, along with any drivers attached to them.
  - After booting, you can use dmesg to see messages related to hardware devices, including HDDs.
  - Running dmesg | grep sda (assuming sda is your HDD) can help you see messages related to the detection of your HDD.

- dd (Data Duplicator): This command is used for copying and converting data. It can be used to perform operations like backing up a disk's contents or copying data between different media. It is not used for detecting or listing hardware.
- du (Disk Usage): This command reports the amount of disk space used by files and directories. It is useful for monitoring disk usage but does not provide information about hardware detection.

- dc (Desk Calculator): This is a reverse-polish calculator which supports arbitrary precision arithmetic. It is not related to hardware or disk management at all.
3. iptables(a tool used for configuring the Linux kernel's netfilter firewall)
- Filter Table: The default table if no other table is specified. It is used to control the authorization of data packets to and from the system. The standard chains in the filter table are INPUT, FORWARD, and OUTPUT.

- NAT Table: This table is used for network address translation (NAT). It alters packets' source and destination addresses as they pass through. The typical chains in the NAT table are PREROUTING, POSTROUTING, and OUTPUT.

- Mangle Table: Used for specialized packet alteration. This table can be used for altering packet headers in various ways (e.g., adjusting TTL values). The chains in the mangle table include PREROUTING, INPUT, FORWARD, OUTPUT, and POSTROUTING.

- Raw Table: Used mainly for configuring exemptions from connection tracking. The chains in the raw table are PREROUTING and OUTPUT.

- Security Table: Used for Mandatory Access Control (MAC) networking rules, such as those enabled by SELinux. The chains here are INPUT, OUTPUT, and FORWARD.
4. disk commands
  - `du`: Stands for disk usage. It's used to estimate file space usage.
  - `df`: Stands for disk free. It's used to show the amount of free disk space on file systems.
  - `dc`: Stands for desktop calculator. It's an arbitrary precision calculator.

