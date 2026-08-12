# 18 · The AI Era: AI Practices for Every Layer (AI-Native Organizations)

> In 2026, the management paradigm is shifting from "people + tools" to "people + AI + tools."
> This chapter answers two questions:
> ① Within this book's eight-layer framework, where can each layer adopt AI right now?
> ② What does an "AI-native organization" look like, and how do you get there step by step?
>
> The author is himself an AI-organization practitioner (this repo is maintained jointly by a human founder + AI collaborators, with 20+ automated tasks deployed).

---

## 0. The Honest Bottom Line

- ✅ **AI can already be deployed in at least 6 of the 8 layers** — not in the future tense, but right now
- ⚠️ **What AI cannot replace**: strategic intuition, founder relationships, cultural inheritance, final accountability — these must stay with humans
- 📌 **The right posture**: AI is an "amplifier + advanced driver assistance," not "autonomous driving"
- 🎯 The 2026 dividing line: **for structured, repetitive tasks, AI can significantly cut per-task human hours — actual gains depend on data quality, process redesign, review costs, and model-call costs** (no unverified multiples promised; ROI must be measured per scenario)

---

## 1. The Eight-Layer Framework × AI Practice Map

> For each layer: what AI can do / which tools / maturity (🟢 production-ready · 🔵 semi-mature · 🟠 early stage)

### ① Strategy & Steering (strategy / budget / KPIs & performance / review)

| AI practice | What it does | Example tools | Maturity |
|:---|:---|:---|:---|
| Market intelligence | The macro/industry/competitor views of the Five Views — AI auto-aggregates news, research reports, and competitor moves | Intelligence radar (TrendRadar), AI search, research report summaries | 🟢 |
| Scenario planning | AI generates 2-4 future scenarios + contingency plans for each | LLM + prompt frameworks | 🔵 |
| Competitive monitoring | Auto-tracks competitor pricing / new products / hiring / funding | Crawlers + LLM summaries | 🟢 |
| Budget simulation | What-if: change one parameter and see the impact on net profit | BI + natural-language LLM queries | 🔵 |
| Review minutes | Monthly operating meetings auto-transcribed + variance attribution + action-item extraction | Speech-to-text + LLM | 🟢 |

**Case**: within the "Five Views" of Huawei's (Chinese technology giant) BLM, AI can significantly automate the **initial gathering and summarization** of macro, industry, and competitive information; information verification, customer insight, internal capability assessment, and strategic trade-offs still require humans.

### ② Governance (equity / ring-fencing / compliance)

| AI practice | What it does | Maturity |
|:---|:---|:---|
| Contract review | AI scans equity agreements, articles of association, and contracts for abnormal clauses | 🟢 |
| Compliance checks | AI checks whether related-party transaction pricing deviates from market prices (transfer-pricing red line) | 🔵 |
| Board materials | Auto-generates board reporting decks / monthly operating reports | 🟢 |
| Cross-border regulatory monitoring | AI tracks regulatory changes in target countries (e.g., PMTA/TPD for e-cigarettes) | 🟢 |

### ③ Value Chain (R&D / production / supply / sales / service)

| Stage | AI practice | Example tools | Maturity |
|:---|:---|:---|:---|
| Sales/business | AI auto-follows up leads, writes quotation emails, builds customer profiles | CRM AI, email AI | 🟢 |
| R&D | AI-assisted design (structure/circuit/code), patent search, competitor teardowns | Copilot, AI retrieval | 🟢 |
| PMC | AI predicts production scheduling, delivery dates, and material-kit completeness warnings | Forecasting models + ERP data | 🔵 |
| Production | AI visual QC (defect detection), predictive equipment maintenance | Industrial vision models | 🟢 |
| QC | Auto-generated inspection reports, customer-complaint classification and attribution | LLM + vision | 🟢 |
| Customer service | 24/7 AI customer service + automatic complaint classification/escalation | Chatbots | 🟢 |

**Highest-priority pilots for manufacturers**: visual QC + complaint classification + delivery-date prediction (highest ROI, fastest to implement).

### ④ Organization (departments & collaboration)

| AI practice | What it does | Maturity |
|:---|:---|:---|
| AI-agent employees | AI agents join departments as "virtual employees" (e.g., an "AI buyer," an "AI order tracker") | 🔵 |
| Process automation | RPA + AI handles documents / approvals / reconciliation automatically | 🟢 |
| Organizational knowledge base | A "company brain": all SOPs, documents, and experience fed to AI; employees Q&A anytime | 🟢 |
| Meeting minutes | Weekly/review meetings auto-minuted + task assignment | 🟢 |

### ⑤ Resource Foundation (people / finance / materials / data)

| Resource | AI practice | Maturity |
|:---|:---|:---|
| People | AI resume screening, interview-assessment support, onboarding Q&A | 🟢 |
| Finance | AI invoice recognition and booking, reconciliation, cash-flow forecasting, cost-anomaly alerts | 🟢 |
| Materials | AI sourcing and price comparison, supplier risk monitoring, supply-interruption warnings | 🔵 |
| Data | Natural-language BI queries (ask a question, get a report), automated data-quality checks | 🟢 |

**Case (this book's own practice)**: the author's team has turned "data" into an AI cockpit — revenue/margin/inventory/cash flow are aggregated automatically every day and pushed to Feishu (Lark, the Chinese workplace collaboration platform), where AI generates a daily operating report with anomalies flagged in red.

### ⑥ Moat

| AI practice | What it does | Maturity |
|:---|:---|:---|
| R&D speed | AI-assisted R&D = patents/new-product iteration at double speed | 🟢 |
| Data moat | Business data + AI analysis = insights competitors don't have | 🔵 |
| Operating efficiency | AI cost reduction = cost advantage = one of the hardest moats | 🟢 |
| Personalization | AI delivers one-to-one service/product configuration for every customer | 🔵 |

**Note**: AI is a "tool"; moats are still built from "people + organization + data." AI strengthens a moat but cannot conjure one out of thin air.

### ⑦ Risk & Compliance

| AI practice | What it does | Maturity |
|:---|:---|:---|
| Anti-fraud / anomaly detection | AI flags abnormal transactions, expense claims, and inventory shrinkage | 🟢 |
| Compliance monitoring | AI scans contracts/documents for compliance | 🔵 |
| Sentiment / crisis early warning | AI monitors brand sentiment, competitor negatives, and industry risks 24/7 | 🟢 |
| Audit support | AI sample selection, discovery of anomalous audit leads | 🔵 |

### ⑧ Decision Engine

| AI practice | What it does | Maturity |
|:---|:---|:---|
| Decision advisor | AI aggregates information → presents options/trade-offs/evidence chains to the CEO | 🟢 |
| Red-team challenger | AI plays devil's advocate: points out biases and blind spots in your decisions | 🔵 |
| Real-time cockpit | AI answers "what's the state of the company right now" anytime | 🟢 |
| Post-decision analysis | AI tracks outcomes and tests assumptions after a decision | 🔵 |

**Key point**: AI is the advisor, not the commander. Final decision authority, accountability, and trust must remain with people.

---

## 2. AI-Native Organizations: Three Forms

> The three forms are not a timeline or a linear progression — **a single company can combine them**: customer service on AI agents, finance still on copilots, R&D already at process-level automation. The distinguishing dimension is "how deeply AI participates in the business."

### Form 1: AI-Enhanced (tool augmentation)

```
Traditional organization + AI tools
Humans do everything; AI makes them faster
e.g., employees use AI to write emails, build reports, look things up
```

**How to tell**: AI is a personal tool — no persistent state, no direct calls into business systems, decision authority unchanged.

### Form 2: AI-Collaborative (role-level collaboration)

```
Humans + AI agents form the team together
AI is a "member": it has its own role, tasks, and deliverables
e.g., an AI sales assistant auto-follows leads, an AI QC inspector watches the line 24/7,
an AI finance assistant reconciles accounts
```

**How to tell**: AI has a role and long-term context, can call into some business systems to execute bounded tasks, and key actions require human review.

**This repo's author's practice**: this repo is maintained jointly by a "human founder + AI collaborators" — AI handles content drafting, deployment reviews, and document generation; humans handle judgment, direction, and final approval. It is a minimal specimen of Form 2.

### Form 3: AI-Native (process/organization redesign, exploratory stage)

```
Core processes, data, and accountabilities are designed around human-AI collaboration
AI drives bounded processes; humans supervise, decide, and handle exceptions
e.g., AI executes bounded tasks within functional processes like sales/customer service/finance,
while humans manage goals, permissions, and red lines
```

**How to tell**: core processes are redesigned around human-AI collaboration; AI has persistent state, can execute actions, and operates within permission boundaries with audit logs.

> ⚠️ **Honest warning**: Form 3 today is mostly "demos run, production unverified." Production deployment should start with **a single process, least privilege, and reversible actions** — don't let AI autonomously run cross-department operations from day one.

### Open-Source Exploration Projects (snapshot 2026-08-12; ⭐ = that day's value)

| Repo | ⭐ | Claimed positioning | Actually public components | Evidence level |
|:---|:---|:---|:---|:---|
| [Claw-Company/clawcompany](https://github.com/Claw-Company/clawcompany) | 583 | AI company OS: 38 roles / 6 templates / 4-layer memory | Role templates + memory system, TypeScript | README/demo |
| [getnao/sylph](https://github.com/getnao/sylph) | 178 | Company brain: AI agents + skills + self-improvement | MCP integration + agent framework, JavaScript | README/demo |
| [Lifecycle-Innovations-Limited/claude-ops](https://github.com/Lifecycle-Innovations-Limited/claude-ops) | 114 | Claude Code enterprise operations: 57 skills / 21 agents | Claude Code skill pack + integration | README/demo |
| [yomidenzel/BOS](https://github.com/yomidenzel/BOS) | 130 | Turn Claude into a COO (10 AI skills) | Claude Code skill pack (French) | README/demo |
| [felipeluissalgueiro/hive](https://github.com/felipeluissalgueiro/hive) | 20 | Run a company with Claude Code squads | Multi-agent harness, HTML | Early prototype |
| [10Legs/ceo-f500-harness](https://github.com/10Legs/ceo-f500-harness) | 8 | 15 executive agents + decision-permission matrix | Agent prompts + workflows | Early prototype |

> ⚠️ **A note on evidence**: ⭐ is a same-day snapshot and does not indicate adoption or production maturity. The "evidence level" column is based on public READMEs/directories/examples; whether something is production-ready must be verified by you (tests, deployment docs, production case studies).

---

## 3. The Four Steps from Traditional to AI-Native Organization

### Step 1: The Data Foundation (0-3 months)

Without data, AI spins its wheels. Build the "data" foundation first (Ch. 05):
- [ ] Get ERP/CRM running with clean data
- [ ] Operating cockpit (daily revenue / margin / cash flow / inventory)
- [ ] Feed AI with 3+ months of historical data

### Step 2: Pilot 3 High-ROI Scenarios (3-6 months)

Prioritize scenarios that are "high-frequency, repetitive, data-backed, and fault-tolerant":

| Scenario | Why first | Time to results |
|:---|:---|:---|
| AI customer service / complaint classification | High frequency, data already available | 2-4 weeks |
| AI daily operating report / review | Simple, immediately useful | 1-2 weeks |
| AI visual QC | Highest ROI | 1-3 months |
| AI sales-lead follow-up | Direct revenue upside | 1-2 months |

### Step 3: From "AI Tool" to "AI Team Member" (6-12 months)

- Give AI agents explicit roles (AI buyer / AI order tracker / AI finance assistant)
- Define its "input → task → output → reviewer" contract
- Establish AI permission boundaries (what it can see, what it can do, what it can't do)

### Step 4: Build AI Governance (in parallel with pilots, not after)

> ⚠️ **Governance is not something you start at step 4** — establish minimal governance before the first pilot, or AI will enter the business ahead of the rules. Step 4 is about systematizing governance.

- **AI asset inventory**: which models/tools/agents are used, who is responsible, where data flows
- **Data lineage and permissions**: what data AI can see, who can grant access, sensitive data (customer privacy / trade secrets) isolated
- **Least-privilege principle**: AI is read-only by default; executing actions requires approval; tool calls are auditable
- **Prompt-injection and data-exfiltration defenses**: documents/inputs AI processes may carry malicious instructions; sandboxing/filtering required
- **Human review of AI output**: key decisions and external-facing documents must be human-reviewed
- **AI audit logs**: what AI did, on what basis, who approved it
- **Incident response**: what to do when AI errs or exceeds its authority, how to roll back
- **Human-AI division of labor**: what stays permanently human (strategy / relationships / accountability / innovation)
- **Model change management**: assess impact before swapping models or changing prompts; maintain an evaluation set

### Cross-Cutting AI Capabilities (infrastructure shared by all layers)

- Software engineering / IT service desk / DevOps automation
- Cybersecurity operations and data governance
- Marketing content localization and process mining
- Model/prompt evaluation sets, red-team testing
- AI vendor management and procurement

---

## 4. Ready-to-Use Templates: AI Practice Checklists

### Department-Level AI Pilot Application Form

```
Department: __________
Pain point (one sentence): __________
What AI can do: __________
Data required: __________
Estimated savings in people/time: __________
Risks & fault tolerance: __________
Pilot duration: __________
Reviewer: __________
```

### Human-AI Division of Labor

| Task | Human | AI assists | AI fully automated | Reviewer |
|:---|:---|:---|:---|:---|
| Strategic direction | ✅ | ✅ intelligence | ❌ | — |
| Customer quotes | ✅ final call | ✅ price suggestion | ❌ | CEO |
| Complaint classification | ❌ | ❌ | ✅ | QC department |
| Daily operating report | ❌ | ❌ | ✅ | Finance |
| Large purchases | ✅ approval | ✅ price comparison | ❌ | General manager |
| Contract initial review | ✅ final review | ✅ pre-review | ❌ | Legal / owner |

---

## 5. Risks and Boundaries (must be honest)

| Risk | Description | Countermeasure |
|:---|:---|:---|
| AI hallucination | AI confidently makes things up | Key decisions must be human-verified + give AI data sources |
| Data security | Trade secrets fed to cloud AI | Use local/private deployment for sensitive data (e.g., Ollama) |
| Over-reliance | Human judgment atrophies | Schedule regular "no-AI days" to exercise judgment |
| Agent going rogue | AI does things it shouldn't | Permission boundaries + audit logs + red-line checklist |
| Fake efficiency | Demos look good but aren't really used | Pilots must quantify ROI; cut them if they fall short |

---

## 6. One-Line Summary

> **An AI-native organization is not about "replacing people with AI" — it's about using AI to free human energy from repetitive work and focus it on judgment, relationships, and innovation.**
> Start with the data foundation, pilot 3 high-ROI scenarios, then make AI a team member, and finally build AI governance.
> A company that skips AI practice in 2026 is like a company that skipped smartphones in 2010.

---

## Contributing

PRs welcome:
- AI practice cases from your industry (manufacturing / cross-border / services / finance…)
- Hands-on AI tool reviews (what works / pitfalls / cost)
- Real experiment logs from AI-native organizations
- Failure cases: why AI pilots failed (the most valuable)
