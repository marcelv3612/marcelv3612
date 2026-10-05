# Marcel Valový, PhD

<div align="center">
<p><strong>AI Engineering Team Lead · Founder of TradeGuard<br>Agent Platforms &amp; Evals · MCP Server Developer · Human–AI Collaboration Researcher</strong></p>
<p><em>Ex-Oracle · JAXB · EclipseLink MOXy · JDK 9 · 16+ years shipping enterprise systems</em></p>
<p>
<a href="https://linkedin.com/in/marcelv3612">LinkedIn</a> ·
<a href="https://scholar.google.com/citations?user=fQUPwoQAAAAJ">Google Scholar</a> ·
<a href="https://www.researchgate.net/profile/Marcel-Valovy-2">ResearchGate</a> ·
<a href="https://stackoverflow.com/users/3832336/marcelv3612">Stack Overflow (663)</a>
</p>
</div>

**Evals first, architecture second.** I build agentic systems around golden sets, measured baselines and deterministic code wherever it fits. My work connects production AI engineering with research into developer autonomy, motivation and human–AI collaboration.

## What I build

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>Current work</h3>
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
<h3>AI and agent stack</h3>
<p><strong>Orchestration:</strong> MCP servers; Claude Code skills, subagents and plugins; LangChain and LangGraph; Mixture-of-Agents, agent boards and the Agent Factory pattern.</p>
<p><strong>Developer tools:</strong> Claude Code, Cursor, Codex and Gemini CLI.</p>
<p><strong>Evals:</strong> agent-specific golden sets, cross-vendor LLM judging, precision/recall, hallucination rate, provenance, and median/p95 latency and cost budgets.</p>
<p><strong>Models:</strong> Anthropic Claude, Kimi, OpenAI APIs, Azure AI Foundry, AWS Bedrock, Hugging Face Transformers, Ollama and llama.cpp.</p>
<p><strong>Retrieval:</strong> Neo4j/Cypher, pgvectorscale and DiskANN on PostgreSQL, and hybrid BM25/vector search.</p>
</td>
</tr>
</table>

## Agent platforms and evaluation

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>aOS at Amdocs</h3>
<p>Built a green-field agentic platform with an agent board, planner, clerk and knowledge-graph memory. Strong individual-agent scores masked an application-level retrieval bottleneck, so I added golden sets for retrieval itself.</p>
<p>I replaced the LLM “data librarian” with deterministic, parameterised Cypher behind a narrow MCP tool, and revised the graph schemas and indexes.</p>
<ul>
<li><strong>Retrieval precision/recall:</strong> ~50% → ~95%.</li>
<li><strong>Provenance:</strong> ~50% → 90%+.</li>
<li><strong>Median latency:</strong> 30 s → 1.1 s.</li>
<li><strong>p95 latency:</strong> 50 s → 1.8 s.</li>
<li><strong>Cost:</strong> ~10× lower after removing retry loops.</li>
</ul>
<p>Latency includes the Haiku call interpreting results. The Agent Factory then enabled consultants to create agents over synthetic data without code, each with its own auto-generated golden set.</p>
</td>
<td width="50%" valign="top">
<h3>Moira · Enterprise Product Builder</h3>
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

## AI engineering at EuroWAG

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>Touchless invoice pairing</h3>
<p>Fuzzy matching, targeted LLM resolution and human escalation for unresolved anomalies.</p>
<ul>
<li><strong>300 fuel vendors</strong> onboarded to fully touchless pairing.</li>
<li><strong>99.99% accuracy</strong> and <strong>98% straight-through processing</strong>; the remaining <strong>2% of cases</strong> are handled by an LLM agent.</li>
<li>Vendor verification using separated reference and hidden sets, regression runs, and production confirmation across billing cycles.</li>
<li>KPIs covering touchless share, matching coverage, pair correctness, LLM top-up coverage and escalation rate.</li>
</ul>
</td>
<td width="50%" valign="top">
<h3>Developer platform and FinOps</h3>
<ul>
<li>Shared <strong>Claude Code toolkit</strong> used by <strong>~100 engineers</strong> across two units; team leads report <strong>10–20% faster delivery</strong>.</li>
<li><strong>AutoDoc:</strong> AI-generated, human-verified documentation for a <strong>19-service</strong> domain, with human-in-the-loop editing.</li>
<li>Enterprise knowledge base aggregated for agent context.</li>
<li>Founded an <strong>AI Guild</strong> and a <strong>biweekly AI Lab</strong>.</li>
<li><strong>Log Analytics spend:</strong> €12.4k → €1.7k/month, <strong>−86.5%</strong>, confirmed on billed invoices; <strong>~€130k/year saved</strong>.</li>
<li>Follow-up FinOps campaign on shared platform subscriptions.</li>
</ul>
</td>
</tr>
</table>

## Engineering toolkit and production impact

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>Core toolkit</h3>
<p><strong>Languages:</strong> Java (expert, 16+ years), Rust (expert), Kotlin and Python (advanced), TypeScript (proficient), Cypher (advanced).</p>
<p><strong>Backend:</strong> Spring Boot, Quarkus 3.x, Micronaut, Kafka, Debezium CDC, gRPC, GraphQL, REST and WebSockets; CQRS, Saga and Outbox patterns.</p>
<p><strong>Cloud:</strong> Azure (expert), AWS, GCP, Kubernetes, Docker, Helm, Pulumi and GitLab CI/CD.</p>
<p><strong>Observability:</strong> Honeycomb, Prometheus, Grafana and ELK.</p>
<p><strong>Data:</strong> PostgreSQL (expert), Neo4j, Cosmos DB, MongoDB, Redis, Elasticsearch, jOOQ, Hibernate and R2DBC.</p>
</td>
<td width="50%" valign="top">
<h3>Production systems</h3>
<ul>
<li><strong>90% trader success</strong> at TradeGuard, with <strong>200+ validated</strong>.</li>
<li><strong>800K CZK</strong> AI platform revenue.</li>
<li><strong>&lt;10 ms</strong> trading latency with a Rust engine.</li>
<li><strong>600K+ transactions/hour</strong> payment throughput.</li>
<li><strong>300K+ transaction writes/minute</strong> fintech scale.</li>
<li><strong>200+ production microservices</strong> and systems serving <strong>millions of users</strong>.</li>
</ul>
</td>
</tr>
</table>

## Research in human–AI collaboration

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>Developer motivation and autonomy</h3>
<p><strong>PhD, VŠE Prague, defended October 2025:</strong> <a href="https://arxiv.org/abs/2511.00417"><em>Human-AI Programming Role Optimization: Developing a Personality-Driven Self-Determination Framework</em></a>.</p>
<p><strong>Key finding:</strong> AI-assisted development increases programmer motivation by <strong>23–65%</strong> when optimised for individual Big Five personality types and working styles through Self-Determination Theory.</p>
<p>I apply this work to agent leadership and support roles, interfaces that respect developer autonomy, measuring AI benefit beyond productivity, and enterprise adoption through the AI Guild and AI Lab.</p>
<p><strong>11 peer-reviewed publications · 73 citations · 3 Best Paper Awards · 200+ students taught</strong></p>
</td>
<td width="50%" valign="top">
<h3>Selected publications</h3>
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

## Open source and enterprise foundations

<table width="100%">
<tr>
<td width="50%" valign="top">
<h3>Oracle and Eclipse</h3>
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
<h3>Enterprise experience and interests</h3>
<p><strong>16+ years</strong> across fintech, telecom, CRM, IoT and trading: EuroWAG, Amdocs, T-Mobile Czech Republic, Oracle, Home Credit International, Rockwell Automation, Ministry of Interior CZ, DNZ Finance and Adastra.</p>
<p><strong>Building:</strong> evals-first agent harnesses, enterprise MCP servers, knowledge-graph memory, and Rust/Python hybrid systems.</p>
<p><strong>Exploring:</strong> AI unit economics per invoice, release and incident; agent payment protocols; autonomous orchestration; and browser automation with AI.</p>
</td>
</tr>
</table>

## Connect

Open to agent-platform engineering, evals and reliability, MCP development, research collaboration and technical consulting.

**Prague / Remote-first · currently Asia** · [marcel@tradeguard.cz](mailto:marcel@tradeguard.cz) · [LinkedIn](https://linkedin.com/in/marcelv3612)

**Languages:** Czech · English · Russian
