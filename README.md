<div align="center">

# ⚡ InterviewForge AI

### The Ultimate AI-Powered Coding Interview Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-20+-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.4-blue?logo=typescript)](https://typescriptlang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-316192?logo=postgresql)](https://postgresql.org/)
[![Redis](https://img.shields.io/badge/Redis-7-DC382D?logo=redis&logoColor=white)](https://redis.io/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker&logoColor=white)](https://docker.com/)
[![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?logo=github-actions)](https://github.com/features/actions)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

**[Live Demo](https://interviewforge.ai)** • **[Documentation](docs/)** • **[API Reference](docs/api-reference.md)** • **[Report Bug](https://github.com/interviewforge/interviewforge-ai/issues)**

</div>

---

## 📸 Screenshots

| Dashboard | Interview Session | Coding Playground |
|-----------|-----------------|-------------------|
| ![Dashboard](docs/screenshots/dashboard.png) | ![Interview](docs/screenshots/interview.png) | ![Playground](docs/screenshots/playground.png) |

| Forum | Leaderboard | Admin Panel |
|-------|-------------|-------------|
| ![Forum](docs/screenshots/forum.png) | ![Leaderboard](docs/screenshots/leaderboard.png) | ![Admin](docs/screenshots/admin.png) |

---

## 🚀 Features

<details>
<summary><b>🔐 Authentication & Security</b></summary>

- JWT authentication with access + refresh tokens (httpOnly cookies)
- OAuth login with Google and GitHub (Passport.js)
- Email verification on registration
- Forgot/reset password via email link
- Rate limiting on auth endpoints (5 req/min)
- bcrypt password hashing (12 rounds)
- CSRF protection
- XSS prevention with DOMPurify

</details>

<details>
<summary><b>📊 Analytics Dashboard</b></summary>

- Real-time performance metrics
- Interview score trends (Chart.js)
- Skill radar charts
- Activity heatmap (GitHub-style)
- Recent interview history
- Comparison against leaderboard averages

</details>

<details>
<summary><b>🎯 AI Interview Module</b></summary>

- Create interviews: select language, difficulty (Easy/Medium/Hard/Expert), duration, company, topic
- GPT-4o generates tailored interview questions
- Real-time interview timer with warnings
- Webcam + microphone management
- Fullscreen enforcement
- **Anti-cheating system**:
  - Tab switching detection and flagging
  - Copy/paste detection
  - Webcam monitoring with frame analysis
  - Activity logging and audit trail

</details>

<details>
<summary><b>🤖 AI Evaluation Engine</b></summary>

- Automatic answer evaluation with 0–100 scoring rubric
- Detailed written feedback per answer
- Specific improvement suggestions
- Follow-up question generation based on answers
- Interview summary with key insights
- Skill gap analysis

</details>

<details>
<summary><b>💻 Coding Playground</b></summary>

- Monaco Editor (same as VS Code)
- Syntax highlighting + IntelliSense autocomplete
- Run code via Judge0 API
- 7 supported languages: Python, JavaScript, TypeScript, Java, C++, Go, Rust
- Live console output
- 10 editor themes (dark/light)
- Code saving and sharing

</details>

<details>
<summary><b>💬 Discussion Forum</b></summary>

- Reddit-style post creation and voting
- Nested comment threading (3 levels)
- Upvote/downvote posts and comments
- Bookmark posts for later
- Tag-based organization and filtering
- Full-text search (PostgreSQL pg_trgm)
- Markdown editor for rich posts

</details>

<details>
<summary><b>🏆 Gamification</b></summary>

- XP point system
- 15 unique achievement badges
- Global, weekly, and friends leaderboards
- Profile statistics and rank tracking

</details>

<details>
<summary><b>💳 Subscription & Payments</b></summary>

- Stripe integration (monthly + yearly plans)
- Webhook handling for subscription events
- Invoice generation and download
- Upgrade/downgrade/cancel subscription
- Premium features gating

</details>

<details>
<summary><b>🛡️ Admin Panel</b></summary>

- Dashboard with platform-wide analytics
- User management (view, ban, delete)
- Interview moderation
- Content moderation (forum posts/comments)
- Export data as CSV/JSON
- Automated reports

</details>

---

## 🏗️ Architecture

```
interviewforge-ai/
├── apps/
│   ├── web/                          # Next.js 14 (App Router)
│   │   ├── src/
│   │   │   ├── app/                  # Pages (40+)
│   │   │   ├── components/           # Reusable components (100+)
│   │   │   ├── hooks/                # Custom React hooks (15+)
│   │   │   ├── services/             # API service layer
│   │   │   ├── store/                # Redux Toolkit state
│   │   │   ├── middleware.ts          # Next.js middleware
│   │   │   └── utils/
│   │   └── ...config files
│   └── api/                          # Express.js REST API
│       ├── src/
│       │   ├── controllers/          # Request handlers
│       │   ├── services/             # Business logic
│       │   ├── repositories/         # Database access
│       │   ├── middlewares/          # Express middleware
│       │   ├── routes/               # API routes
│       │   ├── validators/           # Zod validators
│       │   ├── workers/              # BullMQ background jobs
│       │   ├── socket/               # Socket.io events
│       │   └── utils/
│       └── prisma/                   # Database schema
├── packages/
│   └── shared/                       # Shared types, validators, constants
├── docker/                           # Docker configuration
├── nginx/                            # Nginx reverse proxy
└── .github/workflows/                # CI/CD pipelines
```

### Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                        Client (Next.js)                      │
│  Redux  │  TanStack Query  │  Socket.io Client  │  Stripe   │
└─────────────────────────┬───────────────────────────────────┘
                          │ HTTPS / WSS
┌─────────────────────────▼───────────────────────────────────┐
│                    Nginx (Reverse Proxy)                     │
│              Rate Limiting │ SSL Termination                 │
└────────┬─────────────────────────────────┬──────────────────┘
         │ /api/*                          │ /*
┌────────▼────────────────┐    ┌───────────▼──────────────────┐
│   Express.js API (4000) │    │  Next.js SSR/SSG (3000)      │
│  ┌──────────────────┐   │    └──────────────────────────────┘
│  │   Controllers     │   │
│  │   Services        │   │
│  │   Repositories    │   │
│  └─────────┬─────────┘   │
└────────────┼─────────────┘
         ┌───┴────┐
┌────────▼──┐  ┌──▼──────────────────────────────┐
│PostgreSQL │  │            Redis                 │
│ (Prisma)  │  │  Sessions │ Cache │ BullMQ Queue │
└───────────┘  └─────────────────────────────────┘
                           │
              ┌────────────▼────────────┐
              │    Background Workers    │
              │  Email │ AI │ Reports   │
              └─────────────────────────┘
```

---

## 🛠️ Tech Stack

### Frontend
| Technology | Version | Purpose |
|---|---|---|
| Next.js | 14 | React framework with App Router |
| TypeScript | 5.4 | Type safety |
| Tailwind CSS | 3.4 | Styling |
| Shadcn/ui | latest | UI component library |
| Framer Motion | 11 | Animations |
| Redux Toolkit | 2 | Global state management |
| TanStack Query | 5 | Server state & caching |
| React Hook Form | 7 | Form management |
| Zod | 3 | Schema validation |
| Axios | 1.6 | HTTP client |
| Chart.js | 4 | Analytics charts |
| Monaco Editor | 0.47 | Code editor |
| Socket.io Client | 4 | Real-time features |

### Backend
| Technology | Version | Purpose |
|---|---|---|
| Node.js | 20 | Runtime |
| Express.js | 4.18 | HTTP framework |
| TypeScript | 5.4 | Type safety |
| Prisma ORM | 5.11 | Database ORM |
| PostgreSQL | 16 | Primary database |
| Redis | 7 | Caching + queues |
| Socket.io | 4 | Real-time events |
| BullMQ | 5 | Background job queue |
| Passport.js | 0.7 | OAuth strategies |
| OpenAI SDK | 4 | AI features |
| Stripe SDK | 14 | Payments |
| Cloudinary | 2 | File storage |
| Nodemailer | 6 | Email sending |
| Zod | 3 | Input validation |
| Helmet | 7 | Security headers |
| Winston | 3 | Structured logging |

### Infrastructure
| Technology | Purpose |
|---|---|
| Docker + Compose | Containerization |
| Nginx | Reverse proxy + SSL |
| GitHub Actions | CI/CD |
| Vercel | Frontend deployment |
| Railway | Backend deployment |

---

## ⚡ Quick Start

### Prerequisites

- Node.js 20+
- Docker Desktop
- npm 10+

### 1. Clone & Install

```bash
git clone https://github.com/interviewforge/interviewforge-ai.git
cd interviewforge-ai
npm install
```

### 2. Configure Environment

```bash
cp .env.example .env
```

Edit `.env` and fill in your API keys:
- `OPENAI_API_KEY` — [OpenAI Platform](https://platform.openai.com/)
- `GOOGLE_CLIENT_ID` / `GOOGLE_CLIENT_SECRET` — [Google Console](https://console.cloud.google.com/)
- `GITHUB_CLIENT_ID` / `GITHUB_CLIENT_SECRET` — [GitHub Developer Settings](https://github.com/settings/developers)
- `STRIPE_SECRET_KEY` — [Stripe Dashboard](https://dashboard.stripe.com/)
- `CLOUDINARY_*` — [Cloudinary Console](https://cloudinary.com/)

### 3. Start Infrastructure

```bash
docker-compose up -d postgres redis
```

### 4. Database Setup

```bash
npm run db:migrate
npm run db:seed
```

### 5. Start Development

```bash
npm run dev
```

- 🌐 **Frontend**: http://localhost:3000
- 🔌 **API**: http://localhost:4000
- 📚 **Swagger**: http://localhost:4000/api/docs

---

## 🐳 Docker Setup (Full Stack)

```bash
# Start all services (API + Web + DB + Redis + Nginx)
docker-compose up -d

# View logs
docker-compose logs -f

# With dev tools (pgAdmin + Redis Commander)
docker-compose --profile dev-tools up -d

# Production mode
NODE_ENV=production docker-compose --profile production up -d
```

---

## 🚀 Deployment

### Vercel (Frontend)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/interviewforge/interviewforge-ai)

### Railway (Backend)

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template)

See [Deployment Guide](docs/deployment.md) for complete instructions.

---

## 📚 API Reference

Full Swagger documentation available at:
- **Development**: http://localhost:4000/api/docs
- **Production**: https://api.interviewforge.ai/docs

### Quick Reference

```
POST   /api/v1/auth/register              — Register new user
POST   /api/v1/auth/login                 — Login
POST   /api/v1/auth/refresh               — Refresh access token
GET    /api/v1/interviews                 — List interviews
POST   /api/v1/interviews                 — Create interview
POST   /api/v1/interviews/:id/start       — Start interview session
POST   /api/v1/code/run                   — Execute code
POST   /api/v1/questions/generate         — AI: generate questions
POST   /api/v1/questions/:id/evaluate     — AI: evaluate answer
GET    /api/v1/leaderboard                — Global leaderboard
POST   /api/v1/payments/checkout          — Create Stripe checkout
```

See [Full API Reference](docs/api-reference.md).

---

## 🧪 Testing

```bash
# Run all tests
npm run test

# Run with coverage
npm run test -- --coverage

# Run E2E tests
npm run test:e2e

# Run specific workspace
npm run test --workspace=apps/api
```

---

## 📁 Folder Structure

```
apps/api/src/
├── config/          # App, DB, Redis, email, OAuth configs
├── controllers/     # Route handlers (thin layer)
├── services/        # Business logic
├── repositories/    # Data access layer (Prisma)
├── middlewares/     # Auth, rate limit, validation, logging
├── routes/          # Express routers
├── validators/      # Zod schemas
├── workers/         # BullMQ background jobs
├── socket/          # Socket.io event handlers
└── utils/           # Helpers, logger, crypto

apps/web/src/
├── app/             # Next.js App Router pages
├── components/
│   ├── ui/          # Shadcn primitives
│   ├── layout/      # Navbar, Sidebar, Footer
│   ├── auth/        # Login, Register forms
│   ├── dashboard/   # Dashboard widgets
│   ├── interview/   # Interview session components
│   ├── playground/  # Monaco editor wrapper
│   ├── forum/       # Forum components
│   ├── admin/       # Admin panel components
│   └── shared/      # Buttons, Modals, Skeletons
├── hooks/           # useAuth, useInterview, useSocket, etc.
├── services/        # Axios API service layer
├── store/           # Redux slices + RTK Query
└── utils/           # Formatters, validators, helpers
```

---

## 🗺️ Roadmap

- [ ] Video interview recording and playback
- [ ] Team/company accounts with shared interview pools
- [ ] AI-powered resume analysis
- [ ] Multi-language interview transcription
- [ ] Mock behavioral interview (non-coding)
- [ ] Mobile apps (React Native)
- [ ] Browser extension for LeetCode practice
- [ ] Integration with HackerRank / Codeforces problems
- [ ] Peer interview matching

---

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments

- [OpenAI](https://openai.com/) for GPT-4o API
- [Shadcn/ui](https://ui.shadcn.com/) for beautiful components
- [Vercel](https://vercel.com/) for Next.js and hosting
- [Prisma](https://prisma.io/) for the incredible ORM
- [Judge0](https://judge0.com/) for code execution API

---

<div align="center">

Built with ❤️ by the **InterviewForge Team**

⭐ Star this repo if you find it useful!

</div>
