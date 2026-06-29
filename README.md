# web-design-skills

A focused pack of **5 web and UI design skills** for AI coding agents
(Claude Code, OpenCode, Codex, Cursor, etc.). One `npx skills add` command
installs the whole pack.

## Install

```bash
npx -y skills add Neutralthiscrazy/web-design-skills --global -a claude-code
```

Replace `claude-code` with `opencode`, `codex`, `cursor`, `cline`, or
`amp` to target a different agent. Omit `--global` (`-g`) to install
project-locally instead.

That's the **only** command end users need. The installer clones this repo,
detects all 5 `*/SKILL.md` files, and copies them into your agent's
`~/.agents/skills/<dirname>/` directory.

## What's installed

After the command finishes you'll see 5 new directories in your agent's
skills folder:

| Skill | What it does |
|---|---|
| `frontend-design` | Distinctive, opinionated **visual design** for any stack — picks palette, typography, signature element per brief instead of giving templated defaults |
| `react-best-practices` | **React + Next.js performance** patterns from Vercel Engineering — data fetching, bundle optimization, server components |
| `web-design-guidelines` | **Audit/review tool** for any HTML/CSS/JS code — checks against Vercel Web Interface Guidelines (compliance + UX review) |
| `vanilla-web` | **Plain HTML/CSS/JS** (no framework) — modular ESM, SRP, shippable runnable files, light verification |
| `wcag-accessibility-audit` | **WCAG 2.1/2.2 audit** — POUR principles (Perceivable, Operable, Understandable, Robust), A/AA/AAA conformance levels |

All 5 fire only when their description matches your request — there is no
overlap. See `ATTRIBUTIONS.md` for the full source attribution table.

## Why this pack

For users who buy an AI-coding key to build web/UI work, each of these
skills targets a different stage:

- **Starting new UI?** → `frontend-design` (opinionated aesthetic)
- **Working with React / Next.js?** → `react-best-practices` (perf)
- **Have a draft and want feedback?** → `web-design-guidelines` (audit)
- **Building static page or no-framework prototype?** → `vanilla-web` (stack rules)
- **Need accessibility compliance?** → `wcag-accessibility-audit` (a11y)

## Source / vendoring

This is an **aggregation pack** — each `SKILL.md` was vendored unmodified from a
public upstream:

- `anthropics/skills` → `frontend-design`
- `vercel-labs/agent-skills` → `react-best-practices` + `web-design-guidelines`
- `janjaszczak/cursor` → `vanilla-web`
- `mastepanoski/claude-skills` → `wcag-accessibility-audit`

See [`ATTRIBUTIONS.md`](./ATTRIBUTIONS.md) for full credits, licenses, and re-sync
instructions. Vendored files retain their upstream copyright and license terms;
the MIT license on this repository covers only the meta-files
(`README.md`, `ATTRIBUTIONS.md`, `LICENSE`).

## Companion packs

- [`Neutralthiscrazy/minecraft-skills`](https://github.com/Neutralthiscrazy/minecraft-skills) —
  5-skill pack covering Minecraft plugin-dev, modding, multiloader, datapack,
  testing (vendored from `Jahrome907/minecraft-agent-skills`).

## Requirements

- Node.js 18+ with `npx` (the installer uses `npx` to fetch and run the
  Skills CLI).
- No API keys or accounts needed.

## License

MIT for meta-files. Vendored SKILL.md files retain upstream licensing — see
`ATTRIBUTIONS.md`.
