<p align="center">
  <img src="./assets/profile-hero.svg" alt="Juemimgcd — Runtime, Memory, Security" width="100%" />
</p>

<p align="center">
  <a href="./README.md">简体中文</a>
  ·
  <a href="./README.zh-TW.md">繁體中文</a>
  ·
  <a href="./README.en.md">English</a>
  ·
  <strong>日本語</strong>
  ·
  <a href="./README.fr.md">Français</a>
</p>

<h1 align="center">こんにちは、Juemimgcd です 👋</h1>

<h3 align="center">私が作るのは「会話できるデモ」ではなく、長期稼働し、障害から復旧でき、監査可能な Agent システムです。</h3>

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

## 3つの独立したリポジトリではなく、1つのエンジニアリングストーリー

私は Agent を実際のソフトウェアシステムとして設計します。モデルは判断を担う一要素にすぎません。システムを本番で成立させるのは、ランタイム、状態、データ所有権、権限、証拠、復旧機構、そしてセキュリティ境界です。

<table>
  <tr>
    <td width="33%" valign="top">
      <strong>⚙️ Runtime / Integration</strong><br/><br/>
      Skills、Tools、Providers、Sessions、Workflows を通じて Agent を企業システムへ接続し、利用者の実権限を維持します。
    </td>
    <td width="33%" valign="top">
      <strong>🧠 Memory / Intelligence</strong><br/><br/>
      検索可能で、統制でき、復旧可能な長期記憶を構築し、会話や非同期処理をまたいで文脈を保ちます。
    </td>
    <td width="33%" valign="top">
      <strong>🛡️ Security / Verification</strong><br/><br/>
      決定論的ポリシー、攻撃ケース、Evidence、Replay により、越権・漏えい・汚染・承認回避がないことを検証します。
    </td>
  </tr>
</table>

```text
AtlasClaw  →  Agent Runtime と企業システム統合
Memoria    →  長期記憶、知識ガバナンス、耐久実行
Attacker   →  攻撃評価、証拠の閉ループ、セキュリティ検証
```

---

## 01 / AtlasClaw

### [Enterprise Agent Framework for multi-system integration](https://github.com/CloudChef/atlasclaw)

> 社員が1つの対話窓口から、安全にデータを照会し、ワークフローを起動し、既存システムを操作できる基盤です。

| 私の役割 | プロジェクト | 実行形態 | リンク |
|---|---|---|---|
| Open-source Contributor | Enterprise Agent Framework | Embedded / Standalone | [Repository](https://github.com/CloudChef/atlasclaw) · [Website](https://atlasclaw.ai/en/) |

企業ソフトウェアは CRM、ITSM、監視、HR、財務、OA などに分散しています。難しいのは API を1本追加することではなく、異なるデータモデル、ID、権限、監査規則、ワークフロー境界を正しく扱うことです。

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

### 取り組んでいる中核テーマ

- **Thin Core + Rich Providers**：共通ランタイムだけを Core に置き、認証、業務スキル、システムスクリプトは Provider に分離します。
- **Skills による業務能力**：業務シナリオ、判断境界、ツール利用方法を明示し、モデルを制御された範囲で動かします。
- **統一された接点**：REST、SSE、WebSocket、Webhook が、対話、組み込み Agent、プログラム自動化を支えます。
- **実権限の継承**：操作は認証済みユーザーの対象システム権限で実行し、RBAC や監査を迂回しません。
- **交換可能なモデルと統合層**：モデル Provider、企業 Provider、Tools、Skills を独立して拡張できます。

AtlasClaw を通じて、個別の Agent 機能から、ID 伝播、権限制御、セッション継続、ツール登録、失敗の可視化、新システムの低コスト統合までを担う再利用可能な基盤へと関心が広がりました。

**Core Stack**

`Python` `FastAPI` `Pydantic AI` `Provider Registry` `Skills` `Tools` `Workflow` `SSE` `WebSocket`

---

## 02 / Memoria

### [A durable memory and knowledge system for personal AI](https://github.com/juemimgcd/Reminder)

> 文書、会話、経験、振り返りを、検索・統制・追跡できる長期記憶へ変換し、Agent に本当の連続性を与えます。

| 形態 | 中核 | 稼働システム | リンク |
|---|---|---|---|
| Full-stack AI Application | Long-term Memory + RAG + Durable Agent | Mneme / Memoria | [Repository](https://github.com/juemimgcd/Reminder) · [Live](https://www.mneme.com.cn) |

Memoria は Mneme の知能中核です。「文書をアップロードして質問する」だけではありません。Knowledge Base、Document、Chunk、Evidence、Memory Candidate、Canonical Memory、Revision、Relation、Profile、Growth Report、Recommendation に、明確な所有権とライフサイクルを持たせます。

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

### システムとして備える能力

- **知識パイプライン全体**：アップロード、解析、分割、索引、検索、Rerank、生成、引用検証を追跡可能な1本の流れにします。
- **長期記憶ガバナンス**：候補、正規記憶、改訂、関係、削除フェンス、操作監査により品質とプライバシーを守ります。
- **Durable Agent Run**：PostgreSQL に実行事実を保存し、Redis は調整に限定。リース、再試行、キャンセル、再生、復旧を標準機能にします。
- **制御可能な会話進化**：`interrupt`、`followup`、`steer` は不透明な Prompt を書き換えず、明確な Run / Trace 関係を作ります。
- **明示的な Multi-Agent 選択**：単一 Agent の高速経路を既定にし、ユーザーが選択した場合だけ有界な並列証拠収集を開始します。
- **有界推論**：検索範囲、Top-K、Provider 呼び出し、Token、コスト、期限、追加ラウンドを制限します。
- **イベント駆動の配送**：Outbox / Inbox、Celery、Heartbeat、承認、通知、Dead Letter により、副作用を再試行・追跡可能にします。
- **モデル耐障害性と文脈統制**：主系／予備モデル、一時的再試行、Provider Cooldown、有界圧縮、本文を漏らさない公開イベント。
- **本番可観測性**：Request / Run / Event 相関、Health、Readiness、Prometheus Metrics、アラート、Runbook。

長期記憶で最も難しいのはベクトル類似度ではありません。所有者、出所、有効性、削除、遅延イベント、重複副作用、順序です。そのため Ownership、Evidence、Idempotency、Ordering、Deletion Fence、Audit を中核概念にしています。

**Core Stack**

`Python` `FastAPI` `Vue 3` `PostgreSQL` `pgvector` `Redis` `Celery` `Neo4j` `BGE-M3` `Docker Compose`

---

## 03 / Attacker

### [Evidence-backed security evaluation for AI Agents](https://github.com/juemimgcd/Attacker)

> 明示的に許可された隔離環境で、再現可能な攻撃、決定論的ポリシー、永続的証拠に基づいて Agent を評価します。

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

### 3つの評価深度

| 段階 | 対象 | 主な証拠 |
|---|---|---|
| **Black-box** | Prompt Injection、Prompt 漏えい、機密データ、文脈汚染、資源制限 | Request / Response / Evaluator |
| **Gray-box Agent** | Tool 越権、危険引数、承認回避、Tool Output Injection、Planner ループ | Tool / Policy / Approval Trace |
| **Stateful Agent** | Memory / RAG 汚染、ID 分離、Checkpoint 復旧、Replay | Memory / Retrieval / Checkpoint Event |

### エンジニアリング上の重点

- **Deterministic Core, Agentic Orchestration**：LangGraph は次の手順を提案できますが、Target、Case、Tool、承認、予算、停止条件は Core が所有します。
- **Policy Before Execution**：すべての Target / Tool 呼び出しは、副作用の前に Policy Gate を通過します。
- **Evidence Before Claims**：Finding は永続化された Evidence を参照し、レポートはモデル文脈ではなく業務事実から再構築できます。
- **Bounded Autonomy**：Provider 試行、呼び出し、Token、コスト、時間、応答サイズをハード制限します。
- **Safe Recovery**：Checkpoint 復旧時に Policy を再検証し、モデル呼び出し、Target 呼び出し、Finding を重複させません。
- **Replay Diff**：固定 Dataset / Policy で `fixed`、`new`、`persistent`、`regressed` を比較します。
- **Secret Separation**：認証情報をイベント、レポート、スナップショット、Checkpoint に保存しません。
- **Default-safe Target Policy**：明示的な許可がない公開／解決不能 Target は既定で拒否します。

Attacker の目的は「一度だけ攻撃を成功させる」ことではありません。セキュリティ結果を再現可能、認可済み、証拠付き、修正後に比較可能なものにします。

**Core Stack**

`Python 3.12` `FastAPI` `LangGraph` `Pydantic` `SQLAlchemy Async` `Alembic` `SQLite / PostgreSQL` `pytest` `Pyright`

---

## 3つのプロジェクトに共通する原則

| 原則 | 実践 |
|---|---|
| **Model proposes, system decides** | モデルは分析・提案し、Policy、Schema、予算、承認が実行可否を決めます。 |
| **Durable facts over volatile context** | 復旧と監査はデータベース事実に基づき、Redis と Checkpoint は調整に使います。 |
| **Evidence before confidence** | 回答、記憶、Finding は出典、イベント、証拠まで遡れるようにします。 |
| **Failure is part of the design** | 冪等性、再試行、リース、順序、キャンセル、Dead Letter、復旧を最初から設計します。 |
| **Security before side effects** | ID、テナント、権限、Secret、Target、引数を実行前に制約します。 |
| **Production is the whole chain** | API、Worker、Migration、可観測性、CI、Container、配備、Runbook までを製品能力と捉えます。 |

## 技術マップ

| Layer | Technologies | What I build |
|---|---|---|
| **Agent Runtime** | LangGraph, Pydantic AI, Skills, Tools, Providers | ルーティング、状態機械、ツール呼び出し、ワークフロー、承認、有界自律 |
| **RAG & Memory** | BGE-M3, pgvector, Reranker, Neo4j | 検索、証拠、引用、記憶ガバナンス、Profile、Relation |
| **Backend** | Python, FastAPI, Pydantic, SQLAlchemy Async, Alembic | API Contract、ドメインモデル、トランザクション、冪等性、サービス境界 |
| **Async & Data** | PostgreSQL, Redis, Celery, Outbox / Inbox | Durable Run、キュー、イベント配送、復旧、整合性 |
| **Frontend** | TypeScript, Vue 3, React, Vite | Agent ワークスペース、ストリーミング UI、実行状態、可視化 |
| **Security & Quality** | Policy Gate, Replay, pytest, Ruff, Pyright | 認可評価、Evidence、静的検査、振る舞い検証、CI |
| **Delivery** | Docker, Docker Compose, Nginx, GitHub Actions | 環境編成、配備、Health Check、監視、運用 |

## 現在取り組んでいること

- AtlasClaw の Provider / Skill エコシステムと企業統合境界の拡張
- Memoria の文脈ガバナンス、長期記憶品質、検証可能な推論の改善
- Attacker のセキュリティ装備エコシステム、継続評価、本番基盤の強化
- Agent、RAG、システム設計、プロジェクト進化で得た実践的な課題の記録

---

<h3 align="center">Build the runtime. Give it memory. Prove it is safe.</h3>

<p align="center">
  Agent Runtime、長期記憶、RAG、AI セキュリティ評価に取り組んでいる方は、ぜひ交流しましょう。
</p>

<p align="center">
  <a href="https://github.com/juemimgcd">リポジトリを見る</a>
  ·
  <a href="https://blog.csdn.net/2403_88183496">記事を読む</a>
  ·
  <a href="mailto:15551285402@163.com">連絡する</a>
</p>
