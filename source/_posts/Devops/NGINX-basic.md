---
title: NGINX Basics
date: 2023-06-30 19:05:29
tags: [DevOps, Nginx]
categories: DevOps
---
- NGINX is a reverse proxy server.

### NGINX vs Apache

![nginx](../../imgs/nginx.jpg)

### Install NGINX on macOS

- `brew install nginx`
- `brew services reload nginx`
- The configuration file is located at `/usr/local/etc/nginx/nginx.conf`.
- Use `curl -I ip/style.css` to get header information.

### Reverse proxy

- A forward proxy acts on behalf of clients, while a reverse proxy acts on behalf of servers.
- A forward proxy is a proxy server that sends requests to other servers on behalf of a client and returns the responses to that client.
- A reverse proxy is a network service that handles client requests on behalf of servers and forwards those requests to backend servers on an internal network.

---

## 中文版

- NGINX 是一款反向代理服务器。

### NGINX 与 Apache

![nginx](../../imgs/nginx.jpg)

### 在 macOS 上安装 NGINX

- `brew install nginx`
- `brew services reload nginx`
- 配置文件位于 `/usr/local/etc/nginx/nginx.conf`。
- 使用 `curl -I ip/style.css` 获取响应头信息。

### 反向代理

- 正向代理代表客户端，而反向代理代表服务器。
- 正向代理（Forward Proxy）是一种代理服务器，它代表客户端向其他服务器发送请求，并将响应返回给客户端。
- 反向代理（Reverse Proxy）是一种网络服务，它代表服务器处理客户端请求，并将这些请求转发到内部网络中的后端服务器。

