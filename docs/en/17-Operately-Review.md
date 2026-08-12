# Operately Deployment Review: The Open-Source Company Operating System (tested 2026-08-12)

> This article extends docs/13 — a hands-on deployment review of Operately, the open-source project from that survey which best fits this management framework.
> Test environment: macOS (Apple Silicon) + Docker Desktop 29.5.1 · Operately 1.8.0 · tested 2026-08-12

---

## 1. What Is Operately

**Positioning**: an open-source company operating system that replaces the "blank canvas" with built-in "validated processes."

- Core selling point: helps you align goals, projects, and teams — "no COO required" (their words)
- For: teams of 5-100 people; tech companies, startups, nonprofits, consultancies, compliance-oriented organizations
- License: Apache 2.0 (self-hostable, commercial use allowed)
- Stack: Elixir/Phoenix backend + React/TypeScript frontend + GraphQL + PostgreSQL
- Stars: ~540 (as of 2026-08-12)

**The problem it solves**: Notion/ClickUp give you unlimited freedom but zero guidance; Operately gives you "built-in cadence" — goal reviews, project check-ins, and accountability flows out of the box.

---

## 2. Feature Modules (mapped to our framework)

| Module | Framework chapter | Description |
|:---|:---|:---|
| Goals / OKRs | 01 Strategy & Steering (KPIs & performance) | Links company-level goals to daily work |
| Project Management | 04 Organization (collaboration) | Task boards, milestones, check-ins |
| Team Spaces | 04 Organization (departments) | A home for every department |
| Message Boards | 04 Organization (communication) | Replaces email-thread discussions |
| Documents & Files | 05 Resource Foundation (data) | Document hub |
| Team Management | 10 People & Iceberg Model | Onboarding, permissions, structure |
| Execution Cadence | 01 Strategy & Steering (review) | Built-in check-in rhythm (weekly/monthly) |
| CLI & API | 05 Resource Foundation (data) | Programmatic access for AI agents |

---

## 3. Hands-On Deployment (the real process)

### 3.1 Steps

```bash
# 1. Download the single-host build
wget -q https://github.com/operately/operately/releases/latest/download/operately-single-host.tar.gz
tar -xzf operately-single-host.tar.gz
cd operately

# 2. Prepare environment variables (install.sh is interactive; for automated deployment, write the env file directly)
cat > operately.env << 'EOF'
DB_HOST=db
DB_USER=postgres
DB_PASSWORD=<your password>
DB_NAME=operately-prod
MIX_ENV=prod
SECRET_KEY_BASE=<random 64 chars>
DATABASE_URL=ecto://postgres:<password>@db/operately-prod
EOF

# 3. Start (wait for the health check)
docker compose up -d --wait
```

### 3.2 ⚠️ Pitfalls Encountered (recorded during testing)

| # | Pitfall | Symptom | Fix |
|:---|:---|:---|:---|
| 1 | **install.sh is interactive** | Asks for domain/SSL/admin email | For automated deployment, write operately.env by hand and skip the script |
| 2 | **DATABASE_URL missing** | Crashes on startup: `environment variable DATABASE_URL is missing` | The env file must include `DATABASE_URL=ecto://postgres:<password>@db/operately-prod` |
| 3 | **Apple Silicon platform warning** | `image platform (linux/amd64) does not match (linux/arm64/v8)` | Official images are amd64-only for now; Apple Silicon runs them under Rosetta emulation (works fine, but not native performance) |
| 4 | **Port mapping 80/443** | Binds to 80/443 by default, requiring root | For local review, change to `4000:4000` |

### 3.3 Verification Status (test completed 2026-08-12 ✅)

![Operately Dashboard](assets/operately-dashboard.png)

- [x] Container startup (app + db)
- [x] Health check passed (/health → HTTP 200)
- [x] Web UI reachable (:4000 → HTTP 200)
- [x] Initialization flow: set up company → admin account → main UI (Spaces/Invite/General)
- [x] Database migration (`Operately.Release.migrate()`)
- [x] Main UI works after full login

> ✅ Tested (2026-08-12): Operately 1.8.0 deployed successfully on macOS Apple Silicon + Docker Desktop 29.5.1; about 15 minutes from download to main UI.

---

## 4. In-Depth Assessment

### 4.1 Strengths

1. **Opinionated**: this is the biggest strength — it's not a blank canvas; it ships with "how to run a company" built in, exactly what SMBs lack
2. **Built-in execution cadence**: automated check-ins and goal reviews solve the classic "we set goals and nobody follows up" problem
3. **Open source and self-hostable**: your data stays in your hands (versus Monday/Asana's per-seat pricing)
4. **AI-agent friendly**: CLI + API + official skills (Codex/Claude Code/OpenClaw) — you can have AI create goals, update projects, and post check-ins for you. **This aligns with this repo's AI-management vision**
5. **Simple pricing**: flat rate (not per seat), friendly to teams

### 4.2 Weaknesses

1. **Software-team DNA**: oriented toward OKRs/project management/docs; supply chain, production, and QC modules for manufacturing are missing — you'll need an ERP alongside it
2. **Elixir stack**: SMB IT teams may not know Elixir (though the single-host Docker deployment doesn't require it)
3. **Not native on Apple Silicon**: amd64 images run under emulation; for production, use x86 servers
4. **Young ecosystem**: ~540 stars; plugins and integrations are still early-stage
5. **"No COO required" cuts both ways**: great for 5-20 people, possibly insufficient at 50-100 (no deep HR/finance modules)

### 4.3 Relationship to This Framework

```
This repo (company-operating-system)   → Methodology: teaches you how to manage
Operately                              → Tool: executes the execution layer for you
ERPNext/Odoo                          → Tool: executes the data foundation for you (finance/inventory)
```

**Best combination**:
- Strategy/review: this repo's methodology + your own operating meetings
- Goals/project cadence: Operately (OKRs + check-ins)
- Finance-integrated operations: ERPNext/Odoo/Kingdee (Chinese ERP vendor)
- Decision-making: Ch. 08 of this repo

---

## 5. Conclusion

| Dimension | Score (out of 5) |
|:---|:---|
| Philosophical fit | ⭐⭐⭐⭐⭐ (exactly the "execution cadence" this framework calls for) |
| Ease of deployment | ⭐⭐⭐⭐ (one Docker command, but env config has pitfalls) |
| Feature completeness | ⭐⭐⭐ (strong on goals/projects, weak on supply chain/finance) |
| Maturity | ⭐⭐⭐ (~540 stars; usable, but the ecosystem is young) |
| Best for | Teams of 5-50; build OKR + project cadence first, then fill the data foundation with an ERP |

**In one sentence**: Operately is one of the best open-source execution tools for a company-management framework — it bakes in the "goals → projects → check-ins → reviews" cadence that Ch. 01 of this framework calls for. But it can't replace an ERP, let alone strategic thinking — for methodology, stick with this repo 😄

---

> 📌 This document is updated continuously with the repo; deployment details will be revised in sync when Operately's upstream changes.
