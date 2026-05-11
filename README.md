# Skill Sage AI

A full-stack web app that compares your resume against a target job description and recommends the specific skills you should upgrade to close the gap — powered by a Llama LLM backend.

> 🏆 **Huawei Cloud Competition 2024** — advanced to Round 2

---

## ✨ Features

- **Resume parsing** — upload your resume and extract structured experience/skills
- **JD analysis** — paste any job description and extract required skills
- **Gap analysis** — LLM-driven comparison highlighting missing or weak skills
- **Skill upgrade recommendations** — ranked, actionable suggestions
- **LinkedIn OAuth login** — sign in with your professional profile
- **Stripe payment integration** — premium features behind paywall

---

## 🏗️ Architecture

![Architecture Diagram](docs/architecture.png)

```
WWW → EIP → VPC
              ├── Public Subnet (App Layer)
              │     ├── ECS — Next.js + tRPC (frontend & backend)
              │     └── HSS — host security
              └── Private Subnet (Data Layer)
                    └── RDS — PostgreSQL

External APIs:
  • LinkedIn API   (authentication)
  • Stripe API     (payment gateway)
  • Segmind API    (Llama inference)
```

**Security:** Database lives in a private subnet, unreachable from the public internet — all traffic goes through the application layer on ECS.

---

## 🛠️ Tech Stack

| Layer        | Tech                                       |
| ------------ | ------------------------------------------ |
| Frontend     | Next.js 15, React, TypeScript, Tailwind    |
| Backend      | tRPC, Node.js                              |
| Database     | PostgreSQL (Huawei RDS) + Drizzle ORM      |
| Auth         | NextAuth.js v5 (LinkedIn OAuth)            |
| Payments     | Stripe                                     |
| LLM          | Llama via Segmind API                      |
| Infra        | Huawei Cloud (ECS, RDS, VPC, EIP, HSS)     |

---

## 🚀 Getting Started

### Prerequisites

- Node.js ≥ 20
- npm (or pnpm/yarn)
- PostgreSQL ≥ 14

### Setup

```bash
git clone https://github.com/JediNakDev/skill-sage-ai.git
cd skill-sage-ai
npm install
cp .env.example .env   # fill in keys below
npm run db:push
npm run dev
```

### Environment Variables

```env
DATABASE_URL=postgresql://...
AUTH_LINKEDIN_ID=...
AUTH_LINKEDIN_SECRET=...
STRIPE_SECRET_KEY=...
STRIPE_WEBHOOK_SECRET=...
SEGMIND_API_KEY=...
AUTH_SECRET=...
AUTH_URL=http://localhost:3000
```

---

## 📦 Deployment (Huawei Cloud)

1. Provision **VPC** with one public and one private subnet
2. Launch **ECS** instance in public subnet, attach **EIP**
3. Provision **RDS PostgreSQL** in private subnet
4. Enable **HSS** for host-level security
5. Configure security groups: only ECS can reach RDS on port 5432
6. Deploy app to ECS, point DNS at EIP

---

## 📂 Project Structure

```
src/
├── app/              # Next.js App Router pages and API routes
├── server/
│   ├── api/          # tRPC routers
│   ├── auth/         # NextAuth configuration
│   └── db/           # Drizzle schema and client
├── trpc/             # tRPC client setup
├── styles/           # Global styles
└── env.js            # Validated environment variables
```

---

## 👥 Team

Built for Huawei Cloud Competition 2024.

---

## 📄 License

MIT
