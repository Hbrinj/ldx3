# We Doubled Engineer Productivity at eBay but Couldn't Change Culture

> Conference talk notes — 2026-06-03

## Speaker / Session

- **Speaker:** Randy Shoup
- **Org:** eBay


## Key Takeaways


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


## Questions to Follow Up

- Research the **DevOps playbook** that eBay executed.


## Action Items
