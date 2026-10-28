# HPPL Pollachi: proof of concept, ROI and scale

**Date:** 28 Oct 2026 · **Audience:** internal (Gawtam, Tejas) · **Status:** plan; nothing agreed with the plant yet · **Inputs:** `Lead_Hindustan_Pencils.md` (facts), `Opportunity_Legacy_Factories_India.md` (problems, market), `Competitors.md`, `Academic_EPFL_IMOS.md` · **Open questions:** `hppl_open_questions.md`

Every assumption carries a question ID (e.g. **[M5]**) from `hppl_open_questions.md`. When a question gets answered, replace the estimate here. Figures from sources are linked; anything marked **(est.)** is my own estimate or arithmetic. 1 lakh = ₹100,000; 1 crore = ₹10 million.

---

## TL;DR

- **Fastest ROI to show (2 weeks, no hardware):** turn the plant's own breakdown register into a costed list of its 10 worst machines. "These 10 machines cost you about ₹X lakh last quarter." It costs us almost nothing and needs only photos of a paper register **[MT2, MT3]**.
- **Within 6–8 weeks:**
  - a Tamil fault-and-fix library recorded by 3–5 senior technicians
  - a WhatsApp assistant that answers a symptom with cited past fixes, with time-to-diagnose measured on real breakdowns
  - optionally, ~₹1 lakh of clip-on sensors on 10 machines, showing idle running, energy waste and stoppages
- **What can't be shown quickly:** avoided major breakdowns. They are rare events and take 6–12 months to prove. Don't promise them in the pilot.
- **Value at Pollachi (est.):** ₹13 lakh to ₹2.4 crore a year, with a base case of **~₹75 lakh**. The low end barely covers a full-plant subscription, so the week-2 data decides whether this plant is worth it. The base case is lower than the opportunity file's ₹0.5–2.4 crore; section 3 explains why.
- **Pilot cost to us:** under ₹50k for weeks 1–6. ₹1–3.5 lakh (~€1,000–3,500) with sensors, plus Tejas's time.
- **Scale:** Pollachi alone is a small account. The scale story is:
  - HPPL's 10 factories
  - machine-dense, ageing Tamil Nadu industries. Tamil Nadu has ~19M of India's 46M working spindles, and 12M of them are over 15 years old ([DT Next](https://www.dtnext.in/amp/story/news/tamilnadu/sima-lauds-tn-govts-subsidy-for-spinning-modernisation-815168))
  - a fault library per machine model that gets better with every plant
  - richer countries with retiring maintenance staff
- **Top risks:**
  - The downtime pool may be small.
  - Senior technicians may not record their fixes.
  - The budget may sit in Mumbai.
  - Tamil speech-to-text may struggle with shop-floor audio.
  - Gawtam is remote, so the pilot depends on Tejas's bandwidth.
  - Infinite Uptime, already in India with 1,000+ plants, could move down-market (`Competitors.md`).

---

## 1. What "immediate ROI" can honestly mean

A predictive-maintenance pitch usually promises fewer breakdowns. At a plant with no data, that takes months to prove: big failures happen a few times a year, so 8 weeks shows almost nothing. What we *can* prove fast:

| What we prove | When | Why it maps to money |
|---|---|---|
| **Visibility:** which machines stop most, for how long, and what that costs | Week 2 | Focuses scarce fitters on the few machines that cause most downtime. It's usually a surprise to management |
| **Faster fixes:** time from "machine stopped" to "cause known" falls on covered machines | Weeks 4–8 | Downtime hours × cost per hour |
| **Captured knowledge:** N fixes from M senior technicians, searchable in Tamil | Weeks 2–6 | An asset the owner can see. It insures against retirements and shortens onboarding |
| **Idle and energy waste:** machines running idle, compressed-air leaks | 1–2 weeks after sensors | Electricity saved, measured directly |
| **Defect counts** (optional) | Weeks 6–12 | Inspector time and returns |

**The hook is the week-2 report.** It costs the plant nothing, uses their own data, and puts a rupee figure on a problem they feel but haven't measured.

---

## 2. How the plant probably works

From the standard wooden-pencil process ([Musgrave](https://musgravepencil.com/blogs/news/howapencilismade), [Ticonderoga](https://weareticonderoga.com/journey-of-a-pencil), [Blackwing](https://blackwing602.com/pages/how-its-made)). Which stages Pollachi runs is unknown **[PL1]**. HPPL says it makes most components in-house ([2018 catalog](https://www.hindustanpencils.com/Hindustan_Pencil_Product_Catalog_2018.pdf)).

| Stage | Machines | Likely failure modes (est.) **[M8]** |
|---|---|---|
| Lead (core) making, if done here | Mixers, extruders, dryers, a kiln at roughly 1,000°C, wax baths | Extruder wear, kiln heating elements and controls, temperature drift. The kiln is the biggest energy user |
| Slats | Circular saws, groovers | Blade and cutter wear, bearings, belts |
| Gluing and sandwiching | Glue applicators, core feeders, presses | Glue nozzles clogging, pneumatic cylinders and valves, feeder jams |
| Shaping | Shaping cutters (hex, round, triangular) | Cutter wear, spindle bearings, motors. Heavy wood dust |
| Lacquering | Paint lines, 4–10 coats, dryers | Nozzles, conveyors, dryer heaters. Solvent fumes may make it a hazardous area **[T9]** |
| Finishing | Printing or stamping, tipping (ferrule and eraser crimping), sharpening | Crimp tooling, feeders, misalignment |
| Inspection and packing | Manual checks, packing machines | Feeders, sealers |
| Utilities | Compressors, dust extraction, generator sets | Air leaks, motor faults, filter clogging |

Two things matter for the product:
- **Many identical machines.** Probably 15–30 models across 200 machines **[M3]**, so one fault story often applies to several machines.
- **Buffers.** Glued sandwiches must dry before shaping, so the line is partly decoupled. A stopped groover may not stop shaping **[M7]**. That roughly halves the cost of a breakdown compared with a fully coupled line.

---

## 3. Baseline model of the plant (est.)

### Assumptions

| Assumption | Value (est.) | Question |
|---|---|---|
| Machines | 200 | [M1] |
| Production lines | ~20 lines of ~10 machines | [PL3] |
| Operating hours | 2 shifts × 8 h × 300 days = 4,800 h per machine a year | [PL4] |
| Breakdowns | 1–2 per machine a month, skewed: ~20% of machines cause ~80% of stops | [M5] |
| Downtime per breakdown | 1.5–2 h on average; 30–50% of it waiting for someone and diagnosing | [MT4] |
| Stops that halt the line | ~50%; the rest are absorbed by buffers | [M7] |
| Plant revenue | ~₹120 crore (₹1,200 crore ÷ 10 factories; crude) | [PL7], [PL10] |
| Contribution margin | 25–35% | [B3] |
| Capacity-limited | In the ~4 peak months before the school year; not off-peak | [B7], [PL5] |
| Loaded wage | ~₹17.5k a month (from the opportunity file) | — |
| Repair spend (parts, outside fitters, motor rewinds) | ₹20–60 lakh a year | [MT8] |
| Electricity | ₹1–3 crore a year, higher if leads are fired here | [B4] |

### Bottom-up cost of breakdowns

| Step | Low | High | Basis |
|---|---|---|---|
| Breakdowns a year | 2,400 | 4,800 | 200 machines × 1–2 a month × 12 |
| Machine-hours down | 3,600 | 9,600 | × 1.5–2 h |
| Line-hours lost | 1,800 | 4,800 | × 50% that halt the line. That's 2–5% of the plant's ~96,000 line-hours, which matches the opportunity file's 2–5% |
| Revenue per line-hour | ₹12,500 | ₹12,500 | ₹120 crore ÷ 96,000 |
| Cost per lost line-hour | ₹1,200 | ₹2,500 | Peak months: lost contribution, ~₹3,750. Off-peak: idle labour and overtime to catch up, ~₹500–1,000. Weighted ~1/3 and ~2/3 |
| **Downtime cost a year** | **₹22 lakh** | **₹1.2 crore** | Mid ~₹58 lakh |
| Plus repair spend | ₹20 lakh | ₹60 lakh | [MT8] |
| **Total cost of breakdowns** | **~₹40 lakh** | **~₹1.8 crore** | Mid ~₹1 crore |

**Why this is below the opportunity file's figure.** The opportunity file took 2–5% of revenue as lost (₹2.4–6 crore) and assumed 20–40% could be recovered. That treats every lost hour as lost *revenue*. In practice:
- Off-peak, the plant catches up later.
- Lost output costs *contribution*, not revenue.
- Buffers absorb half the stops.

The bottom-up figure is the one to defend in front of the plant. If the plant is capacity-limited all year **[B7]**, the top-down figure comes back into play.

---

## 4. ROI levers: the full menu

The levers overlap: several of them shrink the same downtime pool. **Don't add up the ₹ column.** The scenarios below remove the overlaps.

| # | Lever | What we do | Hardware | First evidence | ₹ a year (est.) | How measured | Confidence |
|---|---|---|---|---|---|---|---|
| L1 | **Pareto of the machines that fail most** | Digitise 3–6 months of the breakdown register. Rank machines by downtime. Fix the chronic issues on the top 10 | None | Week 2 | 3–25 lakh | Downtime hours on the top 10, before and after | High for the insight; Low for ₹ |
| L2 | **Cited troubleshooting assistant** | Senior technicians record fault → cause → fix in Tamil. A WhatsApp assistant answers a symptom with the top 3 likely causes and the past cases behind them | None | Weeks 4–8 | 2–30 lakh (15–25% of the downtime pool) | Time to diagnose on covered machines vs the register baseline | Medium-low. The closest study shows experienced workers finishing a repair 21% faster with digital instructions (n=10, [arXiv](https://arxiv.org/pdf/2301.07570)) |
| L3 | **Cover for retirements** | The same library, so a fix outlives the person who knew it | None | Weeks 2–6 (counts) | 0–20 lakh expected value | Stories captured, and machines covered | Low; it's insurance and hard to prove |
| L4 | **Run/idle monitoring** | Clip-on current (CT) clamps show when each machine runs, idles or stops, exposing micro-stops and late starts. Indian plants reportedly run at ~45–50% OEE (overall equipment effectiveness) ([Let's Data Science](https://letsdatascience.com/news/indian-factories-adopt-smart-retrofitting-solutions-f0f094ce), unsourced) | CT clamp + gateway, ~₹4–15k a machine | 1–2 weeks after install | 0–50 lakh; only worth money if the plant can sell more **[B7]** | Run hours per shift, before and after | Medium for the visibility; Low for ₹ |
| L5 | **Early warning** | A baseline-deviation classifier on current and vibration flags drift on the 10 worst machines, before a motor burns out or a spindle seizes | Vibration sensors on 3–5 machines | Months | 2–20 lakh (avoided major failures **[M6]**) | Confirmed early warnings; major failures per year | Low in 8 weeks |
| L6 | **Energy** | Show machines idling with motors on. Find compressed-air leaks: neglected plants lose 20–30% of compressor output to leaks, and repairs bring it under 10% ([DOE fact sheet](https://www.compressedairchallenge.org/data/sites/1/media/library/factsheets2026/fact-sheet-7-compressed-air-system-leaks_updated2026.pdf)) | CT clamps; a rented ultrasonic leak detector | 2–4 weeks | 3–24 lakh (3–8% of the bill **[B4]**) | kWh, before and after | Medium |
| L7 | **Spares** | Learn from the library which parts fail. List obsolete parts at risk. Cut time spent waiting for parts | None | Weeks 6–8 | 2–10 lakh | Waiting-for-parts hours; emergency purchases | Low |
| L8 | **Faster onboarding** | Library entries become job aids. Cut training from 15 days to ~10. Augmentir claims 76% less training time, unverified ([Augmentir](https://augmentir.com/?p=14189)) | None | 2–3 months | 3–10 lakh | Training days; time to full output | Medium |
| L9 | **Supervisor span** | If supervisors exist mainly to hold knowledge, a span of 5–6 operators becomes possible over 1–2 years. Redeploy staff or let attrition shrink headcount; don't cut. Sensitive | None | 1–2 years | 0–40 lakh | Supervisors per shift | Low; politically hard. Don't lead with it |
| L10 | **Vision QC at one station** | A camera at one inspection point counts lead-centring, breakage and paint defects | Camera and lighting, ~₹2–6 lakh (est.) | 6–12 weeks | 0–15 lakh | Inspector hours; defects caught | Low until **[Q1–Q4]** are answered |
| L11 | **Material gate log** | A WhatsApp gate log of arrivals and dispatches, reconciled against SAP | None | 2–4 weeks | 2–10 lakh (part of the opportunity file's ₹9–27 lakh detention estimate) | Truck waiting time; stock mismatches | Low |
| L12 | **Pre-season maintenance** | Use the Pareto to schedule repairs before the school-season peak, when downtime costs ~3× more | None | Next peak | Included in L1, L2 and L5 | Peak-season downtime | Medium |
| L13 | **SAP PM write-back and HQ reports** | Log breakdowns and fixes into SAP's plant-maintenance module, and send HQ one report | None | Later | 0 directly | — | Strategic: it unlocks other plants |

### Scenarios (overlaps removed)

| | Conservative | Base | Optimistic |
|---|---|---|---|
| Downtime levers (L1, L2, L5, L12) | 15% of ₹22 lakh = 3 | 30% of ₹58 lakh = 17 | 45% of ₹1.2 crore = 54 |
| Repair spend (L5, L7) | 10% of ₹20 lakh = 2 | 20% of ₹40 lakh = 8 | 30% of ₹60 lakh = 18 |
| Throughput (L4) | 0 | 15 | 50 |
| Energy (L6) | 3 | 10 | 24 |
| Onboarding (L8) | 3 | 6 | 10 |
| Retirement cover (L3) | 0 | 10 | 20 |
| Supervisor span (L9) | 0 | 0 | 40 |
| QC (L10) | 0 | 5 | 15 |
| Gate log (L11) | 2 | 5 | 10 |
| **Total a year** | **~₹13 lakh** | **~₹76 lakh** | **~₹2.4 crore** |
| Subscription: 200 machines × ₹500 / ₹750 / ₹1,000 a month | ₹12 lakh | ₹18 lakh | ₹24 lakh |
| **Return for the plant** | **~1×** | **~4×** | **~10×** |

**Reading:**
- In the conservative case, a full-plant subscription doesn't pay. Two options would: sell only the knowledge layer (cheaper), or monitor only the 20–40 machines that matter.
- In the base case, it pays clearly. Most of the value comes from downtime and throughput, so **[B1], [B7], [M5] and [MT4]** decide which case is real.

---

## 5. The recommended pilot (Tejas on-site, Gawtam remote)

### Phases

| Phase | Weeks | What happens | Output | Cash cost |
|---|---|---|---|---|
| **0. Prepare** | 0 | Tejas gets answers to the "ask first" questions. Gawtam tests Tamil speech-to-text on sample voice notes **[T1]**, and AI extraction on sample register photos **[T3]** | Go or no-go to pitch | ~₹0 |
| **1. Your own data** | 1–2 | Tejas photographs 3–6 months of the breakdown register and shift reports. Gawtam extracts and checks them | One-page report: top 10 machines, downtime hours, MTTR (mean time to repair), and an estimated ₹ cost | ~₹0 |
| **2. Capture and answer** | 2–6 | Tejas runs 30-minute sessions with 3–5 senior technicians, covering the top 10 machines. They record fault → cause → fix as voice notes, with photos of parts. Gawtam structures the stories into a library (machine, symptom, cause, fix, recorded by, date). A WhatsApp assistant then answers symptoms with the top 3 causes and the cited cases. Every breakdown on a covered machine is logged with its time to diagnose | 30–50 stories; a working assistant; time-to-diagnose numbers | < ₹50k |
| **3. Sense** (optional) | 4–8 | Clip-on CT clamps on 10 machines, including 2–3 compressors, and vibration sensors on 3–5 shapers or motors, all on a cellular gateway. Run/idle and energy dashboard. A baseline-deviation classifier (the PoC pattern, minus the "command" signal) flags anomalies, and the assistant maps each one to the library | Utilisation, idle energy, any confirmed early warnings | ₹1–3 lakh |
| **Side tracks** | Any | One-day compressed-air leak walk with a rented ultrasonic detector (a quick win that builds trust). Collect ~500 QC defect photos to check feasibility | ₹ saved on air; a QC go or no-go | ₹10–20k |
| **Review** | 8 | Results against the success criteria. Proposal for a paid phase 2 | Decision | — |

### Success criteria

| Area | Threshold |
|---|---|
| Data | ≥3 months of breakdowns digitised; the Pareto reviewed with the plant head |
| Knowledge | ≥30 stories from ≥3 senior technicians, covering ≥10 machines |
| Assistant | On ≥15 real breakdowns on covered machines, the actual fix is in the top 3 suggestions ≥60% of the time |
| Speed | Time to diagnose on covered machines down ≥20% against the register baseline. The sample is small, so treat this as directional |
| Sensors (if run) | Run/idle state ≥90% correct against spot checks; at least one anomaly that maintenance agrees was real |
| Commercial | The plant head (and HQ if needed) agrees to a paid phase 2, or names the reason not to |

### Who does what

| Who | Does | Time |
|---|---|---|
| Tejas | Plant access, photos, technician sessions, sensor installation with the plant electrician, weekly check-in with the maintenance head | 1–2 days a week for 8 weeks **[L1, L2]** |
| Gawtam | Extraction, library, assistant, dashboard, analysis, a weekly one-page update, calls with technicians. IST is 4.5 h ahead of Stockholm in winter, so Stockholm mornings are Indian afternoons | 10–15 h a week **[G1]** |
| Plant head (sponsor) | Access, a named contact, the week-2 and week-8 reviews | ~1 h a week |
| Maintenance head | Explains register codes; logs breakdowns on covered machines | 1–2 h a week |
| 3–5 senior technicians | Record stories; try the assistant | 1–2 h a week each **[L5]** |
| Plant electrician | Installs the CT clamps (needs a panel shutdown) | ~1 day **[L8, X7]** |

### Our cost (est.)

| Item | Cost |
|---|---|
| CT clamp kits and gateway, 10 machines | ₹40k–1.5 lakh. Clamps run $50–200 each ([Fabrico](https://www.fabrico.io/blog/oee-on-legacy-machines-without-plcs-sensors-cameras-retrofits/)); add the gateway |
| Vibration sensors, 5 points | ₹10k–1 lakh. DIY-grade ₹1.5–2k a point; commercial ₹12.5–35k (opportunity file) |
| Cellular data | ₹1–2k |
| Speech-to-text | < ₹1,000. Sarvam charges ₹30 per hour of audio ([pricing](https://docs.sarvam.ai/api-reference-docs/pricing)) |
| WhatsApp Business API | < ₹2,000. Utility messages ~₹0.115 each; service messages free until a reported change on 1 Oct 2026 ([ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/india/), vendor). Weeks 1–2 can use a normal WhatsApp number |
| LLM API | ₹5–15k for 2 months |
| Technician honorarium | ₹10–25k (₹200–500 a story) |
| Leak detector rental | ₹5–15k |
| Tejas's travel | ₹10–35k **[L2]** |
| Tejas's fee or equity | To agree **[G4]** |
| **Total cash** | **< ₹50k without sensors; ₹1–3.5 lakh with them** (~€1,000–3,500) |

### Commercial terms

| Option | For | Against |
|---|---|---|
| Fully free pilot | Easiest yes | Tests nothing about willingness to pay. Free pilots drift |
| **Free weeks 1–2, then a nominal ₹50k–1 lakh for weeks 3–8 (recommended)** | The week-2 report earns the right to ask. A small payment tests the budget path **[B5]** | Needs a plant-level spending limit or HQ approval |
| Free, with written conversion terms ("if the criteria are met, phase 2 at ₹X for 6 months") | Commits them up front | Harder to sign before they've seen value |

**After the pilot,** price from value: aim for 10–25% of verified savings. Options:
- **Per plant:** ₹1–2 lakh a month for the knowledge assistant plus monitoring of 20–40 key machines.
- **Per machine:** ₹500–1,500 a month for sensors.
- **Knowledge only:** ₹25–50k a month.
- **Outcome-based:** a fee per verified downtime hour saved, the way Infinite Uptime sells "Production Outcomes as a Service" ([site](https://www.infinite-uptime.com/)). Measurement disputes are the risk **[B14]**.

### Pilot risks

| Risk | Mitigation |
|---|---|
| Senior technicians fear they're training their replacement **[K6]** | Credit each story to the person who recorded it, inside the tool. Pay a per-story honorarium. Have management present it as their legacy |
| Breakdown register is missing or useless **[MT2]** | Start a simple WhatsApp breakdown log on day 1. The baseline then takes 4 weeks instead of 0 |
| Tamil speech-to-text fails on noise and Tanglish (Tamil mixed with English part names) **[T1]** | Phone held close; record away from the machine; a custom vocabulary of part names; text fallback |
| Tejas's bandwidth **[L1]** | Front-load weeks 1–2; keep later visits short and scheduled |
| HQ blocks it or delays it **[B5]** | Keep the pilot under the plant head's spending limit; send the week-2 report to HQ as well |
| Workers see sensors as surveillance **[X2, X3]** | Monitor machines, not people. Agree in writing that pilot data isn't used for individual discipline |
| A suggested fix causes damage or injury **[X6]** | Suggestions are advisory; technicians decide; lockout rules are unchanged |
| The lacquer area is a hazardous zone **[T9]** | No sensors there in the pilot |

---

## 6. What competitors' ROI claims tell us

| Vendor | What it claims | What the claim rests on | Would it hold at HPPL? | What it would cost HPPL |
|---|---|---|---|---|
| **Tractian** | 401% ROI, 36% less downtime | A Verdantix model of a *hypothetical* $200M, 12-site customer (`Competitors.md`) | Not as a promise. Plants with no data start far behind | ~₹71 lakh a year for 200 sensors at a third-party ~$35 a sensor a month. Not sold in India |
| **Infinite Uptime** (Pune) | "Production Outcomes as a Service". Up to 10% lower maintenance cost and up to 2.5% more throughput. 3× ROI in under 12 months (Vedanta) and 9× in under 6 months (a cement plant). First prescription in ~2 weeks; validated outcomes in 2–3 months. ~1,000 plants ([site](https://www.infinite-uptime.com/)) | Customer case studies from heavy industry | Its 2-week-to-first-insight rhythm is the right one to copy. Its customers are steel and cement, where an hour of downtime costs far more | Not public. Aimed at heavy assets |
| **Augmentir** (connected-worker platform) | 27% less downtime, 37% more productivity, 76% less training time, 26% less rework ([site](https://augmentir.com/?p=14189)) | Undisclosed | The closest product to the knowledge layer; the numbers are marketing | Not public; US-centric |
| **Indian IoT/OEE vendors** | Retrofit monitoring on legacy machines | One vendor listing: ₹6,000–18,000 a machine a month as SaaS, or ₹35,000–80,000 a machine in hardware ([Trade4Asia](https://www.trade4asia.com/suppliers/industry-smart-manufacturing)) | Visibility, yes. No diagnosis and no knowledge layer | ₹1.4–4.3 crore a year for 200 machines, above any plausible HPPL budget |
| **Benchmarks** | Predictive maintenance costs ~30–40% less than run-to-failure, and 8–12% less than preventive (DOE, via [Reliamag](https://reliamag.com/topics/guides/predictive-maintenance-roi-benchmarks-what-the-studies-show)) | A 2010 federal guide; dated | Use as a range only | — |

**What we can credibly say:** "We'll measure it on your machines in 8 weeks, against your own breakdown register." Don't quote other vendors' percentages as our own.

**Pricing insight:** Indian IoT listings price monitoring at ₹6,000+ a machine a month, so the ₹500–1,000 in `CLAUDE.md` may be too low. HPPL's real ceiling is its value pool (₹13 lakh to ₹2.4 crore), not competitors' prices. Monitoring fewer machines at a higher price may beat monitoring all 200 cheaply.

---

## 7. Scalability (unrestricted)

### 7.1 Where it can go

| Step | Size (est. unless linked) | Why it could work | What has to be true |
|---|---|---|---|
| **All of HPPL** | 10 factories in 5 regions ([company site](https://hindustanpencils.com/about-us/)). At ~200 machines each, ~2,000 machines → ₹1.8–3.6 crore a year at ₹750–1,500 a machine a month | Same products, probably the same machine models **[S1]**. One library serves all plants | Pollachi succeeds and HQ buys centrally **[S2]** |
| **Pencil and stationery makers** | India's pencil market is ~₹4,000 crore ([YourStory](https://yourstory.com/2024/12/doms-success-story-pencil-market-india)). DOMS (FY25 revenue ₹1,913 crore), Kokuyo Camlin, Flair and others: perhaps 20–50 sizeable plants **[S3]** | Same process; references travel within an industry | A small vertical. Worth it as references, not as the market |
| **Tamil Nadu spinning mills** | ~19M of India's 46M working spindles, 12M over 15 years old ([DT Next](https://www.dtnext.in/amp/story/news/tamilnadu/sima-lauds-tn-govts-subsidy-for-spinning-modernisation-815168)). Tamil Nadu has ~55% of India's spinning mills ([TN Textiles](https://tntextiles.tn.gov.in/cooperative-spinning-mills)) | Very machine-dense, from a few makers (LMW is in Coimbatore), so one library per ring-frame model serves hundreds of mills. Tamil-speaking, an hour from Pollachi | Mills pay despite thin margins **[S4, S5]** |
| **Other Coimbatore-region clusters** | Pumps: ~40% of India's pump sets; ~600 units on paper, many inactive ([Deccan Herald](https://www.deccanherald.com/amp/story/business%2Fcoimbatores-motor-pump-makers-deeply-challenged-by-gujarat-peers-3685168)). Also foundries, Tiruppur knitwear and Hosur auto parts. Pollachi coir has ~400 units, but over half are defunct ([DT Next](https://www.dtnext.in/news/tamilnadu/pollachis-coir-units-in-distress-amid-industrys-continuous-downward-spiral-793803)), so skip it | Association channels (SIMA, CODISSIA, TANSTIA) sell to a whole cluster **[S11]** | Small units pay less. Target 100+ worker plants |
| **All of India** | TAM ~₹2,700 crore (~$320M) bottom-up (opportunity file) | Speech-to-text exists for 22 Indian languages, so language expansion is cheap ([DQ India](https://www.dqindia.com/data-and-ai/sarvam-ai-launches-audio-model-for-22-indian-languages-11071691)) | A local field partner per cluster (the "Tejas model") |
| **Other emerging markets** | Bangladesh, Vietnam and Indonesia textiles; Africa; Latin America | The same brownfield, low-IT, low-price pattern | Tractian is strong in Latin America |
| **Rich countries' retiring workforce** | US manufacturing needs ~3.8M workers through 2033, ~2.8M of them to replace retirees. The US has ~538k industrial machinery mechanics, maintenance workers and millwrights (Deloitte/MI and BLS, via [Reliamag](https://reliamag.com/topics/guides/manufacturing-maintenance-skills-gap-statistics)) | Knowledge capture pays 10–20× more where wages are high. Gawtam is in Stockholm, near Nordic sawmills, pulp and paper (hypothesis) | Competition is stronger (Augmentir, Siemens findIQ). It needs the India proof first |
| **Machine-maker channel** | e.g. LMW's installed base | Makers want aftermarket service revenue. A per-model library is valuable to them | They may build it themselves; Siemens findIQ already targets machine builders **[S6]** |

### 7.2 What compounds

- **A library per machine model.** Each plant's fixes improve the answers for the same model elsewhere. That's the data network effect, and the main reason this is more than a services business. It needs consent and anonymisation **[C4]**.
- **Signal models that transfer.** Domain adaptation and unseen-fault generation (`Academic_EPFL_IMOS.md`) could carry a fault signature from one plant's machine to another's without waiting for it to fail. Unproven outside bearing datasets.
- **The same engine as direction A.** "Symptom → cause → fix, with a citation" holds whether the source is a requirement document or a technician's voice note. Factory robots in these plants later would join the two directions.

### 7.3 What limits scale

| Limit | Why | Mitigation |
|---|---|---|
| **Onboarding labour per plant** (the consultancy trap) | Capturing stories needs someone on the floor | Field partners per cluster; self-serve recording by plant staff; a pre-built library per machine model, so plant #20 needs far less capture than plant #1 |
| Hardware logistics | Installing, replacing and supporting sensors | Cellular clamps; a local installer partner; hardware optional |
| Payment collection | Indian B2B customers pay slowly (45–90 days **[B12]**) | Annual prepay discounts; an Indian entity |
| Price ceiling | Low margins | Monitor the machines that matter, not all 200; price from value |
| Founder in Stockholm | Sales and trust are local | Tejas or a hired field lead; one visit a quarter |
| Language and dialect | Tamil first; each language needs testing | Speech-to-text providers cover 22 languages; the part-name vocabulary is the real work |

### 7.4 Unit economics sketch (est.)

| Item | Value |
|---|---|
| ARR per plant | ₹9–36 lakh (~$11–42k): 100–200 machines × ₹750–1,500 × 12, or a per-plant licence |
| Onboarding cost per plant | ₹2–5 lakh: 4–6 weeks of a field partner, plus hardware if we own it |
| Running cost per plant | ₹0.6–1.8 lakh a year: speech-to-text, LLM, WhatsApp, cellular data |
| Gross margin | 70–85% software-only; 50–65% with hardware amortised |
| Payback on onboarding | 2–6 months |

### 7.5 ARR scenarios (est.)

| Path | Year 1 | Year 3 | Year 5 |
|---|---|---|---|
| **Bootstrapped:** Tamil Nadu only, with HPPL plus local mills and pump makers | 1–3 plants, ₹10–50 lakh | 20–40 plants, ₹3–8 crore | 60–120 plants, ₹10–25 crore (~$1.2–3M) |
| **Venture:** all of India, multi-plant groups, a machine-maker channel, one market abroad | 3–5 plants, ₹0.5–1 crore | 100–200 plants, ₹15–40 crore (~$2–5M) | 500–1,000 plants plus abroad, ₹100–250 crore (~$12–30M) |

The opportunity file's 3-year SOM (~50 plants, ~₹4.5 crore ARR) sits between the two paths. Tractian reached a $1.4B valuation with 2,000+ facilities, which shows the venture path is possible. It did so with sensors and in richer markets.

---

## 8. What would change this plan

**Stop or pivot if:**
- The week-2 data shows total downtime under ~₹20 lakh a year. Then sell QC or the knowledge layer only, or move to a more machine-dense plant (spinning).
- Senior technicians won't record even 15 stories in 3 weeks.
- The budget sits only at HQ, with no path in.
- Tamil speech-to-text can't reach usable accuracy, even with close-talk audio and a part-name vocabulary.

**Push harder if:**
- The Pareto shows ~10 machines causing most downtime (focus works).
- The plant is capacity-limited in peak season (throughput value).
- The plant head forwards the week-2 report to HQ unprompted.
- Another HPPL plant or a nearby mill asks for the same thing.

---

## Sources

[Musgrave](https://musgravepencil.com/blogs/news/howapencilismade) · [Ticonderoga](https://weareticonderoga.com/journey-of-a-pencil) · [Blackwing](https://blackwing602.com/pages/how-its-made) · [HPPL 2018 catalog](https://www.hindustanpencils.com/Hindustan_Pencil_Product_Catalog_2018.pdf) · [HPPL about](https://hindustanpencils.com/about-us/) · [arXiv AR repair study](https://arxiv.org/pdf/2301.07570) · [Let's Data Science](https://letsdatascience.com/news/indian-factories-adopt-smart-retrofitting-solutions-f0f094ce) · [DOE compressed-air fact sheet](https://www.compressedairchallenge.org/data/sites/1/media/library/factsheets2026/fact-sheet-7-compressed-air-system-leaks_updated2026.pdf) · [Augmentir](https://augmentir.com/?p=14189) · [Fabrico](https://www.fabrico.io/blog/oee-on-legacy-machines-without-plcs-sensors-cameras-retrofits/) · [Sarvam pricing](https://docs.sarvam.ai/api-reference-docs/pricing) · [ChatMaxima WhatsApp pricing](https://chatmaxima.com/whatsapp-api-pricing/india/) · [Infinite Uptime](https://www.infinite-uptime.com/) · [Trade4Asia](https://www.trade4asia.com/suppliers/industry-smart-manufacturing) · [Reliamag PdM ROI](https://reliamag.com/topics/guides/predictive-maintenance-roi-benchmarks-what-the-studies-show) · [Reliamag skills gap](https://reliamag.com/topics/guides/manufacturing-maintenance-skills-gap-statistics) · [YourStory](https://yourstory.com/2024/12/doms-success-story-pencil-market-india) · [DT Next spindles](https://www.dtnext.in/amp/story/news/tamilnadu/sima-lauds-tn-govts-subsidy-for-spinning-modernisation-815168) · [TN Textiles](https://tntextiles.tn.gov.in/cooperative-spinning-mills) · [Deccan Herald pumps](https://www.deccanherald.com/amp/story/business%2Fcoimbatores-motor-pump-makers-deeply-challenged-by-gujarat-peers-3685168) · [DT Next coir](https://www.dtnext.in/news/tamilnadu/pollachis-coir-units-in-distress-amid-industrys-continuous-downward-spiral-793803) · [DQ India](https://www.dqindia.com/data-and-ai/sarvam-ai-launches-audio-model-for-22-indian-languages-11071691)

---

## Change log

- 28 Oct 2026: created. Immediate ROI, a bottom-up baseline, the lever menu, an 8-week pilot with Tejas on-site, and scalability.
- 28 Oct 2026: added Infinite Uptime moving down-market to the top risks.
