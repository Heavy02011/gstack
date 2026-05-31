# CONTEXT_REVERSE.md
> **Domain-specific parameters for gstack.**
> Swap these values to regenerate an equivalent AI-engineering-workflow toolkit for a different creator, company, or vertical.
> This file is the only thing you need to change — PLAN_REVERSE.md consumes it verbatim.

---

## 1. Creator & Identity

| Key | Value |
|-----|-------|
| `CREATOR_NAME` | Garry Tan |
| `CREATOR_HANDLE` | @garrytan |
| `CREATOR_TITLE` | President & CEO, Y Combinator |
| `CREATOR_BACKGROUND` | First eng/PM/designer at Palantir; co-founded Posterous (sold to Twitter); built Bookface (YC's internal social network); worked with Coinbase, Instacart, Rippling at inception |
| `CREATOR_VOICE` | Direct, high-conviction, builder-first. Celebrates craft. Uses data to kill arguments. Quotes Karpathy and Willison in context. |
| `CREATOR_GITHUB` | garrytan |
| `REPO_NAME` | gstack |
| `REPO_FULL_NAME` | garrytan/gstack |
| `REPO_URL` | https://github.com/garrytan/gstack |

---

## 2. Project Purpose & Positioning

| Key | Value |
|-----|-------|
| `PRODUCT_TAGLINE` | Turns Claude Code into a virtual engineering team |
| `PRODUCT_DESCRIPTION` | 23 specialist slash-command skills + 8 power tools for the full sprint: Think → Plan → Build → Review → Test → Ship → Reflect |
| `PRODUCT_DOMAIN` | Developer tooling / AI-assisted software engineering |
| `PRODUCT_PEERS` | OpenClaw (247K ⭐), Linear, Raycast, Warp, Zed |
| `PRODUCT_LICENSE` | MIT |
| `PRIMARY_AI_HOST` | Claude Code (Anthropic) |
| `SUPPORTED_AI_HOSTS` | Claude Code, OpenAI Codex CLI, OpenCode, Cursor, Factory Droid, Slate, Kiro, Hermes, GBrain |
| `TARGET_USERS` | Technical founders; first-time Claude Code users; tech leads and staff engineers |
| `INSTALL_PATH` | `~/.claude/skills/gstack` |

---

## 3. Productivity Narrative

| Key | Value |
|-----|-------|
| `PRODUCTIVITY_CLAIM` | ~810× 2013 pace in logical lines/day (11,417 vs 14); 240× total 2013 year output shipped YTD 2026 |
| `PROOF_WINDOW` | 60 days: 3 production services, 40+ shipped features, part-time while running YC |
| `MEASUREMENT_METHODOLOGY` | Logical code changes (not raw LOC); normalized for AI inflation; 40 public + private `garrytan/*` repos; demo repo excluded |
| `LOC_CONTROVERSY_DOC` | docs/ON_THE_LOC_CONTROVERSY.md |
| `KARPATHY_QUOTE` | "I don't think I've typed like a line of code probably since December, basically, which is an extremely large change." |
| `KARPATHY_SOURCE` | No Priors podcast, March 2026 |
| `OPENCLAW_REFERENCE` | Peter Steinberger built OpenClaw (247K GitHub stars) essentially solo with AI agents |

---

## 4. The Sprint Model (Skill Roles)

Each skill maps to a "specialist" persona. Adjust names/roles for a different org context.

| Skill | Persona | One-liner |
|-------|---------|-----------|
| `/office-hours` | YC Office Hours | Six forcing questions that reframe your product |
| `/plan-ceo-review` | CEO / Founder | Find the 10-star product inside the request |
| `/plan-eng-review` | Eng Manager | Lock architecture, data flow, edge cases, tests |
| `/plan-design-review` | Senior Designer | Rate design dimensions 0–10; AI Slop detection |
| `/plan-devex-review` | DX Lead | 20–45 forcing questions; TTHW benchmarking |
| `/design-consultation` | Design Partner | Complete design system from scratch |
| `/design-shotgun` | Design Explorer | 4–6 mockup variants; comparison board |
| `/design-html` | Design Engineer | Mockup → shippable production HTML, zero deps |
| `/design-review` | Designer Who Codes | Audit + fix; atomic commits; before/after screenshots |
| `/review` | Staff Engineer | Bugs that pass CI but blow up in prod |
| `/investigate` | Debugger | Iron Law: no fixes without root cause |
| `/devex-review` | DX Tester | Live onboarding audit; TTHW timed; screenshots |
| `/qa` | QA Lead | Find bugs, fix them, commit, re-verify |
| `/qa-only` | QA Reporter | Bug report only, no code changes |
| `/pair-agent` | Multi-Agent Coordinator | Browser-sharing across AI agents; ngrok tunnel |
| `/cso` | Chief Security Officer | OWASP Top 10 + STRIDE; 17 FP exclusions; 8/10 confidence gate |
| `/ship` | Release Engineer | Sync main, run tests, bump VERSION, push, open PR |
| `/land-and-deploy` | Release Engineer | Merge → CI → deploy → verify production |
| `/canary` | Post-deploy Monitor | Post-deploy production health checks |
| `/autoplan` | Auto-pipeline | CEO + Design + Eng + DX reviews sequentially |
| `/retro` | Retro Lead | Weekly engineering retrospective |
| `/codex` | Second Opinion | Codex/OpenAI review pass |
| `/spec` | Ticket Writer | Turn ideas into GitHub issues / backlog items |
| `/careful` / `/guard` | Safety Mode | Restrict agent autonomy |
| `/freeze` / `/unfreeze` | Directory Lock | Limit edits to a path |
| `/context-save` / `/context-restore` | Checkpoint | Save/resume session state |
| `/document-release` | Release Docs | Post-ship documentation update |
| `/document-generate` | Doc Generator | Write docs from scratch |
| `/learn` | Learning Log | Surface per-project operational learnings |
| `/health` | Code Quality | Code quality dashboard |
| `/benchmark` | Perf Benchmarker | Page speed / performance regression |
| `/make-pdf` | PDF Publisher | Document to publication-quality PDF |
| `/gstack-upgrade` | Upgrader | Self-upgrade gstack in place |
| `/setup-deploy` | Deploy Config | Wire up deployment for project |
| `/setup-browser-cookies` | Cookie Import | Import real-browser cookies for auth testing |
| `/setup-gbrain` | GBrain Setup | Connect GBrain memory layer |
| `/sync-gbrain` | GBrain Sync | Sync memory with GBrain |
| `/open-gstack-browser` | Browser Launcher | Launch headed browser |
| `/connect-chrome` | Chrome Connect | CDP connect to running Chrome |
| `/plan-tune` | Question Tuner | Tune question sensitivity |
| `/office-hours` (OpenClaw native) | Conversational | Runs directly in OpenClaw agent |
| `/gstack-openclaw-ceo-review` | Conversational | CEO review in OpenClaw |
| `/gstack-openclaw-investigate` | Conversational | Debugging in OpenClaw |
| `/gstack-openclaw-retro` | Conversational | Retro in OpenClaw |

---

## 5. Design System

| Key | Value |
|-----|-------|
| `AESTHETIC` | Industrial / Utilitarian — function-first, data-dense, monospace as personality |
| `ACCENT_DARK` | amber-500 `#F59E0B` |
| `ACCENT_LIGHT` | amber-600 `#D97706` |
| `ACCENT_TEXT_DARK` | amber-400 `#FBBF24` |
| `ACCENT_TEXT_LIGHT` | amber-700 `#B45309` |
| `SURFACE_DARK` | `#141414` |
| `BASE_DARK` | `#0C0C0C` |
| `SURFACE_LIGHT` | `#FFFFFF` |
| `BASE_LIGHT` | `#FAFAF9` |
| `FONT_DISPLAY` | Satoshi (Black 900 / Bold 700) — from Fontshare CDN |
| `FONT_BODY` | DM Sans (Regular 400 / Medium 500 / Semibold 600) — Google Fonts |
| `FONT_MONO` | JetBrains Mono (Regular 400 / Medium 500) — Google Fonts |
| `GRAIN_TEXTURE` | SVG feTurbulence; dark opacity 0.03, light 0.02; fixed, z-index 9999 |
| `BORDER_RADIUS_CARD` | 12px |
| `BORDER_RADIUS_BUTTON` | 8px |
| `MAX_CONTENT_WIDTH` | 1200px |
| `REFERENCE_SITES` | formulae.brew.sh, linear.app, warp.dev |

---

## 6. Builder Ethos (Principles)

These are injected into every skill preamble. Replace for a different cultural context.

| Principle | Summary |
|-----------|---------|
| **Boil the Lake** | Completeness is near-zero cost with AI. Always do the complete thing. Lake = boilable scope; ocean = multi-quarter migration. |
| **Search Before Building** | Three knowledge layers: Tried-and-true (Layer 1), New-and-popular (Layer 2), First-principles (Layer 3). Prize Layer 3 eureka moments. |
| **User Sovereignty** | AI recommends; user decides. Even when two models agree on a change that contradicts user intent, present + ask, never act. |

---

## 7. Technology Stack

| Component | Technology |
|-----------|-----------|
| Runtime | Bun ≥ 1.0 + Node.js (Windows fallback) |
| Package manager | Bun |
| Browser automation | Playwright (headless Chromium) + custom CDP bridge |
| PDF generation | Custom `make-pdf` binary (Bun) |
| Design pipeline | Custom `design` binary (Bun) — daemon + gallery + variants |
| Memory / brain | GBrain (optional, self-hosted Supabase) |
| Browser extension | Manifest V3 Chrome extension (CDP inspector + sidepanel terminal) |
| CI | GitHub Actions + GitLab CI (`/.gitlab-ci.yml`) |
| Skills format | Markdown with YAML frontmatter (`SKILL.md`) |
| Telemetry | JSONL append-only logs in `~/.gstack/analytics/` |
| Team sync | `gstack-team-init` + auto-update check (throttled to 1×/hour) |

---

## 8. Community & Ecosystem

| Key | Value |
|-----|-------|
| `COMMUNITY_SITE` | (gstack community dashboard — live + interactive) |
| `CHANGELOG_URL` | CHANGELOG.md in repo root |
| `DOCS_DIR` | `docs/` |
| `CONTRIBUTING_GUIDE` | CONTRIBUTING.md |
| `OPENCLAW_INTEGRATION` | ACP-based multi-agent; gstack skills work in every spawned Claude Code session |
| `CLAWHUB_SKILLS` | `gstack-openclaw-office-hours`, `gstack-openclaw-ceo-review`, `gstack-openclaw-investigate`, `gstack-openclaw-retro` |
| `SLOP_SCAN` | `slop-scan` npm package; `slop-scan.config.json` for AI-slop detection |
| `VERSION_FILE` | `VERSION` (semver: `MAJOR.MINOR.PATCH.BUILD`) |

---

## 9. Analytics & Telemetry

| Key | Value |
|-----|-------|
| `TELEMETRY_STORE` | `~/.gstack/analytics/skill-usage.jsonl` |
| `LEARNINGS_STORE` | `~/.gstack/projects/{slug}/learnings.jsonl` |
| `QUESTION_LOG` | `~/.gstack/question-log.jsonl` |
| `TIMELINE_LOG` | `~/.gstack/timeline.jsonl` |
| `SESSION_DIR` | `~/.gstack/sessions/` |
| `CONFIG_FILE` | `~/.gstack/config.yaml` |

---

## 10. Security Model

| Key | Value |
|-----|-------|
| `FILE_PERMISSIONS` | `umask 077` on install — all new files owner-only (0o600 / 0o700) |
| `REDACT_ENGINE` | `lib/redact-engine.ts` — strips secrets before any log/push |
| `REDACT_PREPUSH_HOOK` | `bin/gstack-redact-prepush` — git pre-push hook |
| `CDP_ALLOWLIST` | `browse/src/cdp-allowlist.ts` — restricts CDP commands |
| `CONTENT_SECURITY` | `browse/src/content-security.ts` — CSP enforcement |
| `GBRAIN_GUARDS` | `lib/gbrain-guards.ts` — fail-closed guards for destructive ops |
| `COOKIE_SCOPE` | `cookie-import-browser` only imports from user-controlled browsers |
