# 你好，我是Juemimgcd 👋

一名专注于 **Agent / RAG / AI 应用开发** 的学生开发者，主要使用 **Python、FastAPI、LangChain、LangGraph** 构建可落地的 AI 应用后端。

我正在持续把“能跑起来的 Demo”，做成“结构清晰、链路完整、能够部署上线的系统”。

目前重点关注：

- **Agent 工作流设计**：任务拆解、状态管理、工具调用与结果收敛
- **RAG 后端实现**：文档上传、切分、索引、检索、问答主链路
- **结构化抽取与任务编排**：把自然语言请求转成稳定、可执行的结果
- **工程化与部署**：异步任务、数据库建模、前后端分离、云端部署与排障

---

## 我在做什么

- 🔭 持续迭代 **Mneme**：个人记忆型 Agent / RAG 应用
- 🧠 深入学习 **LangGraph、结构化搜索 Agent、异步任务工作流**
- ⚙️ 关注 **AI 应用的可解释性、可观测性与工程完整度**
- ✍️ 在 CSDN 持续输出 **RAG、Agent 与项目复盘** 相关内容

---

## 技术栈

**AI 应用开发**
`LangChain` `LangGraph` `RAG` `Pydantic` `结构化抽取` `Schema 设计`

**后端开发**
`Python` `FastAPI` `SQLAlchemy 2.x Async` `PostgreSQL` `MySQL` `Redis` `Celery` `JWT`

**检索与数据链路**
`Milvus` `向量检索` `文档切分` `索引构建` `检索增强生成`

**工程化与部署**
`Docker` `Docker Compose` `Linux` `Git` `Pytest` `阿里云部署` `腾讯云部署`

---

## 代表项目

### Mneme｜个人记忆型 Agent 应用
一个面向个人长期内容沉淀的记忆型 RAG 系统，围绕知识库、文档处理、检索问答与记忆视图构建完整链路。

我主要负责：
- 基于 FastAPI 实现后端核心链路
- 完成用户、知识库、文档、分块、记忆条目等核心数据建模
- 打通文档上传、切分、索引、检索、问答流程
- 参与前后端联调与前后端分离部署

**Tech Stack**  
`FastAPI` `PostgreSQL` `SQLAlchemy` `Milvus` `LangChain` `RAG` `Docker`

- 后端仓库：<[你的 Mneme 后端链接](https://github.com/juemimgcd/Mneme)>
- 前端仓库：<你的 Mneme 前端链接>

---

### formatter_agent｜状态驱动结构化搜索 Agent
一个将自然语言查询转换为结构化结果的轻量 Agent 系统，强调状态驱动、可解释性与可调试性。

我主要做了：
- 设计 `TaskCompiler -> Policy -> ToolRunner -> Reducer -> Finalizer` 执行链路
- 显式维护 `AgentState / slots / evidence / warnings`
- 接入多源搜索召回、结构化抽取、fallback 与 Excel 导出
- 使用 Celery + Redis 构建异步任务工作流
- 结合吞吐、P95 / P99、错误率与结果质量做压测评估

**Tech Stack**  
`FastAPI` `Celery` `Redis` `PostgreSQL` `LangChain` `LangGraph` `Pydantic`

- 项目地址：<你的 formatter_agent 链接>

---

## 我希望自己成为怎样的开发者

我希望自己不仅能完成功能开发，也能真正做好：

- 清晰的数据建模
- 稳定的系统链路
- 可解释、可调试的 Agent 流程
- 可部署、可迭代的 AI 应用工程

相比“堆技术名词”，我更在意系统是否真的完整、稳定、能持续演进。

---

## 联系我

- GitHub: https://github.com/juemimgcd
- CSDN: https://blog.csdn.net/2403_88183496
- Email: 15551285402@163.com

*Thanks for visiting my profile! Feel free to explore my projects and reach out for collaboration opportunities.* 🚀
