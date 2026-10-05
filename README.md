# 👋 Marcel Valový, PhD

<div align="center">
<h3>AI Engineering Team Lead · Founder of TradeGuard<br>Agent Platforms &amp; Evals · MCP Server Developer · Human–AI Collaboration Researcher</h3>
<p><em>Ex-Oracle · JAXB · EclipseLink MOXy · JDK 9 · 16+ years shipping enterprise systems</em></p>
<p>
<a href="https://linkedin.com/in/marcelv3612"><img src="https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge" alt="LinkedIn: Connect"></a>
<a href="https://scholar.google.com/citations?user=fQUPwoQAAAAJ"><img src="https://img.shields.io/badge/Google_Scholar-Publications-4285F4?style=for-the-badge" alt="Google Scholar: Publications"></a>
<a href="https://www.researchgate.net/profile/Marcel-Valovy-2"><img src="https://img.shields.io/badge/ResearchGate-Profile-00CCBB?style=for-the-badge" alt="ResearchGate: Profile"></a>
<a href="https://stackoverflow.com/users/3832336/marcelv3612"><img src="https://img.shields.io/badge/StackOverflow-663-orange?style=for-the-badge" alt="Stack Overflow (663)"></a>
</p>
</div>

> **Evals first, architecture second.** I build agentic systems around golden sets, measured baselines and deterministic code wherever it fits. My work connects production AI engineering with research into developer autonomy, motivation and human–AI collaboration.

## 🚀 What I build

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>🚀 Current work</h3>

```rust
let focus = vec![
    "Evals-first agent platforms",
    "MCP + orchestration",
    "Knowledge-graph memory",
    "LLM cost + latency",
    "Rust trading systems",
    "AI agent payments",
];
```


<ul>
<li><strong>Founder @ <a href="https://tradeguard.software">TradeGuard</a>:</strong> AI trading infrastructure and Moira, an Enterprise Product Builder for eval-driven product development.</li>
<li><strong>AI Engineering Team Lead @ EuroWAG:</strong> touchless invoice pairing, an AI developer platform and AI-driven FinOps for fleet payments.</li>
<li><strong>Current client engagement @ FinnoCore:</strong> building a fintech payment and transaction core.</li>
<li><strong>Postdoctoral Researcher, part-time @ VŠE Prague:</strong> human–AI collaboration; PhD defended in October 2025.</li>
</ul>
<p><strong>Independent project · in development:</strong> payment infrastructure for AI agents, exploring x402, off-chain authorization and batched settlement.</p>
<p>My focus spans evals-first agent development, orchestration, enterprise MCP servers, knowledge-graph memory and retrieval, LLM routing, cost and latency engineering, and high-performance trading systems.</p>
</td>
<td width="50%" valign="top">
<h3>🤖 AI and agent stack</h3>
<p><strong>Orchestration:</strong> MCP servers; Claude Code skills, subagents and plugins; LangChain and LangGraph; Mixture-of-Agents, agent boards and the Agent Factory pattern.</p>
<p><strong>Developer tools:</strong> Claude Code, Cursor, Codex and Gemini CLI.</p>
<p><strong>Evals:</strong> agent-specific golden sets, cross-vendor LLM judging, precision/recall, hallucination rate, provenance, and median/p95 latency and cost budgets.</p>
<p><strong>Models:</strong> Anthropic Claude, Kimi, OpenAI APIs, Azure AI Foundry, AWS Bedrock, Hugging Face Transformers, Ollama and llama.cpp.</p>
<p><strong>Retrieval:</strong> Neo4j/Cypher, pgvectorscale and DiskANN on PostgreSQL, and hybrid BM25/vector search.</p>
</td>
</tr>
</table>

## 🧪 Agent platforms and evaluation

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>📡 aOS at Amdocs</h3>
<p>Built a green-field agentic platform with an agent board, planner, clerk and knowledge-graph memory. Strong individual-agent scores masked an application-level retrieval bottleneck, so I added golden sets for retrieval itself.</p>
<p>I replaced the LLM “data librarian” with deterministic, parameterised Cypher behind a narrow MCP tool, and revised the graph schemas and indexes.</p>
<h4>🔎 Illustrative MCP retrieval</h4>

```cypher
CALL db.index.fulltext.queryNodes(
  'entityIndex', $term
)
YIELD node AS e, score
CALL apoc.path.subgraphNodes(
  e, {maxLevel: $hops}
)
YIELD node AS ctx
RETURN e, score,
  collect(DISTINCT ctx) AS context
ORDER BY score DESC
LIMIT $k
```


<table width="100%">
<tr><th>Metric</th><th>Result</th></tr>
<tr><td>🎯 Retrieval precision/recall</td><td><strong>~50% → ~95%</strong></td></tr>
<tr><td>🧭 Provenance</td><td><strong>~50% → 90%+</strong></td></tr>
<tr><td>⚡ Median latency</td><td><strong>30 s → 1.1 s</strong></td></tr>
<tr><td>⏱️ p95 latency</td><td><strong>50 s → 1.8 s</strong></td></tr>
<tr><td>💸 Cost</td><td><strong>~10× lower</strong></td></tr>
</table>
<p><sub>Cost fell after removing retry loops.</sub></p>
<p>Latency includes the Haiku call interpreting results. The Agent Factory then enabled consultants to create agents over synthetic data without code, each with its own auto-generated golden set.</p>
</td>
<td width="50%" valign="top">
<h3>📈 Moira · Enterprise Product Builder</h3>
<h4>🔁 Illustrative evaluation flow</h4>

```python
golden = make_golden(agent.spec)
report = judge.cross_vendor(
    agent, golden,
    criteria=[
        "accuracy", "hallucinations",
        "provenance", "cost", "latency",
    ],
)
if report.passes(thresholds):
    release(agent)
else:
    revise_and_review(agent, report)
```


<p>Built <strong>Moira</strong>, an <strong>Enterprise Product Builder</strong> for eval-driven product development. Its trading-agent evaluation harness and Agent Factory features are <strong>in development</strong>, with execution through the TradeGuard platform.</p>
<ul>
<li><strong>Schools:</strong> each LLM vendor develops its own agents; another vendor and a human evaluate them.</li>
<li><strong>Lifecycle:</strong> ingest → design → backtest → forward-test → paper trading → live → archive.</li>
<li><strong>Knowledge graphs:</strong> world models and shared session context for agent coordination.</li>
<li><strong>Auditability:</strong> tracing and provenance are first-class design requirements.</li>
</ul>
<p>The evaluation design pairs each agent with a golden set and checks retrieval accuracy, hallucinations, provenance, cost and latency. Development is ongoing; lifecycle stages describe the intended progression.</p>
</td>
</tr>
</table>

## 🏦 AI engineering at EuroWAG

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>🧾 Touchless invoice pairing</h3>
<p>Fuzzy matching, targeted LLM resolution and human escalation for unresolved anomalies.</p>
<h4>⚙️ Illustrative pairing flow</h4>

```python
def pair(tx, items):
    match = score(tx, items)
    if match.resolved:
        return auto_pair(match)
    result = llm.resolve(match)
    return result or human_review(match)
```


<ul>
<li><strong>300 fuel vendors</strong> onboarded to fully touchless pairing.</li>

<li>Vendor verification using separated reference and hidden sets, regression runs, and production confirmation across billing cycles.</li>
<li>KPIs covering touchless share, matching coverage, pair correctness, LLM top-up coverage and escalation rate.</li>
</ul>
<table width="100%">
<tr><th>Invoice pairing</th><th>Result</th></tr>
<tr><td>🎯 Accuracy</td><td><strong>99.99%</strong></td></tr>
<tr><td>🚀 Straight-through processing</td><td><strong>98%</strong></td></tr>
<tr><td>🤖 Remaining cases</td><td><strong>2% handled by an LLM agent</strong></td></tr>
</table>
</td>
<td width="50%" valign="top">
<h3>🛠️ Developer platform and FinOps</h3>
<ul>
<li>Shared <strong>Claude Code toolkit</strong> used by <strong>~100 engineers</strong> across two units; team leads report <strong>10–20% faster delivery</strong>.</li>
<li><strong>AutoDoc:</strong> AI-generated, human-verified documentation for a <strong>19-service</strong> domain, with human-in-the-loop editing.</li>
<li>Enterprise knowledge base aggregated for agent context.</li>
<li>Founded an <strong>AI Guild</strong> and a <strong>biweekly AI Lab</strong>.</li>

<li>Follow-up FinOps campaign on shared platform subscriptions.</li>
</ul>
<h4>💶 AI-driven FinOps</h4>
<table width="100%">
<tr><th>Log Analytics</th><th>Result</th></tr>
<tr><td>Monthly spend</td><td><strong>€12.4k → €1.7k/month</strong></td></tr>
<tr><td>Reduction</td><td><strong>−86.5%</strong></td></tr>
<tr><td>Annual savings</td><td><strong>~€130k/year saved</strong></td></tr>
</table>
<p><sub>Confirmed on billed invoices.</sub></p>
</td>
</tr>
</table>

## 🛠️ Engineering toolkit and production impact

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>🧰 Core toolkit</h3>
<h4>💻 Languages</h4>

```text
Rust       ████████░░ Expert
Java       ██████████ Expert
Kotlin     ████████░░ Advanced
Python     ████████░░ Advanced
TypeScript ██████░░░░ Proficient
Cypher     ███████░░░ Advanced
```


<p><strong>Languages:</strong> Java (expert, 16+ years), Rust (expert), Kotlin and Python (advanced), TypeScript (proficient), Cypher (advanced).</p>
<h4>⚙️ Backend</h4>
<p> Spring Boot, Quarkus 3.x, Micronaut, Kafka, Debezium CDC, gRPC, GraphQL, REST and WebSockets; CQRS, Saga and Outbox patterns.</p>
<h4>☁️ Cloud</h4>
<p> Azure (expert), AWS, GCP, Kubernetes, Docker, Helm, Pulumi and GitLab CI/CD.</p>
<h4>🔭 Observability</h4>
<p> Honeycomb, Prometheus, Grafana and ELK.</p>
<h4>🗄️ Data</h4>
<p> PostgreSQL (expert), Neo4j, Cosmos DB, MongoDB, Redis, Elasticsearch, jOOQ, Hibernate and R2DBC.</p>
</td>
<td width="50%" valign="top">
<h3>📊 Production systems</h3>
<table width="100%">
<tr><th>Metric</th><th>Result</th></tr>
<tr><td>🎯 Trader success<br>TradeGuard</td><td><strong>90%<br>200+ validated</strong></td></tr>
<tr><td>💰 AI platform revenue</td><td><strong>800K CZK</strong></td></tr>
<tr><td>⚡ Trading latency<br>Rust engine</td><td><strong>&lt;10 ms</strong></td></tr>
<tr><td>🏦 Payment throughput</td><td><strong>600K+<br>transactions/hour</strong></td></tr>
<tr><td>📈 Fintech scale</td><td><strong>300K+<br>transaction writes/minute</strong></td></tr>
<tr><td>🧩 Production microservices</td><td><strong>200+</strong></td></tr>
<tr><td>🌍 Users served</td><td><strong>millions of users</strong></td></tr>
</table>
</td>
</tr>
</table>

## 🔬 Research in human–AI collaboration

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>🧠 Developer motivation and autonomy</h3>
<p><strong>PhD, VŠE Prague, defended October 2025:</strong> <a href="https://arxiv.org/abs/2511.00417"><em>Human-AI Programming Role Optimization: Developing a Personality-Driven Self-Determination Framework</em></a>.</p>
<p><strong>Key finding:</strong> AI-assisted development increases programmer motivation by <strong>23–65%</strong> when optimised for individual Big Five personality types and working styles through Self-Determination Theory.</p>
<p>I apply this work to agent leadership and support roles, interfaces that respect developer autonomy, measuring AI benefit beyond productivity, and enterprise adoption through the AI Guild and AI Lab.</p>
<table width="100%">
<tr><th>Research impact</th><th>Result</th></tr>
<tr><td>📝 Publications</td><td><strong>11 peer-reviewed publications</strong></td></tr>
<tr><td>📚 Citations</td><td><strong>73 citations</strong></td></tr>
<tr><td>🏆 Awards</td><td><strong>3 Best Paper Awards</strong></td></tr>
<tr><td>🎓 Teaching</td><td><strong>200+ students taught</strong></td></tr>
</table>
</td>
<td width="50%" valign="top">
<h3>📚 Selected publications</h3>
<ul>
<li><strong>PeerJ Computer Science (Q1):</strong> <a href="https://doi.org/10.7717/peerj-cs.2774">Personality-based pair programming</a>.</li>
<li><strong>IEEE ICSME (CORE-A):</strong> <a href="https://doi.org/10.1109/ICSME58846.2023.00050">The Psychological Effects of AI-Assisted Programming on Students and Professionals</a>; <strong>45 citations</strong>.</li>
<li><strong>EASE (CORE-A):</strong> Psychological Aspects of Pair Programming.</li>
<li><strong>ACIE ’25:</strong> Blockchain-Driven Transparent Research; <strong>Best Paper</strong>.</li>
<li><strong>CIMPS ’22:</strong> <strong>Best Paper</strong>.</li>
<li><strong>DD FIS VŠE ’22:</strong> <strong>Best Paper</strong>.</li>
<li><strong>PROFES 2026, accepted:</strong> <em>Delegation without Abdication</em>; qualitative study with <strong>13 developers</strong>.</li>
</ul>
<p><a href="https://scholar.google.com/citations?user=fQUPwoQAAAAJ">Publication list</a></p>
</td>
</tr>
</table>

## 🌟 Open source and enterprise foundations

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>☕ Oracle and Eclipse</h3>
<p>Designed and implemented <strong>Bean Validation (JSR 303)</strong> integration on both sides of Java XML binding.</p>
<ul>
<li><strong>JAXB:</strong> Bean Validation support in the XJC and JXC plugins; the BV-annotation package shipped in the <strong>JDK 9</strong> distribution.</li>
<li><strong>EclipseLink MOXy:</strong> integration released in <strong>EclipseLink 2.6 (2015)</strong>.</li>
<li><strong>57–92% performance improvements.</strong></li>
<li><strong>50+ merged Eclipse pull requests.</strong></li>
</ul>
<p><a href="https://www.eclipse.org/lists/eclipselink-dev/msg07133.html">EclipseLink committer</a> · <a href="https://github.com/eclipse-ee4j/eclipselink">EclipseLink repository</a></p>
</td>
<td width="50%" valign="top">
<h3>🎯 Enterprise experience and interests</h3>
<p><strong>16+ years</strong> across fintech, telecom, CRM, IoT and trading: EuroWAG, Amdocs, T-Mobile Czech Republic, Oracle, Home Credit International, Rockwell Automation, Ministry of Interior CZ, DNZ Finance and Adastra.</p>
<h4>🛠️ Building</h4>
<p> evals-first agent harnesses, enterprise MCP servers, knowledge-graph memory, and Rust/Python hybrid systems.</p>
<h4>🔎 Exploring</h4>
<p> AI unit economics per invoice, release and incident; agent payment protocols; autonomous orchestration; and browser automation with AI.</p>
</td>
</tr>
</table>

## 💬 Connect

<div align="center">

Open to agent-platform engineering, evals and reliability, MCP development, research collaboration and technical consulting.

**Prague / Remote-first · currently Asia** · [marcel@tradeguard.cz](mailto:marcel@tradeguard.cz) · [LinkedIn](https://linkedin.com/in/marcelv3612)

**Languages:** Czech · English · Russian

<p><em>“The best AI systems don’t replace humans; they amplify human judgment with superhuman data processing.”</em></p>

<h3>🏆 Quick Stats</h3>
<p>
<img src="https://img.shields.io/badge/Languages-Czech%20%7C%20English%20%7C%20Russian-blue?style=flat-square" alt="Languages: Czech, English and Russian">
<img src="https://img.shields.io/badge/Experience-16%2B%20years-green?style=flat-square" alt="Experience: 16+ years">
<img src="https://img.shields.io/badge/AI%2FML-Agents%20%7C%20Evals%20%7C%20MCP%20%7C%20KG-purple?style=flat-square" alt="AI/ML: Agents, Evals, MCP and Knowledge Graphs">
<img src="https://img.shields.io/badge/Publications-11-orange?style=flat-square" alt="Publications: 11">
<img src="https://img.shields.io/badge/Citations-73-red?style=flat-square" alt="Citations: 73">
</p>
</div>
