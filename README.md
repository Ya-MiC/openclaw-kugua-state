# 🦞 苦瓜 Agent 完整状态记录

> 本仓库记录了 OpenClaw 苦瓜 Agent 的完整配置、状态、记忆机制、心跳检查、技能和定时任务。  
> 可用于迁移、复现或参考。

---

## 📁 目录结构

```
openclaw-kugua-state/
├── README.md              # 本文件
├── 01-system-config.md    # 系统配置
├── 02-memory-system.md    # 记忆系统
├── 03-heartbeat.md        # 心跳机制
├── 04-skills.md           # 技能列表
├── 05-cron-jobs.md        # 定时任务
├── 06-gateway.md          # Gateway 网关
├── 07-identity.md         # 身份设定
└── 08-migration-guide.md  # 迁移指南
```

---

## 🎯 核心特性

### 1. 记忆系统
- **长期记忆**: `MEMORY.md` — 重要决策、项目状态、用户偏好
- **每日记忆**: `memory/YYYY-MM-DD.md` — 每日工作记录
- **心跳清理**: 每2小时压缩上下文，保留关键信息

### 2. 心跳机制
- **检查周期**: 每30分钟
- **检查内容**: 日历、天气、重要提醒
- **智能输出**: 有事提醒，无事发 `HEARTBEAT_OK`

### 3. 定时任务
- `memory-consolidate`: 每2小时整理记忆
- `taipei-weather-check`: 每日4次检查天气

### 4. 技能系统
- 系统内置 50+ Skills
- 飞书 Skills 9 个
- 工作区自定义 Skills 2 个

---

## 📊 当前状态快照

| 项目 | 状态 |
|------|------|
| Agent 名称 | kugua |
| 运行时长 | 稳定运行 |
| 内存占用 | ~1GB |
| Cron Jobs | 2 个 |
| Skills | 60+ |
| 记忆文件 | 持续更新 |

---

## 🔗 相关链接

- [OpenClaw 官方文档](https://docs.openclaw.ai)
- [ClawHub 技能市场](https://clawhub.com)
- [GitHub 仓库](https://github.com/Ya-MiC/openclaw-kugua-state)

---

<div align="center">

**🦞 苦瓜 Agent — 稳定、智能、持续进化**

</div>
