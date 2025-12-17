# 👋 Marcel Valový, PhD

<div align="center">
  
**AI Agent Platform Engineer | MCP Server Developer | Eclipse Committer | Human-AI Collaboration Researcher**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://linkedin.com/in/marcelv3612)
[![ResearchGate](https://img.shields.io/badge/ResearchGate-Profile-00CCBB)](https://www.researchgate.net/profile/Marcel-Valovy)
[![Google Scholar](https://img.shields.io/badge/Google_Scholar-Publications-4285F4)](https://scholar.google.com)
[![Stack Overflow](https://img.shields.io/badge/StackOverflow-663-orange)](https://stackoverflow.com/users/3832336/marcelv3612)

</div>

---

<table>
<tr>
<td width="50%" valign="top">

### 🚀 What I Build
```rust
let current_focus = vec![
    "AI agent platforms & orchestration",
    "MCP servers for tool integration",
    "RAG systems & vector search",
    "High-performance trading systems", 
    "Event-driven microservices at scale",
];
```

**Current:**
- 🤖 Founder/CEO @ [TradeGuard](https://tradeguard.software) - AI trading platform (90% success rate, revenue-generating)
- 🏦 Senior/Staff Engineer @ EuroWAG - ML automation, MCP servers, AI agents
- 🔧 Eclipse Foundation Committer (50+ contributions)
- 🎓 PhD in Human-AI Collaboration (Defended Oct 2025)

</td>
<td width="50%" valign="top">

### 🤖 AI & Agent Stack

**Agent Orchestration:**
- MCP (Model Context Protocol) servers
- LangChain & LangGraph workflows
- Claude Code, GitHub Copilot, Gemini CLI
- Custom agentic pipelines

**LLM & Embeddings:**
- OpenAI API (GPT-4, text-embedding-3-small)
- Azure AI Foundry
- Anthropic Claude API
- RAG implementations

**Vector Databases:**
- pgvectorscale + DiskANN (PostgreSQL)
- Semantic search & similarity matching
- Hybrid search (BM25 + vector)

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
Java      ████████████████ Expert (15+ years)
Kotlin    ████████████░░  Advanced
Python    ████████████░░  Advanced (ML/AI)
TypeScript████████░░░░░░  Proficient
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
- Prometheus • Grafana • ELK

**Data:**
- PostgreSQL (expert) • Cosmos DB • MongoDB
- Redis • Elasticsearch
- jOOQ • Hibernate • R2DBC

</td>
<td width="50%" valign="top">

### 📊 Impact & Achievements

**Production Systems:**
| Metric | Achievement |
|--------|-------------|
| 🎯 Trader success | **90%** (TradeGuard, 200+ validated) |
| 💰 AI platform revenue | **800K CZK** |
| ⚡ Trading latency | **<10ms** (Rust engine) |
| 🏦 Payment throughput | **600K+** txs/hour |
| 🤖 ML automation rate | **70%** (invoice matching) |
| 📈 Fintech scale | **300K+** txs/min |

**Research & Open Source:**
| Metric | Achievement |
|--------|-------------|
| 📝 Publications | **10** peer-reviewed |
| 📚 Citations | **50+** |
| 🏆 Best Paper Awards | **3** |
| 🎓 Students taught | **200+** |
| 🔧 Eclipse PRs | **50+** merged |

</td>
</tr>
</table>

---

### 🤖 AI Agent & Automation Projects

<table>
<tr>
<td width="50%" valign="top">

#### 🔧 MCP Server Development
Building Model Context Protocol servers for AI agent orchestration:
```python
# MCP server for enterprise knowledge base
@mcp.tool()
async def search_documents(query: str) -> list[Document]:
    embeddings = openai.embed(query)
    return vector_db.similarity_search(embeddings, k=10)
```
- Tool integration for Claude, GPT-4
- Enterprise knowledge base access
- Automated code review pipelines
- CI/CD documentation generation

#### 🧠 RAG & Vector Search
```sql
-- pgvectorscale with DiskANN for semantic search
SELECT content, embedding <=> $1 AS distance
FROM documents
ORDER BY embedding <=> $1
LIMIT 10;
```
- Hybrid search (semantic + keyword)
- Document chunking strategies
- Embedding optimization
- Real-time index updates

</td>
<td width="50%" valign="top">

#### 🏦 ML Invoice Automation (EuroWAG)
```python
# Fuzzy matching + ML scoring pipeline
class InvoiceMatcher:
    def match(self, vendor_tx, invoice_items):
        features = self.extract_features(vendor_tx, invoice_items)
        confidence = self.ml_model.predict(features)
        if confidence > 0.85:
            return AutoMatch(confidence)
        return HumanReview(confidence)
```
- **70% automation rate** on 500K invoices/month
- OpenAI API for data normalization
- LangChain for agentic decisions
- Anomaly detection for fraud

#### 🤖 TradeGuard AI Platform
```rust
// High-performance Rust trading engine
impl TradingAgent {
    async fn evaluate(&self, market: &MarketData) -> Decision {
        let risk = self.prospect_theory.assess(market);
        let emotion = self.detect_fomo(self.user_state);
        self.ml_model.decide(risk, emotion, market)
    }
}
```
- Behavioral AI (Kahneman's Prospect Theory)
- Real-time emotion/FOMO detection
- Multi-exchange integration (HyperLiquid, Binance, Bybit)

</td>
</tr>
</table>

---

### 🔬 Research: Human-AI Collaboration

<table>
<tr>
<td width="60%" valign="top">

**PhD Dissertation (Defended October 2025):**  
*"Human-AI Programming Role Optimization: Developing a Self-Determination Framework"*

**Key Finding:**  
AI-assisted development increases programmer motivation by **23-65%** when optimized for individual personality types (Big Five) and working styles (Self-Determination Theory).

**Practical Applications:**
- 🎯 When AI agents should lead vs. support developer decisions
- 🖥️ Designing interfaces that respect developer autonomy
- 📊 Measuring AI tool effectiveness beyond productivity metrics
- 🏢 Change management for AI adoption in enterprise

</td>
<td width="40%" valign="top">

**Select Publications:**
- **PeerJ CS** (Q1): Personality-Driven Pair Programming 
- **IEEE ICSME** (CORE-A): AI-Assisted Programming Psychology *(30 citations)*
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

**Eclipse Foundation:**
- [EclipseLink](https://github.com/eclipse-ee4j/eclipselink) contributor
- JSR-303 Bean Validation (JAXB)
- Java 9 SDK enhancements
- **57-92%** performance improvements
- 50+ merged PRs

**Interests:**
- AI agent tooling
- MCP ecosystem
- Rust systems programming

</td>
<td width="33%" valign="top">

### 🎯 Enterprise Experience

**15+ Years Building:**
- 100+ microservices in production
- Systems serving millions of users
- Fintech, CRM, IoT, Trading platforms

**Notable Clients:**
- 📱 T-Mobile Czech Republic
- 💳 DNZ Finance (crypto)
- 🏛️ Ministry of Interior CZ
- 🏭 Rockwell Automation
- 🏦 Home Credit International
- ☕ Oracle Corporation

</td>
<td width="33%" valign="top">

### 🔧 Current Interests

**Building:**
- MCP servers for enterprise AI
- LangGraph multi-agent workflows
- Vector search optimization
- Rust + Python hybrid systems

**Exploring:**
- AI agent payment protocols
- Autonomous agent orchestration
- Web data for RAG pipelines
- Browser automation + AI

</td>
</tr>
</table>

---

<div align="center">

### 💬 Let's Connect

**Open to:**  
AI Agent Platform Engineering • MCP Server Development • Research Collaboration • Technical Consulting

📧 **marcelv3612@gmail.com**  
🌏 **Location:** Prague / Remote-first (currently Asia)  
💼 **Status:** Exploring AI agent platform & research engineering roles

---

*"The best AI systems don't replace humans—they amplify human judgment with superhuman data processing."*

---

### 🏆 Quick Stats

![](https://img.shields.io/badge/Languages-Czech%20%7C%20English%20%7C%20Russian-blue)
![](https://img.shields.io/badge/Experience-15%2B%20years-green)
![](https://img.shields.io/badge/AI%2FML-MCP%20%7C%20LangChain%20%7C%20RAG-purple)
![](https://img.shields.io/badge/Publications-10%2B-orange)
![](https://img.shields.io/badge/Citations-50%2B-red)

</div>
