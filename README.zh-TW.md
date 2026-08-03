<p align="center">
  <img src="./assets/profile-hero.svg" alt="Juemimgcd — Runtime, Memory, Security" width="100%" />
</p>

<p align="center">
  <a href="./README.md">简体中文</a>
  ·
  <strong>繁體中文</strong>
  ·
  <a href="./README.en.md">English</a>
  ·
  <a href="./README.ja.md">日本語</a>
  ·
  <a href="./README.fr.md">Français</a>
</p>

<h1 align="center">你好，我是 Juemimgcd 👋</h1>

<h3 align="center">我打造的不是「會聊天的 Demo」，而是能長期運行、可以恢復、能夠稽核的 Agent 系統。</h3>

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

## 我打造的，不是三個互不相關的儲存庫

我習慣把 Agent 當作真實的軟體系統來設計。模型只是其中的判斷元件；真正決定系統能否落地的，是執行環境、狀態、資料歸屬、權限、證據、恢復機制與安全邊界。

<table>
  <tr>
    <td width="33%" valign="top">
      <strong>⚙️ Runtime / Integration</strong><br/><br/>
      透過 Skills、Tools、Providers、Sessions 與 Workflows，讓 Agent 連接真實企業系統，同時繼承使用者的實際權限。
    </td>
    <td width="33%" valign="top">
      <strong>🧠 Memory / Intelligence</strong><br/><br/>
      建立可檢索、可治理、可恢復的長期記憶，在多輪對話與非同步任務中維持脈絡連續性。
    </td>
    <td width="33%" valign="top">
      <strong>🛡️ Security / Verification</strong><br/><br/>
      以確定性策略、攻擊案例、Evidence 與 Replay，證明 Agent 沒有越權、洩漏、污染狀態或繞過審批。
    </td>
  </tr>
</table>

```text
AtlasClaw  →  建立 Agent Runtime 與企業系統整合能力
Memoria    →  建立長期記憶、知識治理與可恢復執行能力
Attacker   →  建立攻擊評測、證據閉環與安全驗證能力
```

---

## 01 / AtlasClaw

### [Enterprise Agent Framework for multi-system integration](https://github.com/CloudChef/atlasclaw)

> 讓企業員工透過單一對話入口，安全查詢資料、觸發工作流程並操作既有系統。

| 我的角色 | 專案定位 | 運行模式 | 連結 |
|---|---|---|---|
| Open-source Contributor | 企業級 Agent Framework | Embedded / Standalone | [Repository](https://github.com/CloudChef/atlasclaw) · [Website](https://atlasclaw.ai/en/) |

企業軟體分散在 CRM、ITSM、監控、HR、財務與 OA 等系統中。困難不只是「再接一個 API」，而是不同系統擁有不同的資料模型、身分、權限、稽核規則與工作流程邊界。

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

### 我參與和關注的核心方向

- **Thin Core + Rich Providers**：核心只承擔通用執行環境，認證、領域技能與系統腳本留在 Provider 中。
- **Skills 驅動的業務能力**：用 Skills 描述業務場景、決策邊界與工具使用方式，使模型在受控範圍內行動。
- **統一互動入口**：REST、SSE、WebSocket 與 Webhook 同時服務對話、嵌入式 Agent 與程式化自動化。
- **真實權限繼承**：所有動作沿用已認證使用者在目標系統中的權限，不繞過 RBAC，也不隱藏平台稽核軌跡。
- **可替換的模型與整合層**：模型 Provider、企業系統 Provider、Tools 與 Skills 可以獨立演進。

AtlasClaw 讓我的焦點從「實作單一 Agent 功能」走向「設計可被不同企業系統重用的 Agent 基礎設施」：身分傳遞、權限約束、會話連續、工具註冊、失敗暴露，以及新系統的低成本接入。

**Core Stack**

`Python` `FastAPI` `Pydantic AI` `Provider Registry` `Skills` `Tools` `Workflow` `SSE` `WebSocket`

---

## 02 / Memoria

### [A durable memory and knowledge system for personal AI](https://github.com/juemimgcd/Reminder)

> 將文件、對話、經歷與復盤沉澱為可檢索、可治理、可追蹤的長期記憶，讓 Agent 真正擁有連續性。

| 專案形態 | 核心定位 | 線上系統 | 連結 |
|---|---|---|---|
| Full-stack AI Application | 長期記憶 + RAG + Durable Agent | Mneme / Memoria | [Repository](https://github.com/juemimgcd/Reminder) · [Live](https://www.mneme.com.cn) |

Memoria 是 Mneme 系統的智慧核心。它不只是「上傳文件後問問題」，而是讓知識庫、文件、Chunk、Evidence、記憶候選、正式記憶、版本、關係、個人畫像、成長報告與建議都具有明確的資料歸屬與生命週期。

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

### 已形成的系統能力

- **完整知識鏈路**：上傳、解析、切分、索引、召回、Rerank、回答生成與引用驗證形成閉環。
- **長期記憶治理**：Memory Candidate、Canonical Memory、Revision、Relation、刪除圍欄與操作稽核共同維護品質與隱私。
- **Durable Agent Run**：PostgreSQL 保存執行事實，Redis 只負責協調；租約、重試、取消、事件重放與故障恢復都是一等能力。
- **可控制的會話演進**：`interrupt`、`followup` 與 `steer` 形成明確的 Run / Trace 關係，而不是修改執行中的黑盒 Prompt。
- **明確的 Multi-Agent 選擇**：預設保留單 Agent 快速路徑；只有使用者選擇後才啟用有界平行取證。
- **有界推理**：檢索範圍、Top-K、Provider 呼叫、Token、成本、截止時間與補充輪次都有硬限制。
- **事件驅動交付**：Outbox / Inbox、Celery、Heartbeat、審批、通知、自動化與 Dead Letter 讓副作用可重試、可追蹤。
- **模型韌性與脈絡治理**：主備模型、瞬時重試、Provider Cooldown、有界壓縮，以及不洩漏正文的公開事件。
- **生產可觀測性**：Request / Run / Event 關聯、Health、Readiness、Prometheus Metrics、告警規則與運維 Runbook。

長期記憶最困難的不是向量相似度，而是歸屬、來源、有效性、刪除語意、遲到事件、重複副作用與順序。因此 Memoria 把 Ownership、Evidence、Idempotency、Ordering、Deletion Fence 與 Audit 當成核心領域概念。

**Core Stack**

`Python` `FastAPI` `Vue 3` `PostgreSQL` `pgvector` `Redis` `Celery` `Neo4j` `BGE-M3` `Docker Compose`

---

## 03 / Attacker

### [Evidence-backed security evaluation for AI Agents](https://github.com/juemimgcd/Attacker)

> 在明確授權的隔離環境中，以可重複攻擊、確定性策略與持久化證據評測 Agent。

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

### 三種評測深度

| 階段 | 範圍 | 主要證據 |
|---|---|---|
| **純黑盒** | Prompt Injection、提示洩漏、敏感資料、脈絡污染、資源限制 | Request / Response / Evaluator |
| **灰盒 Agent** | 工具越權、危險參數、審批繞過、Tool Output Injection、Planner 迴圈 | Tool / Policy / Approval Trace |
| **帶狀態 Agent** | Memory / RAG 污染、身分隔離、Checkpoint 恢復、Replay | Memory / Retrieval / Checkpoint Event |

### 工程重點

- **Deterministic Core, Agentic Orchestration**：LangGraph 可以提出下一步，但 Target、Case、Tool、審批、預算與停止條件由 Core 決定。
- **Policy Before Execution**：每個 Target 或 Tool 呼叫都必須在副作用發生前通過 Policy Gate。
- **Evidence Before Claims**：每個 Finding 都引用持久化 Evidence；報告依靠業務事實重建，而不是模型上下文。
- **Bounded Autonomy**：Provider 嘗試、呼叫次數、Token、成本、持續時間與回應大小都有硬預算。
- **Safe Recovery**：Checkpoint 恢復後重新驗證 Policy，不重複模型呼叫、Target 呼叫或 Finding。
- **Replay Diff**：以固定 Dataset 與 Policy 比較 `fixed`、`new`、`persistent` 與 `regressed`。
- **Secret Separation**：憑證不進入事件、報告、快照或 Checkpoint。
- **Default-safe Target Policy**：未明確授權的公網或不可解析 Target 預設拒絕。

Attacker 不追求「讓攻擊偶然成功一次」，而是讓安全結果可重複、具備授權、由證據支撐，並能在修復後比較。

**Core Stack**

`Python 3.12` `FastAPI` `LangGraph` `Pydantic` `SQLAlchemy Async` `Alembic` `SQLite / PostgreSQL` `pytest` `Pyright`

---

## 三個專案背後的統一方法

| 原則 | 我的工程取向 |
|---|---|
| **Model proposes, system decides** | 模型可以分析和建議；Policy、Schema、預算與審批決定什麼能執行。 |
| **Durable facts over volatile context** | 資料庫事實負責恢復與稽核，Redis 和 Checkpoint 負責協調，但不是最終真相。 |
| **Evidence before confidence** | 回答、記憶與安全 Finding 都必須回到來源、事件和證據。 |
| **Failure is part of the design** | 從一開始設計冪等、重試、租約、順序、取消、Dead Letter 與恢復。 |
| **Security before side effects** | 身分、租戶、權限、Secret、Target 與參數在執行前受到約束。 |
| **Production is the whole chain** | API、Worker、Migration、可觀測性、CI、Container、部署與 Runbook 都是產品能力。 |

## 技術版圖

| Layer | Technologies | What I build |
|---|---|---|
| **Agent Runtime** | LangGraph, Pydantic AI, Skills, Tools, Providers | 路由、狀態機、工具呼叫、工作流程、審批與有界自治 |
| **RAG & Memory** | BGE-M3, pgvector, Reranker, Neo4j | 檢索、證據、引用、記憶治理、畫像與關係 |
| **Backend** | Python, FastAPI, Pydantic, SQLAlchemy Async, Alembic | API Contract、領域模型、交易、冪等與服務邊界 |
| **Async & Data** | PostgreSQL, Redis, Celery, Outbox / Inbox | Durable Run、任務佇列、事件投遞、恢復與一致性 |
| **Frontend** | TypeScript, Vue 3, React, Vite | Agent 工作臺、串流互動、執行狀態與視覺化 |
| **Security & Quality** | Policy Gate, Replay, pytest, Ruff, Pyright | 授權評測、Evidence、靜態檢查、行為驗證與 CI |
| **Delivery** | Docker, Docker Compose, Nginx, GitHub Actions | 環境編排、部署、健康檢查、監控與運維 |

## 現在仍在推進

- 擴展 AtlasClaw 的 Provider / Skill 生態與企業整合邊界
- 持續完善 Memoria 的脈絡治理、長期記憶品質與可驗證推理
- 推進 Attacker 的安全裝備生態、持續評測與生產化基礎
- 持續記錄 Agent、RAG、系統設計與專案演進中的真實工程問題

---

<h3 align="center">Build the runtime. Give it memory. Prove it is safe.</h3>

<p align="center">
  如果你也在研究 Agent Runtime、長期記憶、RAG 或 AI 安全評測，歡迎交流。
</p>

<p align="center">
  <a href="https://github.com/juemimgcd">探索我的儲存庫</a>
  ·
  <a href="https://blog.csdn.net/2403_88183496">閱讀我的筆記</a>
  ·
  <a href="mailto:15551285402@163.com">聯絡我</a>
</p>
