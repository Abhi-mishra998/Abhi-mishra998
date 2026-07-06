# Abhishek Mishra

**AI Infrastructure Engineer** · Hyderabad, India
Building the runtime layer that makes autonomous AI agents safe to deploy in production.

[aegisagent.in](https://aegisagent.in) · [portfolio](https://portfolio-self-seven-1zphd40voq.vercel.app) · [blog](https://projectsphere.hashnode.dev) · [linkedin.com/in/abhishek-mishra-eng](https://www.linkedin.com/in/abhishek-mishra-eng/) · abhishekmishra09896@gmail.com

---

I design and ship production AI systems and the cloud infrastructure that keeps them reliable. My focus is the boundary between autonomous agents and the systems they act on — the layer that decides which actions run, blocks the ones that shouldn't, and produces a cryptographically verifiable record of everything that happened.

Currently AI Infrastructure Engineer at **ByteHubble.ai**, **AWS Community Builder** in the AI Engineering category, and creator of **Aegis** — an open-source runtime security control plane for AI agents.

**Open to** senior AI Engineering / AI Infrastructure / Platform Engineering / Backend Engineering / Cloud Engineering roles. On-site · Hybrid · Remote. Based in Hyderabad, open to Gurugram, Bangalore, Mumbai, Pune.

---

## Flagship work

### Aegis — Runtime security control plane for autonomous AI agents

Every tool call an AI agent makes is intercepted, authenticated, policy-checked, risk-scored on behavioral signals, and cryptographically logged **before** it executes. Blocks the dangerous action before it runs; produces an audit chain any external auditor can verify offline.

**Live** [aegisagent.in](https://aegisagent.in) · **Source** [Abhi-mishra998/aegis](https://github.com/Abhi-mishra998/aegis) · **Engineering deep dive** [projectsphere.hashnode.dev](https://projectsphere.hashnode.dev/i-built-a-runtime-firewall-for-ai-agents) · **License** Apache 2.0

- **12 microservices · 24 Docker containers · 510+ pytest cases · < 30 ms p95** on the deny path, < 72 ms p50 end-to-end
- **5,400+ AI governance decisions** processed in the first production window
- **10,000+ adversarial security scenarios** run against the platform before beta open — every failure mode published
- **Cryptographic trust chain** — per-decision ed25519 receipts, HMAC-chained across 16 shards, daily Merkle root, all offline-verifiable with a two-line CLI (`acp verify-chain`)
- **Runtime kill switch** dual-writes Redis + Postgres; verified to survive a `FLUSHDB` mid-incident
- **Autonomy contracts** enforce per-agent action budgets, deny-lists, and approval-required lists in code, not comments
- **Identity graph** — Postgres-native compromise simulation returns quantified blast radius at BFS depth 3
- **SDKs on PyPI:** `aegis-anthropic` · `aegis-openai` · `aegis-langchain` · `aegis-bedrock` · `aegis-aevf`
- **Reference deployment on AWS `ap-south-1`:** Auto Scaling Group + ALB + RDS PostgreSQL Multi-AZ + ElastiCache Redis + WAFv2 + multi-region CloudTrail + customer-managed KMS, all provisioned by Terraform

**Stack** — Python 3.11 · FastAPI · PostgreSQL 15 · Redis 7 · OPA/Rego · Docker · Kubernetes · Terraform · AWS · React 18 · Prometheus · Grafana · Jaeger

Aligned to **OWASP Agentic Top-10** and drafted against **EU AI Act** operator controls.

---

### Revora — Revenue Recovery OS for Indian B2B service businesses

Proposals, invoices, AI follow-ups, and recovery analytics on one dashboard. Every recommendation is backed by evidence — days silent, unanswered follow-ups, days overdue — not opaque AI scores. In beta with ByteHubble and one external design partner.

**Live** [revenue-recovery-os1.vercel.app](https://revenue-recovery-os1.vercel.app) · **Source** [Abhi-mishra998/revenue-recovery-os](https://github.com/Abhi-mishra998/revenue-recovery-os) · **90-second walkthrough** [Drive](https://drive.google.com/file/d/1fYYko3czhO7s8P7IijeGuUOexBnRzTzw/view)

- **Signed audit chain** on every write — ed25519 signature + hash-chained to the previous entry; tamper is detectable, not just discouraged
- **PostgreSQL Row-Level Security** for multi-tenancy — the database refuses cross-tenant reads even if the app forgets a `WHERE`
- **PII redact-before-LLM** — emails, phones, PAN, GSTIN, Aadhaar never leave your infrastructure in cleartext; rehydration on the way back
- **Value-tier model routing** — cheap proposals route to Claude Haiku 4.5, high-value proposals to stronger models; cost stays proportional to stakes
- **AI kill-switch** — one admin toggle disables every LLM endpoint (outage, cost runaway, jailbreak)
- **Dual-engine DB** — PostgreSQL 16 + pgvector in production, MongoDB 7 warm as rollback path
- **DPDP export + delete** — one-click JSON export and cascade-delete of every record, both audit-signed (India DPDP Act, 2023 compliant)

**Stack** — FastAPI · PostgreSQL 16 + pgvector · React 19 · Tailwind · shadcn/ui · Anthropic Claude Haiku 4.5 · Neon · Render · Vercel

---

### ZyntraOps — AI-powered autonomous SRE for Kubernetes

Detects incidents, runs root-cause analysis, and executes safe remediation actions on Kubernetes clusters. Hybrid pipeline — deterministic rules for known failures (`CrashLoopBackOff`, `OOMKilled`, `ImagePullBackOff`), LLM reasoning for the long tail. Safety guardrails on every action.

**Source** [Abhi-mishra998/ZyntraOps](https://github.com/Abhi-mishra998/ZyntraOps)

- **MTTR from 30–60 minutes to < 10 seconds** in simulated incident scenarios
- Guardrails: bounded rollback, pod-restart caps, human-approval for cluster-scoped operations
- Prometheus-native observability integration
- FastAPI backend · React frontend · PostgreSQL state store

Related: [SentinelOps](https://github.com/Abhi-mishra998/SentinelOps) (real-time incident detection + RCA + automated remediation on K8s), [Astrixion](https://github.com/Abhi-mishra998/Astrixion) (autonomous SRE decision engine with hybrid policy + LLM reasoning + reinforcement-style execution).

---

## Adjacent work I ship on top of Aegis

- **[Aegis-avatar-agent](https://github.com/Abhi-mishra998/Aegis-avatar-agent)** — a talking avatar of me wired to the Aegis knowledge base. Real-time conversation instead of documentation browsing. Turn detection, streaming responses, WebRTC.
- **Voice agent for Aegis onboarding** — Deepgram Nova-3 STT → hybrid BM25 + embeddings + reranker retrieval → Groq Llama-3.1-8B-Instant reasoning → Cartesia Sonic-3 TTS, orchestrated with LiveKit Agents. Users ask "how does the kill switch work?" and get answers in seconds instead of reading 200 pages of docs.
- **[bigquery-agent-gcp](https://github.com/Abhi-mishra998/bigquery-agent-gcp)** — natural-language BigQuery agent with schema-aware SQL generation and safety rails.

---

## Experience

**AI Infrastructure Engineer — ByteHubble.ai** *Jul 2025 – Present · Hyderabad · On-site*
Architected and shipped [Aegis](https://github.com/Abhi-mishra998/aegis). Design and build AI-powered applications and autonomous agent workflows using LLMs, RAG, MCP, Python, FastAPI, PostgreSQL, AWS. Automate cloud infrastructure and deployment workflows using Docker, Kubernetes, Terraform. Own backend services, APIs, data pipelines for production customer and internal platforms. Partner with founders on platform architecture, technical strategy, and customer demonstrations.

**AWS Community Builder — AI Engineering** *Mar 2026 – Present · Remote · Part-time*
Selected for contributions to cloud infrastructure and AI engineering community. Share technical content, open-source projects, and discussions on AWS, Kubernetes, Terraform, and AI systems.

**AI Engineer Intern — ByteHubble.ai** *Jul 2024 – Jul 2025 · Remote*
Built AI features and backend services in Python + FastAPI + PostgreSQL + AWS. Integrated LLM applications with databases and third-party APIs. Assisted with cloud-native deployments, monitoring, CI/CD automation using Docker and AWS.

**Cyber Security Specialist Intern — Cyber Vidyapeeth Foundation** *Jul – Sep 2023*
Built a Python packet sniffer using Scapy + socket programming. Real-time network traffic analysis to identify protocols and anomalies.

Earlier — NPTEL Intern (cloud-hosted app on AWS, Grade A++), System Specialist at AICTE (IoT prototypes).

---

## Recognition & funding

- **AWS Community Builder** — AI Engineering category (Mar 2026 – Present)
- **$500 community-builders grant** — awarded for early Aegis development
- **$300 AWS League ML leaderboard prize** — arrived at exactly the right moment
- **AWS startup credits** — funded the jump from local Mac to production AWS infrastructure
- **NPTEL Discipline Star** — IIT Madras (Top Performer Recognition, 20+ credits across CS courses)
- **Advanced DevOps & Cloud Engineering Program** — HCL GUVI, Grade A (credential yetw992casnhg267)
- **Oracle Certified Associate** — OCI Foundations
- **Outstanding Student Leadership Award** — Panipat Institute of Engineering and Technology
- **Best Leadership Award 2022** — PIET
- **Hackathon Finalist** — KR Mangalam (AI Education App)

Full certifications archive → [tinyurl.com/abhishek9880-certs](https://tinyurl.com/abhishek9880-certs)

> "Abhishek is a great learner, whom someone can definitely rely on and take him to the team. I vouch for him."
> — **Sourav Saha**, Manager, IT Infrastructure & Cloud Operations at MSM Unify · 21× Microsoft & AWS Certified

---

## Education

**B.Tech (Honours), Information Technology** — Panipat Institute of Engineering and Technology, Kurukshetra University *2021 – 2025 · CGPA 8.2*

Class Representative for four years. Technical Event Head. Cloud & DevOps technical lead. Core member of NSS. 20+ NPTEL credits from IIT-run courses in systems, networking, and security as part of the Honours curriculum.

---

## Technical range

**Languages** Python · Bash · SQL · JavaScript / TypeScript · HCL (Terraform) · YAML

**AI / LLM** Claude (Anthropic) · OpenAI · Groq · Amazon Bedrock · LangChain · FAISS · pgvector · RAG · Model Context Protocol (MCP) · function calling · OPA/Rego for declarative policy · ed25519 for signed decisions

**Backend** FastAPI · Pydantic · asyncpg · SQLAlchemy · Redis · PostgreSQL 14+ (Row-Level Security, pgvector, HMAC chains, transactional outbox)

**AWS** EC2 · Auto Scaling · ALB · RDS Multi-AZ · ElastiCache · Route 53 · CloudFront · S3 · CloudTrail · CloudWatch · IAM · KMS · Secrets Manager · SSM Parameter Store · WAFv2 · VPC endpoints · Systems Manager

**Kubernetes & containers** Docker · Docker Compose · Amazon EKS · Helm · nginx-ingress · ALB Ingress · cert-manager · IRSA

**IaC & DevOps** Terraform · Ansible · CloudFormation · GitHub Actions · Jenkins · GitLab CI · AWS CodePipeline

**Security & scanning** OPA/Rego · ed25519 · HMAC chains · Merkle trees · RS256 JWT · bcrypt · PostgreSQL RLS · WAFv2 · SSRF hardening · Trivy · Checkov · Bandit · Gitleaks · SonarQube

**Observability** Prometheus · Grafana · Jaeger · OpenTelemetry · structlog

**Frontend** React 18/19 · Vite · CRA + Craco · Tailwind · shadcn/ui · framer-motion

**Data & vector** PostgreSQL · pgvector · MongoDB · Redis · Neon · S3 · DynamoDB · FAISS

---

## Writing & speaking

I write engineering deep-dives at [projectsphere.hashnode.dev](https://projectsphere.hashnode.dev/) — the *why* behind design decisions, uncensored, with the failures.

**Recent long-form:**
- **[I built a runtime firewall for AI agents](https://projectsphere.hashnode.dev/i-built-a-runtime-firewall-for-ai-agents)** — why ed25519 over RSA, why a Merkle log instead of a plain hash chain, what tried to break Aegis during development
- Voice AI infrastructure — Deepgram → hybrid retrieval → Groq Llama-3.1 → Cartesia, orchestrated with LiveKit
- Cost optimization on early-stage AWS — Cost Explorer visibility, right-sizing, Lambda-based dev-env sleep automation

**Video walkthroughs**
- [5-min Aegis walkthrough](https://drive.google.com/file/d/1Eojid76NcrRLC1Gp302i113pNgrH1hso/view) — kill switch, audit chain, blast-radius simulation, ed25519 receipt verification
- [Aegis extended feature reel](https://drive.google.com/drive/folders/1cAnCFmF6SEqaqTbiijuj0HyGwXmy1lhZ) — additional demos, UI walkthroughs, incident replay
- [Revora 90-second demo](https://drive.google.com/file/d/1fYYko3czhO7s8P7IijeGuUOexBnRzTzw/view) — upload → auto-mapping → dashboard → AI follow-up → signed audit chain

I write build-in-public on [linkedin.com/in/abhishek-mishra-eng](https://www.linkedin.com/in/abhishek-mishra-eng/) for the AI-engineering community (3,100+ followers).

---

## What I look for in a role

- **Real ownership** of a system that reaches production, not a slice of a slice of a ticket
- **Product-adjacent work** — I'm at my strongest when engineering decisions connect to a business outcome
- **A team that ships more than it slides** — reviewers who care about deploy correctness, not decks
- **Infrastructure with weight** — something a customer notices when it's down

## What I bring to a team

- **Systems that don't fail silently.** Every gate in Aegis's pipeline denies on dependency timeout. Every write in Revora is signed. Correctness by construction over correctness by review.
- **Bias for the boring, load-bearing details.** Redis + Postgres dual-writes for kill switches. Transactional outbox for billing. RLS instead of app-level tenant checks. The parts that keep the system honest at 3am.
- **Comfort at every layer of the stack.** From a Terraform module to a FastAPI route to a React component to a Postgres index. I don't hand off at team boundaries.
- **A build-in-public habit.** Every architecture decision, every AWS billing mistake, every "why we rewrote this" is documented. If someone can reproduce the build from the repo, that's the bar.

---

## Selected smaller projects

| Project | What it does | Stack |
|---|---|---|
| [devops-build-by-Abhi](https://github.com/Abhi-mishra998/devops-build-by-Abhi) | Dockerized React app with Jenkins pipeline, GitHub webhooks, EC2 SSH deploy — end-to-end CI/CD | React 18 · nginx · Docker · Jenkins · EC2 |
| [mlops-diabetes-prediction-aws](https://github.com/Abhi-mishra998/mlops-diabetes-prediction-aws) | Production MLOps pipeline on EKS with HTTPS, IRSA, auto-scaling, zero-downtime rollouts — **99.9% availability** | FastAPI · scikit-learn · EKS · ECR · Route 53 · ACM |
| [devsecops-todo-api](https://github.com/Abhi-mishra998/devsecops-todo-api) | Secure CI/CD for Node.js with Trivy vulnerability scanning + automated Docker Hub deployment | Jenkins · Docker · Trivy · Node.js |
| [cloudformation-AWS-zero-to-hero](https://github.com/Abhi-mishra998/cloudformation-AWS-zero-to-hero) | Infrastructure-as-Code templates for full VPC/EC2/RDS provisioning | CloudFormation · IaC · VPC · RDS |
| [prometheus-grafana-quick-setup](https://github.com/Abhi-mishra998/prometheus-grafana-quick-setup) | Docker-Compose stack with pre-configured dashboards for system monitoring | Prometheus · Grafana · Docker |
| [jenkins-docker-aws-pipeline](https://github.com/Abhi-mishra998/jenkins-docker-aws-pipeline) | Full CI/CD for AWS deployments with Dockerized app and Python automation | Jenkins · Docker · AWS · Python |
| [AWS-EKS-Kubernetes-Ingress-with-ALB-Routing](https://github.com/Abhi-mishra998/AWS-EKS-Kubernetes-Ingress-with-ALB-Routing) | Scalable EKS deployment with ALB Ingress, TLS termination, path-based routing | EKS · ALB · Kubernetes · CloudWatch |
| [static-website-using-AWS-CI-CD](https://github.com/Abhi-mishra998/static-website-using-AWS-CI-CD) | Automated static-site deployment with CodePipeline + CodeBuild + CloudFront + SSL | CodePipeline · CodeBuild · S3 · CloudFront |

Full portfolio → 76 public repositories at [github.com/Abhi-mishra998](https://github.com/Abhi-mishra998).

---

## Contact

The fastest path: **[abhishekmishra09896@gmail.com](mailto:abhishekmishra09896@gmail.com)**.

Also on [LinkedIn](https://www.linkedin.com/in/abhishek-mishra-eng/) · [portfolio](https://portfolio-self-seven-1zphd40voq.vercel.app) · [blog](https://projectsphere.hashnode.dev/) · [GitHub](https://github.com/Abhi-mishra998).

If you're working on AI infrastructure, agent security, platform engineering, or Kubernetes automation and want to compare notes — or if you're hiring in this space — I'd like to hear from you.
