<div align="center">

<img src="./logo.png" alt="CodexaX" width="120" />

# CodexaX

**AI 原生代码编辑器 · 基于 VS Code 二次开发**

🌐 **简体中文 ｜ [English](./README.en.md)**

[![Gitee](https://img.shields.io/badge/Gitee-codexa--x-C71D23?logo=gitee&logoColor=white)](https://gitee.com/bright-boy/codexa-x)　[![GitHub](https://img.shields.io/badge/GitHub-CodexaX-181717?logo=github&logoColor=white)](https://github.com/694475668/CodexaX)

</div>

---

> CodexaX 是一款基于 VS Code（code-oss）深度二开的 **AI 原生代码编辑器**，内置 AI 对话、智能体（Agent）、行内补全、代码库语义检索，并配套自研的多模型路由后端、账号计费体系与管理后台。**支持私有化部署。**

## 🎬 演示视频

<div align="center">

[![观看 CodexaX 演示视频](./screenshot-20260614-203611.png)](./CodexaX-demo.mp4)

▶️ **[点击观看完整演示](./CodexaX-demo.mp4)**（约 14 分钟）

</div>

## ✨ 功能特性

- 🗨️ **AI 对话**：编辑器内流式问答、上下文感知、Mermaid 图表渲染、多会话管理。
- 🤖 **智能体 Agent**：自主多步执行、工具调用、代码自动编辑与逐项回滚、后台任务。
- ⌨️ **行内补全**：基于光标前后文（FIM）的 Tab 补全，独立限流、低延迟。
- 🔍 **代码库检索（RAG）**：工作区向量索引 + 语义搜索，让 AI 理解整个项目。
- 🔀 **多模型路由**：Claude / DeepSeek / GPT / Gemini / xAI / Ollama 一键切换，统一计费。
- 👤 **账号与计费**：手机验证码登录、JWT、SSO、API Key、用量统计、月度上限、Stripe 订阅。
- 🛠️ **管理后台**：模型 / 供应商 / 用户 / 用量可视化运营。
- 🚀 **运维**：自动更新、多平台发布、私有化部署。

> 完整功能说明见：[CodexaX-产品功能说明.md](./CodexaX-产品功能说明.md)

## 📸 产品截图

### 编辑器

| | |
|---|---|
| ![编辑器主界面与多模型切换](./screenshot-20260614-203611.png) | ![设置 · 账户](./screenshot-20260614-203859.png) |
| 编辑器主界面：AI 聊天面板 + Agent 模式 + 多模型切换 | 设置 · 账户（登录态 / 套餐 / 退出） |
| ![设置 · 套餐与用量](./screenshot-20260614-203909.png) | ![设置 · MCP 工具](./screenshot-20260614-203919.png) |
| 设置 · 套餐与用量统计 | 设置 · Tools & MCP（MCP 工具市场） |
| ![设置 · 技能 Skills](./screenshot-20260614-203927.png) | ![设置 · 钩子 Hooks](./screenshot-20260614-203941.png) |
| 设置 · Skills 技能库 | 设置 · Hooks 工作区钩子脚本 |
| ![设置 · 代码库索引](./screenshot-20260614-203948.png) | |
| 设置 · Indexing 代码库索引（RAG，本地向量检索） | |

### 官网

| | |
|---|---|
| ![官网首页（英文）](./screenshot-20260614-200419.png) | ![官网首页（中文）](./screenshot-20260614-200539.png) |
| 官网首页（英文） | 官网首页（中文） |
| ![功能介绍](./screenshot-20260614-200439.png) | ![定价](./screenshot-20260614-200451.png) |
| 功能介绍：Agents / MCP / Skills / Rules / 多模型 | 定价：Free / Pro / Team |
| ![文档中心](./screenshot-20260614-200504.png) | ![企业版](./screenshot-20260614-200515.png) |
| 文档中心 | 企业版：SSO / SAML / 私有化 / 审计 |
| ![更新日志](./screenshot-20260614-200524.png) | ![登录](./screenshot-20260614-200552.png) |
| 更新日志 Changelog | 登录：手机短信验证码 / 密码 |

### 用户控制台

| | |
|---|---|
| ![控制台概览](./screenshot-20260614-200815.png) | ![API Keys](./screenshot-20260614-200835.png) |
| 控制台概览：调用次数 / Token / 消费 | API Keys 管理 |
| ![账单](./screenshot-20260614-200845.png) | |
| 账单：套餐与消费明细 | |

## 📁 仓库结构

```
.
├── vscode-src/      # 编辑器：VS Code（code-oss）二开，含 CodexaX 品牌与 AI 扩展
│   └── extensions/  #   codexax-chat（对话/Agent）、codexax-auth（登录/多模型）、theme-codexax …
├── codexax/         # 后端 monorepo（pnpm workspace）
│   ├── apps/api/    #   API 服务（Node + Hono + SQLite，端口 8787）
│   ├── apps/web/    #   官网（Next.js，端口 3000）
│   ├── apps/admin/  #   管理后台（Next.js，端口 3001）
│   ├── editor/      #   编辑器扩展源码
│   └── packages/    #   共享代码
├── 参考源码/         # 参考项目（仅研究用）
├── 截图/             # 产品截图
└── CodexaX-产品功能说明.md
```

## 🚀 快速开始（本地开发）

**环境要求**：Node.js ≥ 20、pnpm 9、（编辑器）Node 22。

**1）启动后端（API + 官网 + 后台）**
```bash
cd codexax
pnpm install
pnpm dev
# API   → http://localhost:8787
# Web   → http://localhost:3000
# Admin → http://localhost:3001
```

**2）启动编辑器（CodexaX 客户端）**
```bash
cd vscode-src
npm install            # 首次安装依赖（含原生模块编译）
npm run watch          # 持续编译（常驻，勿关）
./scripts/code.sh      # 启动编辑器
```

> 开发模式下编辑器默认连接本地 `http://localhost:8787`；如需连接生产，在设置中配置 `codexax.apiBase`。

## ⚙️ 配置

- 后端环境变量见 `codexax/.env.development` / `.env.production`（端口、`JWT_SECRET`、`DB_PATH`、短信、Stripe 等）。
- **模型与供应商**通过**管理后台**可视化配置（增删模型、密钥、定价倍率、上下架），无需改代码。
- 数据默认存于 SQLite，可平滑升级到 Postgres / pgvector。

## 📦 部署

后端（API + Web + Admin）与编辑器客户端均可独立部署：后端可用 PM2 / Docker 托管；编辑器内置自动更新服务（`/update`、`/download`），支持 macOS / Windows / Linux 出包发布。模型密钥与数据完全自控。

## 🔗 仓库地址

- Gitee：https://gitee.com/bright-boy/codexa-x
- GitHub：https://github.com/694475668/CodexaX

## 📮 联系与交流

- 微信（WeChat）：**bright1668**
- QQ：**694475668**

---

<sub>© CodexaX · 仅供演示与评估，具体能力以实际版本为准。</sub>
