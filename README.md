# 你好，我是 Juemimgcd 👋

> 我在构建真正能长期运行的 AI Agent 系统：有清晰的边界、可靠的状态、可追踪的证据，也经得起失败与攻击。

目前专注于 **Agent Runtime、长期记忆 / RAG、Agent 安全评测**。相比把模型接进一个 Demo，我更关心系统在多用户、多轮会话、异步任务、权限约束和生产故障下是否依然可靠。

[GitHub](https://github.com/juemimgcd) · [CSDN](https://blog.csdn.net/2403_88183496) · [Email](mailto:15551285402@163.com)

---

## 代表项目

### 01 · [AtlasClaw](https://github.com/CloudChef/atlasclaw)

**面向企业多系统集成的 Agent Framework。**

AtlasClaw 让用户通过一个对话入口连接 CRM、ITSM、监控、HR、财务等企业系统。它既可以嵌入现有产品，也可以作为独立的企业 Agent 平台运行；核心保持轻量，具体系统能力通过 Provider 和 Skill 扩展。

我作为开源贡献者参与项目建设，重点关注：

- Agent Runtime、工具调用、工作流编排与会话 / 记忆管理
- Provider Registry 与可插拔的企业系统集成
- REST、SSE、WebSocket、Webhook 等多入口交互
- 继承真实用户权限的执行上下文、租户边界与审计约束

`Python` `FastAPI` `Pydantic AI` `Skills` `Providers` `SSE` `WebSocket`

[查看源码 →](https://github.com/CloudChef/atlasclaw) · [项目网站 →](https://atlasclaw.ai/en/)

---

### 02 · [Memoria](https://github.com/juemimgcd/Reminder)

**面向个人长期内容沉淀的记忆与知识智能体。**

Memoria 是 Mneme 系统中的智能核心。它把文档、对话、经历和复盘转化为可检索、可治理、可追踪的长期记忆，并提供知识库问答、个人画像、关系图谱、成长分析与主动建议。

这不是一条简单的 RAG 调用链，而是一套面向长期运行设计的完整系统：

- BGE-M3 + pgvector 检索、证据选择、引用校验与可选的有界 Multi-Agent 推理
- PostgreSQL Durable Run、Redis 会话 FIFO、租约续期、事件重放与恢复
- Outbox / Inbox、Celery、Heartbeat、审批、通知和事件驱动自动化
- 记忆候选、版本、关系、删除围栏与审计组成的治理链路
- FastAPI + Vue 3 工作台，以及 Docker Compose / Nginx 生产部署

`Python` `FastAPI` `Vue 3` `PostgreSQL` `pgvector` `Redis` `Celery` `Neo4j` `Docker`

[查看源码 →](https://github.com/juemimgcd/Reminder) · [在线站点 →](https://www.mneme.com.cn)

---

### 03 · [Attacker](https://github.com/juemimgcd/Attacker)

**面向 AI Agent 的授权安全评测与 Replay 平台。**

Attacker 在明确授权的隔离环境中执行结构化攻击与安全对照用例，通过确定性 Evaluator、Policy Gate 和可恢复工作流记录证据，再从持久化事实生成 Finding、报告与 Replay 差异。

V1 已完成 30 条覆盖三种深度的评测用例：

- **纯黑盒**：Prompt Injection、系统提示泄露、敏感数据、上下文污染与资源预算
- **灰盒 Agent**：工具 / 参数越权、审批绕过、Tool Output Injection 与 Planner 循环
- **带状态 Agent**：Memory / RAG 污染、身份隔离、Checkpoint 恢复与 Replay
- Deterministic / Adaptive 双运行模式，支持 `fixed`、`new`、`persistent`、`regressed` 差异分类
- Evidence-backed Finding、人工审批、硬预算、恢复后 Policy 重校验与凭据隔离

`Python 3.12` `FastAPI` `LangGraph` `SQLAlchemy Async` `Alembic` `Pydantic` `pytest`

[查看源码 →](https://github.com/juemimgcd/Attacker)

---

## 我关注的工程问题

```text
AtlasClaw  →  如何让 Agent 安全地连接并操作真实企业系统
Memoria    →  如何让 Agent 拥有可治理、可恢复的长期记忆
Attacker   →  如何证明 Agent 在攻击、越权和状态污染下仍然可信
```

- **有界自治**：模型负责判断，Policy、预算和审批决定它可以走多远
- **证据优先**：结论来自可追踪的 Evidence，而不是不可审计的黑盒输出
- **状态可靠**：重试、恢复、幂等、事件顺序和持久化是核心能力，不是补丁
- **安全边界**：身份、权限、租户、Secret 和副作用必须在执行前得到约束
- **可运行工程**：API、Worker、数据库、可观测性、CI 和部署链路共同构成产品

## 技术栈

**Agent & AI**

`Agent Runtime` `RAG` `LangGraph` `Pydantic AI` `Embedding` `Reranker` `Multi-Agent`

**Backend & Data**

`Python` `FastAPI` `Pydantic` `SQLAlchemy Async` `PostgreSQL` `pgvector` `Redis` `Celery` `Neo4j`

**Frontend & Delivery**

`TypeScript` `Vue 3` `React` `Vite` `Docker` `Docker Compose` `Nginx` `GitHub Actions`

---

欢迎查看这些项目的源码、架构文档和演进记录。如果你也在研究 Agent Runtime、长期记忆或 AI 安全评测，欢迎交流。
