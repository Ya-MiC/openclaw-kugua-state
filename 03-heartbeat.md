# 03 - 心跳机制

## 概述

苦瓜 Agent 使用**智能心跳机制**，定期检查重要事项，避免频繁打扰用户。

---

## 心跳配置

### HEARTBEAT.md

```markdown
# HEARTBEAT.md

# 保持此文件为空（或仅包含注释）以跳过心跳 API 调用。
# 在下方添加任务，当需要 Agent 定期检查某些事项时使用。
```

### 心跳提示

```
Read HEARTBEAT.md if it exists (workspace context). 
Follow it strictly. 
Do not infer or repeat old tasks from prior chats. 
If nothing needs attention, reply HEARTBEAT_OK.
```

---

## 心跳行为

### 有事时

- 发送提醒消息
- 包含具体内容和行动建议
- 不包含 `HEARTBEAT_OK`

### 无事时

- 回复: `HEARTBEAT_OK`
- OpenClaw 自动识别并丢弃心跳确认
- 不打扰用户

---

## 心跳检查内容（建议轮换）

### 每2-4小时检查一次

1. **日历检查**
   - 未来24-48小时是否有会议/日程
   - 重要日期提醒

2. **天气检查**
   - 未来6小时是否有雨
   - 极端天气预警

3. **消息检查**
   - 重要未读消息
   - 提及通知

4. **项目状态**
   - Git 仓库状态
   - 待提交更改

---

## 心跳状态追踪

### 文件: memory/heartbeat-state.json

```json
{
  "lastChecks": {
    "email": 1703275200,
    "calendar": 1703260800,
    "weather": null
  }
}
```

---

## 心跳 vs Cron

| 场景 | 心跳 | Cron |
|------|------|------|
| 多任务批量检查 | ✅ | ❌ |
| 需要会话上下文 | ✅ | ❌ |
| 精确时间触发 | ❌ | ✅ |
| 独立任务执行 | ❌ | ✅ |

---

## 最佳实践

1. **轮换检查**: 不要每次心跳都检查所有内容
2. **智能判断**: 有重要事件才提醒
3. **避免打扰**: 深夜 (23:00-08:00) 除非紧急不提醒
4. **状态记录**: 记录上次检查时间，避免重复
