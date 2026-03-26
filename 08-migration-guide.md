# 08 - 迁移指南

## 快速迁移

### 1. 备份当前状态

```bash
# 打包工作区
cd ~/.openclaw
tar -czf workspace-kugua-backup.tar.gz workspace-kugua/

# 打包配置
cp config.yaml config.yaml.backup
```

---

### 2. 克隆状态仓库

```bash
# 克隆
git clone https://github.com/Ya-MiC/openclaw-kugua-state.git
cd openclaw-kugua-state
```

---

### 3. 恢复配置

#### 系统配置

```bash
# 创建工作区
mkdir -p ~/.openclaw/workspace-kugua

# 复制核心文件
cp 01-system-config.md ~/.openclaw/workspace-kugua/
cp 07-identity.md ~/.openclaw/workspace-kugua/SOUL.md
```

#### 记忆系统

```bash
# 创建记忆目录
mkdir -p ~/.openclaw/workspace-kugua/memory

# 创建 MEMORY.md
touch ~/.openclaw/workspace-kugua/MEMORY.md
```

---

### 4. 配置 Cron Jobs

使用提供的 cron 配置：

```bash
# 参见 05-cron-jobs.md
# 使用 Gateway API 添加任务
```

---

### 5. 安装 Skills

#### 系统内置

```bash
# 系统自带，无需安装
```

#### 飞书 Skills

```bash
# 安装 OpenClaw Lark 扩展
# 参见官方文档
```

#### 自定义 Skills

```bash
# 克隆到工作区
cd ~/.openclaw/workspace-kugua/skills
git clone <skill-repo>
```

---

## 迁移到新 AI

### 选项 1: 同一 OpenClaw 实例

```bash
# 1. 创建新 Agent 配置
cd ~/.openclaw
cp -r workspace-kugua workspace-new-agent

# 2. 修改 config.yaml
# 3. 重启 Gateway
systemctl --user restart openclaw-gateway
```

### 选项 2: 新服务器

```bash
# 1. 安装 OpenClaw
# 2. 克隆状态仓库
# 3. 恢复配置
# 4. 启动服务
```

### 选项 3: 其他 AI 平台

```bash
# 提取核心配置：
# - 记忆系统结构
# - 心跳机制逻辑
# - 技能映射表
# - 用户偏好

# 根据平台适配
```

---

## 检查清单

### 迁移前

- [ ] 备份工作区
- [ ] 备份配置文件
- [ ] 记录 Cron Jobs
- [ ] 导出记忆文件

### 迁移后

- [ ] 验证 Gateway 运行
- [ ] 测试消息路由
- [ ] 检查 Cron Jobs
- [ ] 验证记忆系统
- [ ] 测试技能功能

---

## 故障排查

### 常见问题

#### 1. 记忆文件不加载

```bash
# 检查文件权限
chmod 644 ~/.openclaw/workspace-kugua/MEMORY.md

# 检查路径配置
cat ~/.openclaw/config.yaml | grep memory
```

#### 2. Cron Jobs 不执行

```bash
# 检查 Gateway 日志
journalctl --user -u openclaw-gateway -n 100

# 验证任务配置
curl -X GET "http://localhost:8080/api/cron"
```

#### 3. Skills 不工作

```bash
# 检查技能路径
ls -la ~/.openclaw/workspace-kugua/skills/

# 验证 SKILL.md
cat ~/.openclaw/workspace-kugua/skills/academic-research/SKILL.md
```

---

## 参考资源

- [OpenClaw 官方文档](https://docs.openclaw.ai)
- [ClawHub 技能市场](https://clawhub.com)
- [GitHub 仓库](https://github.com/Ya-MiC/openclaw-kugua-state)

---

<div align="center">

**迁移成功后，记得更新 MEMORY.md！**

</div>
