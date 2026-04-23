---
marp: true
theme: uncover
paginate: true
size: 16:9
header: "OSDay 2026 · Florence · Open Source in Production"
footer: "Diego Braga · linkedin.com/in/diegobraga86 · #osday"
lang: en
style: |
  /* === Accessibility-first theme ===
   * - Atkinson Hyperlegible (Braille Institute, low-vision optimized)
   *   with Verdana fallback (designed for screen legibility, ubiquitous)
   * - All foreground colors verified WCAG AA against pure-black background:
   *   body white #FFFFFF (21:1), amber #FFD166 (~13:1), sky #A8E6FF (~14:1),
   *   mint #B5F0B5 (~13:1), warn #FF8A8A (~7:1), muted #D0D0D0 (~16:1).
   * - Body 30px / small 24px / line-height 1.5 for readability.
   */
  @import url('https://fonts.googleapis.com/css2?family=Atkinson+Hyperlegible:wght@400;700&display=swap');

  section {
    background: #000000;
    color: #FFFFFF;
    font-family: "Atkinson Hyperlegible", Verdana, Geneva, sans-serif;
    font-size: 24px;
    line-height: 1.35;
    text-align: left;
    letter-spacing: 0.01em;
    padding: 50px 60px;
  }
  section.center { text-align: center; }

  h1, h2, h3 { font-weight: 700; line-height: 1.15; margin: 0.4em 0; }
  h1 { color: #FFD166; font-size: 1.7em; }
  h2 { color: #A8E6FF; font-size: 1.4em; }
  h3 { color: #B5F0B5; font-size: 1.15em; letter-spacing: 0.5px; }

  p, ul, ol, blockquote, table { margin: 0.5em 0; }
  li { margin-bottom: 0.25em; }

  strong { color: #FFD166; }

  blockquote {
    border-left: 6px solid #A8E6FF;
    padding-left: 1em;
    color: #FFFFFF;
    font-style: normal;
  }

  code {
    background: #2D2D2D;
    color: #FFFFFF;
    padding: 2px 6px;
    border-radius: 4px;
  }

  pre code { background: #2D2D2D; color: #FFFFFF; }

  table {
    font-size: 20px;
    border-collapse: collapse;
  }
  th, td { padding: 0.3em 0.6em; border: 1px solid #555555; }
  th { background: #1A1A1A; color: #FFD166; }

  a { color: #A8E6FF; text-decoration: underline; }
  a:hover, a:focus { color: #FFD166; outline: 2px solid #FFD166; }

  .stat {
    font-size: 88px;
    color: #FFD166;
    font-weight: 800;
    line-height: 1;
  }
  .stat-label {
    font-size: 24px;
    color: #FFFFFF;
  }
  .small { font-size: 20px; color: #D0D0D0; font-style: normal; }
  .small em { font-style: normal; }
  .warn { color: #FF8A8A; font-weight: 700; }
  .ok   { color: #B5F0B5; font-weight: 700; }

  /* Decorative-only marks: hide from screen readers via aria-hidden in markup */

  /* === Override uncover theme variables for high-contrast slide chrome === */
  section {
    --color-background: #000000;
    --color-background-paginate: #000000;
    --color-foreground: #FFFFFF;
    --color-header: #FFFFFF;
    --color-header-shadow: transparent;
    --color-highlight: #FFD166;
    --color-highlight-hover: #FFD166;
    --color-highlight-heading: #FFD166;
    --color-dimmed: #D0D0D0;
  }

  /* Slide-internal header/footer (from `header:` / `footer:` frontmatter)
   * — bare selectors so Marpit's `section X` scoping reaches them.
   * Default uncover sizes these at ~.45em (≈ 11 px) which is unreadable
   * from the back of the room; force a fixed 18 px. */
  header, footer {
    color: #FFFFFF !important;
    text-shadow: none !important;
    background: #000000 !important;
    opacity: 1 !important;
    font-size: 18px !important;
  }

  /* Page-number indicator (Marp renders this as section:after).
   * Default ~.6em (≈ 14 px) is small + sits over the bottom-right
   * gradient-corner. Force a readable size and remove the
   * decorative gradient corner so the number stands alone. */
  section:after {
    font-size: 22px !important;
    color: #FFFFFF !important;
    text-shadow: none !important;
    background: transparent !important;
  }

  /* Title slide: force explicit colors on inline em/strong with their own
   * background-color hint so axe can compute contrast unambiguously */
  h1, h2, h3, p { background-color: transparent; }
  em { color: inherit !important; font-style: italic; background-color: #000000; }
  strong { color: #FFD166 !important; background-color: #000000; }

  /* Marp Bespoke on-screen controls (OSC) are disabled at build time
   * via --bespoke.osc=false; their styling is therefore not needed here.
   * Keyboard navigation (arrows, space, F=fullscreen) still works. */
---

<!-- _class: center -->

![bg blur:6px brightness:0.25 Abstract photo of multicoloured source code on a dark screen — used as a decorative background; the talk content is in the foreground text](assets/hero-code.jpg)

# Open Source in Production

## Why Your Company Needs an OSPO
### *(Before It's Too Late)*

<br>

**OSDay 2026** · Florence
**Diego Braga** · CTO & Co-founder, Krateo PlatformOps

<!--
TIMING: 45 min total — aim for 35 min talk + 10 min Q&A.

OPEN WITH (≤ 30 seconds):
1. Thank OSDay organisers / Codemotion.
2. Acknowledge the Code of Conduct (osday.dev/code-of-conduct) and
   reaffirm we're operating under it for the whole talk + Q&A.
3. Say loud and clear that the slides, transcript, and accessibility
   statement are public at github.com/braghettos/osday-ospo — anyone
   who prefers to follow along on their own device can do so right
   now (better contrast, screen reader, larger text, etc.).

THEN HOOK:
"Hands up — who works at a company with a formal Open Source Program
Office?" Usually 2-5%. Then: "Hands up — who uses open source in
production every day?" Everyone. That gap is the entire talk.
-->

---

## Who I am · Who you are

**Me:** Chief Technology Officer (CTO) & Co-founder at **Krateo PlatformOps**.
Background in modernizing legacy applications — breaking monoliths into microservices, designing automation flows across the entire stack (app → physical machine), and enabling CI/CD *(continuous integration and continuous deployment)* through orchestrated Disaster Recovery and Change Management.

**You, probably:**
- A developer shipping code that's 80%+ open source
- An Engineering Manager (EM) or CTO worrying about compliance & security
- Someone who's googled "what does an OSPO actually do"

**The deal for the next 35 minutes:**
You'll leave with the language, the data, and the roadmap to start one.

<!--
Be honest about who you are. Don't oversell credentials.
The promise at the bottom is the contract — keep it.
-->

---

<!-- _class: center -->

![bg blur:4px brightness:0.3 Abstract glitch-art visualisation of broken digital code fragments — the visual mood for the part of the talk about unmanaged open source risk](assets/glitch.jpg)

# Part 1
## The Problem
### *Open Source is eating your codebase. Are you in control?*

<!--
3 minutes. Set the stakes hard.
-->

---

## A small number to start

<div class="stat">87%</div>
<div class="stat-label">of code in production contains open source components</div>

<br>

**Translation:** *Your* code is mostly *other people's* code.

You inherited the bugs. You inherited the licenses. You inherited the maintainers — or their absence.

<span class="small">Source: Black Duck OSSRA 2026, audited codebases across 16 industries.</span>

<!--
Pause for effect after the 87%. Let it land.
The "you inherited" line is the rhetorical pivot — you're already in the open source business whether you signed up or not.
-->

---

## The numbers get worse · vulnerabilities

| | |
|---|---|
| **581** | average vulnerabilities per codebase *(+107% YoY)* |
| **78%** | codebases with high-risk vulnerabilities |
| **44%** | codebases with critical-risk issues *(remote code execution, data breach)* |
| **68%** | codebases with license conflicts |

<span class="small">Black Duck OSSRA 2026 · 2,400+ commercial codebases audited</span>

<!--
Don't read the table. Pick one number and tell a story:
- 581 vulns is not a backlog you "get to next sprint"
- 44% RCE/breach risk is not theoretical
Pause after each. Next slide adds the supply-chain side.
-->

---

## The numbers get worse · supply chain

| | |
|---|---|
| **93%** | codebases with components inactive for 2+ years |
| **92%** | codebases with components 4+ years out-of-date |
| **65%** | organisations hit by a supply-chain attack last year |

<br>

**Translation:** almost every dependency you ship is years stale, and two-thirds of you have already been targeted.

<span class="small">Same source · Black Duck OSSRA 2026</span>

<!--
This is the "and that's just half of it" beat. The vulnerability
numbers are about today's bugs; the staleness numbers are about
tomorrow's bugs you're not patching.
-->

---

## Welcome to the Wild West

Without anyone owning open source, every team reinvents:

- 🔓 **Compliance** — "What license is this dep again?"
- 🛡️ **Security** — "Who patches transitive deps?"
- 🔄 **Reuse** — "Three teams just wrote the same client."
- 🤝 **Contribution** — "Can I send this PR upstream?"
- 🎓 **Onboarding** — "How do we even *use* GitHub here?"

Each unanswered question is a **decision tax** paid by every engineer, every day.

<!--
The "decision tax" framing is the one to land. Engineers viscerally
recognize it. Use a local example if you have one — "we shipped X
because we couldn't find Y, then six months later replaced X with Y."
-->

---

## What "no OSPO" looks like in real life

**🔥 Equifax (2017)** — 147M records breached. Root cause: an unpatched **CVE** *(a publicly known security vulnerability)* in Apache Struts.
*A single team owned patching. Nobody owned awareness.*

**🔥 Heartbleed (2014)** — 2 maintainers, $2K/year donations, securing half the internet's TLS.
*Everyone consumed it. Nobody invested in it.*

**🔥 Log4Shell (2021)** — 3 days of global panic. Why? Nobody had an SBOM.
*"Are we vulnerable?" "…we'll get back to you."*

**🔥 xz utils backdoor (2024)** — A multi-year social-engineering attack on a single overworked maintainer.
*The supply chain runs on volunteers. Treat it that way.*

<!--
These are the "ghost stories" of OSS. Most of the audience lived through
Log4Shell. Ask: "Where were you the night Log4Shell dropped?" — get a
laugh, then make the point: an OSPO doesn't prevent CVEs, but it makes
sure you can answer "are we exposed?" in minutes, not days.
-->

---

<!-- _class: center -->

# Part 2
## What is an OSPO?
### Open Source Program Office — and no, it's not "the legal team but for GitHub"

<!--
4 minutes. Define it precisely so the rest of the talk lands.
-->

---

## Definition

> *"An Open Source Program Office is the **center of competency** for an organization's open source operations and structure."*
>
> **— TODO Group · OSPO Glossary**

It is **not**:
- A legal review queue
- A compliance gate that says "no"
- A side project of the CTO's chief of staff

It **is**:
- The team that makes open source *strategic* instead of *accidental*
- The single place where legal, security, engineering, and community meet

<span class="small">Source: ospoglossary.todogroup.org</span>

<!--
The negation list is the most useful part. Audiences have wrong mental
models. Surface them first, then replace them.
-->

---

## Two faces of an OSPO

<br>

| **Inward-facing** | **Outward-facing** |
|---|---|
| Policy, process, tooling | Community engagement |
| Education & enablement | Foundation memberships |
| Compliance & security | Public contributions |
| InnerSource culture | Brand & recruiting |
| Metrics & reporting | Standards participation |

The OSPO is the **bridge** between *your* organization and the *open source* ecosystem you depend on.

<!--
The bridge metaphor is sticky. Reuse it later when discussing case studies.
-->

---

## The 5 roles inside an OSPO

🛠️ **Enabler** — removes friction, builds tooling, automates compliance

🧭 **Counselor** — advises on trends, technologies, "build vs. adopt vs. contribute"

📣 **Advocate** — promotes adoption internally, contribution externally

🌱 **Environmentalist** — keeps critical upstream projects healthy

🚪 **Gatekeeper** — enforces policy, manages risk, signs off on releases

<br>

**You don't need 5 people. You need someone wearing all 5 hats — explicitly.**

<span class="small">Source: TODO Group OSPO Mindmap</span>

<!--
The "5 hats, 1 person" line is the bridge to "you can start small."
Foreshadow the roadmap section here.
-->

---

## "But we're not Big Tech"

That's exactly *why* you need one.

| If you have… | …an OSPO is worth it |
|---|---|
| > 20 engineers | Decision tax compounds quickly |
| Customer contracts with IP/SBOM clauses | Compliance is a sales blocker |
| Any regulated workload (fintech, health, auto) | Auditors will ask. Have an answer. |
| Mergers & acquisitions (M&A) on the horizon | Open source due diligence is now standard |
| AI-generated code in production | License provenance is a 2026 problem |

**Capital One** — heavily regulated bank, OSPO since 2015.
**Porsche** — automotive manufacturer, OSPO since 2020.
**Comcast** — telco, two OSPOs (NBC + cable).

<!--
This is where you defuse the "we're too small" objection. Adjust
examples to the audience's industry if you can.
-->

---

<!-- _class: center -->

# Part 3
## The 4 Pillars
### *What an OSPO actually does, week to week*

<!--
8 minutes. The technical meat of the talk. One slide per pillar + an
overview. Don't go too deep — point them at the mindmap.
-->

---

## The 4 pillars

<br>

| Pillar | Day-to-day work |
|---|---|
| **1. Strategy & Governance** | Policy · risk · M&A due diligence |
| **2. Compliance & Security** | SBOM · CVEs · license scanning |
| **3. Contribution & Upstream** | Pull requests · projects · CLAs |
| **4. Culture & Talent** | InnerSource · training · recruiting |

<br>

Different orgs weight them differently. **All four exist.**

<!--
Verbalize each pillar out loud — the table is a memory aid, not the
content. Pause briefly after each row.
-->

---

## Pillar 1 · Strategy & Governance

**The question:** *Why are we using/contributing/releasing open source at all?*

- Define open source **strategy** aligned to business goals
- Set **policies**: when to consume, when to contribute, when to release
- Stand up an **Open Source Review Board** (legal + security + engineering)
- Make **risk explicit**: brand, IP, competitive, license
- Support **M&A** due diligence (target's open source software / OSS posture)

> *"There is nothing traditional about Capital One and our approach to technology."* — Capital One OSPO

<!--
Governance is the unsexy pillar but the foundation. Without it, the
other three are firefighting. Mention the Open Source Review Board
concept — it's a concrete artifact people can take home.
-->

---

## Pillar 2 · Compliance & Security

**The question:** *Do we know what's in our software, and is it safe?*

- Maintain an **SBOM** (Software Bill of Materials) for every product
- Automate **license scanning** in CI (Snyk, FOSSA, ScanCode, OSS Review Toolkit)
- Track **vulnerabilities** continuously, not just at release
- Define **license classification** (allowed, conditional, forbidden)
- Comply with **OpenChain ISO/IEC 5230**, **SPDX**, **CRA** *(EU Cyber Resilience Act, in force 2027)*

**The bar is rising fast.** EU CRA, US EO 14028, customer SBOM requirements.

<!--
The CRA is the regulatory hammer dropping on European companies in
2027. If your audience is European, lead with this. SBOM is no longer
optional.
-->

---

## Pillar 3 · Contribution & Upstream

**The question:** *Are we good citizens of the projects we depend on?*

- Process for **upstreaming patches** (don't carry forks forever)
- **Contributor License Agreement (CLA)** / **Developer Certificate of Origin (DCO)** infrastructure — *CLA Assistant* is open source
- **Project incubation** playbooks (naming, governance, license, hosting)
- Foundation memberships: **Linux Foundation, Apache, Eclipse, OpenSSF, CNCF** *(Cloud Native Computing Foundation)*
- Recognize and **reward** internal contributors

**Why it matters:**
> *"The collective knowledge of our engineers grows by interacting with the open source community."* — Uber OSPO

<!--
Most orgs are pure consumers. Becoming a contributor is a culture
shift. Frame it as "you can't influence what you don't contribute to" —
critical when a key dep changes direction.
-->

---

## Pillar 4 · Culture & Talent

**The question:** *Do our engineers know how to work in the open?*

- **InnerSource**: open source practices applied internally (transparency, PRs, public roadmaps)
- **Training**: licensing basics, contribution workflow, project management
- **Ambassador programs**: identify internal OSS leaders
- **Recruitment**: a public OSS presence is the #1 dev-employer signal
- **Recognition**: OSS contributions visible in performance reviews

**Comcast:** OSS engagement *"helped the company recruit new developers."*

<!--
This is the pillar most CTOs underweight and most engineers care about.
If you're pitching internally, use the recruitment angle — it
quantifies easily.
-->

---

## All four pillars · in one picture

<br>

| Pillar | Owner archetype | Key artifact | Failure mode |
|---|---|---|---|
| **Strategy & Governance** | Counselor | OSS policy doc | Decisions made ad-hoc |
| **Compliance & Security** | Gatekeeper | SBOM + scan pipeline | "Are we vulnerable?" *(no answer)* |
| **Contribution & Upstream** | Advocate | Forking & CLA process | Permanent forks, no influence |
| **Culture & Talent** | Enabler + Environmentalist | InnerSource + training | Wheel reinvented quarterly |

<!--
This is the "screenshot this" slide. Single-glance summary of the
whole pillar section.
-->

---

<!-- _class: center -->

# Part 4
## Show Me the ROI
### *The CFO doesn't care about your culture deck*

<!--
6 minutes. Translate everything to dollars/euros and risk reduction.
This is the section that wins your C-level pitch.
-->

---

## ROI · Costs avoided

🛡️ **Security incident avoided**
*Average data breach: $4.88M (IBM 2024). One Log4Shell-class incident pays for the OSPO forever.*

⚖️ **License lawsuit avoided**
*GPL violation settlements regularly hit 6-7 figures. M&A deals stall on license findings.*

📋 **Audit cost reduced**
*SBOM-on-demand turns a 4-week audit into a 4-hour query.*

🏗️ **Reinvented-wheel cost avoided**
*Three teams writing the same internal SDK = ~6 engineer-months.*

<!--
The breach number is concrete and famous. Use it. The audit number is
the one CFOs feel — they live through audits.
-->

---

## ROI · Speed

⚡ **Faster procurement**
*Pre-approved license list = no legal review for 90% of new deps.*

⚡ **Faster M&A**
*OSS due diligence in days, not months.*

⚡ **Faster shipping**
*Engineers stop asking "can I use this?" — they ask "is it on the list?"*

⚡ **Faster onboarding**
*New hires use the same OSS playbook everywhere in the org.*

> SAP shifted *"from policing developers to enabling them through simpler forms, automation of process steps, and support team services."*

<!--
Speed is the developer-friendly framing of the same governance work.
Same outcome, different vocabulary depending on who's listening.
-->

---

## ROI · Strategic upside

🚀 **Co-innovation** — share R&D cost with partners (cf. Porsche + Bosch + Here on OSS Review Toolkit)

🎯 **Influence** — shape the roadmap of dependencies you actually rely on

🧲 **Recruiting** — top engineers want to work where they can contribute publicly

📣 **Brand** — being a known OSS contributor is a *free* engineering brand

🛠️ **Standards seat** — participate in OpenChain, SPDX, CNCF, CRA working groups

> *"This type of co-innovation, for me, is the most compelling aspect about the whole open source movement."* — SAP OSPO

<!--
This is the slide that gets the CTO nodding. Strategic upside is hard
to quantify but easy to recognize. Use the SAP quote as your closer
for this section.
-->

---

## ROI · The numbers others have published

| Org | Outcome |
|---|---|
| **Microsoft** | 12,000+ employees actively contributing, 10K+ repos managed centrally |
| **SAP** | Ranked #7 globally on GitHub by contributor count |
| **Comcast** | ~10× growth in upstream contributions in 5 years |
| **Uber** | Multiple projects donated to CNCF / LF AI; reduced engineering cost |
| **Capital One** | OSS adoption in regulated banking became a recruiting magnet |

These aren't ad campaigns. They're TODO Group case studies.

<span class="small">Source: todogroup.org/resources/case-studies</span>

<!--
Numbers from public, vendor-neutral case studies. Cite the source so
the audience can verify. Trust = leverage.
-->

---

<!-- _class: center -->

![bg blur:5px brightness:0.3 A diverse group of people collaborating around a laptop — symbolising the cross-functional teams the case studies in this section come from](assets/community.jpg)

# Part 5
## Real Stories
### *Successes worth copying. Failures worth fearing.*

<br>

<span class="small">**Legend:** ✅ = success story (worth copying) · 🔥 = failure story (worth fearing)</span>

<!--
8 minutes. The most memorable section. Stories beat slides.
Mix 3-4 successes with 2 failures. Failures are the warning shots.
The legend is for accessibility — Codemotion guideline #4 — but it
also reinforces the framing for sighted attendees.
-->

---

## ✅ Success · Capital One — OSPO in regulated banking

**Context:** 8th-largest US bank. Highly regulated. OSPO since **2015**.

**What they built:**
- Two governance bodies: tactical **Review Board**, strategic **Steering Committee**
- Corporate **OSS Policy & Standard** (2016) covering use, contribution, sponsorship
- Active in **Linux Foundation, Apache, CNCF, TODO Group**

**Lesson for everyone else:**
*Even in the most risk-averse industry on Earth, an OSPO is the way you say* ***yes*** *to open source — safely.*

<!--
Capital One is the perfect "if they can, you can" story. Especially
useful for fintech / health / public sector audiences.
-->

---

## ✅ Success · Microsoft — the impossible pivot

**Context:** Once *"Linux is a cancer."* Now: 10,000+ repos, 12,000+ active OSS contributors.

**What they built:**
- OSPO that *facilitates*, not controls — local management owns decisions
- Internal tooling (GHCrawler, OSS portal) → released as open source
- Acquired GitHub. Acquired npm. Steering OpenSSF.

**Lesson for everyone else:**
*Cultural transformation at a 200K-person company took ~10 years and one consistent OSPO.*
*Yours will be faster.*

<!--
Use the "Linux is a cancer" quote — it always lands. Reminds the room
that even the most hostile org can flip.
-->

---

## ✅ Success · SAP — from policing to enabling

**Context:** Enterprise software giant. OSPO since 2018, OSS practice since 1998.

**What they built:**
- Virtual, cross-functional team (multiple board areas, scrum sprints)
- Outbound contribution guidelines since **2008**
- Open-sourced **Gardener** (Kubernetes management) and **Kyma**
- Contributes to Eclipse JGit, EGit, Mat, Tycho

**Lesson for everyone else:**
*The OSPO matures from gate → guide → growth engine. Plan for that arc.*

<!--
SAP shows the maturity ramp. Most new OSPOs start as "the no team" —
help them see what year-3 looks like.
-->

---

## ✅ Success · Porsche — non-software-native goes OSS-first

**Context:** Carmaker becoming a software company. Inspired by Tesla's 2-ECU *(Electronic Control Unit)* architecture vs. traditional carmakers' dozens.

**What they built:**
- OSPO formally in **2020**, after pre-OSPO efforts since **2018**
- "Coordinators" embedded in product teams (federated model)
- Co-developed **OSS Review Toolkit** with Bosch + Here Technologies
- Goal: shift in-house embedded software from **10–20% to 60%** in 5 years

**Lesson for everyone else:**
*Your industry doesn't have to be "software" for an OSPO to be existential.*

<!--
Best example for non-tech-native audiences. The Tesla framing is the
hook — it's a strategic-level argument disguised as a technical one.
-->

---

## 🔥 Failure · Equifax (2017) — what no OSPO costs

- **147 million** consumer records breached
- Root cause: an unpatched **Apache Struts** CVE — known for **2 months**
- $700M+ in settlements. CIO and CSO out within a week.

**What an OSPO would have prevented:**
- ✅ A central inventory of *every* Struts deployment (SBOM)
- ✅ Owned escalation path for high-severity OSS CVEs
- ✅ Automated patch tracking instead of email-based reminders
- ✅ A single answerable owner for "are we exposed?"

> *Equifax didn't lack security. It lacked open source* ***ownership.***

<!--
The pause after the Equifax case lets the cost sink in. Then the
checklist shows that none of these are exotic — they're hygiene the
OSPO normalizes.
-->

---

## 🔥 Failure · The xz backdoor (2024) — supply chain reality

- A **multi-year social engineering** campaign against one burned-out maintainer
- Backdoor merged into a near-ubiquitous Linux compression library
- Caught **by accident** by a Microsoft engineer noticing 500ms latency

**What an OSPO doesn't prevent — but does protect against:**
- ✅ Knowing *which* of your products ship xz (SBOM again)
- ✅ Sponsoring/staffing critical upstream maintainers (OpenSSF Alpha-Omega)
- ✅ Treating supplier diversity for code like for hardware

**The single-maintainer dependency is everywhere in your stack.** Find them.

<!--
The xz story is the most current and visceral example of supply-chain
risk. The "find them" line is your call to action — go run a survey
of your most critical, least-staffed deps.
-->

---

<!-- _class: center -->

# Part 6
## Where to Start
### *Even if you have one person and zero budget*

<!--
5 minutes. Concrete. Walk-out actionable.
-->

---

## The minimum viable OSPO

You don't need a 20-person team. You need **one person with a mandate**.

**Week 1**
- Get an executive sponsor (CTO, CIO, or CISO)
- Inventory: how many repos? how many production deps? who currently approves licenses?

**Month 1**
- One-page **OSS policy** (use / contribute / release)
- Pre-approved **allowed-license list** (MIT, Apache-2.0, BSD…)
- Set up **SBOM generation** in one CI pipeline as a pilot

**Quarter 1**
- Stand up the **Open Source Review Board** (legal + security + 1 senior eng)
- Automate SBOM across all repos
- Publish an **internal OSS portal** (wiki + checklists)

<!--
This is the slide attendees will photograph. Make it concrete and
sequenced. They should leave feeling "I can start Monday."
-->

---

## The C-level pitch · in 3 slides

**Slide 1 · Risk**
> *"68% of our codebases have license conflicts. We don't know which 68%."*

**Slide 2 · Cost**
> *"One Log4Shell-class incident costs more than 5 years of an OSPO."*

**Slide 3 · Upside**
> *"OSS-active companies recruit 30% faster. We're losing offers to them."*

**Ask:** *"Give me one FTE (full-time employee), an executive sponsor, and 6 months. I'll show you the SBOM coverage, license posture, and a contribution program."*

<!--
This is the pitch. Three slides. Risk, cost, upside. End on an ask
that's small enough to say yes to.
-->

---

## You're not alone · Resources

**TODO Group** — todogroup.org · the global OSPO community
- Glossary, mindmap, case studies, surveys

**OSPO Alliance** — ospo.zone · the European arm (Eclipse Foundation)
- *Good Governance Initiative*, regional working groups

**OpenChain** — openchainproject.org · ISO/IEC 5230 compliance
- The international standard for OSS license compliance

**OpenSSF** — openssf.org · supply-chain security
- Scorecard, Sigstore, Alpha-Omega, S2C2F

**InnerSource Commons** — innersourcecommons.org

**Linux Foundation training** — LFC191, LFC193, LFC194

<!--
Don't read every URL. Tell them the slides are public — and they are
the curated reading list.
-->

---

<!-- _class: center -->

# Part 7
## Wrap

---

## Three things to take away

<br>

### 1. You're already in the open source business
*87% of your code is OSS. The question isn't whether to engage — it's whether you do it consciously.*

### 2. An OSPO is the org's "open source operating system"
*Strategy, compliance/security, contribution, culture. Four pillars. One owner.*

### 3. Start small, start now
*One person. One sponsor. One SBOM. One quarter. Compound from there.*

<!--
Three takeaways, three sentences each. This is the slide they'll
remember tomorrow morning. Keep it tight.
-->

---

<!-- _class: center -->

# Thank you · Grazie

## Questions?

![w:220 QR code that opens github.com/braghettos/osday-ospo — slides, transcript, accessibility statement, and audit results](assets/qr-repo.png)

**Scan ↑** or open `github.com/braghettos/osday-ospo`

**Get in touch:** `linkedin.com/in/diegobraga86`

<span class="small">Sources: TODO Group · ospoglossary.todogroup.org · ospomindmap.todogroup.org · Black Duck OSSRA 2026</span>

<!--
10 minutes for Q&A.
Likely questions to prepare:
- "How is an OSPO different from DevSecOps / AppSec?"
- "Who reports to whom — CTO, CISO, Legal?"
- "What if our company is fully proprietary, no OSS releases planned?"
- "How do you measure OSPO success in year 1?"
- "What's the bare minimum tool stack?" (GitHub + FOSSA/Snyk + CLA Assistant + Bitergia, per Uber)
- "How does the EU CRA change this in 2027?"
-->
