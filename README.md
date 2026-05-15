# omni-embed-portal-skills

Claude Code plugins for scaffolding white-label Omni Analytics embed portals.

## Plugins

### [`create-omni-embed-portal`](./create-omni-embed-portal)

A skill that scaffolds a complete white-label React + Vite + Vercel embed portal modeled after the reference implementation at <https://fishtankbubble.vercel.app>.

Given a customer website URL and Omni credentials, it produces a deployable app with:

- **Config page** — auto-scan brand identity from a URL, with 21-industry mock fallback
- **Overview tab** — hero + 3 portal CTAs (AI Chat / Dashboards / Hub)
- **Dashboard tab** — single Omni dashboard embed
- **AI Chat tab** — Omni's AI agent (Blobby) embed with configurable Connection
- **Flights tab** — embedded dashboard with runtime filter controls via postMessage
- **Hub tab** — `mode=APPLICATION` embed scoped to a per-brand entity folder
- **Per-user access filters** via Omni user attributes
- **Per-brand dynamic theming** via synthesized Omni `customTheme` JSON

## Install

Clone this repo into your `~/.claude/plugins` directory, or use Claude Code's plugin commands:

```bash
git clone <repo-url> ~/.claude/plugins/omni-embed-portal-skills
```

Then in any Claude Code session, the `create-omni-embed-portal` skill will be available. Trigger it with prompts like:

- "Build me a white-label Omni embed portal for `https://stripe.com`"
- "Recreate fishtankbubble for `<customer>` using these Omni credentials"
- "Spin up a demo embed app pointed at `<url>`"

## Reference

- **Live demo**: <https://fishtankbubble.vercel.app>
- **Reference repo** (the actual code this skill scaffolds): <https://github.com/fishtankau/fishtank-bubble>
- **Omni Embed docs**: <https://docs.omni.co/embed/setup/standard-sso>

The skill's `SKILL.md` cites specific files and line numbers from the reference repo. When working through the skill, clone or browse <https://github.com/fishtankau/fishtank-bubble> as the source of truth for exact code shapes (API payloads, postMessage events, CSS classes, etc.).

## Video walkthroughs

Two recorded demos show the end-to-end flow the scaffolded app produces. Watch these before invoking the skill to understand what you're building:

1. **[Configuring and Embedding Demo Application](https://ro.am/share/kf9rvxy2-ozyawaf7-v4gvj2ai-0mle9r94)** — operator side: scanning a customer website, picking an industry template, wiring Omni credentials, theming, Hub entity folder setup, and AI Chat connection settings.
2. **[Embedding POC Portal with Demo Settings](https://ro.am/share/gkr2v39j-5qtvqps2-0vldo04z-cljhd3l6)** — end-user side: logging in as different regions, walking the Overview → Dashboard → AI Chat → Flights (with live filter postMessage) → Hub tabs in the embedded portal.

The fishtank-bubble repo's README also embeds these recordings alongside a written walkthrough of every Config field and every dashboard tab.
