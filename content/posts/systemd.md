---
title: "Systemd"
date: 2024-11-01T17:01:48+08:00
draft: false
---

- `systemd` 是一种用于管理 Linux 系统和服务的**初始化系统**。
- 每个 `systemd` 单元文件通常放在 `/etc/systemd/system/` 目录下，文件后缀通常为 `.service`（服务）、`.timer`（定时任务）等。

---

## systemd 服务单元文件例子

## 1. 创建服务文件

首先在 `/etc/systemd/system/` 目录下创建一个名为 `example.service` 的服务文件：

```bash
sudo nano /etc/systemd/system/example.service
```

---

## 2. 编辑服务单元文件

在 `example.service` 中添加以下内容：

```ini
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

### 📌 配置解析：

- **[Unit]**
    - `Description`：服务描述
    - `After=network.target`：服务将在网络启动后启动

- **[Service]**

    - `Type=simple`：表示这是一个简单的进程
    - `ExecStart`：执行 Python 脚本
    - `Restart=on-failure`：如果服务失败，自动重启
    - `User`：指定运行该服务的用户
    - `Environment="PYTHONUNBUFFERED=1"`：确保 Python 输出实时显示

- **[Install]**
    - `WantedBy=multi-user.target`：该服务将在多用户模式下启动

---

## 3. 启动并启用服务

保存文件后，执行以下命令使配置生效并启动服务：

```bash
sudo systemctl daemon-reload
sudo systemctl start example.service
```

让服务在 **开机时自动启动**：

```bash
sudo systemctl enable example.service
```

---

## 4. 检查服务状态

运行以下命令查看服务状态：

```bash
sudo systemctl status example.service
```

---

## 5. 停止和禁用服务

**停止服务**：

```bash
sudo systemctl stop example.service
```

**禁用服务开机自启**：

```bash
sudo systemctl disable example.service
```

---



