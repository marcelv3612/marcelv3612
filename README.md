# 👋 Marcel Valový, PhD

<div align="center">

**AI Engineering Team Lead | Agent Platforms & Evals | MCP Server Developer | Human-AI Collaboration Researcher**

*Ex-Oracle (JAXB · EclipseLink MOXy · JDK 9) · 16+ years shipping enterprise systems*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://linkedin.com/in/marcelv3612)
[![ResearchGate](https://img.shields.io/badge/ResearchGate-Profile-00CCBB)](https://www.researchgate.net/profile/Marcel-Valovy-2)
[![Google Scholar](https://img.shields.io/badge/Google_Scholar-Publications-4285F4)](https://scholar.google.com/citations?user=fQUPwoQAAAAJ)
[![Stack Overflow](https://img.shields.io/badge/StackOverflow-663-orange)](https://stackoverflow.com/users/3832336/marcelv3612)

</div>

---

> **Evals first, architecture second.** I build agentic systems the way I was trained to build research: golden sets before features, measured baselines before claims, and deterministic code wherever an LLM is not earning its place in the path.

---

<table>
<tr>
<td width="50%" valign="top">

### 🚀 What I Build
```rust
let current_focus = vec![
    "Evals-first agent development (golden sets, regression gates)",
    "AI agent platforms & orchestration",
    "MCP servers & Claude Code toolkits (skills, subagents, plugins)",
    "Knowledge graphs for agent memory & retrieval",
    "LLM routing, cost & latency engineering (AI FinOps)",
    "High-performance trading systems",
];
```

**Current:**
- 🏦 **AI Engineering Team Lead @ EuroWAG** (fintech, fleet payments): touchless invoice pairing, an AI developer platform used by ~100 engineers, AI-driven FinOps
- 🤖 **Founder @ [TradeGuard](https://tradeguard.software)**: AI trading platform + **Moira**, an eval harness and Agent Factory for trading agents
- 🎓 **Postdoctoral Researcher (part-time) @ VŠE Prague**: Human-AI Collaboration; PhD defended there Oct 2025

**Previously:**
- 📡 **Amdocs**: built **aOS**, an agentic platform framework; replaced an LLM retrieval step with deterministic graph queries (precision/recall ~50% → ~95%, median latency 30 s → 1.1 s)

</td>
<td width="50%" valign="top">

### 🤖 AI & Agent Stack

**Agent Orchestration:**
- MCP (Model Context Protocol) servers
- Claude Code skills, subagents & plugins
- LangChain & LangGraph workflows
- Mixture-of-Agents / agent boards, Agent Factory pattern
- Claude Code, Cursor, Codex, Gemini CLI

**Evals & Quality:**
- Golden sets per agent, cross-vendor LLM judging
- Retrieval precision/recall, hallucination rate, provenance
- Cost & latency budgets (median / p95)

**LLM & Embeddings:**
- Anthropic Claude (primary) • Kimi • OpenAI APIs
- Azure AI Foundry • AWS Bedrock
- HuggingFace Transformers • local inference (Ollama, llama.cpp)

**Retrieval & Knowledge:**
- Neo4j / Cypher knowledge graphs
- pgvectorscale + DiskANN (PostgreSQL)
- Hybrid search (BM25 + vector)

</td>
</tr>
</table>

---

### 🧪 Featured: Agentic Platforms Measured, Not Assumed

<table>
<tr>
<td width="50%" valign="top">

#### 📡 aOS: Agentic Platform Framework (Amdocs)
Green-field agentic platform (agent board, planner, clerk, knowledge-graph memory). The user-facing agents scored well on golden sets but underperformed in the application, so I wrote golden sets for the retrieval layer itself. The evidence said the LLM "data librarian" was the bottleneck; I replaced it with deterministic, parameterised Cypher behind a deliberately narrow MCP tool, plus new KG schemas and indexes.

```cypher
// Illustrative: the MCP tool accepts only a search term and optional hops
CALL db.index.fulltext.queryNodes('entityIndex', $term) YIELD node AS e, score
CALL apoc.path.subgraphNodes(e, {maxLevel: $hops}) YIELD node AS ctx
RETURN e, score, collect(DISTINCT ctx) AS context
ORDER BY score DESC LIMIT $k
```

| Metric | Before (LLM librarian) | After (deterministic) |
|--------|------------------------|-----------------------|
| Retrieval precision / recall | ~50% | **~95%** |
| Provenance | ~50% | **90%+** |
| Median latency | 30 s | **1.1 s** |
| p95 latency | 50 s | **1.8 s** |
| Cost | 1× | **~10× lower** |

<sub>Latency includes a Haiku call interpreting results. Cost fell because retry loops between clerk, planner and agent board disappeared.</sub>

Then built the **Agent Factory**: consultants create new agents over synthetic data without touching code, and each agent ships with its own auto-generated golden set.

</td>
<td width="50%" valign="top">

#### 🔁 Agent Factory Eval Loop (aOS → Moira)
```python
# Each new agent gets its own golden set, generated and judged
# by a *different* LLM vendor than the one that built it.
golden = generator.make_questions(agent.spec, n=20, difficulty="graded")
while True:
    report = judge.score(agent, golden, criteria=[
        "retrieval_accuracy", "hallucination_rate",
        "provenance", "cost", "latency",
    ])
    if report.passes(thresholds):
        break
    agent.prompt = judge.propose_revision(agent.prompt, report)
```

#### 📈 Moira (TradeGuard, in progress)
An eval harness for training and evaluating "market wizard" trading agents, executed through the TradeGuard platform:
- **Schools**: each LLM vendor raises its own agents; another vendor and a human evaluate them
- **Lifecycle as phases**: ingest → design (Agent Factory) → backtest → forward-test → paper trading → live → archive
- **World model in knowledge graphs**; agents coordinate through a session KG
- **Auditability, tracing and provenance** as first-class requirements

</td>
</tr>
</table>

---

### 🏦 AI Engineering @ EuroWAG

<table>
<tr>
<td width="50%" valign="top">

#### 🧾 Touchless Invoice Pairing (IPA)
```python
# Fuzzy scoring + LLM top-up; a human is called only for
# anomalies the pipeline cannot resolve on its own.
class InvoicePairing:
    def pair(self, vendor_tx, invoice_items):
        match = self.matching_engine.score(vendor_tx, invoice_items)
        if match.resolved:
            return AutoPair(match)
        resolved = self.llm_resolver.try_resolve(match)
        return resolved or HumanReview(match.anomaly)
```
- **300 fuel vendors** onboarded to fully touchless pairing
- Vendor verification with separated reference / hidden sets, regression runs and production confirmation across billing cycles
- KPIs: touchless share, matching coverage vs pair correctness, LLM top-up coverage, escalation rate

</td>
<td width="50%" valign="top">

#### 🛠️ AI Developer Platform & Enablement
- Shared **`.claude/` toolkit**: commands, skills, subagents, MCP servers and setup guides, used by **~100 people** across two engineering units; team leads report **10–20% faster** delivery
- **AutoDoc**: AI-generated, human-verified documentation for a 19-service domain, with HITL editing
- Enterprise knowledge base aggregated for agent context
- Founded **AI Guild** and hands-on **AI Lab** (biweekly)

#### 💶 AI-Driven FinOps
- Production Log Analytics spend **€12.4k → €1.7k / month (−86.5%)**, confirmed on billed invoices; **~€130k / year** saved
- Follow-up campaign on shared platform subscriptions

</td>
</tr>
</table>

---

<table>
<tr>
<td width="50%" valign="top">

### 🛠️ Tech Stack

**Languages:**
```
Rust      ████████████░░  Expert (systems, trading)
Java      ████████████████ Expert (16+ years)
Kotlin    ████████████░░  Advanced
Python    ████████████░░  Advanced (ML/AI)
TypeScript████████░░░░░░  Proficient
Cypher    ██████████░░░░  Advanced (knowledge graphs)
```

**Backend & Microservices:**
- Spring Boot • Quarkus 3.x • Micronaut
- Apache Kafka • CDC (Debezium)
- gRPC • GraphQL • REST • WebSockets
- Event-driven (CQRS, Saga, Outbox)

**Cloud & DevOps:**
- Kubernetes • Docker • Helm
- Azure (expert) • AWS • GCP
- Pulumi IaC • GitLab CI/CD
- Prometheus • Grafana • ELK • Honeycomb

**Data:**
- PostgreSQL (expert) • Neo4j • Cosmos DB • MongoDB
- Redis • Elasticsearch
- jOOQ • Hibernate • R2DBC

</td>
<td width="50%" valign="top">

### 📊 Impact & Achievements

**Agentic AI:**
| Metric | Achievement |
|--------|-------------|
| 🎯 Retrieval precision/recall (aOS) | **~50% → ~95%** |
| ⚡ Agent latency, median (aOS) | **30 s → 1.1 s** |
| 💸 Agent cost (aOS) | **~10× lower** |
| 🧾 Touchless invoice pairing | **300** fuel vendors |
| 🛠️ AI toolkit adoption | **~100** engineers |
| 💶 Observability spend | **−86.5%** (~€130k/yr) |

**Production Systems:**
| Metric | Achievement |
|--------|-------------|
| 🎯 Trader success | **90%** (TradeGuard, 200+ validated) |
| 💰 AI platform revenue | **800K CZK** |
| ⚡ Trading latency | **<10ms** (Rust engine) |
| 🏦 Payment throughput | **600K+** txs/hour |
| 📈 Fintech scale | **300K+** txn writes/min |

**Research & Open Source:**
| Metric | Achievement |
|--------|-------------|
| 📝 Publications | **11** peer-reviewed |
| 📚 Citations | **73** <!-- verify on Google Scholar before publishing --> |
| 🏆 Best Paper Awards | **3** |
| 🎓 Students taught | **200+** |
| 🔧 Eclipse PRs | **50+** merged |

</td>
</tr>
</table>

---

### 🔬 Research: Human-AI Collaboration

<table>
<tr>
<td width="60%" valign="top">

**PhD Dissertation (Defended October 2025, VŠE Prague):**
*"Human-AI Programming Role Optimization: Developing a Self-Determination Framework"*

**Key Finding:**
AI-assisted development increases programmer motivation by **23–65%** when optimized for individual personality types (Big Five) and working styles (Self-Determination Theory).

**Practical Applications:**
- 🎯 When AI agents should lead vs. support developer decisions
- 🖥️ Designing interfaces that respect developer autonomy
- 📊 Measuring AI tool effectiveness beyond productivity metrics
- 🏢 Change management for AI adoption in enterprise (applied daily via AI Guild / AI Lab)

</td>
<td width="40%" valign="top">

**Select Publications:**
- **PeerJ CS** (Q1): Personality-Driven Pair Programming
- **IEEE ICSME** (CORE-A): AI-Assisted Programming Psychology *(45 citations)*
- **EASE** (CORE-A): Psychological Aspects of Pair Programming
- **ACIE'25**: Blockchain-Driven Transparent Research *(Best Paper)*
- **CIMPS'22**: *(Best Paper)*
- **DD FIS VSE'22**: *(Best Paper)*

</td>
</tr>
</table>

---

<table>
<tr>
<td width="33%" valign="top">

### 🌟 Open Source

**Oracle / Eclipse Foundation:**
- Designed and implemented **Bean Validation (JSR 303)** integration on both sides of Java XML binding:
  - **JAXB**: BV support in the XJC and JXC plugins; BV-annotation package shipped in the **JDK 9** distribution
  - **[EclipseLink](https://github.com/eclipse-ee4j/eclipselink) MOXy**: released in EclipseLink 2.6 (2015)
- **57–92%** performance improvements
- 50+ merged PRs

**Interests:**
- AI agent tooling & evals
- MCP ecosystem
- Rust systems programming

</td>
<td width="33%" valign="top">

### 🎯 Enterprise Experience

**16+ Years Building:**
- 200+ microservices in production
- Systems serving millions of users
- Fintech, telecom, CRM, IoT, trading platforms

**Where I've Built:**
- 🏦 EuroWAG (fleet payments)
- 📡 Amdocs (agentic platforms)
- 📱 T-Mobile Czech Republic
- ☕ Oracle Corporation
- 🏦 Home Credit International
- 🏭 Rockwell Automation
- 🏛️ Ministry of Interior CZ
- 💳 DNZ Finance (crypto)
- 📊 Adastra

</td>
<td width="33%" valign="top">

### 🔧 Current Interests

**Building:**
- Evals-first agent harnesses
- MCP servers for enterprise AI
- Knowledge-graph agent memory
- Rust + Python hybrid systems

**Exploring:**
- Measuring AI benefit via unit economics (cost per invoice / release / incident)
- AI agent payment protocols
- Autonomous agent orchestration
- Browser automation + AI

</td>
</tr>
</table>

---

<div align="center">

### 💬 Let's Connect

**Open to:**
AI Agent Platform Engineering • Evals & Agent Reliability • MCP Server Development • Research Collaboration • Technical Consulting

📧 **marcel@tradeguard.cz**
🌏 **Location:** Prague / Remote-first (currently Asia)
💼 **Status:** Building @ TradeGuard · Leading AI Engineering @ EuroWAG

---

*"The best AI systems don't replace humans; they amplify human judgment with superhuman data processing."*

---

### 🏆 Quick Stats

![](https://img.shields.io/badge/Languages-Czech%20%7C%20English%20%7C%20Russian-blue)
![](https://img.shields.io/badge/Experience-16%2B%20years-green)
![](https://img.shields.io/badge/AI%2FML-Agents%20%7C%20Evals%20%7C%20MCP%20%7C%20KG-purple)
![](https://img.shields.io/badge/Publications-11-orange)
![](https://img.shields.io/badge/Citations-73-red)

</div>
