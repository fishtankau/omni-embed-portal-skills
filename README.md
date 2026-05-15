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

## Recording Summaries

White-label React + Vite portal that embeds **Omni Analytics** — dashboards, AI chat, per-customer entity folders, and access-filtered data — behind a configurable brand.

**Live demo app:** <https://fishtankbubble.vercel.app>

## 🎥 Recording Summaries

### First Recording: Overview of the Default Embed Demo Portal

📹 **[Watch on Roam →](https://ro.am/share/kf9rvxy2-ozyawaf7-v4gvj2ai-0mle9r94)**

This recording provides a walkthrough of the **standard embed portal demo**, showcasing another embed portal user experience using generic data.

* **Default Portal Experience:** Displays a pre-configured "SEATAC Airport" brand, featuring a landing page with an overview portal page and Omni embed tabs.
* **Performance Comparison:** Showcases a dedicated tab for comparing load times and performance between JavaScript events and URL parameter embedding.
* **Identity & Access:** Demonstrates Role-Based Access Control (RBAC) and the use of user attributes to filter dashboard data (e.g., East Region Manager view).
* **Custommisation:** Highlights the integration of application filters passing values to Omni embedded dashboards.

---

### Second Recording: Configuring Custom POCs and Demo Instances

📹 **[Watch on Roam →](https://ro.am/share/gkr2v39j-5qtvqps2-0vldo04z-cljhd3l6)**

This recording demonstrates how to use the **configuration page** to transition from the default setup to a specific customer Proof of Concept (POC) or leverage demo instance.

* **Advanced Configuration:** Details how to expand "Advanced Options" to input instance API and Embed keys, allowing the app to fetch specific dashboards from different environments.
* **Dynamic Customization:** Shows how to override scanned data with manual values for products and services, accelerating a more custom demo aligned to prospect's industry.
* **Instance Switching:** Provides a step-by-step guide on generating new keys and updating domain settings to successfully launch a tailored customer instance.

---

## What this app is

A single React app that lets you:

- Point at **any customer website URL** and auto-generate a branded portal (logo, colors, key messages, products) from the site's HTML.
- Fall back to a **industry template library** (Healthcare, Finance, Tech, Retail, …) when the site blocks scraping.
- Embed **Omni dashboards** via signed SSO URLs, themed per-brand on the fly.
- Embed Omni's **AI chat agent (Blobby)** with configurable connection scope.
- Spin up a **per-brand Hub** using Omni's APPLICATION-mode entity folder — Omni auto-provisions one folder per `entity` key on first SSO.
- Update dashboard filters from **outside the iframe** via `dashboard:filter-change-by-url-parameter` postMessage events (see the Flights tab).
