# 02 - 记忆系统

## 架构设计

苦瓜 Agent 采用**双层记忆架构**：

### 1. 长期记忆 (MEMORY.md)

**位置**: `/root/.openclaw/workspace-kugua/MEMORY.md`

**用途**: 
- 重要决策
- 项目状态
- 用户偏好
- 长期待办

**更新频率**: 有重要事件时更新

**示例内容**:

```markdown
# MEMORY.md - 长期记忆

## 核心项目

### 1. 飞书机器人团队 (7个)
| 机器人 | 账号 | 部门 | 职能 |
|--------|------|------|------|
| 🥒 黄瓜 CFO | huanggua | 户部·财政司 | 财务管理 |
| 🍈 甜瓜 CMO | tiangua | 礼部·外交司 | 外交沟通 |
...

## 用户偏好

### Ya mic (@YaMic188)
- 平台: Telegram
- GitHub: Ya-MiC
- 偏好: 关注隐私和财务安全
```

---

### 2. 每日记忆 (memory/YYYY-MM-DD.md)

**位置**: `/root/.openclaw/workspace-kugua/memory/`

**用途**:
- 每日工作记录
- 临时待办
- 会话日志

**更新频率**: 每日自动创建，每2小时整理

---

## 记忆清理机制

### 定时任务: memory-consolidate

```json
{
  "name": "memory-consolidate",
  "schedule": "0 */2 * * *",
  "timezone": "Asia/Taipei",
  "action": "整理最近2小时的工作记录到 memory/YYYY-MM-DD.md 文件。压缩旧上下文，保留关键决策和待办事项。"
}
```

### 清理逻辑

1. 读取最近2小时的会话
2. 提取关键决策、待办、重要事件
3. 写入当日 memory 文件
4. 清理上下文中的冗余信息
5. 保留最近50条消息上下文

---

## 记忆检索

### 使用方法

```python
# 搜索记忆
memory_search(query="飞书机器人")

# 获取记忆片段
memory_get(path="MEMORY.md", from=1, lines=50)
```

---

## 安全约束

- **长期记忆** 仅在主会话加载
- **每日记忆** 可在群聊等共享上下文读取
- **敏感信息** 不写入记忆文件
- **用户偏好** 定期审核更新

---

## 文件结构

```
workspace-kugua/
├── MEMORY.md              # 长期记忆
├── memory/
│   ├── 2026-03-15.md      # 每日记忆
│   ├── 2026-03-16.md
│   ├── 2026-03-17.md
│   └── ...
├── AGENTS.md              # 工作区规则
├── SOUL.md                # 身份设定
└── USER.md                # 用户信息
```
