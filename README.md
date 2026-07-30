<p align="center">
  <img src="./assets/profile-hero.svg" alt="Juemimgcd — Runtime, Memory, Security" width="100%" />
</p>

<h1 align="center">你好，我是 Juemimgcd 👋</h1>

<h3 align="center">我构建的不是“会聊天的 Demo”，而是能长期运行、能够恢复、可以审计的 Agent 系统。</h3>

<p align="center">
  Agent Runtime · Long-term Memory · RAG · Multi-Agent · AI Security · Production Engineering
</p>

<p align="center">
  <a href="https://github.com/juemimgcd">GitHub</a>
  ·
  <a href="https://blog.csdn.net/2403_88183496">CSDN</a>
  ·
  <a href="mailto:15551285402@163.com">Email</a>
</p>

---

## 我构建的，不是三个互不相关的仓库

我习惯把 Agent 当作一个真实的软件系统来设计：模型只是其中的判断组件，真正决定系统能否落地的，是运行时、状态、数据、权限、证据、恢复机制和安全边界。

这三个项目恰好覆盖了我最关心的完整工程链路：

<table>
  <tr>
    <td width="33%" valign="top">
      <strong>⚙️ Runtime / Integration</strong><br/><br/>
      Agent 如何连接真实企业系统，组织 Skills、Tools、Providers、Sessions 与 Workflows，并继承用户的真实权限。
    </td>
    <td width="33%" valign="top">
      <strong>🧠 Memory / Intelligence</strong><br/><br/>
      Agent 如何拥有可检索、可治理、可恢复的长期记忆，并在多轮会话和异步任务中保持上下文连续。
    </td>
    <td width="33%" valign="top">
      <strong>🛡️ Security / Verification</strong><br/><br/>
      如何用确定性策略、攻击用例、Evidence 与 Replay，证明 Agent 没有越权、泄露、污染或绕过审批。
    </td>
  </tr>
</table>

```text
AtlasClaw  →  建立 Agent Runtime 与企业系统连接能力
Memoria    →  建立长期记忆、知识治理与可恢复执行能力
Attacker   →  建立攻击评测、证据闭环与安全验证能力
```

---

## 01 / AtlasClaw

### [Enterprise Agent Framework for multi-system integration](https://github.com/CloudChef/atlasclaw)

> 让企业员工通过一个对话入口，安全地查询数据、触发工作流并操作多个现有系统。

| 我的角色 | 项目定位 | 运行模式 | Links |
|---|---|---|---|
| Open-source Contributor | 企业级 Agent Framework | Embedded / Standalone | [Repository](https://github.com/CloudChef/atlasclaw) · [Website](https://atlasclaw.ai/en/) |

企业软件往往被分散在 CRM、ITSM、监控、HR、财务、OA 等系统中。难点不仅是“接一个 API”，而是不同系统拥有完全不同的数据模型、权限体系、审计逻辑和工作流边界。

AtlasClaw 在这些系统之上提供统一的 Agent 层：

```text
Web UI / Embedded Panel / Chat Platform / Webhook
                         ↓
              API & Channel Adapters
                         ↓
        Session · Memory · Agent Engine · Workflow
                         ↓
             Skills · Tools · Provider Registry
                         ↓
       CRM · ITSM · Monitoring · HR · Finance · OA
```

### 我参与和关注的核心方向

- **Thin Core + Rich Providers**：核心只负责通用运行时，认证、技能和系统脚本留在 Provider 中，避免把平台逻辑堆进 Agent Runner。
- **Skills 驱动的业务能力**：Skills 描述业务场景、决策边界与工具使用方式，让模型在受控范围内完成分析、协调和执行。
- **统一的交互入口**：REST、SSE、WebSocket 与 Webhook 共同服务于人机对话、嵌入式 Agent 和程序化自动化。
- **真实权限继承**：执行动作沿用已认证用户在目标系统中的权限，不通过 Agent 绕过 RBAC，也不把平台审计搬到黑盒里。
- **可替换的模型与集成层**：模型 Provider、企业系统 Provider、Tools 与 Skills 都可以独立扩展，让框架适配不同组织的技术栈。

### 为什么这个项目重要

AtlasClaw 让我从“实现一个 Agent 功能”进一步走向“设计一套可以被不同企业系统复用的 Agent 基础设施”。我更关注的不只是一次回答是否正确，而是身份如何传递、权限如何约束、会话如何持续、工具如何注册、失败如何暴露，以及新的系统如何低成本接入。

**Core Stack**

`Python` `FastAPI` `Pydantic AI` `Provider Registry` `Skills` `Tools` `Workflow` `SSE` `WebSocket`

---

## 02 / Memoria

### [A durable memory and knowledge system for personal AI](https://github.com/juemimgcd/Reminder)

> 把文档、对话、经历和复盘沉淀为可检索、可治理、可追踪的长期记忆，让 Agent 真正拥有连续性。

| 项目形态 | 核心定位 | 在线系统 | Links |
|---|---|---|---|
| Full-stack AI Application | 长期记忆 + RAG + Durable Agent | Mneme / Memoria | [Repository](https://github.com/juemimgcd/Reminder) · [Live](https://www.mneme.com.cn) |

Memoria 是 Mneme 系统中的智能核心。它不只是“上传文档后问问题”，而是围绕个人长期内容建立完整的数据与运行闭环：知识库、文档、Chunk、Evidence、记忆候选、正式记忆、版本、关系、画像、成长报告和建议都拥有明确的数据归属与生命周期。

### 一条能够长期运行的 RAG / Memory 链路

```text
Browser / API
      ↓
Mneme FastAPI ───────────────→ PostgreSQL Durable Run
      │                               ↓
      ├─ Document Pipeline      Redis Session FIFO
      ├─ Outbox / Inbox               ↓
      └─ Task Records            Memoria Agent API
                                      ↓
                     Retrieval · Evidence · Answer
                          ↓          ↓          ↓
                       pgvector   PostgreSQL   Neo4j
```

### 已经形成的系统能力

- **完整知识链路**：文档上传、解析、切分、索引、召回、Rerank、回答生成和引用校验形成闭环。
- **长期记忆治理**：记忆候选、Canonical Memory、Revision、Relation、删除围栏和操作审计共同维护记忆质量与隐私边界。
- **Durable Agent Run**：运行记录持久化在 PostgreSQL，Redis 只承担协调；支持租约、重试、取消、事件重放和故障恢复。
- **可控制的会话演进**：支持 `interrupt`、`followup` 与 `steer`，每次控制都会形成独立的 Run / Trace 关联，而不是修改正在执行的黑盒 Prompt。
- **显式 Multi-Agent 选择**：默认保留单 Agent 快速路径；只有用户选择后才启用有界 Multi-Agent 检索，由固定角色并行取证并通过 EvidenceJudge 收敛证据。
- **安全的有界推理**：统一限制检索范围、Top-K、模型调用次数、Token、成本、全局截止时间和补充轮次，不允许递归生成新的 Agent。
- **事件驱动工程**：PostgreSQL Outbox / Inbox、Celery、Heartbeat、审批、通知、自动化和 Dead Letter 使跨系统副作用可以重试并追踪。
- **模型韧性与上下文治理**：支持主备模型、瞬时重试、Provider Cooldown、有界上下文压缩以及不泄露正文的公共运行事件。
- **生产可观测性**：统一 Request / Run / Event 关联，提供 Health、Readiness、Prometheus Metrics、告警规则和运维 Runbook。

### 我在 Memoria 中真正想解决的问题

长期记忆系统最难的部分，不是向量相似度，而是“这条记忆属于谁、来自哪里、是否仍然有效、删除后会不会被迟到事件重新写回、失败重试会不会产生重复副作用”。因此 Memoria 把 Ownership、Evidence、Idempotency、Ordering、Deletion Fence 和 Audit 当成核心模型，而不是后期补丁。

**Core Stack**

`Python` `FastAPI` `Vue 3` `PostgreSQL` `pgvector` `Redis` `Celery` `Neo4j` `BGE-M3` `Docker Compose`

---

## 03 / Attacker

### [Evidence-backed security evaluation for AI Agents](https://github.com/juemimgcd/Attacker)

> 在明确授权的隔离环境中，用可重复攻击、确定性策略和持久化证据评测 Agent，而不是依赖一次性的人工判断。

| 当前版本 | 评测模式 | 证据与报告 | Link |
|---|---|---|---|
| V1 complete | Deterministic / Adaptive | Finding / Report / Replay | [Repository](https://github.com/juemimgcd/Attacker) |

Attacker 把 AI Agent 安全评测建模为一条严格受控的工作流：

```text
Target + Dataset + Policy
          ↓
     Evaluation Run
          ↓
 Policy Gate / Approval / Budget
          ↓
 Evidence Event → Finding → JSON / Markdown Report
          ↓
 Replay → fixed / new / persistent / regressed
```

### V1：三种深度、30 条攻击与安全对照

| 阶段 | 用例数 | 评测范围 | 关键证据 |
|---|---:|---|---|
| **纯黑盒** | 12 | Prompt Injection、系统提示泄露、敏感数据、上下文污染、资源消耗 | Request / Response / Evaluator |
| **灰盒 Agent** | 10 | 工具越权、危险参数、审批绕过、Tool Output Injection、Planner 循环 | Tool / Policy / Approval Trace |
| **带状态 Agent** | 8 | Memory / RAG 污染、跨身份污染、Checkpoint 恢复、Replay | Memory / Retrieval / Checkpoint Event |
| **合计** | **30** | 每个阶段同时包含攻击样例与正常或安全拒绝对照 | Evidence-backed Finding |

### 这个项目的工程重点

- **Deterministic Core, Agentic Orchestration**：LangGraph 可以提出下一步，但 Target、Case、Tool、审批、预算和停止条件始终由确定性 Core 决定。
- **Policy Before Execution**：所有 Target 与 Tool 调用先经过 Policy Gate；高风险动作没有审批就不能产生副作用。
- **Evidence Before Claims**：每个 Finding 必须引用持久化 Evidence，报告可以只依赖业务数据库重建，不依赖模型上下文。
- **Bounded Autonomy**：调用次数、物理 Provider 尝试、Token、成本、持续时间和响应大小都有硬预算。
- **Safe Recovery**：Checkpoint 恢复后重新执行 Policy 校验，不重复模型请求、Target 调用或 Finding。
- **Replay Diff**：固定 Dataset 与 Policy，对修复前后的目标执行 Replay，并区分 `fixed`、`new`、`persistent` 与 `regressed`。
- **Secret Separation**：凭据不写入事件、报告、运行快照或 Checkpoint；恢复和 Replay 时必须重新提供运行时 Target。
- **Default-safe Target Policy**：默认拒绝未明确授权的公网或不可解析目标，项目仅面向授权测试与隔离环境。

Attacker 关注的不是“能不能让模型攻击成功”，而是如何让一次安全发现具备完整的可重复性、授权记录、执行证据和修复对比，从而真正进入工程评审与持续验证流程。

**Core Stack**

`Python 3.12` `FastAPI` `LangGraph` `Pydantic` `SQLAlchemy Async` `Alembic` `SQLite / PostgreSQL` `pytest` `Pyright`

---

## 三个项目背后的统一方法

| 原则 | 我的工程取向 |
|---|---|
| **Model proposes, system decides** | 模型可以分析和提出动作，但 Policy、Schema、预算与审批决定什么能够执行。 |
| **Durable facts over volatile context** | 数据库事实负责恢复和审计，Redis 与 Checkpoint 负责协调，不把易失状态当作最终真相。 |
| **Evidence before confidence** | 回答、记忆和安全 Finding 都必须能回到来源、事件和证据。 |
| **Failure is part of the design** | 从一开始设计幂等、重试、租约、顺序、取消、Dead Letter 和恢复，而不是上线后再补。 |
| **Security before side effects** | 身份、租户、权限、Secret、Target 与工具参数必须在副作用发生前被约束。 |
| **Production is the whole chain** | API、Worker、数据迁移、可观测性、CI、容器、部署和 Runbook 都属于产品能力。 |

## 技术版图

| Layer | Technologies | What I build |
|---|---|---|
| **Agent Runtime** | LangGraph, Pydantic AI, Skills, Tools, Providers | 路由、状态机、工具调用、工作流、审批与有界自治 |
| **RAG & Memory** | BGE-M3, pgvector, Reranker, Neo4j | 检索、证据、引用、记忆治理、画像与关系 |
| **Backend** | Python, FastAPI, Pydantic, SQLAlchemy Async, Alembic | API Contract、领域模型、事务、幂等与服务边界 |
| **Async & Data** | PostgreSQL, Redis, Celery, Outbox / Inbox | Durable Run、任务队列、事件投递、恢复与一致性 |
| **Frontend** | TypeScript, Vue 3, React, Vite | Agent 工作台、流式交互、运行状态与可视化 |
| **Security & Quality** | Policy Gate, Replay, pytest, Ruff, Pyright | 授权评测、Evidence、静态检查、行为验证与 CI |
| **Delivery** | Docker, Docker Compose, Nginx, GitHub Actions | 环境编排、部署、健康检查、监控与运维 |

## 现在仍在推进

- 扩展 AtlasClaw 的 Provider / Skill 生态与企业集成边界
- 继续完善 Memoria 的上下文治理、长期记忆质量与可验证推理
- 推进 Attacker 的安全装备生态、持续评测和生产化基础
- 持续记录 Agent、RAG、系统设计与项目演进中的真实工程问题

---

<h3 align="center">Build the runtime. Give it memory. Prove it is safe.</h3>

<p align="center">
  如果你也在研究 Agent Runtime、长期记忆、RAG 或 AI 安全评测，欢迎交流。
</p>

<p align="center">
  <a href="https://github.com/juemimgcd">Explore my repositories</a>
  ·
  <a href="https://blog.csdn.net/2403_88183496">Read my notes</a>
  ·
  <a href="mailto:15551285402@163.com">Get in touch</a>
</p>
