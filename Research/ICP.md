# ICP Research

**Date:** 27 Oct 2026 · **Status:** seeded from the hackathon PDF; no research done yet · **Owner:** `icp-analyst`

Figures from sources are linked. Anything marked **(est.)** is an estimate.

---

## TL;DR

- TODO: the best beachhead segment, who pays, and why.
- **Two candidate markets:** A, robot and vehicle testing (P1–P5, from the hackathon), and B, legacy factories in India (P6). Which comes first is the open decision.
- Within A, the hackathon's own split: **pre-deployment testing (HIL/SIL, CI)** vs **deployed-fleet triage**. These are different products with different buyers.

---

## 1. Candidate segments at a glance

| # | Segment (users) | Likely payer | Pain | Proven WTP? | Size | Integration ease | Verdict |
|---|---|---|---|---|---|---|---|
| P1 | Automotive HIL/SIL test teams (OEMs and tier-1 suppliers) | Test / validation department | TODO | TODO | TODO | TODO | TODO |
| P2 | Robotics scale-ups: pre-deployment testing and CI | Engineering lead / CTO | TODO | TODO | TODO | TODO | TODO |
| P3 | Deployed robot fleets: field triage and maintenance | Fleet ops / support | TODO | TODO | TODO | TODO | TODO |
| P4 | Industrial robot OEMs and factory integrators (e.g. ABB, Kickmaker) | Engineering / quality | TODO | TODO | TODO | TODO | TODO |
| P5 | Medical robotics and medtech (regulated requirements, PLM) | Quality / regulatory | TODO | TODO | TODO | TODO | TODO |
| P6 | Brownfield Indian factories with legacy machines (first lead: Hindustan Pencils, Pollachi) | Plant head / owner | Breakdowns on ~20-year-old machines; fault know-how held by staff in their 50s; QC; material monitoring | Unproven; low margins | ~30,000 factories with 100+ workers in India (est.) | Low software maturity (SAP only); needs sensor retrofit | Promising new segment; see `Opportunity_Legacy_Factories_India.md` |

---

## 2. Segment deep-dives

TODO, one subsection per segment:
- who has the pain and how they handle it today
- who buys, budget owner, and sales cycle
- what requirements look like (tools, formats, regulation such as ISO 26262 or IEC 62304)
- what live-system access looks like (ROS 2, HIL rig, proprietary middleware)
- on-prem / IP constraints

---

## 3. Scorecard

Criteria fixed in `CLAUDE.md`: scored 1–5, half points allowed.

| Criterion | P1 | P2 | P3 | P4 | P5 |
|---|---|---|---|---|---|
| Pain intensity | | | | | |
| Willingness to pay | | | | | |
| Market size | | | | | |
| Reachability for a solo founder | | | | | |
| Competitive whitespace | | | | | |
| Integration ease | | | | | |
| Founder fit | | | | | |
| **Total (/35)** | | | | | |

---

## 4. Recommendation

TODO.

---

## 5. Validation plan

### Interview guide (test engineers)

Drafted after the hackathon for an automotive HIL test engineer; reuse it for any test engineer.

**Daily workflow**
- What do you actually do on a typical day?
- Where do you hit friction: logistics, team dynamics, or time to complete a task?
- What do you use AI coding tools (e.g. Cursor) for day to day? It may not match our assumptions.

**Tooling potential**
- Do you also design control systems yourself? If so, the tool could be a design aid, not only a testing aid.

**Access and permissions**
- Can you modify low-level sensors?
- Can you modify high-level PLM systems?

**System testing scope**
- Are all systems tested simultaneously across PLM and live deployment?
- When something fails, can you isolate one system's fault from another's, or does fault correlation make that hard?

**Organisational context**
- Which department are you in, and what does it own?
- What is your role and responsibility in the team?

**Data**
- Can you (or your team) share sample or dummy data in its real format?

### Other sources before interviews

- Public YouTube channels of test engineers: check for workflow insight before asking anyone.
- A second test engineer, for another perspective.

### Leads

See `SUMMARY.md` section 5. Each lead with real detail gets its own `Research/Lead_*.md` file.

---

## Change log

- 27 Oct 2026: created from the hackathon PDF; segments seeded, no research yet.
- 27 Oct 2026: added P6 (labour-heavy Indian manufacturers) from the Hindustan Pencils lead.
- 27 Oct 2026: reframed P6 as brownfield factories with legacy machines, after desk research and the follow-up with Tejas.
- 27 Oct 2026: TL;DR reframed as two candidate markets (A: P1–P5; B: P6).
