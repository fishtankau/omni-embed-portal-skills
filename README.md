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

1. **[Configuring and Embedding Demo Application](https://ro.am/share/kf9rvxy2-ozyawaf7-v4gvj2ai-0mle9r94)** — what the embedded portal looks like *to end users* once it's configured. Operator scans the brand (CTAG airport), fixes up logo/colors/key messages, sets the entity-folder name, then logs in as an East-region manager and walks Overview → AI Chat → the RBAC dashboard tab (showcasing JavaScript-event filters vs. URL-parameter filters side-by-side) → Hub.

2. **[Embedding POC Portal with Demo Settings](https://ro.am/share/gkr2v39j-5qtvqps2-0vldo04z-cljhd3l6)** — *operator-side rewire*: scan a different customer site, fall back to industry-template default values when scans fail, expand "Advanced — Omni configuration" at the bottom of the Config page to drop in a fresh embed key + API key + vanity domain (`<org>.demo.exploreomni.dev`), pick a dashboard from the auto-fetched list, optionally clear the theme + region user attribute. Notably: **unchecking the region attribute auto-hides the RBAC tab** — tab visibility is config-driven. End result: a fresh portal scoped to a new entity (`mypass`) with the Hub auto-provisioned for it.

The [fishtank-bubble README](https://github.com/fishtankau/fishtank-bubble#-video-walkthroughs) reproduces both transcripts paraphrased alongside a written walkthrough of every Config field and every dashboard tab.
