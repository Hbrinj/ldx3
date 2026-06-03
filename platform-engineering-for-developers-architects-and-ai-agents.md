# Platform Engineering for Developers, Architects, and the Rest of Us (AI Agents)

> Conference talk notes — 2026-06-03

## Speaker / Session

- **Speaker:** Daniel Bryant
- **Org:** Syntasso


## Key Takeaways


## Notes

### Premise

- **AI increases the demand for platforms.**
- **Platform architecture is as important as software architecture.**
- Three layers: **App · Platform (capabilities) · Infrastructure.**
- **Build platforms to maximise the flow of value** — do that and you'll **do well for both humans and agents.**

### Framing

- This talk's lineage started **4 years ago** — from **Kubernetes**, then **PaaS** — but **what next?**
- The recurring question: **how much do I build myself, buy, or blend?**
- **Cognitive load increased** as the **tooling exploded** and became **more complex.**
- **Platform and infrastructure exploded** — lots of **baggage.**
- **How do I manage my platform and update it?**
  - Folks are **moving away from the front ends and going direct to MCPs.**
  - That means **you're creating problems without considerations for the platform.**
- **Software creation is now faster than organisations can safely operationalise it.**

### Slide: "Gartner: What is platform engineering?"

> "Platform engineering **improves developer experience** and productivity by providing **self-service capabilities** with **automated infrastructure operations**.
>
> It is trending because of its promise to optimise the developer experience and accelerate product teams' delivery of customer value."

- Gartner "Diagram of Platform Engineering" layers (top → bottom):
  - **Product and Service Teams** (consumers) → via a **Developer Portal**.
  - **Digital Platform**: Reusable Components · Tools · Platform Services · Knowledge — built by a **Platform Team**.
  - **Infrastructure Platform** sitting over **Infrastructure Complexity**.
- Source: https://www.gartner.com/en/articles/what-is-platform-engineering (slide branded **Kratix.io**).

### Slide: "What is a platform, anyway?"

> "A digital platform is a **foundation of self-service APIs, tools, services, knowledge and support** which are arranged as a **compelling internal product**. Autonomous delivery teams can make use of the platform to **deliver product features at a higher pace, with reduced coordination**."
>
> — **Evan Bottcher**, https://martinfowler.com/articles/talk-about-platforms.html

### Why platforms?

- Platform teams need to **provide everything as a service** to **rapidly and sustainably deliver value to end users.**
- **Decrease risk** and **automate manual processes.**
- To **increase efficiency**, you need to **manage and scale your digital platform resources as a fleet.**
- Think about **platform metrics** — e.g. **how long does it take you to create and offer a new platform capability?**
  - Often it's **months** in many orgs.
  - Companion metric: **how long does it take you to provision an instance of a platform capability?**
  - And: **how long does it take to do a controlled upgrade** — i.e. **time to compliance?**

## Questions to Follow Up


## Action Items
