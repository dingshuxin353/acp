# ACP (Agent Communication Protocol)

让你的 AI Agent 能和其他 Agent 高质量协作，而你只负责复制转发。

ACP 是一套面向 **人类中转场景** 的 Agent 通信规范：消息结构化、可审阅、可追溯，且能跨 Claude Code / Codex / OpenClaw 使用。

## 为什么值得用

当你同时在用多个 Agent（本地开发、云端部署、测试验证、文档整理）时，常见问题是：

- 口头转述容易丢信息
- 每次都要重复解释背景
- 新 Agent 接入慢、协作不稳定

ACP 把协作过程标准化：

- **人能读**：消息是 Markdown，能先审阅再转发
- **AI 能懂**：统一 Type/From/Context 等结构，减少误解
- **上下文可裁剪**：发给对方的是“完成任务真正需要的信息”
- **协作会进化**：通过 `agent-profile` + `contacts` 持续沉淀协作记忆
- **人机团队可同步**：可以和你的人类同事/伙伴的 Agent 做结构化进度同步

## 典型场景

1. **本地开发 + 云端部署**
   - 本地 Agent 写代码
   - 云端 Agent 部署运维
   - 人类做消息中转

2. **多 Agent 分工流水线**
   - A 做方案，B 实现，C 验证
   - 通过 ACP 串成一个稳定闭环

3. **跨平台协作**
   - Claude Code、Codex、OpenClaw 混用
   - 统一通信协议，降低切换成本

4. **需要留痕和复盘**
   - 每条消息可回看
   - 适合团队协作和长期迭代

## 快速开始

把下面这句提示词直接发给你的 AI：

```text
请按以下 ACP 安装文档为当前项目完成安装，过程中每一步先向我确认再执行；优先使用 GitHub 文档，若访问受限则使用镜像链接：
GitHub: https://github.com/dingshuxin353/acp/blob/main/install.md
镜像: https://ai.weijennie.com/acp/install.md
```

安装完成后：

- Claude Code：`/agent-msg ...`
- Codex / OpenClaw：`$agent-msg ...`

## 项目结构

```text
acp/
├── install.md            # 给 AI 的安装指南
├── protocol.md           # ACP 协议定义（消息结构与类型）
├── CLAUDE.md             # ACP 运行规范（发送/接收流程）
└── agent-msg/
    └── SKILL.md          # 通信 skill
```

## ACP 的核心设计

- **消息即教程**：首次通信可附协议摘要，不懂 ACP 也能快速上手
- **AI 自动选类型**：无需人手动选择 Ask/Reply/Briefing
- **首次建联先 Introduce**：先交换名片，再进入正事
- **敏感信息默认脱敏**：避免把 key/密码等内容带出

## FAQ

### Q1: 为什么不直接让两个 Agent 自己连？
A: 很多真实场景下，跨环境直连并不稳定或不可用。ACP 假设“人类中转”是常态，优先解决今天就能落地的问题。

### Q2: 如果对方 Agent 不懂 ACP 怎么办？
A: 首次消息可自带简版协议说明，对方照格式回即可。

### Q3: ACP 只是一个消息模板吗？
A: 不止。它的价值在于“结构化 + 上下文裁剪 + 记忆沉淀”这整套协作机制。

---

如果你希望 Agent 协作从“聊天碰运气”升级到“可控、可复用、可规模化”，ACP 就是这一层通信基础设施。
