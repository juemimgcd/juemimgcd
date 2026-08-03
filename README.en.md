<p align="center">
  <img src="./assets/profile-hero.svg" alt="Juemimgcd — Runtime, Memory, Security" width="100%" />
</p>

<p align="center">
  <a href="./README.md">简体中文</a>
  ·
  <a href="./README.zh-TW.md">繁體中文</a>
  ·
  <strong>English</strong>
  ·
  <a href="./README.ja.md">日本語</a>
  ·
  <a href="./README.fr.md">Français</a>
</p>

<h1 align="center">Hi, I'm Juemimgcd 👋</h1>

<h3 align="center">I build Agent systems that run for the long term, recover from failure, and remain auditable—not chat demos.</h3>

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

## One engineering story, not three unrelated repositories

I treat an Agent as a real software system. The model is one decision-making component; the runtime, state, data ownership, permissions, evidence, recovery, and safety boundaries determine whether the system can actually ship.

My three main projects cover that end-to-end path:

<table>
  <tr>
    <td width="33%" valign="top">
      <strong>⚙️ Runtime / Integration</strong><br/><br/>
      Connect Agents to real enterprise systems through Skills, Tools, Providers, Sessions, and Workflows while preserving the user's actual permissions.
    </td>
    <td width="33%" valign="top">
      <strong>🧠 Memory / Intelligence</strong><br/><br/>
      Build searchable, governable, and recoverable long-term memory that keeps context coherent across conversations and asynchronous work.
    </td>
    <td width="33%" valign="top">
      <strong>🛡️ Security / Verification</strong><br/><br/>
      Use deterministic policy, attack cases, Evidence, and Replay to prove that an Agent did not overreach, leak, poison state, or bypass approval.
    </td>
  </tr>
</table>

```text
AtlasClaw  →  Agent runtime and enterprise integration
Memoria    →  Long-term memory, knowledge governance, and durable execution
Attacker   →  Adversarial evaluation, evidence closure, and security verification
```

---

## 01 / AtlasClaw

### [Enterprise Agent Framework for multi-system integration](https://github.com/CloudChef/atlasclaw)

> A secure conversational entry point for employees to query data, trigger workflows, and operate across existing enterprise systems.

| My role | Positioning | Runtime modes | Links |
|---|---|---|---|
| Open-source Contributor | Enterprise Agent Framework | Embedded / Standalone | [Repository](https://github.com/CloudChef/atlasclaw) · [Website](https://atlasclaw.ai/en/) |

Enterprise software is fragmented across CRM, ITSM, monitoring, HR, finance, and office automation. The hard part is not calling one more API; it is reconciling different data models, identities, permissions, audit rules, and workflow boundaries.

AtlasClaw provides a unified Agent layer above those systems:

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

### What I contribute to and care about

- **Thin Core + Rich Providers**: keep generic runtime concerns in the core and leave authentication, domain skills, and system scripts in Providers.
- **Skills as business capabilities**: describe business scenarios, decision boundaries, and tool usage so the model acts within an explicit operating envelope.
- **Unified interaction surfaces**: REST, SSE, WebSocket, and Webhook serve human conversations, embedded Agents, and programmatic automation.
- **Real permission inheritance**: actions execute with the authenticated user's permissions in the target system; the Agent does not bypass RBAC or hide platform audit trails.
- **Replaceable model and integration layers**: model Providers, enterprise Providers, Tools, and Skills evolve independently.

AtlasClaw moved my focus from implementing individual Agent features to designing reusable Agent infrastructure: identity propagation, permission enforcement, session continuity, tool registration, explicit failure, and low-cost integration of new systems.

**Core Stack**

`Python` `FastAPI` `Pydantic AI` `Provider Registry` `Skills` `Tools` `Workflow` `SSE` `WebSocket`

---

## 02 / Memoria

### [A durable memory and knowledge system for personal AI](https://github.com/juemimgcd/Reminder)

> Turn documents, conversations, experiences, and reflection into searchable, governable, and traceable long-term memory.

| Product shape | Core focus | Live system | Links |
|---|---|---|---|
| Full-stack AI Application | Long-term Memory + RAG + Durable Agent | Mneme / Memoria | [Repository](https://github.com/juemimgcd/Reminder) · [Live](https://www.mneme.com.cn) |

Memoria is the intelligence core of Mneme. It is more than “upload a document and ask questions.” Knowledge bases, documents, chunks, evidence, memory candidates, canonical memories, revisions, relations, profiles, growth reports, and recommendations all have explicit ownership and lifecycles.

### A durable RAG and memory path

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

### System capabilities

- **Complete knowledge pipeline**: upload, parse, chunk, index, retrieve, rerank, generate, and validate citations as one traceable flow.
- **Long-term memory governance**: memory candidates, canonical memory, revisions, relations, deletion fences, and operational audit protect quality and privacy.
- **Durable Agent Runs**: PostgreSQL stores execution facts while Redis coordinates; leases, retries, cancellation, replay, and recovery are first-class behavior.
- **Controllable conversation evolution**: `interrupt`, `followup`, and `steer` create explicit Run and Trace relationships instead of mutating an opaque in-flight prompt.
- **Explicit Multi-Agent choice**: the fast single-Agent path remains the default; bounded parallel evidence gathering starts only when the user selects it.
- **Bounded reasoning**: retrieval scope, Top-K, provider calls, tokens, cost, deadlines, and follow-up rounds all have hard limits.
- **Event-driven delivery**: PostgreSQL Outbox / Inbox, Celery, Heartbeat, approvals, notifications, automation, and Dead Letter make side effects retryable and observable.
- **Model resilience and context governance**: primary/fallback models, transient retries, provider cooldown, bounded compaction, and public events that do not leak content.
- **Production observability**: Request / Run / Event correlation, health, readiness, Prometheus metrics, alert rules, and operational runbooks.

The hardest memory problem is not vector similarity. It is ownership, provenance, validity, deletion semantics, late events, duplicate side effects, and ordering. Memoria therefore treats Ownership, Evidence, Idempotency, Ordering, Deletion Fence, and Audit as core domain concepts.

**Core Stack**

`Python` `FastAPI` `Vue 3` `PostgreSQL` `pgvector` `Redis` `Celery` `Neo4j` `BGE-M3` `Docker Compose`

---

## 03 / Attacker

### [Evidence-backed security evaluation for AI Agents](https://github.com/juemimgcd/Attacker)

> Evaluate Agents in explicitly authorized, isolated environments through repeatable attacks, deterministic policy, and durable evidence.

| Status | Evaluation modes | Evidence and reporting | Link |
|---|---|---|---|
| V1 complete | Deterministic / Adaptive | Finding / Report / Replay | [Repository](https://github.com/juemimgcd/Attacker) |

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

### Three evaluation depths

| Stage | Scope | Primary evidence |
|---|---|---|
| **Black-box** | Prompt injection, prompt leakage, sensitive data, context pollution, resource limits | Request / Response / Evaluator |
| **Gray-box Agent** | Tool overreach, dangerous arguments, approval bypass, tool-output injection, planner loops | Tool / Policy / Approval Trace |
| **Stateful Agent** | Memory and RAG poisoning, identity isolation, checkpoint recovery, replay | Memory / Retrieval / Checkpoint Event |

### Engineering focus

- **Deterministic Core, Agentic Orchestration**: LangGraph may propose the next step, but the Core owns targets, cases, tools, approvals, budgets, and termination.
- **Policy Before Execution**: every target or tool call crosses the Policy Gate before side effects can occur.
- **Evidence Before Claims**: every Finding cites persisted Evidence; reports rebuild from business facts rather than model context.
- **Bounded Autonomy**: provider attempts, calls, tokens, cost, duration, and response size all have hard budgets.
- **Safe Recovery**: resumed checkpoints revalidate policy and do not duplicate model calls, target calls, or Findings.
- **Replay Diff**: compare fixed datasets and policies across versions as `fixed`, `new`, `persistent`, or `regressed`.
- **Secret Separation**: credentials never enter events, reports, snapshots, or checkpoints.
- **Default-safe Target Policy**: public or unresolved targets are rejected unless explicitly authorized.

Attacker is not about making an attack succeed once. It makes a security result reproducible, authorized, evidence-backed, and comparable after remediation.

**Core Stack**

`Python 3.12` `FastAPI` `LangGraph` `Pydantic` `SQLAlchemy Async` `Alembic` `SQLite / PostgreSQL` `pytest` `Pyright`

---

## The engineering principles behind all three projects

| Principle | How I apply it |
|---|---|
| **Model proposes, system decides** | Models analyze and suggest; policy, schemas, budgets, and approvals determine what can execute. |
| **Durable facts over volatile context** | Database facts drive recovery and audit; Redis and checkpoints coordinate but are not the final truth. |
| **Evidence before confidence** | Answers, memories, and security Findings must resolve back to sources, events, and evidence. |
| **Failure is part of the design** | Idempotency, retries, leases, ordering, cancellation, Dead Letter, and recovery are designed from day one. |
| **Security before side effects** | Identity, tenancy, permissions, secrets, targets, and arguments are constrained before execution. |
| **Production is the whole chain** | APIs, workers, migrations, observability, CI, containers, deployment, and runbooks are product capabilities. |

## Technology map

| Layer | Technologies | What I build |
|---|---|---|
| **Agent Runtime** | LangGraph, Pydantic AI, Skills, Tools, Providers | Routing, state machines, tool calls, workflows, approval, bounded autonomy |
| **RAG & Memory** | BGE-M3, pgvector, Reranker, Neo4j | Retrieval, evidence, citations, memory governance, profiles, relations |
| **Backend** | Python, FastAPI, Pydantic, SQLAlchemy Async, Alembic | API contracts, domain models, transactions, idempotency, service boundaries |
| **Async & Data** | PostgreSQL, Redis, Celery, Outbox / Inbox | Durable runs, queues, event delivery, recovery, consistency |
| **Frontend** | TypeScript, Vue 3, React, Vite | Agent workspaces, streaming UX, runtime state, visualization |
| **Security & Quality** | Policy Gate, Replay, pytest, Ruff, Pyright | Authorized evaluation, evidence, static analysis, behavior checks, CI |
| **Delivery** | Docker, Docker Compose, Nginx, GitHub Actions | Environment orchestration, deployment, health checks, monitoring, operations |

## What I am working on now

- Expanding the AtlasClaw Provider / Skill ecosystem and enterprise integration boundaries
- Improving Memoria's context governance, long-term memory quality, and verifiable reasoning
- Growing Attacker's security equipment ecosystem, continuous evaluation, and production foundations
- Documenting real engineering problems in Agents, RAG, system design, and project evolution

---

<h3 align="center">Build the runtime. Give it memory. Prove it is safe.</h3>

<p align="center">
  If you work on Agent runtimes, long-term memory, RAG, or AI security evaluation, I'd be glad to connect.
</p>

<p align="center">
  <a href="https://github.com/juemimgcd">Explore my repositories</a>
  ·
  <a href="https://blog.csdn.net/2403_88183496">Read my notes</a>
  ·
  <a href="mailto:15551285402@163.com">Get in touch</a>
</p>
