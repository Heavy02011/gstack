# gstack Prompts & Skills Cheatsheet

This cheatsheet distills the repo's generated `SKILL.md` prompts, templates, routing preamble, and companion docs into a quick operator reference. Use it when deciding which gstack specialist prompt to invoke, what each skill is optimized for, and what artifacts it should produce.

## Mental model

gstack is a role-based AI engineering workflow: each slash command loads a specialized prompt with its own operating mode, checklists, tools, and quality gates. The root prompt routes natural-language requests to these skills when proactive routing is enabled.

The default sprint loop is:

```text
Think → Plan → Build → Review → Test → Ship → Reflect
```

Recommended happy path:

1. **Frame the opportunity** with `/office-hours`.
2. **Create an executable spec** with `/spec` when the work needs a ticket or handoff.
3. **Review the plan** with `/autoplan` or targeted plan reviews.
4. **Implement** the chosen plan.
5. **Review and debug** with `/review`, `/investigate`, and `/cso` as needed.
6. **Verify behavior** with `/qa`, `/design-review`, `/devex-review`, and `/benchmark`.
7. **Ship and monitor** with `/ship`, `/land-and-deploy`, and `/canary`.
8. **Document and learn** with `/document-release`, `/document-generate`, `/retro`, `/learn`, and context tools.

## Prompt surfaces in this repo

| Surface | Where it lives | Edit policy | Purpose |
|---|---|---|---|
| Root gstack prompt | `SKILL.md.tmpl` → `SKILL.md` | Edit the `.tmpl`, regenerate output | Global routing, browser setup, and skill invocation rules. |
| Individual skills | `<skill>/SKILL.md.tmpl` → `<skill>/SKILL.md` | Edit the `.tmpl`, regenerate output | Specialist role prompts and workflows. |
| Model overlays | `model-overlays/*.md` | Edit directly | Host/model-specific wording and behavioral adaptations. |
| Host prompts/config | `hosts/*.ts`, `openclaw/*.md` | Edit directly | Install/routing behavior for Claude, Codex, OpenClaw, Cursor, etc. |
| Supporting checklists | e.g. `review/checklist.md`, `review/specialists/*.md`, `qa/references/*.md` | Edit directly | Deep reference material loaded by skills. |
| Generated public docs | `docs/skills.md`, `README.md` sections | Usually generated or curated | Human-readable overview; keep in sync with skills. |

## Skill routing quick reference

### Product discovery and plan-mode review

| Skill | Use when the user says... | What it does | Primary output |
|---|---|---|---|
| `/office-hours` | "Is this worth building?", new product idea, fuzzy opportunity, pitch, brainstorm | YC-style product interrogation. Pushes beyond the stated feature into pain, demand, wedge, and buyer/user reality. | Reframed product direction, risks, alternatives, design-doc seed. |
| `/spec` | "Write a spec", "make a ticket", "turn this into a GitHub issue", backlog-ready work | Converts vague intent into an executable five-phase spec. Can file an issue and optionally launch implementation in a fresh worktree. | Precise spec / issue with acceptance criteria and handoff context. |
| `/autoplan` | "Review the whole plan", "run all plan reviews", high-stakes plan | Runs CEO → design → engineering → DX plan reviews in sequence with encoded decision principles. | Integrated reviewed plan with only taste decisions escalated. |
| `/plan-ceo-review` | "Think bigger", "is this ambitious enough?", strategy/scope review | Founder-mode challenge. Finds the 10-star product and chooses expansion, selective expansion, hold-scope, or reduction. | Strategic scope decision and sharper product bet. |
| `/plan-design-review` | "Review the design of this plan", UX/UI plan concerns | Rates design dimensions, explains what a 10 looks like, and revises the plan. | Improved design plan and scored design rubric. |
| `/plan-eng-review` | "Does the architecture make sense?", execution plan review | Locks architecture, data flow, state transitions, failure modes, diagrams, edge cases, and tests. | Technical spine: diagrams, risk list, test matrix. |
| `/plan-devex-review` | API/CLI/SDK design, onboarding plan, "will developers love this?" | Reviews TTHW, magical moments, friction points, personas, and competitor benchmarks. | DX score, persona traces, improved developer-facing plan. |
| `/plan-tune` | "Stop asking me that", tune approval/question behavior | Reviews AskUserQuestion prompts and records per-question preferences. | Question-sensitivity preferences and psychographic notes. |
| `/design-consultation` | Brand, visual identity, design system from scratch | Researches landscape and proposes aesthetic, type, color, layout, spacing, and motion system. | Complete design direction plus preview assets/context. |

### Implementation support, review, and debugging

| Skill | Use when the user says... | What it does | Primary output |
|---|---|---|---|
| `/review` | "Review my diff", pre-landing PR review, "look at my changes" | Staff-engineer review for bugs that pass CI but fail in production; can auto-fix obvious issues. | Findings, fixes, pass/fail gate, TODOs for risky gaps. |
| `/codex` | "Get a Codex second opinion", adversarial review, consult OpenAI Codex | Wraps Codex CLI in review, challenge, or consult modes. | Independent review or adversarial analysis. |
| `/claude` | Non-Claude host wants Claude review/challenge/consult | Wraps Claude Code CLI similarly for hosts that are not already Claude. | Independent Claude review or consultation. |
| `/investigate` | Bug, crash, "why is this broken?", confusing behavior | Root-cause debugger. Iron law: investigate before fixing; traces facts, hypotheses, and failed attempts. | Root cause, evidence trail, minimal fix plan or fix. |
| `/cso` | Security audit, OWASP, STRIDE, secrets, supply chain | Infrastructure-first security audit spanning secrets, dependencies, CI/CD, LLM/AI, skills, and app trust boundaries. | Security findings prioritized by risk and remediation. |
| `/health` | "Health check", code quality dashboard | Runs project quality tools and produces weighted score/trends. | Composite health score and prioritized improvements. |
| `/freeze` | Restrict edits to one directory | Blocks writes outside a chosen path. | Active edit boundary. |
| `/unfreeze` | Remove edit restrictions | Clears the active freeze boundary. | Full edit scope restored. |
| `/careful` | Safety mode for destructive commands | Warns before dangerous commands like deletes, resets, and force pushes. | Destructive-command guardrails. |
| `/guard` | Maximum safety mode | Combines `/careful` and `/freeze`. | Destructive-command warnings plus directory edit boundary. |

### Browser QA, visual design, scraping, and DX

| Skill | Use when the user says... | What it does | Primary output |
|---|---|---|---|
| `/browse` | Open/test/navigate a page, inspect UI, take screenshots | Gives the agent a persistent headless Chromium browser for clicks, screenshots, responsive checks, forms, uploads, dialogs, and state verification. | Browser evidence: screenshots, snapshots, DOM/state observations. |
| `/open-gstack-browser` | "Open the visible browser", watch agent actions | Launches GStack Browser with sidebar extension so the user can observe/control actions. | Visible AI-controlled browser session. |
| `/connect-chrome` | Same visible-browser need on hosts using legacy name | Alias-style skill for launching GStack Browser with sidebar. | Visible browser session. |
| `/setup-browser-cookies` | Authenticated QA, import real browser cookies | Opens picker to import Chromium-family cookies into headless session. | Authenticated browser state. |
| `/pair-agent` | Pair remote agent with this browser | Generates setup key and instructions for OpenClaw, Hermes, Codex, Cursor, etc. | Remote-agent browser pairing instructions. |
| `/qa` | "Test this site", "find bugs", "does this work?" | Runs systematic browser QA, fixes bugs atomically, adds regression tests, and re-verifies. | Bug fixes, commits, screenshots, regression coverage. |
| `/qa-only` | "Report bugs only", no code changes | Same browser QA methodology without fixing. | Structured bug report, health score, repro steps, screenshots. |
| `/design-review` | Live site looks off, visual polish audit | Performs visual QA for spacing, hierarchy, inconsistency, AI slop, and slow interactions, then fixes. | Visual fixes, before/after screenshots, atomic commits. |
| `/design-shotgun` | Explore multiple design directions | Generates variants, opens comparison board, collects structured feedback, iterates. | Approved visual direction or comparison board. |
| `/design-html` | Turn approved design into production HTML/CSS | Generates production-quality Pretext-native HTML/CSS, with framework awareness. | Production-ready UI markup/styles. |
| `/devex-review` | Live developer onboarding/docs audit | Actually tries the docs/getting-started flow, measures TTHW, screenshots errors. | DX audit, friction report, improvements. |
| `/scrape` | Extract data from a web page | Prototypes data extraction with browser primitives; repeated intents route to codified browser skills. | JSON data extraction result. |
| `/skillify` | Codify a successful scrape | Converts recent `/scrape` flow into reusable browser-skill script, fixture, and test. | Permanent fast browser-skill. |

### Release, deploy, monitoring, and performance

| Skill | Use when the user says... | What it does | Primary output |
|---|---|---|---|
| `/ship` | "Ship it", push, PR, deploy request | Detects/merges base, runs tests, reviews diff, bumps version/changelog, commits, pushes, opens PR. | Ready PR and release notes. |
| `/landing-report` | Queue status, what versions/workspaces are waiting | Read-only dashboard for workspace-aware ship/version queue. | Queue report. |
| `/land-and-deploy` | "Merge and deploy", approved PR to production | Merges PR, waits for CI/deploy, verifies production health. | Landed release and production verification. |
| `/setup-deploy` | Configure deploy verification | Detects Fly, Render, Vercel, Netlify, Heroku, Actions, or custom deployment details. | Deploy config for `/land-and-deploy`. |
| `/canary` | Monitor production after deploy | Browser-driven post-deploy checks for console errors, page failures, screenshots, and performance drift. | Canary report and alerts. |
| `/benchmark` | Page speed, Core Web Vitals, perf regression | Baselines and compares load time, web vitals, and resource sizes. | Performance baseline/comparison report. |
| `/benchmark-models` | Compare skills across Claude/GPT/Gemini | Runs same prompt across models and compares latency, tokens, cost, and optional quality. | Cross-model benchmark table/report. |

### Documentation, memory, operations, and project hygiene

| Skill | Use when the user says... | What it does | Primary output |
|---|---|---|---|
| `/document-release` | Update docs after shipping | Reads docs vs diff, maps Diataxis coverage, updates stale docs. | Updated README/reference/how-to/tutorial/explanation docs. |
| `/document-generate` | Generate docs from scratch | Creates Diataxis docs for feature/module/project. | New tutorial, how-to, reference, or explanation docs. |
| `/make-pdf` | Turn markdown into a polished PDF | Produces publication-quality PDFs with margins, breaks, headers, page numbers, and typography. | PDF artifact. |
| `/context-save` | Save progress/checkpoint | Captures git state, decisions, and remaining work. | Restorable work context. |
| `/context-restore` | Resume previous work | Loads saved context across branches/workspaces. | Restored work summary and next steps. |
| `/learn` | Show/prune/export learnings | Manages persistent project learnings across sessions. | Learning report or memory edits. |
| `/retro` | Weekly retro, "what did we ship?" | Analyzes commits, work patterns, team/person breakdowns, test health, streaks. | Retrospective with trends and growth opportunities. |
| `/setup-gbrain` | Set up cross-session memory | Installs/configures gbrain, local/Supabase brain, MCP, trust policy. | Working gbrain memory integration. |
| `/sync-gbrain` | Refresh memory/search guidance from repo | Syncs code surfaces to gbrain and updates agent search guidance. | Current indexed repo memory and CLAUDE guidance. |
| `/gstack-upgrade` | Update gstack | Detects install mode, upgrades, and shows changes. | Upgraded gstack installation. |

### iOS live-device QA

| Skill | Use when the user says... | What it does | Primary output |
|---|---|---|---|
| `/ios-qa` | QA a SwiftUI app on a real iPhone | Connects via USB CoreDevice tunnel/StateServer, reads Swift source, runs vision-driven QA. | Device bug report with screenshots and traces. |
| `/ios-fix` | Fix a bug found by iOS QA | Edits source, rebuilds, redeploys, verifies on real device. | Verified iOS bug fix. |
| `/ios-design-review` | Visual audit on iPhone | Screenshots screens and grades against Apple HIG and project design docs. | iOS design audit and fixes/recommendations. |
| `/ios-clean` | Remove debug bridge before release | Strips DebugBridge package, StateServer, DebugOverlay, codegen, and app hooks. | Release-clean iOS app. |
| `/ios-sync` | Refresh iOS debug bridge templates | Regenerates StateServer, DebugOverlay, Package, and typed accessors from upstream templates. | Updated iOS QA bridge. |

## Common prompt chains

| Goal | Suggested chain | Notes |
|---|---|---|
| Validate a new product idea | `/office-hours` → `/autoplan` | Start with demand/pain before architecture. |
| Turn fuzzy request into implementable work | `/spec` → `/plan-eng-review` → implement → `/review` | Use `/plan-ceo-review` first when scope is uncertain. |
| Build a web feature end to end | `/office-hours` → `/autoplan` → implement → `/review` → `/qa` → `/ship` | Add `/design-review` for user-visible changes. |
| Debug production bug | `/investigate` → minimal fix → regression test → `/review` → `/qa` | Do not skip root-cause evidence. |
| Security-sensitive change | `/plan-eng-review` → `/cso` → implement → `/review` | Re-run `/cso` for auth, secrets, LLM, or infra changes. |
| Polish a live UI | `/design-review` → `/qa` → `/benchmark` | Screenshots are required evidence for visual changes. |
| Improve developer onboarding | `/plan-devex-review` → implement docs/API changes → `/devex-review` | Measure actual TTHW, not claimed TTHW. |
| Prepare release | `/review` → `/qa` → `/document-release` → `/ship` | `/ship` may also run its own checks and PR flow. |
| Merge and watch production | `/land-and-deploy` → `/canary` | Use `/setup-deploy` once per project if deploy config is unknown. |
| Authenticated browser testing | `/setup-browser-cookies` → `/qa` or `/browse` | Use environment variables for test credentials. |
| Extract repeatable web data | `/scrape` once or twice → `/skillify` | Codified scrape paths become much faster. |
| Resume after context switch | `/context-restore` → continue → `/context-save` | Helpful across Conductor/worktree boundaries. |

## Decision rules

- **If the request is about deciding what to build**, start with `/office-hours` or `/plan-ceo-review`.
- **If the request is about making work executable**, use `/spec` or `/plan-eng-review`.
- **If the request is about correctness before landing**, use `/review`.
- **If the request is about unknown broken behavior**, use `/investigate` before fixing.
- **If the request is about a real UI or deployment**, use browser-backed skills: `/browse`, `/qa`, `/design-review`, `/devex-review`, `/benchmark`, or `/canary`.
- **If the request is about release mechanics**, use `/ship`; if already approved and ready for production, use `/land-and-deploy`.
- **If the request is about safety constraints**, use `/careful`, `/freeze`, `/guard`, or `/unfreeze`.
- **If the request is about durable knowledge**, use `/context-save`, `/context-restore`, `/learn`, `/setup-gbrain`, or `/sync-gbrain`.

## Maintenance notes for prompt authors

- Skill outputs are generated from templates. Edit `SKILL.md.tmpl`, not generated `SKILL.md`.
- Regenerate skill output with `bun run gen:skill-docs --host codex` for Codex-specific output, or the appropriate host flag for another host.
- Run `bun run skill:check` after prompt/template changes.
- Use `bun test` or `bun run test:free` for free test coverage.
- Keep routing text in the root prompt consistent with newly added, renamed, or removed skills.
- Keep README and `docs/skills.md` aligned when user-facing skill behavior changes.
