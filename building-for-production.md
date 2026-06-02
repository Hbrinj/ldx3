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

## Questions to Follow Up


## Action Items

