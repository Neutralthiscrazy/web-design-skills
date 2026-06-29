# ATTRIBUTIONS

Each skill in this repository has been **vendored unmodified** from an upstream
source. Vendored files retain their original copyright and license terms, as
listed below. This repository's MIT license applies only to the meta-files
(`README.md`, `ATTRIBUTIONS.md`, `LICENSE`); for the vendored SKILL.md files,
the upstream terms govern.

## Vendored skills

### `frontend-design/SKILL.md`

- **Upstream**: [anthropics/skills](https://github.com/anthropics/skills)
- **Source path**: `skills/frontend-design/SKILL.md`
- **License**: Anthropic Skills License (see `LICENSE.txt` in upstream repo —
  summary: free to use, modify, and distribute with attribution)
- **Vendored commit**: pin to `main` branch at vendoring time
- **Description** (from upstream frontmatter):
  > Guidance for distinctive, intentional visual design when building new UI or
  > reshaping an existing one. Helps with aesthetic direction, typography, and
  > making choices that don't read as templated defaults.

### `react-best-practices/SKILL.md`

- **Upstream**: [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)
- **Source path**: `skills/react-best-practices/SKILL.md`
- **License**: MIT (declared in upstream SKILL.md frontmatter; upstream repo
  has no top-level LICENSE file)
- **Vendored commit**: pin to `main` branch at vendoring time
- **Description** (from upstream frontmatter — `name` field is
  `vercel-react-practices` in upstream, retained as-is for fidelity):
  > React and Next.js performance optimization guidelines from Vercel
  > Engineering. This skill should be used when writing, reviewing, or
  > refactoring React/Next.js code to ensure optimal performance patterns.
- **Note**: Upstream repo also contains 12 other skills (web-design-guidelines,
  vercel-cli-with-tokens, vercel-optimize, react-native-skills, deploy-to-vercel,
  etc.); we vendor only `react-best-practices` to keep the pack focused.

### `web-design-guidelines/SKILL.md`

- **Upstream**: [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)
- **Source path**: `skills/web-design-guidelines/SKILL.md`
- **License**: MIT (same upstream repo as `react-best-practices`)
- **Vendored commit**: pin to `main` branch at vendoring time
- **Description** (from upstream frontmatter):
  > Review UI code for Web Interface Guidelines compliance. Use when asked to
  > "review my UI", "check accessibility", "audit design", "review UX", or
  > "check my site against best practices".
- **Note**: Same upstream repo as `react-best-practices`; both vendored to
  keep the install surface small.

### `vanilla-web/SKILL.md`

- **Upstream**: [janjaszczak/cursor](https://github.com/janjaszczak/cursor)
- **Source path**: `skills/vanilla-web/SKILL.md`
- **License**: No LICENSE file in upstream repo; courtesy attribution applies
  and we treat upstream content as "all rights reserved" by default while
  redistributing unmodified with full credit
- **Vendored commit**: pin to `main` branch at vendoring time
- **Description** (from upstream frontmatter):
  > Build or modify plain HTML/CSS/JavaScript (no framework) using modular ES
  > modules (ESM), SRP, minimal global state, and shippable runnable files
  > with lightweight verification. Use for static pages, small UI widgets,
  > vanilla JS refactors, and quick prototypes without React/Vue/Angular.
- **Note**: Upstream repo contains 28 skills total (mcp-browser-verify,
  mcp-playwright, mcp-postman, python-backend, structured-delivery, etc.);
  we vendor only `vanilla-web` to keep the pack focused on the user-facing
  nic­he.

### `wcag-accessibility-audit/SKILL.md`

- **Upstream**: [mastepanoski/claude-skills](https://github.com/mastepanoski/claude-skills)
- **Source path**: `skills/wcag-accessibility-audit/SKILL.md`
- **License**: MIT (upstream LICENSE explicitly states MIT)
- **Vendored commit**: pin to `main` branch at vendoring time
- **Description** (from upstream frontmatter):
  > Comprehensive web accessibility audit using WCAG 2.1/2.2 guidelines.
  > Evaluate compliance across 4 POUR principles (Perceivable, Operable,
  > Understandable, Robust) with A, AA, AAA conformance levels.
- **Note**: Upstream repo contains 12 skills (gdpr, nist, owasp, etc.); we
  vendor only `wcag-accessibility-audit` to keep the pack focused.

## Why we vendor instead of central-install

Each upstream skill lives inside a **multi-skill repo**. If we pointed users
at `npx skills add anthropics/skills --skill frontend-design`, the install
command would do the right thing (--skill flag filters), but the install log
would say "Found 17 skills, Selected 1" — confusing for end users.

By vendoring the 5 SKILL.md files into our own flat repo, the install log
says "Found 5 skills, Installed 5" — clean, predictable, mirrors our
`Neutralthiscrazy/minecraft-skills` pack pattern.

## Re-syncing from upstream

To re-sync a vendored skill from its upstream source (e.g. after an upstream
push):

```bash
# Example: re-sync frontend-design from anthropics/skills
curl -sL \
  https://raw.githubusercontent.com/anthropics/skills/main/skills/frontend-design/SKILL.md \
  > frontend-design/SKILL.md
git add frontend-design/SKILL.md
git commit -m "web-design: re-sync frontend-design from upstream"
```

We do NOT modify vendored skill content (the upstream 'name' field is left
exactly as the upstream author wrote it, so any conflict markers or diffs
stay interpretable for re-sync).

## Naming convention

All 5 vendored skills sit at the top level of this repo:

```
Neutralthiscrazy/web-design-skills/
├── frontend-design/SKILL.md
├── react-best-practices/SKILL.md
├── web-design-guidelines/SKILL.md
├── vanilla-web/SKILL.md
└── wcag-accessibility-audit/SKILL.md
```

Each directory name equals the directory users see in
`~/.agents/skills/<dirname>/SKILL.md` after install.

## De-dup decision: zero overlap

The 5 skills were chosen to span 5 distinct web/UI niches with no overlap:

| Skill | Stack / concern | Triggers on |
|---|---|---|
| `frontend-design` | any framework, opinionated aesthetic | "build me a distinctive UI" |
| `react-best-practices` | React + Next.js | "review React perf" |
| `web-design-guidelines` | any HTML/CSS, audit/review | "review my UI" |
| `vanilla-web` | HTML/CSS/JS, no framework | "build a static page" |
| `wcag-accessibility-audit` | any web app, compliance | "audit a11y" |

Skills coexist side-by-side in `~/.agents/skills/` — each fires only when its
description matches the user's request, so there is no conflict at run-time.
