# 05 - 定时任务

## 当前 Cron Jobs

### 1. memory-consolidate

**用途**: 每2小时整理记忆

```json
{
  "id": "9990ea8e-3b60-4c15-a242-002ebcc28b6a",
  "name": "memory-consolidate",
  "enabled": true,
  "schedule": {
    "kind": "cron",
    "expr": "0 */2 * * *",
    "tz": "Asia/Taipei"
  },
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "整理最近2小时的工作记录到 memory/YYYY-MM-DD.md 文件。压缩旧上下文，保留关键决策和待办事项。"
  },
  "delivery": {
    "mode": "announce",
    "channel": "telegram",
    "to": "7297458680"
  }
}
```

---

### 2. taipei-weather-check

**用途**: 每日4次检查天气，有雨提醒带伞

```json
{
  "id": "cf44786a-7846-4a4b-8d44-38cecbd36710",
  "name": "taipei-weather-check",
  "enabled": true,
  "schedule": {
    "kind": "cron",
    "expr": "0 7,12,17,21 * * *",
    "tz": "Asia/Taipei"
  },
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "检查泉州丰泽区黎明职业大学天气，如果未来6小时有雨，提醒主公带伞。查询后清理历史天气数据，释放内存。"
  },
  "delivery": {
    "mode": "announce",
    "channel": "telegram",
    "to": "7297458680"
  }
}
```

---

## Cron 管理命令

### 查看所有任务

```bash
# 通过 API
curl -X GET "https://your-gateway/api/cron" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

### 添加新任务

```json
{
  "name": "task-name",
  "schedule": {
    "kind": "cron",
    "expr": "0 9 * * *",
    "tz": "Asia/Taipei"
  },
  "payload": {
    "kind": "agentTurn",
    "message": "任务内容"
  },
  "sessionTarget": "isolated",
  "delivery": {
    "mode": "announce",
    "channel": "telegram",
    "to": "user_id"
  }
}
```

### 删除任务

```bash
# 通过 API
curl -X DELETE "https://your-gateway/api/cron/{jobId}" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

---

## Schedule 类型

### 1. at - 一次性任务

```json
{
  "kind": "at",
  "at": "2026-03-26T15:00:00+08:00"
}
```

### 2. every - 间隔任务

```json
{
  "kind": "every",
  "everyMs": 3600000
}
```

### 3. cron - Cron 表达式

```json
{
  "kind": "cron",
  "expr": "0 */2 * * *",
  "tz": "Asia/Taipei"
}
```

---

## 最佳实践

1. **避免过于频繁**: 间隔至少30分钟
2. **使用时区**: 明确指定 `tz`
3. **清理历史**: 执行后清理临时数据
4. **错误处理**: 设置 `consecutiveErrors` 阈值
