# Operately 实操评测：开源公司操作系统（2026-08-12 实测）

> 本文是 docs/13 的延伸——对调研中「最贴合公司管理体系」的开源项目 Operately 做真实部署评测。
> 部署环境：macOS (Apple Silicon) + Docker Desktop 29.5.1 · Operately 1.8.0 · 2026-08-12 实测

---

## 一、Operately 是什么

**定位**：开源公司操作系统（Open Source Company Operating System），用内置的「已验证流程」代替「空白画布」。

- 核心卖点：帮你协调目标、项目、团队——**不需要 COO**（这是它的原话）
- 适用：5-100人团队，技术公司/创业公司/非营利/咨询/合规导向组织
- 协议：Apache 2.0（可自托管、可商用）
- 语言：Elixir/Phoenix 后端 + React/TypeScript 前端 + GraphQL + PostgreSQL
- Star：~540（2026-08-12）

**它解决的问题**：Notion/ClickUp 给你无限自由但零指引；Operately 给你「内置节奏」——目标评审、项目 check-in、问责流程开箱即用。

---

## 二、功能模块（对应我们的体系）

| 模块 | 对应体系章节 | 说明 |
|:---|:---|:---|
| Goals / OKRs | 01 牵引层（考核） | 公司级目标→日常工作的链接 |
| Project Management | 04 纵向组织（协同） | 任务板、里程碑、check-in |
| Team Spaces | 04 部门 | 每个部门的家 |
| Message Boards | 04 沟通 | 替代邮件讨论 |
| Documents & Files | 05 数 | 文档中心 |
| Team Management | 10 人 | 入职/权限/结构 |
| Execution Cadence | 01 复盘 | 内置 check-in 节奏（周/月） |
| CLI & API | 05 数 | AI agent 可编程接入 |

---

## 三、部署实测（真实过程）

### 3.1 步骤

```bash
# 1. 下载单主机版
wget -q https://github.com/operately/operately/releases/latest/download/operately-single-host.tar.gz
tar -xzf operately-single-host.tar.gz
cd operately

# 2. 准备环境变量（install.sh 是交互式，自动化部署直接写 env）
cat > operately.env << 'EOF'
DB_HOST=db
DB_USER=postgres
DB_PASSWORD=<你的密码>
DB_NAME=operately-prod
MIX_ENV=prod
SECRET_KEY_BASE=<随机64位>
DATABASE_URL=ecto://postgres:<密码>@db/operately-prod
EOF

# 3. 启动（等待健康检查）
docker compose up -d --wait
```

### 3.2 ⚠️ 遇到的坑（实测记录）

| # | 坑 | 现象 | 解决 |
|:---|:---|:---|:---|
| 1 | **install.sh 是交互式的** | 会问域名/SSL/管理员邮箱 | 自动化部署直接手写 operately.env，跳过脚本 |
| 2 | **缺少 DATABASE_URL** | 启动崩溃：`environment variable DATABASE_URL is missing` | env 文件必须包含 `DATABASE_URL=ecto://postgres:密码@db/operately-prod` |
| 3 | **Apple Silicon 平台警告** | `image platform (linux/amd64) does not match (linux/arm64/v8)` | 官方镜像暂只有 amd64，Apple Silicon 走 Rosetta 模拟（功能正常但非原生性能） |
| 4 | **端口映射 80/443** | 默认绑 80/443，需 root 权限 | 本地评测改 `4000:4000` |

### 3.3 验证状态（2026-08-12 实测完成 ✅）

![Operately Dashboard](assets/operately-dashboard.png)

- [x] 容器启动（app + db）
- [x] 健康检查通过（/health → HTTP 200）
- [x] Web UI 可访问（:4000 → HTTP 200）
- [x] 初始化流程：设置公司 → 管理员账号 → 进入主界面（Spaces/Invite/General）
- [x] 数据库迁移（`Operately.Release.migrate()`）
- [x] 完整登录后主界面正常

> ✅ 实测声明（2026-08-12）：Operately 1.8.0 在 macOS Apple Silicon + Docker Desktop 29.5.1 完整部署成功，从下载到主界面约 15 分钟。

---

## 四、深度评价

### 4.1 优点

1. **有观点（Opinionated）**：这是最大优点——不是空白画布，内置了「怎么运营一家公司」的流程，正是中小公司缺的
2. **执行节奏内置**：check-in、目标评审自动化，解决「定了目标没人跟」的通病
3. **开源可自托管**：数据在自己手里（对比 Monday/Asana 的按人头收费）
4. **AI Agent 友好**：CLI + API + 官方 skills（Codex/Claude Code/OpenClaw），可以直接让 AI 帮你创建目标、更新项目、发 check-in——**这与本仓库的 AI 管理愿景一致**
5. **定价简单**：Flat rate（非按人头），对团队友好

### 4.2 缺点

1. **偏「软件团队」基因**：OKR/项目管理/文档为主，制造业的供应链/生产/品控模块缺失——需要和 ERP 配合
2. **Elixir 栈**：中小公司 IT 团队不一定熟悉（但单主机版 docker 部署不需要懂 Elixir）
3. **Apple Silicon 非原生**：amd64 镜像模拟运行，生产环境建议 x86 服务器
4. **生态年轻**：~540 star，插件/集成还在早期
5. **「不需要 COO」是双刃剑**：对 5-20 人很合适，50-100 人可能不够（没有 HR/财务深度模块）

### 4.3 与本体系的关系

```
本仓库（company-operating-system）   → 方法论：教你怎么管
Operately                            → 工具：帮你落地执行层
ERPNext/Odoo                        → 工具：帮你落地数底座（财务/库存）
```

**最佳组合**：
- 战略/复盘：本仓库方法论 + 你的经营会议
- 目标/项目节奏：Operately（OKR + check-in）
- 业财一体：ERPNext/Odoo/金蝶
- 决策：本仓库 08 章

---

## 五、结论

| 维度 | 评分（5分制） |
|:---|:---|
| 理念契合度 | ⭐⭐⭐⭐⭐（就是本体系要的「执行节奏」） |
| 部署难度 | ⭐⭐⭐⭐（docker 一条命令，但 env 配置有坑） |
| 功能完整度 | ⭐⭐⭐（目标/项目强，供应链/财务弱） |
| 成熟度 | ⭐⭐⭐（~540 star，功能可用但生态年轻） |
| 适合谁 | 5-50人团队，先建 OKR 和项目节奏，再用 ERP 补数底座 |

**一句话**：Operately 是「公司管理体系」最好的开源执行工具之一——它把「目标→项目→检查→复盘」的节奏内置了，这正是本体系 01 章要的。但它替代不了 ERP，更替代不了战略思考——方法论还是看本仓库 😄

---

> 📌 本文档随仓库持续更新；部署细节如有变动会在 Operately 上游更新后同步修订。
