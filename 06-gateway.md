# 06 - Gateway 网关

## 概述

OpenClaw Gateway 是苦瓜 Agent 的核心服务，负责消息路由、会话管理、插件协调。

---

## 服务管理

### Systemd 服务

```bash
# 服务名称
openclaw-gateway.service

# 查看状态
systemctl --user status openclaw-gateway

# 启动
systemctl --user start openclaw-gateway

# 停止
systemctl --user stop openclaw-gateway

# 重启
systemctl --user restart openclaw-gateway

# 查看日志
journalctl --user -u openclaw-gateway -f
```

### 用户常驻模式

```bash
# 开启（防止 SSH 断开后进程被回收）
loginctl enable-linger <username>

# 检查状态
ls /var/lib/systemd/linger/
```

---

## 当前状态

```
● openclaw-gateway.service - OpenClaw Gateway (v2026.3.8)
   Loaded: loaded
   Active: active (running)
   运行时长: 22小时+
   内存: 1006.7M
   CPU: 1h 33min
```

---

## 配置文件

### 位置

```
~/.openclaw/config.yaml
```

### 主要配置

```yaml
# 基本配置
agent:
  name: kugua
  model: acym/z-ai/glm5

# 渠道配置
channels:
  - type: telegram
    token: YOUR_BOT_TOKEN
    chat_id: "7297458680"

# 记忆配置
memory:
  backend: qmd
  path: /root/.openclaw/workspace-kugua/memory

# Gateway 配置
gateway:
  bind: 0.0.0.0
  port: 8080
```

---

## API 端点

### Cron 管理

```
GET  /api/cron           # 列出所有任务
POST /api/cron           # 添加任务
DELETE /api/cron/{id}    # 删除任务
POST /api/cron/{id}/run  # 立即执行
```

### 会话管理

```
GET  /api/sessions       # 列出会话
POST /api/sessions       # 创建会话
```

---

## 自我更新

### 更新方式

```bash
# 使用 gateway 工具
gateway action=update.run

# 或手动更新
cd ~/.openclaw
git pull
npm install
systemctl --user restart openclaw-gateway
```

---

## 故障排查

### 常见问题

1. **服务无法启动**
   ```bash
   # 检查端口占用
   lsof -i :8080
   
   # 检查配置
   cat ~/.openclaw/config.yaml
   ```

2. **内存泄漏**
   ```bash
   # 重启服务
   systemctl --user restart openclaw-gateway
   ```

3. **消息无法送达**
   ```bash
   # 检查渠道配置
   # 检查网络连接
   # 查看 Gateway 日志
   journalctl --user -u openclaw-gateway -n 100
   ```
