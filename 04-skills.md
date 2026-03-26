# 04 - 技能列表

## 技能架构

苦瓜 Agent 拥有**三层技能体系**：

---

## 1. 系统内置 Skills (50+)

**位置**: `/usr/lib/node_modules/openclaw/skills/`

### 核心技能

| Skill | 说明 |
|-------|------|
| `weather` | 天气查询 (wttr.in / Open-Meteo) |
| `clawhub` | 技能市场 CLI |
| `healthcheck` | 安全加固检查 |
| `node-connect` | 节点连接诊断 |
| `skill-creator` | 创建/编辑技能 |
| `github` | GitHub 操作 |
| `discord` | Discord 集成 |
| `slack` | Slack 集成 |
| `notion` | Notion 集成 |
| `obsidian` | Obsidian 笔记 |
| `trello` | Trello 看板 |
| `spotify-player` | Spotify 播放器 |
| `summarize` | 文本摘要 |
| `video-frames` | 视频帧提取 |
| `coding-agent` | 编码助手 |
| `gemini` | Gemini API |
| `openai-image-gen` | OpenAI 图像生成 |
| `openai-whisper` | 语音转文字 |
| `sherpa-onnx-tts` | 文字转语音 |

### 完整列表

```
1password
apple-notes
apple-reminders
bear-notes
blogwatcher
blucli
bluebubbles
camsnap
canvas
clawhub
coding-agent
discord
eightctl
gemini
gh-issues
gifgrep
github
gog
goplaces
healthcheck
himalaya
imsg
mcporter
model-usage
nano-banana-pro
nano-pdf
node-connect
notion
obsidian
openai-image-gen
openai-whisper
openai-whisper-api
openhue
oracle
ordercli
peekaboo
sag
session-logs
sherpa-onnx-tts
skill-creator
slack
songsee
sonoscli
spotify-player
summarize
things-mac
tmux
trello
video-frames
voice-call
wacli
weather
xurl
```

---

## 2. 飞书 Skills (9个)

**位置**: `~/.openclaw/extensions/openclaw-lark/skills/`

| Skill | 说明 |
|-------|------|
| `feishu-bitable` | 多维表格操作 |
| `feishu-calendar` | 日历管理 |
| `feishu-channel-rules` | 频道规则 |
| `feishu-create-doc` | 创建文档 |
| `feishu-fetch-doc` | 获取文档内容 |
| `feishu-im-read` | 消息读取 |
| `feishu-task` | 任务管理 |
| `feishu-troubleshoot` | 问题排查 |
| `feishu-update-doc` | 更新文档 |

---

## 3. 工作区自定义 Skills (2个)

**位置**: `/root/.openclaw/workspace-kugua/skills/`

| Skill | 说明 |
|-------|------|
| `academic-research` | 学术论文搜索 (OpenAlex API) |
| `xiaowenzhou-active-maintenance` | 系统维护脚本 |

---

## 技能使用优先级

根据用户设定：

1. **选 skill 的 skill** — 检查是否有适用技能
2. **查 skill 的 skill** — 阅读 SKILL.md 学习用法
3. **写 skill 的 skill** — 需要时创建/修改技能
4. **看记忆** — 先查 MEMORY.md 和 memory/*.md
5. **联网验证** — 确认信息正确性

---

## 技能开发指南

### SKILL.md 结构

```markdown
# SKILL.md

## 描述
技能用途说明

## 使用场景
- 场景1
- 场景2

## 参数
- param1: 说明
- param2: 说明

## 示例
示例用法
```

### 创建新技能

```bash
# 使用 skill-creator
读取 /usr/lib/node_modules/openclaw/skills/skill-creator/SKILL.md
```
