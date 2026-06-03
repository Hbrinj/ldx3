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


## Questions to Follow Up

- Research the **DevOps playbook** that eBay executed.


## Action Items
