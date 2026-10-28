# HPPL Pollachi: open questions

**Date:** 28 Oct 2026 · **Audience:** internal (Gawtam, Tejas) · **Used by:** `hppl_poc.md` (which cites these IDs), `Lead_Hindustan_Pencils.md`

**How to use this:**
- Fill in the **Answer** column as answers come in, with the date and who answered.
- Then replace the matching estimate in `hppl_poc.md` and move confirmed facts into `Lead_Hindustan_Pencils.md`.
- "My estimate" is a guess to argue with, not a fact. Everything in that column is (est.) unless a link is given.

**Legend:**
- **Who** can answer: T = Tejas · P = plant staff (plant head, maintenance, production) · HQ = Mumbai head office · G = Gawtam · D = desk research
- **Priority:** Blocker = needed before pitching the pilot · Pilot = needed before or during the pilot · Later = needed after the pilot
- **Conf.** = my confidence in my estimate: Low, Med or High

---

## Ask first (top 10)

| # | ID | Question |
|---|---|---|
| 1 | MT2 | Is there a breakdown register (paper, Excel or SAP PM), and can we see 3–6 months of it? |
| 2 | M4 | Which 10 machines break down most, and do they stop the line? |
| 3 | B5 | Who signs off on spending: the plant head or Mumbai HQ? What can the plant approve alone? |
| 4 | MT4 | How long is a typical breakdown, and how much of that is waiting for the right person and diagnosing? |
| 5 | B7 | Does the plant sell everything it can make, at least in the peak season? |
| 6 | K2 | Who are the go-to people when a machine stops, how many are there, and when do they retire? |
| 7 | K6 | Would those senior technicians record their fixes, and what would make them willing? |
| 8 | PL1 | What exactly does the Pollachi plant make? |
| 9 | L1 | How often can Tejas be at the plant over 8 weeks? |
| 10 | B6 | Who did Tejas meet (role), and will they take a call with Gawtam? |

---

## PL: Plant and products

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| PL1 | What does the Pollachi plant make: full pencils, leads, slats, erasers, sharpeners, or a mix? | Full wooden pencils from slats onward. Possibly leads too: HPPL makes most components in-house ([catalog](https://www.hindustanpencils.com/Hindustan_Pencil_Product_Catalog_2018.pdf)) | Low | T | Blocker | |
| PL2 | What's the daily output? | 0.5–1.5M pencils a day. The company makes 8.5M a day across 10 factories, ~0.85M on average | Low | T, P | Pilot | |
| PL3 | How many production lines, and how many machines per line? | ~20 lines of ~10 machines | Low | T, P | Pilot | |
| PL4 | How many shifts, and how many working days a year? | 2 shifts (3 in peak season), ~300 days | Med | T | Pilot | |
| PL5 | When is the peak season, and how much higher is output then? | Jan–May, before the school year starts in June; 30–50% above off-peak | Med | P | Pilot | |
| PL6 | Is the plant owned and run by HPPL, or by a contract manufacturer? | HPPL-owned | Med | T | Blocker | |
| PL7 | What is the plant's annual revenue or output value? | ~₹120 crore (₹1,200 crore ÷ 10 factories; crude) | Low | HQ, T | Later | |
| PL8 | Is the plant growing, flat or shrinking? Any new machines planned? | Flat; occasional second-hand machines | Low | T | Later | |
| PL9 | Is the plant ISO 9001 certified? Any other audits (BIS, export customers)? | ISO 9001, yes | Med | D, T | Later | |
| PL10 | Is ₹1,200 crore company revenue right? | Plausible but unverified. HPPL is private, and public estimates vary widely | Low | HQ, D | Later | |

## M: Machines

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| M1 | What's the exact machine count, and how does it split by type: saws, groovers, glue presses, shapers, paint lines, tipping, printing, packing, extruders, kilns, compressors, dust extraction? | 200+ in total: mostly woodworking and finishing machines, plus 5–15 utility machines | Low | T, P | Pilot | |
| M2 | Who made the machines, and do the makers still sell spares and support? | A mix of Indian builders and German, Japanese or Chinese imports. Several makers are gone or no longer support these models | Low | P | Pilot | |
| M3 | How many distinct machine models are there? | 15–30 models, with many identical units of each | Low | P | Pilot | |
| M4 | Which 10 machines fail most? | Shapers, paint-line conveyors and dryers, tipping machines, glue presses, compressors | Low | P | Blocker | |
| M5 | How often does a machine break down? | 1–2 times a month on average, heavily skewed: ~20% of machines cause ~80% of stops | Low | P | Blocker | |
| M6 | How many major failures a year (motor burnout, gearbox, spindle; more than a day down)? | 5–15 plant-wide | Low | P | Pilot | |
| M7 | When one machine stops, does the line stop? How much work-in-progress sits between stages? | About half the time. Glued sandwiches must dry before shaping, which decouples the line there | Low | P, T | Pilot | |
| M8 | What usually fails? | Bearings, belts, cutters and blades, pneumatic cylinders and valves, motors, contactors and sensors, clogged glue or paint nozzles | Med | P | Pilot | |
| M9 | Do any machines have PLCs, drives or energy meters we could read? | A few newer ones have PLCs or variable-frequency drives; most use relay logic | Low | P | Pilot | |
| M10 | How good is the power supply: dips, outages, generator use? | Some dips; diesel-generator backup | Low | P | Later | |
| M11 | Where is it dusty, hot or humid enough to matter for sensors? | Heavy wood dust at the saws and shapers; solvent fumes at the paint line | Med | T | Pilot | |
| M12 | How big is the compressed-air system? | 2–4 compressors | Low | P | Later | |
| M13 | If leads are made here, how is the kiln heated, and how big is it? | Electric kiln; the largest single energy user | Low | P | Later | |

## MT: Maintenance today

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| MT1 | Is there a separate maintenance team? How big, and with which skills (fitters, electricians)? | Yes: 8–20 fitters and electricians across shifts. Operators do basic fixes | Low | T, P | Blocker | |
| MT2 | Are breakdowns logged, and where: a paper register, SAP PM, Excel, a WhatsApp group? | A paper register per shift, kept patchily. Possibly SAP PM entries for big jobs | Low | T | Blocker | |
| MT3 | Can we see 3–6 months of those logs? Are photos OK? | Yes, if the plant head agrees. Handwritten in a Tamil and English mix | Low | T | Blocker | |
| MT4 | How long does a typical breakdown last, split into waiting for a technician, diagnosing, waiting for parts and repairing? | 1.5–2 h on average; 30–50% is waiting and diagnosing | Low | P | Blocker | |
| MT5 | Is there a preventive maintenance schedule, and is it followed? | Lubrication and cleaning routines on paper, loosely followed | Low | P | Pilot | |
| MT6 | Do they call outside fitters or the machine makers? How often, and at what cost? | Local fitters and motor rewinders often; makers rarely | Low | P | Later | |
| MT7 | How are spares managed: a store in SAP MM? Are there stock-outs? Are any parts made locally? | Stores are in SAP MM. Critical spares are sometimes missing, and some parts are machined locally | Low | P | Pilot | |
| MT8 | What is the annual maintenance spend on parts and outside services? | ₹20–60 lakh | Low | P, HQ | Pilot | |
| MT9 | Do they track MTTR, MTBF, downtime % or OEE? | No formal measures; downtime appears in shift reports | Med | P | Pilot | |
| MT10 | Have they ever tried condition monitoring (vibration readings, thermal imaging, oil analysis)? | Never, or a one-off vendor demo | Low | T | Pilot | |
| MT11 | Do maintenance staff use smartphones and WhatsApp at work? Are phones allowed on the floor? | Most have Android phones with WhatsApp; phones may be restricted on the floor | Med | T | Blocker | |

## K: People and knowledge

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| K1 | Are the staff who look after 2–3 machines operators, technicians, or both? | Operators who do minor fixes; real repairs go to a fitter | Low | T | Blocker | |
| K2 | Who are the go-to people when a machine stops, and how many are there? | 3–6 senior fitters or supervisors per shift | Low | T | Blocker | |
| K3 | How many of them retire in the next 5 years? | 30–50% of them; retirement is at 58–60 | Low | P | Pilot | |
| K4 | Is any knowledge written down: maker manuals, personal notebooks, SOPs? | Some English or foreign-language maker manuals in a cupboard; a few personal notebooks | Low | T | Pilot | |
| K5 | What language do technicians speak at work? | Tamil, with English part names (Tanglish). Some migrant workers speak Hindi | Med | T | Blocker | |
| K6 | Would senior technicians record their fixes? What would make them willing? | Willing if credited and recognised (named in the tool, a small honorarium, management recognition). Wary if it looks like replacement | Low | T | Blocker | |
| K7 | Can operators read Tamil text on a phone? | Most can; voice is still preferred | Med | T | Pilot | |
| K8 | Has the plant lost a key person and paid for it? Is there a story? | Likely yes. A story like that is the strongest argument for the pilot | Low | T | Pilot | |
| K9 | Do supervisors exist mainly to hold knowledge, or for discipline and output tracking? | Both, but mostly output tracking | Low | T | Later | |

## B: Money, buyer and budget

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| B1 | What does an hour of downtime cost (lost output, overtime, missed dispatch)? | ₹1,200–2,500 per line-hour on a blended basis; ~₹3,750 in peak season (`hppl_poc.md` section 3) | Low | P | Blocker | |
| B2 | How many downtime hours are there a month? | 300–800 machine-hours | Low | P | Blocker | |
| B3 | What is the contribution margin per pencil or product line? | 25–35% | Low | HQ | Later | |
| B4 | What is the monthly electricity bill? | ₹8–25 lakh a month (₹1–3 crore a year); higher if there's a kiln | Low | P | Pilot | |
| B5 | Who decides on spending: the plant head or HQ? What can the plant approve alone? | HQ approves anything recurring. The plant head can approve one-off spends of ₹1–5 lakh | Low | T | Blocker | |
| B6 | Who did Tejas meet (role), and would they take a call with Gawtam? | The plant manager, or a production or maintenance head. Probably yes | Low | T | Blocker | |
| B7 | Is the plant capacity-limited, selling all it can make, at least in peak season? | Yes in peak season; no off-peak | Low | P | Blocker | |
| B8 | Of all their problems, which do they rank first? | Manpower or QC, as reported first. Maintenance moves up once someone puts a cost on it | Low | T, P | Blocker | |
| B9 | Have they bought software or IoT besides SAP? Have vendors approached them? | Nothing bought; some sensor and ERP vendors have pitched | Low | T | Pilot | |
| B10 | What would they pay, per machine or per plant per month? | ₹500–1,500 a machine for sensors plus the assistant; ₹25–50k a month for the knowledge layer alone | Low | P, HQ | Later | |
| B11 | When is the budget set? | Financial year April–March; budgets set in Feb–Mar | Med | HQ | Later | |
| B12 | How fast do they pay vendors? | 45–90 days | Low | HQ | Later | |
| B13 | Do they prefer capex (buy the sensors) or opex (subscription)? | Small opex, or capex with payback under 12 months | Low | HQ | Later | |
| B14 | Would they accept outcome-based pricing (paying per verified downtime hour saved)? | Interested, but likely to argue about measurement | Low | P, HQ | Later | |
| B15 | Is HQ's bigger pressure cost or quality? How much does DOMS's higher margin weigh on them? | Cost. DOMS reported an 18.2% EBITDA margin in FY25 | Low | HQ | Later | |

## D: Data and IT

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| D1 | Which SAP do they run (ECC or S/4HANA), and which modules (PP, MM, PM, QM)? | ECC or S/4 with finance, MM, SD and PP. PM is probably unused | Low | P, HQ | Pilot | |
| D2 | Who runs SAP: HQ IT or a partner? Could we write into it? | HQ IT or an SAP partner. Writing back needs HQ approval and takes months | Low | HQ | Later | |
| D3 | Is there Wi-Fi on the floor? Does 4G (Jio, Airtel) work inside the sheds? | Office broadband only; 4G works in most areas | Med | T | Pilot | |
| D4 | What production data is recorded each shift (output, rejects, downtime)? | A shift report on paper or Excel, entered into SAP daily | Low | T | Pilot | |
| D5 | Can we photograph or film machines, nameplates, panels, the line, the QC station and the dock? | Allowed with permission; no people, no process secrets | Low | T | Blocker | |
| D6 | Is there CCTV on the lines? | Some, for security | Low | T | Later | |
| D7 | Can data leave the plant, or India? Will they want an NDA? | Not a concern for most data; HQ may ask for an NDA | Low | HQ | Pilot | |

## Q: Quality control

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| Q1 | What is checked, at which stage, and by whom? | End-of-line visual checks: lead centring, breakage, paint, print, tip, length | Low | T | Later | |
| Q2 | How many inspectors are there per shift? | 10–30 | Low | P | Later | |
| Q3 | What are the internal reject rate and the market return rate? | 1–3% internal rejects; returns under 0.5% | Low | P | Later | |
| Q4 | Which defect costs most? | Lead broken inside the pencil. Customers complain, and it can't be seen from outside | Low | P | Later | |
| Q5 | Are rejects reworked, sold as seconds, or scrapped? | Scrapped or sold as seconds | Low | P | Later | |
| Q6 | Can they share ~500 defect photos and the QC checklist? | Yes, with permission | Low | T | Later | |
| Q7 | Do they have any machine vision now? | None | Med | T | Later | |
| Q8 | How fast does the line run at the inspection point? | 100–300 pencils a minute. One 2025 paper ran laser checks at 200 a minute ([MDPI](https://www.mdpi.com/2571-5577/8/6/184)) | Low | P | Later | |

## MM: Material movement

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| MM1 | What do they want to see: arrivals, stock, work in progress, dispatch? | Raw-material arrivals and stock against SAP; work in progress between stages | Low | T | Later | |
| MM2 | What is the actual pain: trucks waiting, wrong stock, lost material? | Not knowing what is where, because SAP lags reality | Low | T | Later | |
| MM3 | Where do Pollachi's slats come from, and how long do they take to arrive? | Kashmir or north India by truck, 5–10 days | Low | P | Later | |
| MM4 | How does the gate work today: a paper register, a weighbridge? | A paper register plus a weighbridge | Med | T | Later | |
| MM5 | Do they pay truck detention charges? | Rarely | Low | P | Later | |

## H: Hiring, training and attrition

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| H1 | Is the 30% attrition yearly? Which roles leave? | Yearly. Mostly young operators and contract or migrant workers, not senior technicians | Med | T | Pilot | |
| H2 | Why do people leave? | Wages at nearby textile and garment units, commute distance, migrants going home | Low | T | Later | |
| H3 | What happens in the 15 days of training, and who trains? | Shadowing an experienced operator; no written SOPs | Low | T | Pilot | |
| H4 | How long until a new hire is fully productive? | 1–3 months | Low | P | Later | |
| H5 | What share of workers are contract rather than permanent? | 40–70% | Low | P | Later | |
| H6 | Are there written SOPs or work instructions? | A few, kept for ISO audits | Low | T | Later | |

## L: Pilot logistics (Tejas on-site)

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| L1 | How often can Tejas be at the plant over 8 weeks? | 1–2 days a week | Low | T | Blocker | |
| L2 | Where does Tejas live, and what do travel time and cost to Pollachi come to? | Coimbatore region, 1–2 h each way | Low | T | Blocker | |
| L3 | Will the plant give Tejas floor access and a named contact? | Yes, if the plant head sponsors the pilot | Low | T | Blocker | |
| L4 | Which machines, or which line, should the pilot cover? | The 10 worst machines from the Pareto, ideally on one bottleneck line | Med | P | Pilot | |
| L5 | How much time can senior technicians spare? | 1–2 h each per week | Low | P | Pilot | |
| L6 | Can Gawtam join video calls with technicians? | Yes. Stockholm mornings are Indian afternoons (IST is 4.5 h ahead in winter) | High | G | Pilot | |
| L7 | Does Gawtam need to visit? | One 1–2-week visit for kickoff or sensors would reduce risk. Not needed for weeks 1–6 | Med | G | Pilot | |
| L8 | Who installs the sensors? | The plant electrician, with Tejas; CT clamps need a panel shutdown | Med | P | Pilot | |
| L9 | Does Tejas need a safety induction or permit? | Yes, a basic induction | Med | P | Pilot | |

## C: Commercial terms

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| C1 | Should the pilot be free or paid? | Free for weeks 1–2; ₹50k–1 lakh for weeks 3–8 | Med | G | Pilot | |
| C2 | Who signs the pilot agreement? | The plant head, with HQ informed | Low | HQ | Pilot | |
| C3 | Do we need a mutual NDA? | Yes | Med | HQ | Pilot | |
| C4 | Who owns the captured library? | HPPL owns its own library. We own the software and an anonymised model per machine type. This must be agreed in writing | Med | G, HQ | Pilot | |
| C5 | Can we name HPPL as a reference customer? | After a success, maybe; family firms are cautious | Low | HQ | Later | |
| C6 | How do we price after the pilot: per machine, per plant, or by outcome? | A per-plant tier with a per-machine add-on for sensors | Med | G | Later | |
| C7 | Do we need an Indian entity or GST registration to invoice? | Yes, or a partner who invoices for us | Med | D | Later | |

## S: Scale and market

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| S1 | Where are HPPL's other 9 factories, and do they run the same machines? | Five regions, including a Kashmir slat link. Same core machines | Low | HQ, D | Later | |
| S2 | Would HQ roll out to more plants if Pollachi works? | Yes, if it's cheap and proven | Low | HQ | Later | |
| S3 | How many pencil and stationery plants in India have 100+ workers? | 20–50 | Low | D | Later | |
| S4 | How many Tamil Nadu spinning mills run LMW machines, and how old are they? | Tamil Nadu has ~19M of 46M working spindles, 12M of them over 15 years old ([DT Next](https://www.dtnext.in/amp/story/news/tamilnadu/sima-lauds-tn-govts-subsidy-for-spinning-modernisation-815168)); LMW is dominant | Med | D | Later | |
| S5 | Do spinning mills have the same knowledge-loss problem, and would they pay? | Yes. Margins are thinner, but the plants are far more machine-dense | Low | D, T | Later | |
| S6 | Would a machine maker (e.g. LMW) partner with us or compete? | Compete on its current models; partner on old models it no longer supports | Low | D | Later | |
| S7 | Do Tractian or Infinite Uptime sell to plants this size in India, and at what price? | Infinite Uptime focuses on heavy industry; Tractian isn't in India | Med | D | Later | |
| S8 | Which cluster comes after pencils? | Spinning first, then pumps (~40% of India's pump sets come from Coimbatore) and foundries | Low | D | Later | |
| S9 | Is the retirement problem big enough in Sweden and the EU to sell there? | Yes, and it pays 10–20× more, but competition is stronger | Low | D, G | Later | |
| S10 | Are there government schemes that fund Industry 4.0 pilots? | Some state schemes for MSMEs; HPPL isn't eligible | Low | D | Later | |
| S11 | Can industry associations (SIMA, CODISSIA, TANSTIA) be sales channels? | Yes, good for cluster sales | Med | D | Later | |
| S12 | Is there a pencil-industry association, or a supplier everyone shares (glue, lacquer, machines), that could open doors? | Probably machine and lacquer suppliers | Low | D | Later | |

## T: Technical feasibility

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| T1 | Can Tamil speech-to-text handle shop-floor audio and Tanglish? | Usable with a phone held close and a part-name vocabulary; 70–85% word accuracy | Low | G (test) | Blocker | |
| T2 | How many stories cover most breakdowns? | 30–50 per machine family cover ~70% of common faults | Low | G | Pilot | |
| T3 | Can AI read the handwritten register accurately? | 70–90% of fields correct; needs a human check | Low | G (test) | Blocker | |
| T4 | Can CT clamps reliably detect run, idle and stop on these machines? | Yes for motor-driven machines; vendors claim 90–95% accuracy ([Fabrico](https://www.fabrico.io/blog/oee-on-legacy-machines-without-plcs-sensors-cameras-retrofits/)) | Med | D | Pilot | |
| T5 | Is vibration worth it on woodworking machines, or is current enough? | Current for machine state; vibration for spindle and bearing health on shapers | Med | G | Pilot | |
| T6 | Will product changeovers (hex to round, colour changes) trigger false alarms? | Yes, unless the classifier knows the operating mode (`Academic_EPFL_IMOS.md`) | Med | G | Pilot | |
| T7 | Will an LLM give correct, cited answers without making things up? | Yes, if answers come only from captured cases and "no match" is allowed. Use deterministic matching where possible | Med | G | Pilot | |
| T8 | What happens when the network drops? | WhatsApp queues messages and sensors buffer data; fine | Med | G | Later | |
| T9 | Is the lacquer area a hazardous zone? | Likely, because of solvent-based lacquer. No sensors there in the pilot | Low | P | Pilot | |
| T10 | How much of the hackathon PoC can be reused? | The concept, and part of the code. Swap "commanded vs measured" for deviation from each machine's normal baseline | Med | G | Later | |

## G: Founder and team (for Gawtam)

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| G1 | How many hours a week can you give this? | 10–15, alongside the job | Low | G | Blocker | |
| G2 | How much of your own cash will you put into the pilot? | ₹1–3.5 lakh (~€1,000–3,500) is needed with sensors; under ₹50k without | Med | G | Blocker | |
| G3 | Will you travel to India for this, and when? | Once in the first 3 months, for 1–2 weeks | Low | G | Pilot | |
| G4 | What is Tejas's role: a friend helping, a paid field partner, or a co-founder with equity? | Paid per day for the pilot; talk about equity if it continues. Agree before starting | Low | G, T | Blocker | |
| G5 | What is Tejas's background, and will the plant see him as credible? | Unknown | Low | G | Pilot | |
| G6 | Does a pilot for direction B pause direction A? | Mostly. A few interviews for A can run in parallel | Med | G | Pilot | |
| G7 | Does your employment contract allow side projects, and who owns the IP? | Unknown; check | Low | G | Blocker | |
| G8 | When do you register a company (India or Sweden)? | Not before a paid phase; needed to invoice (C7) | Med | G | Later | |
| G9 | What result would make you go full-time? | One paying plant plus two more in the pipeline | Low | G | Later | |
| G10 | How do you split time with localE? | Unknown | Low | G | Later | |

## X: Legal, privacy and labour relations

| ID | Question | My estimate | Conf. | Who | Priority | Answer |
|---|---|---|---|---|---|---|
| X1 | Will technicians consent, in writing, to being recorded and named in the tool? | Yes, with a simple consent form in Tamil | Low | T | Blocker | |
| X2 | Is there a union or workers' committee, and must it approve monitoring? | Possibly. Present it as monitoring machines, not people | Low | P | Pilot | |
| X3 | Could machine-utilisation data be used against workers? | People will fear it. Agree in writing that pilot data isn't used for individual discipline | Low | P | Pilot | |
| X4 | Does India's data protection law (the DPDP Act) apply to voice recordings? | Yes. Voices of identifiable people are personal data, so notice and consent are needed | Med | D | Pilot | |
| X5 | Will HQ allow data on a cloud outside India? | Probably; hosting in an Indian region avoids the question | Low | HQ | Pilot | |
| X6 | Who is liable if a suggested fix causes damage or injury? | Suggestions are advisory and technicians decide. State this in the agreement; safety lockout rules stay as they are | Med | G | Pilot | |
| X7 | What electrical safety rules apply to installing CT clamps in panels? | A licensed electrician and a panel shutdown | Med | P | Pilot | |

---

## Change log

- 28 Oct 2026: created with 139 questions and estimates. Absorbs the 15 questions from `Lead_Hindustan_Pencils.md`.
