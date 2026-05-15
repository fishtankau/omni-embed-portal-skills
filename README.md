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

### First Recording: Overview of the Default Embed Demo Portal

📹 **[Watch on Roam →](https://ro.am/share/kf9rvxy2-ozyawaf7-v4gvj2ai-0mle9r94)**

This recording provides a walkthrough of the **standard demo environment**, showcasing the baseline features and user experience of the application.

* **Default Portal Experience:** Displays a pre-configured "SEATAC Airport" brand, featuring a landing page with an overview of services and an embedded AI chat.
* **Performance Comparison:** Showcases a dedicated tab for comparing load times and performance between JavaScript events and URL parameter embedding.
* **Identity & Access:** Demonstrates Role-Based Access Control (RBAC) and the use of user attributes to filter dashboard data (e.g., East Region Manager view).
* **Standard Features:** Highlights the integration of filters, customized application folders, and the centralized Hub.

---

### Second Recording: Configuring Custom POCs and Demo Instances

📹 **[Watch on Roam →](https://ro.am/share/gkr2v39j-5qtvqps2-0vldo04z-cljhd3l6)**

This recording demonstrates how to use the **configuration page** to transition from the default setup to a specific customer Proof of Concept (POC) or a different demo instance.

* **Advanced Configuration:** Details how to expand "Advanced Options" to input unique API and Embed keys, allowing the app to fetch specific dashboards from different environments.
* **Dynamic Customization:** Shows how to override scanned data with manual values for products and services, ensuring the overview page aligns with a specific customer's needs.
* **UI Logic:** Illustrates how the demo interface dynamically adapts based on the config page; unchecking specific attributes or features (like region filters) automatically hides the corresponding tabs in the live portal.
* **Instance Switching:** Provides a step-by-step guide on generating new keys and updating domain settings to successfully launch a tailored customer instance.
