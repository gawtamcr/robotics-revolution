# robotics-revolution

Startup project of Gawtam C R, a solo founder. This folder holds the hackathon material, the market research and, later, the product code. Working name; the PDF calls it the "CRG Hack Idea".

## What it is

One idea, two candidate first markets.

- **The idea: cited diagnosis from captured knowledge.** When a machine misbehaves, the gap between the symptom and its root cause is a *knowledge* problem, not a sensing problem. The knowledge exists, in requirement documents or in experienced people's heads, but nobody can reach it at the moment of failure. The product holds that knowledge as memory, reads the machine, and maps a symptom to the likely cause and fix, citing every source.
- **The shared engine:**
  - Known issues (and requirements, where they exist) held as durable agent memory.
  - Live access to the machine: an MCP server over its middleware (ROS 2 in the PoC), or retrofit sensors and operator reports.
  - A deterministic classifier that turns signals into a *symptom* with a health status, never a root cause. The agent maps the symptom to a cause.
- **Citation is the product, not a feature.** Engineers, operators and auditors won't act on an uncited diagnosis.

### The two directions

| | A. Robot and vehicle testing (hackathon) | B. Legacy factories (India) |
|---|---|---|
| Where the knowledge lives | Requirement documents (PLM, Jira, specs) | Senior technicians' heads; little is documented |
| How it reads the machine | Middleware (ROS 2), HIL rigs, test telemetry | Operator reports first, then retrofit sensors |
| What it cites | Requirement ID and known-issue tag, for engineers and auditors | Past cases and who fixed them, for operators |
| Buyer | Test and validation teams at OEMs and robotics companies | Plant heads at brownfield, low-margin factories |
| Evidence so far | PoC; no interviews | One warm lead (Hindustan Pencils); desk research |
| Main files | `SUMMARY.md` sections 1–7; `Research/ICP.md` P1–P5 | `Research/Opportunity_Legacy_Factories_India.md`; `Research/Lead_Hindustan_Pencils.md`; `Research/ICP.md` P6 |

### Exploration: factory brain (since 28 Oct 2026)

One level above A and B. A plant-level reasoning layer over multi-vendor robot fleets (arms, humanoids, AMRs), machines and people:
- It understands what a change means.
- It re-plans the work across vendors without reprogramming (e.g. switching a paint cell from car doors to hoods).
- It checks its own plans and cites why.

Cited diagnosis is one candidate wedge among seven. Brainstorm and wedge scorecard: `Research/Factory_Brain.md`.

## Current status

- **Source of truth:** the "Current status" section of `SUMMARY.md`. Update it whenever a decision changes.
- **Team:** solo (Gawtam). The idea came from a 4-person team at the Cursor hackathon, RAISE Summit, July 2026. The rest of the team isn't working on it now.
- **Founder:** based in Stockholm, part-time and still exploring. Physical AI depth: robot learning and VLAs, control and RL, world models and simulation, perception. localE is a separate project in its own repo.
- **Focus (28 Oct 2026):** direction B's factory-specific work (the HPPL pilot) is parked while Gawtam brainstorms the factory brain.
- **PoC:** built in about 12 hours at the hackathon, on a self-driving car's steering subsystem. Code is in [gawtamcr/cursor-hack](https://github.com/gawtamcr/cursor-hack); `Code/` here is a placeholder.
- **Validation:** none yet. No customer interviews done; leads are listed in `SUMMARY.md`.
- **Open decision:** which market first, A or B. Decide on what customers say and pay, not on desk research.
- **Open questions:** see `SUMMARY.md`. For A, the biggest one: would a team just prompt an LLM with its requirement doc and logs and get 70% of this for free? For B: will low-margin plants pay, and can technicians' knowledge be captured reliably?

## Files

| Path | Contents |
|---|---|
| `SUMMARY.md` | Current status of both directions, plus a summary of the hackathon material |
| `Pitch/CRG Hack Idea.pdf` | Original hackathon notes: team meetings, pitch, PoC, open questions, interview guide, leads, competitors. Background only; don't edit |
| `Research/ICP.md` | ICP research: candidate segments, scorecard, recommendation, validation plan |
| `Research/Competitors.md` | Competitor analysis: master table, threat ratings, feature-overlap matrix, gaps |
| `Research/Lead_*.md` | One file per customer lead with real detail, e.g. `Lead_Hindustan_Pencils.md` |
| `Research/Opportunity_*.md` | Problem, market and value-proposition analysis for a candidate segment, e.g. `Opportunity_Legacy_Factories_India.md` |
| `Research/Academic_*.md` | Technical state of the art from research groups, e.g. `Academic_EPFL_IMOS.md` |
| `Research/hppl_poc.md` | Internal pilot plan for Hindustan Pencils' Pollachi plant: immediate ROI, value model, 8-week pilot, scalability |
| `Research/hppl_open_questions.md` | Every open question on the HPPL pilot, with an estimate, who can answer, and priority. `hppl_poc.md` cites its IDs |
| `Research/Factory_Brain.md` | Factory brain brainstorm: vision, layer map, physical AI state of the art, critical analysis, candidate wedges and scorecard, company paths, experiments |
| `Research/Interviews_Factory_Brain.md` | Interview guide for the factory brain's experiment E1 (how a change on a robot line goes), with an anonymised interview log |
| `.claude/agents/` | Research agents `icp-analyst`, `competitors-analyst` and `factory-brain-strategist` |
| `Code/` | Product code (placeholder; the PoC is in `gawtamcr/cursor-hack`) |

## Research agents

- **`icp-analyst`** owns `Research/ICP.md`, `Research/Opportunity_*.md` and `Research/Lead_*.md`: who has this pain, who pays, and how to reach them, in both directions.
- **`competitors-analyst`** owns `Research/Competitors.md`. It rates each competitor High, Medium or Low against the current ICP and tags which features it overlaps:

  | Code | Feature |
  |---|---|
  | R | requirements ingestion and traceability |
  | L | live system access (middleware, HIL rig, fleet) |
  | S | symptom detection from telemetry |
  | D | root-cause diagnosis |
  | C | citations and audit trail |
  | F | closed-loop fix and re-test |
  | H | HIL/SIL test execution |
  | V | telemetry visualisation |

- **`factory-brain-strategist`** owns `Research/Factory_Brain.md`. It brainstorms and stress-tests the factory brain, and scores its candidate wedges on the same 7 criteria. It researches on the web only when asked.
- **What they read first:** `SUMMARY.md` and the reports.
- **What they edit:** only their own report, logging each change in its change log. Findings that affect the other report go in the reply.

## Conventions

- **Scorecard:** always the same 7 criteria, scored 1–5 (half points allowed):
  - Pain intensity
  - Willingness to pay
  - Market size
  - Reachability for a solo founder
  - Competitive whitespace
  - Integration ease (access to the customer's requirements and live system; on-prem and IP constraints)
  - Founder fit

  These are localE's criteria, with "Cold-start ease" swapped for "Integration ease", because this is a B2B tool rather than a two-sided app. Don't change them; they keep segments comparable.
- **Analysis:**
  - Stay neutral.
  - Treat anecdotes and the hackathon pitch as hypotheses and test them against data.
  - Cite sources with links, and mark your own estimates "(est.)".
  - Confirm that companies you name are still active.
- **Edits:** when a finding changes a fact or a score, edit the report in place rather than adding a contradicting section.
- **Privacy:** never write personal data about private individuals into the markdown files. Describe leads by role and company type.
- **Naming:** refer to the founder as Gawtam or "the founder".

## Product constraints

**Both directions**
- **The agent must reason from the signal.** In the PoC the fault injector is named like a production ECU, so the agent can't shortcut the diagnosis by reading node names. Keep that constraint in demos and tests.
- **Symptom ≠ root cause.** The classifier emits symptoms only; the diagnosis step cites the requirement, known issue or past case.

**A. Robot and vehicle testing**
- **On-prem or self-hosted is probably mandatory** because of IP sensitivity. Design for it.

**B. Legacy factories**
- **Assume no plant IT.** SAP may be the only software, and old machines often expose no data. Cellular sensors (as Tractian uses) avoid plant networks.
- **Voice-first, in the operators' language:** Tamil at the first lead.
- **Priced for low-margin plants:** about ₹500–1,000 per machine per month (est.), roughly 4–8x below Western tools.

## Key dates

| Date | What |
|---|---|
| July 2026 | Cursor hackathon, RAISE Summit; PoC built |
| 18 and 25 July 2026 | Team follow-up meetings (notes in the PDF) |
