# Building for Production

> Conference talk notes — 2026-06-02

## Speaker / Session

- **Speaker:** Liz Fong
- **Company:** Honeycomb.io

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

## Questions to Follow Up


## Action Items

