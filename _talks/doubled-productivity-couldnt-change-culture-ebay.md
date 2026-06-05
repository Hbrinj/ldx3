---
title: "We Doubled Engineer Productivity at eBay but Couldn't Change Culture"
date: 2026-06-03
speaker: "Randy Shoup (eBay)"
summary: "Randy Shoup on doubling eBay engineering productivity via the DevOps playbook — and how a pathological, risk-averse culture with centralised waterfall planning blunted the gains and ultimately cost him his job."
---

## Key Takeaways

- Randy and team **doubled engineering productivity** at eBay (2x features/bug fixes, 10x deploy frequency, 3x change failure rate, 3x recovery time, 10-day lead time) — but it **didn't save the business**, which stayed flat.
- **Velocity isn't enough**: a **pathological, risk-averse culture** (Westrum) and **centralised waterfall planning** neutralised the engineering gains.
- The transformation playbook that worked: **DevOps fundamentals** (CI, automated testing, streamlined process), **platform↔product partnership**, evangelists surfacing real problems, **friction as input / DORA as output**, PDCA, modularising the app to the org (Conway's law).
- **Change must be top-down, bottom-up AND middle-out** — Randy underestimated the need for **peer-exec buy-in**, which ultimately cost him his job.
- Hard lesson: **route around resistance** rather than appearing to threaten; **legacy execs are masters at survival.**
- 💭 *Nuance (from post-talk research): the Velocity initiative spanned eBay's **~4,500 services** and is framed in public write-ups as an **ongoing/continued success**, not purely a cautionary tale. The "couldn't change culture" angle is Randy's **personal/leadership lens** layered on top of a genuine engineering win.*


## Notes

- Premise: they **doubled engineer productivity** at eBay, but **couldn't change the culture**.
- This is Randy's **proudest achievement** — but it also **got him fired**, due to the inability to change the **pathological culture**.
- Context: **eBay has been a flat business** over the last few years.
- The **US economy grew more than eBay's ecommerce** business did.
  - The **economy grew 6x** in real money, while **eBay grew 0.91x**.

### The productivity wins (DORA-style metrics)

- **Lead time for change: 10 days** — 💭 *better than us!*
- **Features and bug fixes: doubled (2x).**
- **Deployment frequency: 10x.**
- **Change failure rate: improved 3x.**
- **Time to recover: improved 3x.**

### How they did it

- They executed the **DevOps playbook**.
  - ❓ *Follow up: research this — the DevOps playbook.*
- Spent a lot of time on **CI**.
- **Automated testing.**
- **Streamlined team processes** — code reviews and manual signoffs.
- Some of their most meaningful changes: **produce a library** etc., **instead of trying to make service changes that other teams had to test**.
- **Platform and product engineering teams worked together.**
  - Problem they hit: the **platform team would produce new versions, but product engineering wouldn't adopt** them.
  - Turned out the **updates didn't solve product engineering's real problems**.
  - Fix: used a **team of evangelists** sent out to each area to **bring back problems to solve**.
  - Ran a **weekly "team of teams" meeting** that enabled **natural but deliberate collaboration**.

### Measurement

- **DORA metrics were the output; developer friction was the input.**
- **Dashboards for every team, app, and org.**
- Ran proper **Plan-Do-Check-Act (PDCA) cycles.**
- They **identified impediments to flow.**
  - Example conversation they had: *"I see you're deploying once or twice every month — what's going on?"*
  - Mantra: **"Your impediments are my backlog."**
- Division of labor: **platform teams produce tools, product engineers consume tools.**
- **Made it safe to say you were struggling.**
- **Executive support allowed them to keep moving.**
- They **partnered with each of the areas that individuals felt were slow.**
- Started with a **small group**, then **automated things that ended up helping everyone.**
- They **regularly deployed every app.**
- They created a **patch pipeline to update libraries.**
- They **modularized their app to align to the org structure** (Conway's law).
- Built **domain mini apps.**

### Why did velocity not save the company?

- **eBay suffers from the unwillingness to disrupt their historical business model.**
- **Competitors disrupt or arbitrage.**
- The company is **highly risk averse.**
- **Every user-facing change was met with near revolt** — the **"seller straightjacket."**
- When you've been a **flat business**, the setup **pushes you continually towards risk aversion.**
  - **Example of user revolt:** adding **search term correction** — e.g. a seller had misspelled "iphone" as "ifone."
    - Sellers would **buy these cheap** (mispriced because they're hard to find), **rename them, and resell**.
    - The correction would **disrupt that micro business** — hence the revolt.
- They had **centralised waterfall planning** — work can only happen if it's **approved by the executive team.**
  - Work must be **big enough to reach the executive team.**
  - **Smaller projects would need to be tacked on.**
    - 💭 *C1 seems to have this same problem.*
- They became a **feature factory** — in a flat business you **don't want to tie your bonus to growth** when **execution on projects is the preference.**

### Slide: "Culture as Foundation"

- Source: **_Accelerate: The Science of DevOps_** — Nicole Forsgren, PhD; Jez Humble; Gene Kim.
- Nicole Forsgren is the primary author. The book defines **three types of culture** (Westrum typology).
- The speaker placed **eBay in the Pathological** column — *"the terrible... pathological fear."*

| Pathological (Power-Oriented) | Bureaucratic (Rule-Oriented) | Generative (Performance-Oriented) |
| --- | --- | --- |
| Low cooperation | Modest cooperation | High cooperation |
| Messengers "shot" | Messengers neglected | Messengers trained |
| Responsibilities shirked | Narrow responsibilities | Risks are shared |
| Bridging discouraged | Bridging tolerated | Bridging encouraged |
| Failure leads to scapegoating | Failure leads to justice | Failure leads to inquiry |
| Novelty crushed | Novelty leads to problems | Novelty implemented |

- **No real autonomy for teams or individuals.**

### Slide: VP "X"

**Culture of Terror**
- Engineers in constant fear of making any mistake.
- Threatened high performers with poor reviews if they left the team.
- Exceptional engineers and leaders became internal refugees or left the company entirely.

**Empire Building**
- More than 700 employees and contractors to build Buyer Experience.

**Faux Agile**
- Multi-year projects, regularly delayed.
- "Planning Sprints", "Design Sprints", "Development Sprints", "QA Sprints"…
- Personally approved all deployments for more than a year.

**Karma in Action**
- Maneuvered behind the scenes to fire the Chief Architect in 2022.
- Fired by CPO 6 months later.

- 💭 **Why Randy was fired:** he **called out that waterfall setup**, and as a result was **let go** — bad culture.

### Lessons / reflections

- **Successful change is top-down, bottom-up, AND middle-out.**
  - He **should have gotten more buy-in from his peers** — which he **didn't foresee being the problem.**

### Slide: "What I Learned" (with a "HOPE" Scrabble-tiles image)

1. **Top-Down, Bottom-Up, Middle-Out**
   - Engage peer execs as allies from the start.
2. **Route Around Resistance**
   - Better to bypass than to appear to threaten.
   - Legacy execs are masters at survival.
3. **See the Whole Board**
   - Demonstrate results and credibility with Software Delivery, then tackle Planning.
4. **Easier to Transform a Malleable Organization**


## Background: the "DevOps playbook" (follow-up research)

> Added after the talk — high-level context on what "the DevOps playbook" refers to.

- It's not a single proprietary doc. Randy means the **well-established DevOps body of practice** popularised by the **DORA research program**, the book **_Accelerate_** (Forsgren/Humble/Kim), and **_The DevOps Handbook_** (Kim/Humble/Debois/Willis). The eBay "Velocity" initiative was a deliberate application of it.
- **Measure with the four DORA metrics** (the talk's "output"):
  - Deployment frequency · Lead time for change · Change failure rate · Time to restore service.
  - Treat **developer friction/impediments as the leading "input"** that moves those outputs.
- **Core technical capabilities** the playbook pushes:
  - **Continuous integration** + **trunk-based development** (small batches into mainline, not long-lived branches).
  - **Comprehensive automated testing** with fast, reliable feedback.
  - **Deployment automation / regular deploys of every app**; loosely-coupled architecture so teams ship independently (maps to their library-over-shared-service and "domain mini-apps" moves — Conway's law).
- **Organisational / cultural capabilities** (the part eBay couldn't fully crack):
  - **Generative (Westrum) culture**, psychological safety, **loosely-coupled empowered teams** with real autonomy.
  - **Lightweight change approval** instead of centralised, heavyweight (waterfall) sign-off.
- **How eBay rolled it out:** focused on a **few pilot domains** (e.g. Selling, Search, Ads), specific apps within them, and **platform tracks** (build/CI/staging tooling + engineer education) — then expanded. Randy's own framing: it doubled productivity but stalled against pathological culture and exec-gated planning.
- **Randy's public talks on exactly this** (good source material):
  - "Doubling Engineering Productivity at eBay Through DevOps" (YOW! 2022) — https://www.youtube.com/watch?v=sjc8UZvlWYQ
  - "Platform Engineering: Lessons from the Rise and Fall of eBay Velocity" (InfoQ/QCon) — https://www.infoq.com/presentations/platform-engineering-lessons/
  - IT Revolution: "Driving a Tech-Led Reimagination through DevOps at eBay" — https://itrevolution.com/articles/driving-a-tech-led-reimagination-through-devops-at-ebay-2021/
  - DORA capabilities catalogue — https://dora.dev/capabilities/


## Questions to Follow Up

- ~~Research the **DevOps playbook** that eBay executed.~~ ✅ See "Background: the DevOps playbook" above.


## Action Items
