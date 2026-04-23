# Transcript · Open Source in Production: Why Your Company Needs an OSPO

> Linear, plain-text version of the talk for screen-reader users, attendees who prefer reading, and anyone who can't see the slides clearly.
>
> Slides: [github.com/braghettos/osday-ospo](https://github.com/braghettos/osday-ospo)
> Speaker: Diego Braga, CTO & Co-founder at Krateo PlatformOps
> Event: OSDay 2026, Florence — Friday 24 April, 12:30–13:15

---

## Opening

The talk is "Open Source in Production: Why Your Company Needs an OSPO (Before It's Too Late)."

Quick show of hands at the start: how many people work at a company with a formal Open Source Program Office? Usually 2-5 percent. Then: how many use open source in production every day? Everyone. The gap between those two answers is the entire talk.

About me: Diego Braga, CTO and Co-founder at Krateo PlatformOps. Background in modernizing legacy applications — breaking monoliths into microservices, designing automation flows across the entire stack from application down to physical machines, and enabling continuous integration through orchestrated Disaster Recovery and Change Management.

About you, probably: a developer shipping code that's 80%+ open source, an engineering manager or CTO worried about compliance and security, or someone who's googled "what does an OSPO actually do" recently. The deal for the next 35 minutes: you'll leave with the language, the data, and the roadmap to start one.

---

## Part 1 · The Problem

**87 percent of code in production contains open source components.** Source: Black Duck OSSRA 2026 report, audited codebases across 16 industries. The translation: your code is mostly other people's code. You inherited the bugs, you inherited the licenses, you inherited the maintainers — or their absence.

The numbers get worse:
- 581 average vulnerabilities per codebase (a 107 percent year-over-year increase)
- 78 percent of codebases contain high-risk vulnerabilities
- 44 percent contain critical-risk issues like remote code execution or data breach
- 68 percent contain license conflicts
- 93 percent contain components with no development activity for 2+ years
- 92 percent contain components that are 4+ years out-of-date
- 65 percent of organizations were hit by a software supply chain attack last year

Source: Black Duck OSSRA 2026, 2,400+ commercial codebases audited.

**Welcome to the Wild West.** Without anyone owning open source, every team reinvents the answer to: what license is this dependency? Who patches transitive deps? Why are three teams writing the same client? Can I send this PR upstream? How do we even use GitHub here? Each unanswered question is a "decision tax" paid by every engineer, every day.

What "no OSPO" looks like in real life — four warning shots:

- **Equifax (2017)**: 147 million records breached. Root cause was an unpatched Apache Struts CVE. A single team owned patching. Nobody owned awareness.
- **Heartbleed (2014)**: 2 maintainers, 2,000 dollars per year in donations, securing half the internet's TLS traffic. Everyone consumed it. Nobody invested in it.
- **Log4Shell (2021)**: three days of global panic — because nobody had an SBOM (Software Bill of Materials). "Are we vulnerable?" "We'll get back to you."
- **xz utils backdoor (2024)**: a multi-year social-engineering attack on a single overworked maintainer. The supply chain runs on volunteers — treat it that way.

---

## Part 2 · What is an OSPO?

Definition from the TODO Group: an OSPO is the **center of competency** for an organization's open source operations and structure.

What it is **not**: a legal review queue, a compliance gate that says no, a side project of the CTO's chief of staff.

What it **is**: the team that makes open source strategic instead of accidental — the single place where legal, security, engineering, and community meet.

An OSPO has two faces:

- **Inward-facing**: policy, process, and tooling; education and enablement; compliance and security; InnerSource culture; metrics and reporting.
- **Outward-facing**: community engagement; foundation memberships; public contributions; brand and recruiting; standards participation.

The OSPO is the bridge between your organization and the open source ecosystem you depend on.

The TODO Group identifies five roles inside an OSPO:

1. **Enabler** — removes friction, builds tooling, automates compliance
2. **Counselor** — advises on trends, technologies, build-vs-adopt-vs-contribute
3. **Advocate** — promotes adoption internally, contribution externally
4. **Environmentalist** — keeps critical upstream projects healthy
5. **Gatekeeper** — enforces policy, manages risk, signs off on releases

You don't need 5 people. You need someone wearing all 5 hats — explicitly.

"But we're not Big Tech." That's exactly why you need one.

| If you have | An OSPO is worth it |
|---|---|
| More than 20 engineers | Decision tax compounds quickly |
| Customer contracts with IP/SBOM clauses | Compliance is a sales blocker |
| Any regulated workload (fintech, health, automotive) | Auditors will ask. Have an answer. |
| M&A on the horizon | Open source due diligence is now standard |
| AI-generated code in production | License provenance is a 2026 problem |

Examples: Capital One — heavily regulated bank, OSPO since 2015. Porsche — automotive manufacturer, OSPO since 2020. Comcast — telco, two OSPOs.

---

## Part 3 · The 4 Pillars

| Pillar | Day-to-day work |
|---|---|
| 1. Strategy & Governance | Policy, risk, M&A due diligence |
| 2. Compliance & Security | SBOM, CVEs, license scanning |
| 3. Contribution & Upstream | Pull requests, projects, CLAs |
| 4. Culture & Talent | InnerSource, training, recruiting |

Different orgs weight them differently. **All four exist.**

### Pillar 1 · Strategy & Governance

The question: why are we using, contributing, releasing open source at all?

- Define open source strategy aligned to business goals
- Set policies for when to consume, contribute, release
- Stand up an Open Source Review Board (legal + security + engineering)
- Make risk explicit: brand, IP, competitive, license
- Support M&A due diligence (target's OSS posture)
- Define measurable goals annually — like Red Hat does

Quote from Capital One OSPO: "There is nothing traditional about Capital One and our approach to technology."

### Pillar 2 · Compliance & Security

The question: do we know what's in our software, and is it safe?

- Maintain an SBOM (Software Bill of Materials) for every product
- Automate license scanning in CI (Snyk, FOSSA, ScanCode, OSS Review Toolkit)
- Track vulnerabilities continuously, not just at release
- Define license classification: allowed, conditional, forbidden
- Handle mixed-code rules: containers, SDKs, SaaS, APIs
- Comply with OpenChain ISO/IEC 5230, SPDX, and the EU Cyber Resilience Act (CRA, in force 2027)

The bar is rising fast: EU CRA, US Executive Order 14028, customer SBOM requirements.

### Pillar 3 · Contribution & Upstream

The question: are we good citizens of the projects we depend on?

- Process for upstreaming patches (don't carry forks forever)
- CLA / DCO infrastructure (CLA Assistant is open source)
- Patent and legal review before public release
- Project incubation playbooks (naming, governance, license, hosting)
- Foundation memberships: Linux Foundation, Apache, Eclipse, OpenSSF, CNCF
- Recognize and reward internal contributors

Quote from Uber OSPO: "The collective knowledge of our engineers grows by interacting with the open source community."

### Pillar 4 · Culture & Talent

The question: do our engineers know how to work in the open?

- InnerSource: open source practices applied internally (transparency, PRs, public roadmaps)
- Training: licensing basics, contribution workflow, project management
- Ambassador programs: identify internal OSS leaders
- Recruitment: a public OSS presence is the #1 dev-employer signal
- Recognition: OSS contributions visible in performance reviews
- Events: brown bags, conference sponsorships, internal OSS day

Comcast: OSS engagement "helped the company recruit new developers."

### All four pillars in one picture

| Pillar | Owner archetype | Key artifact | Failure mode |
|---|---|---|---|
| Strategy & Governance | Counselor | OSS policy doc | Decisions made ad-hoc |
| Compliance & Security | Gatekeeper | SBOM + scan pipeline | "Are we vulnerable?" — no answer |
| Contribution & Upstream | Advocate | Forking and CLA process | Permanent forks, no influence |
| Culture & Talent | Enabler + Environmentalist | InnerSource + training | Wheel reinvented quarterly |

---

## Part 4 · Show Me the ROI

The CFO doesn't care about your culture deck. Translate everything to dollars/euros and risk reduction.

### Costs avoided

- **Security incident avoided.** Average data breach: 4.88 million dollars (IBM, 2024). One Log4Shell-class incident pays for the OSPO forever.
- **License lawsuit avoided.** GPL violation settlements regularly hit 6-7 figures. M&A deals stall on license findings.
- **Audit cost reduced.** SBOM-on-demand turns a 4-week audit into a 4-hour query.
- **Reinvented-wheel cost avoided.** Three teams writing the same internal SDK is roughly 6 engineer-months.

### Speed

- **Faster procurement.** Pre-approved license list means no legal review for 90% of new dependencies.
- **Faster M&A.** OSS due diligence in days, not months.
- **Faster shipping.** Engineers stop asking "can I use this?" and start asking "is it on the list?"
- **Faster onboarding.** New hires use the same OSS playbook everywhere in the org.

Quote from SAP: shifted "from policing developers to enabling them through simpler forms, automation of process steps, and support team services."

### Strategic upside

- **Co-innovation.** Share R&D cost with partners (e.g. Porsche + Bosch + Here Technologies on the OSS Review Toolkit).
- **Influence.** Shape the roadmap of dependencies you actually rely on.
- **Recruiting.** Top engineers want to work where they can contribute publicly.
- **Brand.** Being a known OSS contributor is a free engineering brand.
- **Standards seat.** Participate in OpenChain, SPDX, CNCF, CRA working groups.

Quote from SAP OSPO: "This type of co-innovation, for me, is the most compelling aspect about the whole open source movement."

### Numbers others have published

| Org | Outcome |
|---|---|
| Microsoft | 12,000+ employees actively contributing, 10K+ repos managed centrally |
| SAP | Ranked #7 globally on GitHub by contributor count |
| Comcast | About 10x growth in upstream contributions in 5 years |
| Uber | Multiple projects donated to CNCF / LF AI; reduced engineering cost |
| Capital One | OSS adoption in regulated banking became a recruiting magnet |

These aren't ad campaigns. They're TODO Group case studies.

---

## Part 5 · Real Stories

### Success — Capital One: OSPO in regulated banking

Context: 8th-largest US bank. Highly regulated. OSPO since 2015.

What they built: two governance bodies — a tactical Review Board and a strategic Steering Committee. A corporate OSS Policy and Standard (2016) covering use, contribution, and sponsorship. Active in Linux Foundation, Apache, CNCF, TODO Group.

Lesson for everyone else: even in the most risk-averse industry on Earth, an OSPO is the way you say *yes* to open source — safely.

### Success — Microsoft: the impossible pivot

Context: once "Linux is a cancer." Now: 10,000+ repos, 12,000+ active OSS contributors.

What they built: an OSPO that *facilitates* rather than controls — local management owns decisions. Internal tooling like GHCrawler and the OSS portal, then released as open source. Acquired GitHub. Acquired npm. Steering OpenSSF.

Lesson: cultural transformation at a 200,000-person company took about 10 years and one consistent OSPO. Yours will be faster.

### Success — SAP: from policing to enabling

Context: enterprise software giant. OSPO since 2018, OSS practice since 1998.

What they built: virtual, cross-functional team across multiple board areas, working in scrum sprints. Outbound contribution guidelines since 2008. Open-sourced Gardener (Kubernetes management) and Kyma. Contributes to Eclipse JGit, EGit, Mat, Tycho.

Lesson: the OSPO matures from gate to guide to growth engine. Plan for that arc.

### Success — Porsche: non-software-native goes OSS-first

Context: carmaker becoming a software company. Inspired by Tesla's 2-ECU architecture vs. their dozens.

What they built: OSPO formally in 2020 after pre-OSPO efforts since 2018. "Coordinators" embedded in product teams (federated model). Co-developed the OSS Review Toolkit with Bosch and Here Technologies. Goal: shift in-house embedded software from 10–20 percent to 60 percent in 5 years.

Lesson: your industry doesn't have to be "software" for an OSPO to be existential.

### Failure — Equifax (2017): what no OSPO costs

- 147 million consumer records breached
- Root cause: an unpatched Apache Struts CVE — known for 2 months
- 700 million dollars in settlements; CIO and CSO out within a week

What an OSPO would have prevented:
- A central inventory of every Struts deployment (SBOM)
- An owned escalation path for high-severity OSS CVEs
- Automated patch tracking instead of email-based reminders
- A single answerable owner for "are we exposed?"

Equifax didn't lack security. It lacked open source *ownership*.

### Failure — The xz backdoor (2024): supply chain reality

- A multi-year social engineering campaign against one burned-out maintainer
- Backdoor merged into a near-ubiquitous Linux compression library
- Caught by accident by a Microsoft engineer noticing 500ms latency

What an OSPO doesn't prevent — but does protect against:
- Knowing which of your products ship xz (SBOM again)
- Sponsoring/staffing critical upstream maintainers (OpenSSF Alpha-Omega)
- Treating supplier diversity for code like for hardware

The single-maintainer dependency is everywhere in your stack. Find them.

---

## Part 6 · Where to Start

### The minimum viable OSPO

You don't need a 20-person team. You need **one person with a mandate.**

**Week 1:**
- Get an executive sponsor (CTO, CIO, or CISO)
- Inventory: how many repos? How many production deps? Who currently approves licenses?

**Month 1:**
- One-page OSS policy: use / contribute / release
- Pre-approved allowed-license list (MIT, Apache-2.0, BSD, etc.)
- Set up SBOM generation in one CI pipeline as a pilot

**Quarter 1:**
- Stand up the Open Source Review Board (legal + security + 1 senior engineer)
- Automate SBOM across all repos
- Publish an internal OSS portal (wiki + checklists)

### The C-level pitch in 3 slides

1. **Risk:** "68 percent of our codebases have license conflicts. We don't know which 68 percent."
2. **Cost:** "One Log4Shell-class incident costs more than 5 years of an OSPO."
3. **Upside:** "OSS-active companies recruit 30 percent faster. We're losing offers to them."

The ask: "Give me one FTE, an executive sponsor, and 6 months. I'll show you the SBOM coverage, license posture, and a contribution program."

### You're not alone — Resources

- **TODO Group** — todogroup.org — the global OSPO community. Glossary, mindmap, case studies, surveys.
- **OSPO Alliance** — ospo.zone — the European arm (Eclipse Foundation). Good Governance Initiative, regional working groups.
- **OpenChain** — openchainproject.org — ISO/IEC 5230 compliance. The international standard for OSS license compliance.
- **OpenSSF** — openssf.org — supply-chain security. Scorecard, Sigstore, Alpha-Omega, S2C2F.
- **InnerSource Commons** — innersourcecommons.org
- **Linux Foundation training** — LFC191, LFC193, LFC194

---

## Part 7 · Wrap

### Three things to take away

1. **You're already in the open source business.** 87 percent of your code is OSS. The question isn't whether to engage — it's whether you do it consciously.
2. **An OSPO is the org's "open source operating system."** Strategy, compliance/security, contribution, culture. Four pillars. One owner.
3. **Start small, start now.** One person. One sponsor. One SBOM. One quarter. Compound from there.

### Q&A

Questions likely to come up — short answers:

- **How is an OSPO different from DevSecOps / AppSec?** AppSec defends the perimeter. The OSPO owns the OSS supply chain end-to-end: licenses, contributions, community health, talent — security is one of four pillars.
- **Who reports to whom — CTO, CISO, Legal?** No single right answer; most successful OSPOs report to CTO or CIO with strong dotted lines to Legal and Security.
- **What if our company is fully proprietary, no OSS releases planned?** You still consume OSS in production — pillars 1, 2, and 4 still apply. Contribution can come later.
- **How do you measure OSPO success in year 1?** SBOM coverage, mean-time-to-patch on OSS CVEs, license-policy violations caught pre-merge, number of contributors trained.
- **What's the bare minimum tool stack?** GitHub + a license/CVE scanner (FOSSA, Snyk, or open source ScanCode) + CLA Assistant + a metrics tool like Bitergia. Per Uber's case study.
- **How does the EU CRA change this in 2027?** SBOM requirements become legal obligations for products sold in the EU; vulnerability disclosure timelines tighten; OSPOs become the natural owner of compliance.

### Contact

Diego Braga — CTO & Co-founder, Krateo PlatformOps
LinkedIn: [linkedin.com/in/diegobraga86](https://www.linkedin.com/in/diegobraga86)
Slides + reading list: [github.com/braghettos/osday-ospo](https://github.com/braghettos/osday-ospo)

Sources: TODO Group glossary (ospoglossary.todogroup.org), OSPO mindmap (ospomindmap.todogroup.org), TODO Group case studies, Black Duck OSSRA 2026 report.

---

*This transcript is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
