# crate-landing

Marketing landing for **Crate IMS** at `https://crate.ersaptaaristo.dev`. Astro 6 static site, deploy via VPS + Caddy.

**Live app demo (separate repo `tryea/crate-webapp`):** [app.crate.ersaptaaristo.dev](https://app.crate.ersaptaaristo.dev)

---

## Why this exists separately

Per [DEC-005](../crate-webapp/docs/decisions/DEC-005-github-workflow-and-deployment.md) and [DEC-006](../crate-webapp/docs/decisions/DEC-006-landing-taste-anchor.md): the landing has different optimization targets than the app (SEO + Lighthouse 100/100/100/100 vs authenticated dashboard interactivity). Splitting them lets the app stay heavy Next.js while the landing stays sub-50ms TBT static Astro.

## Taste anchor (binding)

**Mercury LP grammar** — single-anchor commit per DEC-006. Mixing Linear / Resend / Attio visual moves is forbidden. See the decision record + transcript in the `crate-webapp` repo:

- [DEC-006 decision record](../crate-webapp/docs/decisions/DEC-006-landing-taste-anchor.md)
- [DEC-006 full council transcript](../crate-webapp/docs/council/DEC-006-deliberation.md)

## Stack

- [Astro](https://astro.build) 6.4 — static-first SSG
- [Tailwind CSS v4](https://tailwindcss.com) — `@theme inline` token aliasing
- Bun 1.3+ — package manager
- Geist + Geist Mono (self-host TBD — next iteration)

## Quick start

```bash
bun install
bun run dev          # http://localhost:4321
bun run build        # → ./dist
bun run preview
```

## Token system

`src/styles/globals.css` — light-only port of the `crate-webapp` token vocabulary. Same `--color-canvas` / `--color-ink` / `--color-border` mental model as the app, so a designer hopping between repos doesn't context-switch.

- ✗ NO `.dark` block (Mercury landing is light-only in v1)
- ✗ NO warm-tinted bg (R=G=B oklch chroma=0 only — Attio rejection rule)
- ✓ Section-bg rhythm = alternating `canvas` (white) / `canvas-alt` (neutral cool-gray)
- ✓ Trust-strip mono labels via `font-mono` (max 2–3 sections per DEC-006)

## Roadmap

Issues tracked in `tryea/crate-webapp` (single project board to keep both surfaces aligned):

- **[#5](https://github.com/tryea/crate-webapp/issues/5)** — Mercury-style hero + email capture + trust strip
- **[#6](https://github.com/tryea/crate-webapp/issues/6)** — Port `globals.css` token system (initial commit landed — light-half only)

## License

MIT
