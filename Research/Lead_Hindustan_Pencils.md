# Lead: Hindustan Pencils (HPPL), Pollachi plant

**Date:** 27 Oct 2026 · **Source:** Tejas, a friend of the founder in India, visited the plant. Second-hand notes, not yet checked with the company · **Status:** lead; no direct contact yet

Company and contact are named with the founder's agreement. Figures from sources are linked. Anything marked **(est.)** is my own estimate or arithmetic.

---

## TL;DR

- **Who:** Hindustan Pencils Pvt Ltd (HPPL), maker of Nataraj and Apsara, India's largest pencil maker by its own account. Revenue about ₹1,200 crore (≈ US$140M, est.) with a low profit margin.
- **Three problems reported:**
  1. Material movement: on average 4 inbound and 2 dispatch vehicles a day.
  2. Manpower efficiency: 15 days to train a worker, and 30% attrition month on month.
  3. Pencil checking / QC.
- **Fit with the current product is weak.** robotics-revolution diagnoses failures of robots under test against written requirements. HPPL's problems are labour, logistics and inspection on a largely manual line. QC is the closest match.
- **Why it still matters:** a real manufacturer with named problems, a warm intro, and a founder who is a Tamil-speaking roboticist. It's a candidate design partner for a factory-floor direction, like the Kickmaker lead in `SUMMARY.md`.

---

## 1. Company snapshot

| | |
|---|---|
| Company | Hindustan Pencils Pvt Ltd, Mumbai; founded 1958 ([Wikipedia](https://en.wikipedia.org/wiki/Hindustan_Pencils)) |
| Brands | Nataraj, Apsara |
| Market position | Claims ~45% of India's pencil market ([Wikipedia](https://en.wikipedia.org/wiki/Hindustan_Pencils); not checked against filings). DOMS is the main rival and claims it will overtake HPPL ([Pencil Talk](https://www.penciltalk.org/?p=4680)) |
| Scale | 8.5M pencils, 1.7M sharpeners, 2.7M erasers and 1M pens a day ([2018 catalog](https://www.hindustanpencils.com/Hindustan_Pencil_Product_Catalog_2018.pdf)); ten factories in five regions ([company site](https://hindustanpencils.com/about-us/)) |
| Revenue | ~₹1,200 crore, as reported. Not confirmed in public filings; the company is private |
| Margin | "Low", as reported. Consistent with older public data: profit fell from ~₹9 crore (2015) to ~₹1 crore (2018) ([TradeBrains](https://tradebrains.in/?p=52196)) |
| Pollachi plant | Reported by Tejas. Not found in public sources. What it makes (full pencils, or parts such as slats or leads) is unknown |

**What a low margin means for us:** any fix must pay back fast and in rupees. Expensive robots or long software projects are a hard sell (est.).

---

## 2. The three problems

### 2.1 Material movement

**Reported:** on average 4 inbound and 2 dispatch vehicles a day.

**Reading:** 6 vehicles a day is low traffic, so truck scheduling alone is probably not the pain (est.). More likely candidates:
- slow loading and unloading by hand
- moving material inside the plant between process stages (wood slats, leads, paint, finished cartons)
- congestion at certain hours

**To ask:**
- Is the pain at the gate and dock, or inside the plant?
- What is moved, how (forklift, trolley, by hand), and by how many people?
- How long does a truck take to turn around? What does a delay cost?

**Possible directions (hypotheses):**
- Dock scheduling and yard visibility: cheap software, quick to test.
- Conveyors, palletisation or AMRs (autonomous mobile robots) for internal moves: fits the founder's background, but capital-heavy for a low-margin firm.

### 2.2 Manpower efficiency

**Reported:** 15 days of training per new worker; 30% attrition month on month.

**What those numbers imply (est.):**

| Metric | Value | How |
|---|---|---|
| Average tenure | ~3.3 months (~100 days) | 1 ÷ 0.30 |
| Training as a share of tenure | ~15% | 15 days ÷ ~100 days |
| Annual turnover | ~360% of headcount | 30% × 12 |
| Share of a hiring cohort left after a year | ~1% | 0.70¹² ≈ 0.014 |
| Share of the workforce in training at any time | ~15% | 30% hired each month × half a month of training |

**Check first:** 30% a month is extreme. Is it for contract or migrant workers only, a seasonal spike, or actually 30% a year?

**To ask:**
- Headcount, and which roles churn most.
- Why people leave: wages, migrant workers going home, working conditions.
- What the 15 days of training cover. How much is the machine, and how much is judgement (e.g. spotting defects)?

**Possible directions (hypotheses):**
- Cut time to productivity: visual or video work instructions in Tamil and Hindi, an AI assistant at the station, error-proofing (poka-yoke) on fixtures.
- Automate the highest-churn tasks first.
- Reduce attrition itself. That's an HR problem more than a tech one.

**Link to the pitch:** the hackathon pitch says that knowledge "breaks when the engineer who knew it leaves". At 30% monthly attrition, the same problem hits the shop floor, only faster.

### 2.3 Pencil checking / QC

**Reported:** QC is a challenge. No detail yet.

**Typical pencil defects** (general, to confirm with HPPL): lead off-centre; lead broken or cracked inside the wood (shows up as breaking when sharpened); gaps at the slat joint; paint or lacquer defects; print errors; wrong length or sharpening; loose eraser or ferrule.

**To ask:**
- What is checked, at which stage, and is it by eye, by gauge or by machine?
- How many inspectors? What throughput?
- What are the defect rate and the return or complaint rate? What does an escaped defect cost?
- Can they share defect photos and the QC checklist?

**Possible directions (hypotheses):**
- Machine-vision inspection at the end of the line: an end-face camera for lead centring, and a side camera for paint and print.
- A root-cause loop that links defects back to upstream machine settings, so QC data fixes the process, not only the pencils.

**Link to the product:** this is the closest match. The product maps a symptom to the spec it violates, the root cause and the fix, with citations. "This batch fails the lead-centring spec because grooving machine 3 is drifting" is the same pattern, with a camera instead of ROS telemetry. But the hard part, a reliable vision classifier, is new work; the PoC's classifier doesn't carry over.

---

## 3. Fit with robotics-revolution

| Problem | Overlap with current product | Founder fit | Notes |
|---|---|---|---|
| Material movement | None | Medium (robotics, AMRs) | Capital-heavy; check whether it's the real pain |
| Manpower efficiency | Indirect (tribal-knowledge theme) | Low–medium | Mostly HR and training; software angle is job aids |
| QC | Partial (symptom → spec → cause) | High (vision, control) | Best entry point if HPPL ranks it first |

**Verdict:** HPPL is not an ICP for the current pitch. It has no robots under test and probably no formal requirements tooling (est.). It belongs to a different candidate segment: labour-heavy Indian manufacturers (P6 in `Research/ICP.md`). The open question is whether low margins leave any budget for a fix.

---

## 4. Questions for Tejas

1. Who did you meet (role), and would they take a call with Gawtam?
2. What does the Pollachi plant make: full pencils, or parts?
3. Of the three problems, which one costs them most, and who owns it?
4. Have they tried fixing any of them? Which vendors or tools?
5. The per-problem questions in section 2.
6. Any photos or videos of the line, the QC station or the dock, if allowed.

## 5. Next steps

1. Send Tejas the questions in section 4.
2. If QC ranks first, ask for defect photos and the QC checklist. That's enough to prototype a vision check.
3. Ask `icp-analyst` to research segment P6. Later, ask `competitors-analyst` to cover vision-QC and factory-automation vendors in India.

---

## Change log

- 27 Oct 2026: created from Tejas's visit notes; company facts checked against public sources where possible.
