# 01 - 系统配置

## 基本信息

| 项目 | 值 |
|------|-----|
| Agent 名称 | kugua |
| 主机 | Yamic |
| 操作系统 | Linux 6.18.5-x64v2-xanmod1 (x64) |
| Node 版本 | v24.14.0 |
| 默认模型 | acym/z-ai/glm5 |
| 渠道 | Telegram |
| 时区 | Asia/Bangkok (UTC+7) |

---

## 工作区配置

```
工作目录: /root/.openclaw/workspace-kugua
```

### 核心文件

| 文件 | 说明 |
|------|------|
| `AGENTS.md` | 工作区规则 |
| `SOUL.md` | 身份设定 |
| `USER.md` | 用户信息 |
| `MEMORY.md` | 长期记忆 |
| `TOOLS.md` | 工具配置 |
| `IDENTITY.md` | 详细身份 |
| `HEARTBEAT.md` | 心跳配置 |

---

## 运行时配置

```json
{
  "runtime": "agent=kugua",
  "host": "Yamic",
  "repo": "/root/.openclaw/workspace-kugua",
  "os": "Linux 6.18.5-x64v2-xanmod1 (x64)",
  "node": "v24.14.0",
  "model": "acym/z-ai/glm5",
  "default_model": "acym/z-ai/glm5",
  "shell": "bash",
  "channel": "telegram",
  "capabilities": "inlineButtons",
  "thinking": "off"
}
```

---

## Gateway 服务

```bash
# 服务名称
openclaw-gateway.service

# 状态检查
systemctl --user status openclaw-gateway

# 启动/停止/重启
systemctl --user start openclaw-gateway
systemctl --user stop openclaw-gateway
systemctl --user restart openclaw-gateway

# 开启用户常驻模式（防止 SSH 断开后进程被回收）
loginctl enable-linger <username>
```

---

## 内存使用

```
内存占用: ~1GB
CPU 时间: 1h 33min
运行时长: 22小时+
```

---

## 授权发送者

```
授权 ID: 7297458680 (Ya mic @YaMic188)
```
