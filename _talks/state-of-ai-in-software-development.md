---
title: "State of AI in Software Development"
date: 2026-06-02
speaker: "DX — AI-Assisted Engineering Q1 Impact Report"
summary: "Insights across 400 orgs (50–10,000 engineers): 27.4% of code now AI-authored (up 8% from Q4), daily AI users ship 60% more PRs, dev ramp-up time nearly halved (~80 → ~30 days), and AI-readiness scorecards predict who absorbs the gains."
---

- **Source report:** DX — AI-Assisted Engineering Q1 Impact Report
  - https://getdx.com/uploads/ai-assisted-engineering-q1-impact-report.pdf


## Key Takeaways


## Notes

- The talk's aim is to **share insights across 400 orgs**.
- Engineering org sizes range from **50 to 10,000**.
- **27.4% of code is AI-authored** — up **8% from Q4**.
- **Daily AI users are shipping 60% more PRs.**
- Regular users report:
  - **+2.6%** increase in quality metrics
  - **+2.2%** in maintainability
  - Change failure rates **down 0.11%**
- **Change confidence is volatile** — varies by company.
  - 💭 *My thought: maybe a lot of the negative-leaning companies aren't considering some of their own org limitations and practices.*
- Some companies are shipping as much as **50% more defects**.
- **Junior engineers use AI the most** — they don't have as many learned behaviours.
- **Staff engineers use fewer tokens** for the same use case than junior engineers.
- **Traditional enterprises are using more AI** — primarily due to **structured rollouts**.
- **Larger companies use AI more frequently.**
  - 💭 *My thought: more code, more complexity, more time savings required.*
- Some engineers are still going through **Shadow AI** instead of the enterprise tools.
- **Rust usage has gone up** — it's a very structured language.
- **Dev ramp-up time has almost halved** — from **~80 days to ~30 days**.
- **Engineering managers are shipping 4x more code than last quarter.**
- **75% of designers and PMs also use AI code assistants.**
- We're still tackling only the **initial part of the problem** — most of the time isn't spent on the bottleneck.

### Slide: "Increasingly referred to as AI Readiness…"

Characteristics of an AI-ready codebase:
- Clear, accurate, well-structured documentation
- Data structures with straightforward relations
- Readable, manageable, modular code
- Fast, reliable local and CI feedback loops
- Stable (read: non-flaky) robust test suites

**AI Readiness scorecard (tiered checks):**
- **Bronze:** Defined owner · AGENT.md exists · README.md exists · Local development docs
- **Silver:** >80% code coverage · Linter configured · Branch protection configured
- **Gold:** Uses feature flags · Secret management configured · API schema documentation


## Questions to Follow Up


## Action Items
