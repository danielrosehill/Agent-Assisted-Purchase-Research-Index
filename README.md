# Agent Assisted Purchase Research Index

[![Master Index](https://img.shields.io/badge/Master%20Index-All%20Repositories-purple?style=for-the-badge&logo=github)](https://github.com/danielrosehill/Start-Here)

Templates, agent skills, and demos for the pattern of using an AI agent to drive consumer purchase research — from defining a precise spec to matching products and checking online shopping sources.

**Last Updated:** August 2026

---

## The Pattern

Most AI shopping tools conflate two concerns: *what you want* and *what's currently on the market*. The pattern collected here decouples them:

1. **Spec definition.** An AI agent interviews the user, or parses and verifies raw input, until a precise requirements spec exists — budget, priorities, must-haves, nice-to-haves, constraints.
2. **Product matching.** A separate step reasons over the spec to propose candidate products, independently of any single retailer's inventory.
3. **Availability research.** Online-shopping skills query real retailers for live pricing, stock, and shipping.

Because the spec is decoupled from the research, the same workspace serves small consumer buys (a television) and large ones (a car), and becomes a living source of truth. Slash commands let the user amend the spec as requirements and budgets evolve, while product-availability passes can be re-run any time without starting over.

### Persistent user context across repos

The pattern assumes one repo per purchase — which means the per-repo spec is about *this specific buy*, not about who the user is. Restating general preferences in every new repo (trusted brands, suppliers to avoid, whether this is personal or for a business, recurring priorities like warranty terms or domestic-first sourcing) is wasteful and error-prone.

The fix is a **persistent memory layer** sitting outside the per-repo spec — something like [Mem0](https://github.com/mem0ai/mem0) — that each new purchase-research workspace can read from and write back to. The spec captures what's unique to *this* purchase; the memory layer carries the evergreen context the user shouldn't have to retype:

- Who's buying (personal vs. business, which business)
- Trusted suppliers and brands
- Suppliers or brands to avoid, and why
- General shopping priorities (warranty, support reputation, repairability, sustainability, Israeli-first, etc.)
- Prior purchase decisions worth remembering

Treat the memory layer as part of the pattern, not an optional add-on — it's what makes the per-repo model viable at any real scale.

---

## Table of Contents

- [Agent Skills](#agent-skills)
- [Demos](#demos)
- [Related Plugins](#related-plugins)
- [Templates](#templates)

---

## Agent Skills

### Israel Online Shopping Skill

Claude Code plugin bundling agent skills for online shopping in Israel — comparison shopping across domestic retailers, category-based search, and Israel-vs-international price checks. Ships with Playwright and Tavily MCP, and is a drop-in building block for the Israel-specific template below.

[![View Repo](https://img.shields.io/badge/View-Repo-blue?style=flat&logo=github)](https://github.com/danielrosehill/Israel-Online-Shopping-Skill)

---

## Demos

### Claude Shopping Eval Demo

Worked example of the pattern end-to-end — captured spec, retailer catalog screenshots, and AI-generated recommendations for a real consumer purchase. Useful as a reference when trying the pattern for the first time.

[![View Repo](https://img.shields.io/badge/View-Repo-blue?style=flat&logo=github)](https://github.com/danielrosehill/Claude-Shopping-Eval-Demo)

---

### Agentic Purchase Pipeline

The pattern written up as **eight explicit stages**, with a full worked example — a hardware purchase specified, researched, reversed four times, and ordered. Where the shopping-eval demo captures a single pass over screenshotted catalogues, this one captures the *loop*: research feeding back and changing the spec, which turned out to be where most of the value is.

Two findings from the worked run are generalisable to the whole pattern: compare **landed cost, not list price** (a $40 shipping quote overturned the recommendation on the last step), and **drive the real storefront** rather than trusting search results, because search does not show variant-level stock.

[![View Repo](https://img.shields.io/badge/View-Repo-blue?style=flat&logo=github)](https://github.com/danielrosehill/Agentic-Purchase-Pipeline)

---

## Related Plugins

### New Repo From Template Plugin

Claude Code plugin that spins up a new GitHub repo from any of Daniel's template repos — including both purchase-research templates below — fetched live from the Repo-Starters-And-Templates-Index. The recommended entry point for starting a new purchase-research workspace.

[![View Repo](https://img.shields.io/badge/View-Repo-blue?style=flat&logo=github)](https://github.com/danielrosehill/New-Repo-From-Template-Plugin)

---

## Templates

### Claude Israel Shopping Recommender Template

Israel-focused variant of the purchasing-assistant pattern — domestic-first product evaluation, Amazon-shippability check, and AliExpress fallback, with the Israel Online Shopping skills bundled in. Use this when the target market is Israel.

[![View Repo](https://img.shields.io/badge/View-Repo-blue?style=flat&logo=github)](https://github.com/danielrosehill/Claude-Israel-Shopping-Recommender-Template)

### Claude Purchasing Assistant

General-purpose Claude Code template for purchase planning — interviews the user to build a spec, then runs product-matching and availability passes. The market-agnostic baseline; fork this when no region-specific template fits.

[![View Repo](https://img.shields.io/badge/View-Repo-blue?style=flat&logo=github)](https://github.com/danielrosehill/Claude-Purchasing-Assistant)

---

## License

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
