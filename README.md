# TrustLane

**A multi-tenant freelance marketplace with milestone escrow** - CY-351 Web Application Security, Fall 2026 (NCSA)

> **Educational use only.** This repository intentionally contains security vulnerabilities on the `vulnerable` branch.
> Run it only on a local, isolated machine. Never deploy it to a public network. All data is synthetic.

## Team
| Member | Reg. No. | Primary ownership |
|---|---|---|
| Anas Zeeshan (Lead) | 231250 | Auth/sessions, admin and audit, CORS/CSRF, repo hygiene |
| Alyan Gulzar | 231304 | Contracts, milestones, disputes, wallet/escrow ledger |
| Saad Bin Arif | 231310 | React frontend, file module, messaging, Docker, API tests |

## What it is
Clients hire freelancers or agencies. Contract value is split into milestones, funded into escrow, delivered via file upload, approved and released to the freelancer's wallet. Disputes are resolved by an arbitrator. Roles: Client, Freelancer, Agency Manager, Arbitrator, Platform Admin.

## Branch strategy
| Branch / tag | Purpose |
|---|---|
| `main` | Docs, threat model, findings log, PoC scripts, compose files (protected, PR + review) |
| `vulnerable` | TrustLane-Vuln. Every flaw is marked `// VULN-Vnn` in code |
| `hardened` | TrustLane-Hardened. Same features; every fix marked `// FIX-Vnn` |
| `feature/<name>` | Short-lived work branches, merged by PR |
| Tags | `v0.1-skeleton` (Wk 11), `v0.2-vuln-complete` (Wk 12), `v0.3-hardened` (Wk 13), `v1.0-final` (Wk 14) |

Rules: no direct pushes to `main`, `vulnerable` or `hardened`; small regular commits from all members; hardened fixes committed one vulnerability at a time.

## Planned structure
```
trustlane/
  backend/        # Node.js 20 + Express API (/api/v1)
  frontend/       # React + Vite SPA
  db/             # schema.sql, seed.sql (synthetic data)
  docker/         # compose files per build
  docs/           # scope pack, threat model, findings, design notes
  poc/            # proof-of-concept exploit scripts (own app only)
```

## Run (will be finalised in Phase 1)
```bash
git checkout vulnerable          # or: hardened
docker compose up --build
# SPA: http://localhost:5173    API: http://localhost:4000/api/v1
```

## Documentation index
- `docs/01-scope-pack.pdf` - Phase 0 Scope Pack
- `docs/02-threat-model.md` - Phase 1
- `docs/03-findings-log.md` - Phase 2 (V01-V14 with PoCs)
- `docs/04-hardening-changes.md` - Phase 3
- `docs/05-tradeoffs.md` - Phase 3/4

## Ethics and integrity
Original work of the team; no public vulnerable apps used as a base. Testing is limited to our own local deployments. Any AI tool use is disclosed in the final report. See Section 7 of the Scope Pack.
