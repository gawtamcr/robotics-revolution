# robotics-revolution

Startup project of Gawtam C R, a solo founder. This folder holds the hackathon material, the market research and, later, the product code. Working name; the PDF calls it the "CRG Hack Idea".

## What it is

- **Cited root-cause diagnosis for robots under test.** It connects a company's product requirements to its live machines. When a test fails, it maps the live symptom to the requirement it violates, the root cause, the fix and the known-issue tag, and cites each one.
- **How it works:**
  - Requirements and known issues are held as durable agent memory.
  - An MCP server exposes the live system (ROS 2) to an LLM agent as tools: read health, read stats, inject fault, restart unit.
  - A deterministic, unit-tested classifier turns telemetry into a *symptom* with a health status, never a root cause. The agent does the mapping from symptom to cause.
- **Citation is the product, not a feature.** In safety-critical hardware, engineers won't act on an uncited diagnosis and auditors won't accept it.

## Current status

- **Source of truth:** the "Current status" section of `SUMMARY.md`. Update it whenever a decision changes.
- **Team:** solo (Gawtam). The idea came from a 4-person team at the Cursor hackathon, RAISE Summit, July 2026. The rest of the team isn't working on it now.
- **Founder:** based in Stockholm, part-time and still exploring. localE is a separate project in its own repo.
- **PoC:** built in about 12 hours at the hackathon, on a self-driving car's steering subsystem. Code is in [gawtamcr/cursor-hack](https://github.com/gawtamcr/cursor-hack); `Code/` here is a placeholder.
- **Validation:** none yet. No customer interviews done; leads are listed in `SUMMARY.md`.
- **Open questions:** see `SUMMARY.md`. The biggest one: would a team just prompt an LLM with its requirement doc and logs and get 70% of this for free?

## Files

| Path | Contents |
|---|---|
| `SUMMARY.md` | Summary of the hackathon material, plus current status |
| `Pitch/CRG Hack Idea.pdf` | Original hackathon notes: team meetings, pitch, PoC, open questions, interview guide, leads, competitors. Background only; don't edit |
| `Research/ICP.md` | ICP research: candidate segments, scorecard, recommendation, validation plan |
| `Research/Competitors.md` | Competitor analysis: master table, threat ratings, feature-overlap matrix, gaps |
| `.claude/agents/` | Research agents `icp-analyst` and `competitors-analyst` |
| `Code/` | Product code (placeholder; the PoC is in `gawtamcr/cursor-hack`) |

## Research agents

- **`icp-analyst`** owns `Research/ICP.md`: who has this pain, who pays, and how to reach them.
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

## Product constraints (from the hackathon)

- **The agent must reason from the signal.** In the PoC the fault injector is named like a production ECU, so the agent can't shortcut the diagnosis by reading node names. Keep that constraint in demos and tests.
- **Symptom ≠ root cause.** The classifier emits symptoms only; the diagnosis step cites the requirement and known issue.
- **On-prem or self-hosted is probably mandatory** because of IP sensitivity. Design for it.

## Key dates

| Date | What |
|---|---|
| July 2026 | Cursor hackathon, RAISE Summit; PoC built |
| 18 and 25 July 2026 | Team follow-up meetings (notes in the PDF) |
