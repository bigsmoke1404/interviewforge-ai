# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Multi-language interview transcription
- AI-powered code review integration
- Team/Company accounts
- Interview recording playback
- Advanced analytics with ML insights

---

## [1.0.0] — 2024-04-15

### Added
- 🎉 Initial production release of InterviewForge AI
- Complete user authentication system (JWT + OAuth)
- AI-powered interview generation using GPT-4o
- Real-time coding playground with Monaco Editor
- Discussion forum with nested comments and voting
- Global, weekly, and friends leaderboards
- Stripe subscription payments (monthly/yearly)
- Admin panel with user management and analytics
- XP and achievement badge system
- Email notifications via Nodemailer
- Push notifications via Socket.io
- Docker + Docker Compose setup
- Nginx reverse proxy configuration
- GitHub Actions CI/CD pipelines
- Comprehensive API documentation (Swagger)

### Security
- Helmet.js security headers
- Rate limiting (100 req/15min global, 5/min auth)
- CORS configured for production domains
- bcrypt password hashing (12 rounds)
- JWT short-lived access tokens (15 min)
- Refresh token rotation
- SQL injection protection via Prisma
- XSS protection via DOMPurify

---

## [0.9.0] — 2024-04-01

### Added
- Stripe payment integration with webhooks
- Premium subscription management
- Invoice generation and download
- Admin panel — reports and data export
- CHANGELOG tracking

### Fixed
- Leaderboard ranking calculation edge case with tied scores
- Memory leak in Socket.io disconnect handler

---

## [0.8.0] — 2024-03-15

### Added
- Discussion forum (Reddit-style)
- Nested comment threading (3 levels deep)
- Post voting (upvote/downvote)
- Bookmark posts and questions
- Markdown editor for posts
- Tag-based filtering and search

### Changed
- Forum search now uses PostgreSQL full-text search (pg_trgm)

---

## [0.7.0] — 2024-03-01

### Added
- Leaderboard system (global, weekly, friends)
- XP point system for interview completions
- Achievement badges (15 unique badges)
- Profile statistics and graphs
- GitHub and LinkedIn profile linking

### Fixed
- Profile avatar upload intermittently failing

---

## [0.6.0] — 2024-02-15

### Added
- Monaco Editor coding playground
- Support for Python, JavaScript, TypeScript, Java, C++, Go, Rust
- Judge0 API integration for code execution
- Syntax highlighting and autocomplete
- Code execution console output
- Theme switcher (dark/light, 10 editor themes)

---

## [0.5.0] — 2024-02-01

### Added
- Anti-cheating system
  - Tab switching detection
  - Copy/paste detection
  - Fullscreen enforcement
  - Webcam monitoring alerts
- Interview timer with configurable duration
- Webcam and microphone access management

### Fixed
- Timer drift after browser tab sleep

---

## [0.4.0] — 2024-01-15

### Added
- OpenAI GPT-4o integration
  - Dynamic question generation per topic + difficulty
  - Answer evaluation with scoring (0–100)
  - Detailed feedback with improvement suggestions
  - Follow-up question generation
  - Interview summary generation
- BullMQ job queue for AI evaluation tasks
- AI evaluation results caching (Redis)

---

## [0.3.0] — 2024-01-01

### Added
- Interview module
  - Create interview with language, difficulty, duration, company, topic
  - Interview session management
  - Submit interview and view results
- Admin panel (basic)
  - User management
  - Interview moderation

### Changed
- Migrated from REST-based auth to httpOnly cookie refresh tokens

---

## [0.2.0] — 2023-12-15

### Added
- Analytics dashboard with Chart.js
- Performance metrics
- Recent interview history
- Activity heatmap
- Email verification flow
- Password reset via email
- OAuth: Google login
- OAuth: GitHub login

### Security
- Added CSRF token validation
- Rate limiting on auth routes (5 req/min)

---

## [0.1.0] — 2023-12-01

### Added
- Project initialization with Turborepo monorepo
- Next.js 14 frontend with App Router
- Express.js API with TypeScript
- PostgreSQL database with Prisma ORM
- Redis integration
- User registration and login
- JWT access + refresh token authentication
- Prisma schema with all 18 models
- Docker Compose development environment
- GitHub Actions CI pipeline (lint, test, build)
- ESLint + Prettier configuration
- EditorConfig
- Initial README

[Unreleased]: https://github.com/interviewforge/interviewforge-ai/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.9.0...v1.0.0
[0.9.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.8.0...v0.9.0
[0.8.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.7.0...v0.8.0
[0.7.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.4.0...v0.5.0
[0.4.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.3.0...v0.4.0
[0.3.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/interviewforge/interviewforge-ai/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/interviewforge/interviewforge-ai/releases/tag/v0.1.0
