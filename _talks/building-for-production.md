---
title: "Building for Production"
date: 2026-06-02
speaker: "Liz Fong (Honeycomb)"
summary: "AI doesn't change the fundamentals — it amplifies whatever practices you already have; Honeycomb ships ~44% AI-authored changes by leaning harder on platform engineering, fast CI, continuous deployment, and closed-loop observability."
---

## TL;DR

Liz Fong (Honeycomb.io) on shipping AI-authored code to production at scale. The headline: **AI doesn't change the fundamentals — it amplifies whatever practices you already have.** Honeycomb now has ~44% of changes AI-authored (vs ~25–30% human), accepting ~20% automatically, without reworking the AI code. They didn't "explode" because they leaned *harder* on platform engineering — fast, AI-legible CI (RWX), continuous deployment of small changes, feature flags, and closed-loop observability that ties production signals back to the PR/agent that shipped them.

It isn't free: ~30% more production incidents and more time spent triaging and reducing slop. The honest concessions — this won't transfer to a regulated bank, and cheap spot-fixes tempt you away from systematic ones (write-cost dropping doesn't drop maintenance-cost). Bottom line: reinvest the new throughput into the platform substrate, not marginal features, and remember "we didn't obviously break anything" isn't success — no one is done yet.

## Key Takeaways

- Not aiming for 100% AI-authored changes — AI augments, doesn't replace.
- AI code is shipped as-is — they aren't reworking it after the fact.

## Notes

- **Intercom / Fin** set a bar to **2x their changes into main**.
- They are accepting about **20% of changes automatically**.
- Not 100% AI changes.
- Changed to a **new CI system** — possibly helped them maintain velocity.
- Roughly **25–30% done by humans**, the next **~44% was AI**.
- They aren't reworking the AI code.
- **Swarmio** is roughly matching the raw Git messages — devs may not show "committed by Claude".
- Preference seems to be toward **greenfield projects**.
- Around **Feb 2026** they felt they had more trust — the same developers who used the tool prior started using AI more regularly.
- **So how did they not explode the systems?**
  - **Platform engineering practices** become more important — even more so than before.
  - Companies with dysfunctions are **amplified** by AI, whereas ones with strong platforms are not.
- **Continuous deployment** becomes even more important — small changes should make it to production more frequently.
- Their CI is **legible to AI** — they use **RWX**.
- Your **CI should be faster than your coding session**.
- **Skills and CLAUDE.md** become the substrate that defines how well the AIs perform.
- Humans should be able to **push back on the PRs** — they should be able to look through the PR and stop it from creating bad PRs.
- Just because you **can** do it with AI doesn't mean you **should**.
- They would pull the **raw customer request from Slack into Linear**, closing the loop entirely with **end-to-end checks**.
  - Example flow: write the PR → add telemetry → check it in QA → when it ships in the next release, verify the telemetry and software are working **in prod**.

### Slide: Closed-loop observability for agent work

1. **Instrument the shipped code, not just the agent**
   - Span attributes that link the running code back to the PR and agent session that created it.
   - Not "tokens spent"; rather "this PR shipped Tuesday is the source of Wednesday's anomaly."
2. **Production outcomes matter more than agent activity**
   - Latency, error rate, cost, user behaviour on agent-shipped features.
   - Did it work? What happened to real users?
3. **Closed-loop: production signal feeds the next change**
   - Cost-per-interaction SLOs that fire back into agent context.
   - Anomalies in BubbleUp auto-converting into review-agent rules.

### Costs / Trade-offs

- The team is spending **more time triaging production** — they've had an **uptick of ~30% in production incidents**.
- The team also spends more time **reducing slop**, but also uses the LLMs to **clean up tech debt, upgrade versions, etc.**
- AI is enabling folks to carry out **side quests**.
- **Code review** is catching bugs and creating **shared understanding**.
- They've used AI to **build tooling to understand what AI is shipping** — lots of **feature flagging** occurring.

### Slide: Where the sceptics are right (two concessions)

1. **Bank-LOB engineering won't transfer**
   - "You are not going to radically realign LOB engineering at a bank."
   - What makes this work at Honeycomb is downstream of cultural conditions that don't exist at a regulated enterprise.
2. **Spot-fix vs systematic-fix; complexity has a cost**
   - AI makes spot-fixes so cheap that you keep reaching for them when systematic answers would be better.
   - Write-cost dropping doesn't make maintenance-cost drop with it.

### Slide: Three things to take away

1. **AI amplifies your existing practices**
   - Going fast without autonomy, ownership, and feedback loops is enshittification.
2. **Be deliberate about capacity allocation**
   - Reinvest the new throughput in the platform substrate that lets you absorb more, not in marginal features.
3. **"We didn't obviously break anything" is not success on its own**
   - No one in this room is done. Including us.

## Questions to Follow Up


## Vendor / Booth Notes

Moved to [vendor-booth-notes.md](vendor-booth-notes.md).


## Action Items

- [ ] Research Harness AI Software Delivery Platform — request demo at www.harness.io/demo
- [ ] Research Unblocked
