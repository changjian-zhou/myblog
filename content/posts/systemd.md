---
title: "Systemd"
date: 2024-11-01T17:01:48+08:00
draft: false
---



- systemd 是一种用于管理 Linux 系统和服务的初始化系统。
- 它取代了传统的 init 系统，通过并行启动和按需启动等机制显著提升了启动效率。
- systemd 负责管理和控制系统进程，可以用来启动、停止、重启服务，并提供日志记录、依赖关系管理等功能。
- 每个 systemd 单元文件通常放在 /etc/systemd/system/ 目录下，文件后缀通常为 .service（服务）、.timer（定时任务）等。

## systemd 服务单元文件例子
1. 创建服务文件

首先在 `/etc/systemd/system/` 目录下创建一个名为 `example.service` 的服务文件：



`sudo nano /etc/systemd/system/example.service`

2. 编辑服务单元文件

在 example.service 中添加以下内容：


```
[Unit]
Description=Example Python Script Service
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/python3 /home/user/example.py
Restart=on-failure
User=user
WorkingDirectory=/home/user
Environment="PYTHONUNBUFFERED=1"

[Install]
WantedBy=multi-user.target
```

解释：


- [Unit] 部分定义服务的描述以及依赖。After=network.target 表示这个服务将在网络启动后启动。
- [Service] 部分定义了服务的行为：

Type=simple 表示这个服务是一个简单的进程。

ExecStart 指定服务启动的命令（此处运行 Python 脚本）。

Restart=on-failure 表示在服务失败时自动重启。

User 指定服务运行的用户。

Environment 用来设置环境变量，PYTHONUNBUFFERED=1 可以保证 Python 输出实时显示。

- [Install] 部分定义服务的安装配置，WantedBy=multi-user.target 表示服务将在系统达到多用户模式时启动。


3. 启动并启用服务

保存文件后，执行以下命令使配置生效并启动服务：



`sudo systemctl daemon-reload`

`sudo systemctl start example.service`

要让服务在开机时自动启动，可以运行：



`sudo systemctl enable example.service`

4. 检查服务状态

使用以下命令查看服务状态：



`sudo systemctl status example.service`

5. 停止和禁用服务

要停止服务，可以运行：



`sudo systemctl stop example.service`

要禁用服务的开机自启：



`sudo systemctl disable example.service`

