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
- **AI agents will create more things** — so **what's your fleet management setup?**

### Slide: Platform architecture — three tiers (his favourite model)

| Layer | Why & How? | Who? | What | Example tech |
| --- | --- | --- | --- | --- |
| **Application Choreography** (Developer Control Plane) | "Code, ship, run" — sustainably deliver observable business value to customers (end users) | App developers, Full-stack engineers, DevOps, SREs | UI (Portals), CLI, Declarative config — *software dev lifecycle* | Backstage; Heroku CLI & Netflix Newt; Score; Radius & KubeVela (OAM) |
| **Platform Orchestration** (Platform Orchestrator) | "Design, enable, optimize" — provide x-as-a-service, process automation, and fleet management to developers | Platform engineers, Engineering enablement, DevEx engineers, SREs | Platform API — *platform lifecycle* | Kratix Promise; Humanitec Resource Definition; Crossplane Compositions; Argo/Flux CRDs |
| **Infrastructure Orchestration / Composition** (Infrastructure Control Plane) | "Plan, build, maintain" — provide infrastructure building blocks for consumption and composition to the platform team | Platform engineers, DevOps, Operators, Sysadmins, Infrastructure engineers | IaC, CRDs, Bash scripts — *infrastructure lifecycle* | Terraform; Crossplane; Ansible; Bash |

- Source: https://syntasso.io/post/platform-engineering-orchestrating-applications-platforms-and-infrastructure
- 💭 The **three tiers are his favourites**: Application Choreography (software dev lifecycle) ↔ Platform Orchestration (platform lifecycle) ↔ Infrastructure Orchestration (infrastructure lifecycle).
- Where the activity is today:
  - A lot of orgs are **spending time in the App Choreography layer.**
  - Folks are **getting a lot of AI to write the infra layer.**
  - 💭 *(Implication: the middle — Platform Orchestration — is the under-served layer.)*
  - **App Choreography is putting a lot of pressure on the other layers** (platform + infra).
- Recurring framing: he keeps referring to things as a **socio-technical system** (it's people + tech, not just tech).
- 💭 *My thought: feels like we're standardising on how we build platforms.*
- **Each team / group of teams must own their flow of value** — not just the application or the infrastructure layer.
- **"You build it, you run it"** gets hard at scale: with **~50 teams**, management and upkeep become difficult.
- Enterprises are **using AI to run side quests**, but **operationalising and maintaining** that work is difficult.

### Slide: Team Topologies

- **4 fundamental topologies:**
  - **Stream-aligned team**
  - **Enabling team**
  - **Complicated Subsystem team**
  - **Platform team**
- **3 core interaction modes:**
  - **X-as-a-Service** (highlighted on the slide)
  - **Facilitating**
  - **Collaboration**
- Diagram shows **flow of change** across stream-aligned teams, supported by a platform team underneath (X-as-a-Service).
- Source: https://teamtopologies.com/key-concepts

### Side note: AI agents

- You need to create **bounded agents** — **data-limited** and **context-limited.**

### Slide: Conclusion

- **AI increases the demand for platforms.**
- **Platform architecture is as important as software architecture.**
- **Think three layers:** app, platform (capabilities), infra.
- **Measure platform impact:** time to provision, upgrade, and offering.
- **Build platforms to maximise flow of value.**

## Questions to Follow Up


## Action Items
