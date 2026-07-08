# Security Policy

## Supported Versions

| Version | Supported          |
|---------|--------------------|
| 1.x.x   | ✅ Fully supported |
| < 1.0   | ❌ Not supported   |

## Reporting a Vulnerability

We take the security of InterviewForge AI seriously. If you believe you have found a security vulnerability in our application, please report it to us responsibly.

**Please do NOT report security vulnerabilities through public GitHub issues.**

### How to Report

1. **Email**: Send a detailed report to `security@interviewforge.ai`
2. **Include**:
   - Type of vulnerability (e.g., XSS, SQL injection, authentication bypass)
   - Step-by-step reproduction instructions
   - Proof of concept or exploit code (if applicable)
   - Potential impact assessment
   - Any suggested remediation

### Response Timeline

| Phase | Timeline |
|---|---|
| Acknowledgment | Within 48 hours |
| Initial assessment | Within 5 business days |
| Fix development | Depends on severity |
| Public disclosure | After fix is released |

### Severity Classification

- **Critical** (CVSS 9.0–10.0): Immediate response, patch within 24–72 hours
- **High** (CVSS 7.0–8.9): Patch within 7 days
- **Medium** (CVSS 4.0–6.9): Patch within 30 days
- **Low** (CVSS 0.1–3.9): Patch in next scheduled release

### Security Measures in Place

- JWT authentication with short-lived access tokens
- HTTPS enforced in production
- Helmet.js security headers
- Rate limiting on all endpoints
- Input validation via Zod
- SQL injection protection via Prisma ORM
- XSS protection via DOMPurify on frontend
- CSRF protection
- bcrypt password hashing (12 rounds)
- Environment secrets management
- Regular dependency audits via `npm audit`

### Bug Bounty

We currently do not offer a paid bug bounty program, but all valid vulnerability reporters will be:
- Publicly credited in our CHANGELOG (with permission)
- Given free Premium membership for 1 year

Thank you for helping keep InterviewForge AI and its users safe!
