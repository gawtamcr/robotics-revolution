# Factory brain: brainstorm

**Date:** 28 Oct 2026 · **Owner:** `factory-brain-strategist` · **Purpose:** explore a generic, plant-level reasoning layer for mixed, multi-vendor robot fleets, one level above the factory-specific work · **Status:** brainstorm. Hypotheses, not findings. No web research yet: external facts are marked "(to verify)" and every score is "(est.)".

---

## TL;DR

- **The idea:** a factory brain is a plant-level reasoning layer above robots from many vendors (arms, humanoids, AMRs), plus machines and people. It understands what a change means. It re-plans the work across the fleet, checks its own plan before anything moves, and cites the reasons for each step.
- **The test case:** switch a paint cell from car doors to car hoods without anyone writing robot code.
- **Why Gawtam:** it needs four layers of physical AI at once: reasoning, world models and sim, robot skills, and perception. Gawtam has depth in all four. Most startups own one (est.).
- **The hardest objections:**
  - Platforms (NVIDIA, Siemens, the big robot makers) each own pieces of this.
  - Robot controllers are closed to commands from third parties.
  - Learned policies don't yet meet factory reliability or cycle times.
  - The safety loop must stay certified.
- **Working answer:**
  - The brain plans, verifies and explains; certified controllers execute.
  - For fixed-cycle work: learned at design time, deterministic at run time.
  - Humanoids are just another vendor.
- **Seven candidate wedges.** First-pass scores (est.) favour:
  - a **verifier** for robot programs and learned policies (W5)
  - **intent-to-program** across vendors (W3)
  - **change-impact analysis** (W2)

  Cited diagnosis, the current idea, comes fourth.
- **One loop, three entry points:** change impact (before a change), the verifier (during it) and diagnosis (after it) are the same engine aimed at different moments. Run as a loop, they make up the brain.
- **Next:** interview manufacturing engineers and robot integrators about what a change costs, and build a sim spike of the door → hood switch.

---

## 1. The vision

### In Gawtam's words

> "A plant reasoning layer. But in a futuristic factory, with a lot of humanoids and manipulators with different vendors, the plant should also be able to understand what a change means and communicate effectively between them, reason and critically analyse these. With a mix of 4, a new change in task (for example painting a car door to painting a hood) should be easy to switch without re-programming."
>
> From the brainstorm, 28 Oct 2026; spelling lightly edited. "A mix of 4" means a plant reasoning layer, a world model, a robot brain (skills) and perception, working together.

### Running scenario: from doors to hoods

**Setting:** a paint and finishing area around 2030 (est.):
- two paint robots from vendor A and a sealing robot from vendor B
- a humanoid from vendor C that kits masking parts and loads fixtures
- AMRs (autonomous mobile robots) that move parts between cells
- PLCs (programmable logic controllers), a conveyor, a film-thickness gauge and a vision station
- operators on shift, and one process engineer

**The change:** the cell must paint hoods instead of doors. The colour is the same. The geometry is new, and there is a new film-thickness spec on the leading edge.

**Today (est.):**
- A process engineer and a robot programmer, often from an integrator, generate paths offline from CAD and touch them up on the line.
- They paint test panels, measure film thickness and iterate.
- Separately, someone updates the fixtures, masking, AMR routes, PLC sequences, safety zones and documents.
- It takes days to weeks per change, mostly in skilled hours.

**With a factory brain:**

| Step | What the brain does | Layers used |
|---|---|---|
| 1. Understand | Reads the change (engineering change order, new CAD, new spec) and states plainly how hoods differ from doors | Reasoning, knowledge |
| 2. Impact | Lists everything the change touches: paint and sealing paths, fixtures, masking kit, AMR routes, cycle time, safety zones, quality checks. Cites the spec, CAD and past changes behind each item | Knowledge, plant model |
| 3. Re-plan | Splits the work by capability: new paths for the paint robots, a new kitting list for the humanoid, a new route for the AMRs. Writes each in the vendor's own terms | Reasoning, skills, interop |
| 4. Critique | Simulates the plan (reach, collisions, coverage, film thickness, cycle time). Tries to break it. Flags what it can't verify | World model, sim, verifier |
| 5. Sign-off | Shows the engineer a cited diff: what changes, why, the evidence, and the risks that remain | Interface, citations |
| 6. Deploy | Pushes approved programs through each vendor's adapter. Safety settings stay with the certified controllers | Interop |
| 7. Monitor | Watches the first parts for film thickness, cycle time and symptoms | Perception, classifier |
| 8. Diagnose | If something drifts, maps the symptom to a cause and cites it (the current idea) | Knowledge, reasoning |
| 9. Remember | Stores the change: what worked, what failed, who approved it. The next change starts from here | Memory |

**The point:** in manufacturing, running a fixed line isn't the expensive part. Changing it is. Working hypothesis: **change is the unit of value.**

---

## 2. What a factory brain must do

| Capability | In Gawtam's words | What it means | Hardest part |
|---|---|---|---|
| **Understand** | "understand what a change means" | A live model of the plant (assets, capabilities, state, constraints), plus a predictive model of what happens if something changes | Building the plant model without months of manual modelling |
| **Communicate** | "communicate effectively between them" | Robot to robot: handoffs, shared space, timing. Brain to human: explanations people can check. Both need a vendor-neutral language of capabilities and tasks | Vendors share no command interface; humanoid stacks are closed (to verify) |
| **Reason and critique** | "reason and critically analyse" | A planner proposes; a separate verifier tries to falsify the plan, in sim and against requirements | A verifier that shares the planner's blind spots will just rubber-stamp its plans |
| **Adapt without reprogramming** | "switch without re-programming" | Intent (plain language, CAD, spec) becomes vendor programs or learned-policy parameters, verified before use | Reliability and cycle time of generated programs |
| **Remember and cite** | (the current idea) | Every decision traces to a spec, requirement, past case or role | Capturing knowledge that was never written down |

---

## 3. Layer map

From fleet (bottom) to people (top). **Every product and company name here comes from memory (knowledge up to mid-2026) and is to verify.**

| # | Layer | What it is | What exists today (to verify) | Possible whitespace |
|---|---|---|---|---|
| 1 | Fleet and machines | The physical assets | Arms: ABB, FANUC, KUKA, Yaskawa, Universal Robots. Humanoids: Figure, Agility, Apptronik, Boston Dynamics, UBTech, Unitree. AMRs; PLCs (Siemens, Rockwell); process machines | None for us: no hardware |
| 2 | Vendor control and interop | How you talk to each asset | Vendor languages: ABB RAPID, KUKA KRL, FANUC TP/KAREL, URScript. Standards: OPC UA and its robotics companion spec, VDA 5050 (AMR fleet commands), ROS 2 / ros2_control, Open-RMF (multi-fleet traffic), Asset Administration Shell (AAS, the Industry 4.0 asset description, with capability and skill submodels), MTConnect, PackML. Multi-vendor tools: RoboDK (offline programming with many vendor post-processors), Wandelbots, Mujin, Intrinsic Flowstate, Realtime Robotics | A capability description a reasoning model can use, with robots exposed as tools through MCP-style adapters. The PoC already exposes ROS 2 through MCP |
| 3 | Robot skills | What a robot can do on its own | Classic programs. VLAs (vision-language-action models): Physical Intelligence π0 / π0.5, NVIDIA GR00T, Figure Helix, Google DeepMind Gemini Robotics, Skild. Task-specific AI: GrayMatter Robotics (spraying, sanding without programming), Path Robotics (welding), Augmentus (scan-to-path) | Skills for process work (paint, seal, sand) are niche and crowded. General skills belong to well-funded labs |
| 4 | Perception and plant state | What's happening now | MES (manufacturing execution systems), SCADA, historians, IIoT platforms (e.g. Cognite, Litmus), vision systems, VLMs reading cell video | One queryable view of "what each asset is doing, and why", across vendors |
| 5 | World model and simulation | What would happen if… | Physics sim and digital twins: NVIDIA Isaac Sim / Omniverse (and its factory-fleet "Mega" blueprint), Siemens Process Simulate, Visual Components, ABB RobotStudio. Learned world models: NVIDIA Cosmos, Google DeepMind Genie, Meta V-JEPA | Process-aware checks of a change (e.g. predicted film thickness). A twin that assembles itself from CAD, programs and logs instead of months of modelling |
| 6 | Reasoning and planning | Planner plus verifier | LLM and VLM agents; embodied-reasoning models (Gemini Robotics-ER, NVIDIA Cosmos Reason); industrial copilots (Siemens Industrial Copilot and others) | Plant-level planning across vendors with an **independent** verifier |
| 7 | Knowledge and memory | Why things are the way they are | PLM (Siemens Teamcenter, Dassault 3DEXPERIENCE, PTC Windchill), MES, CMMS (maintenance management), requirement tools. The current cited-diagnosis idea | Links from product changes to robot programs, requirements and past failures, with citations |
| 8 | Human interface | Who decides | Vendor HMIs (operator panels), copilots, dashboards | A sign-off workflow for AI-made changes: who approves what the AI changed, with evidence |

**Reading the map (hypothesis):**
- **The platforms own the infrastructure:** layers 1–2 (robot makers), 5 (NVIDIA, Siemens) and the general part of 3 (the VLA labs).
- **Where a startup can stand:** the independent verifier (6), the change-to-program-to-requirement links (7), process-aware checks (5) and the sign-off workflow (8).
- **Adapters (2) are a means, not a product.**

---

## 4. Physical AI state of the art

Written from memory, with knowledge up to mid-2026. **Everything in this section is to verify.**

| Technology | Where it stands (to verify) | What it enables for the brain | What isn't ready |
|---|---|---|---|
| **VLAs** | π0 (2024) and π0.5 (2025) generalise to new scenes; π0.6-era work adds RL from experience. NVIDIA's GR00T N1 line ships open humanoid models. Gemini Robotics 1.5 and Figure Helix split a slow "thinking" model from a fast control policy | New tasks from demonstrations and language instead of code, especially unstructured ones (kitting, handling) | Success rates far below what a production line needs per cycle (est.); cycle time; certification; per-site data |
| **Cross-embodiment transfer** | Open X-Embodiment / RT-X (2023). GR00T and π models train across many robot bodies | One skill model across vendors: the multi-vendor problem itself | A new body still needs data. Closed industrial controllers often can't stream commands at policy rates (to verify by vendor) |
| **Embodied-reasoning models as orchestrators** | Gemini Robotics-ER plans, points in space and calls tools. NVIDIA Cosmos Reason reasons about physical scenes | The brain's planner can reason about space and call robot skills as tools | Metric precision; hallucination; latency |
| **World models** | NVIDIA Cosmos (synthetic data), Genie 3 (interactive worlds), V-JEPA 2 (latent prediction for planning). Learned world models are used to evaluate robot policies | Evaluate a plan or policy before it runs (the critic); make data for rare cases | Physical accuracy on process quality (paint film, contact forces); enough trust to sign off on |
| **Sim and synthetic data** | Isaac Sim/Lab, MuJoCo (MJX, Playground), Genesis; digital-twin blueprints | Verification; sim-to-real training; data for rare faults | Process physics; building twins cheaply |
| **Agent tool protocols** | MCP (late 2024) is widely adopted; ROS-to-MCP bridges exist; agent-to-agent protocols are emerging | Robots as tools. The PoC already works this way | No safety semantics; no standard schema for robot capabilities |

**Takeaway (hypothesis):**
- Generative models are now good enough to **propose** changes and to **simulate** them roughly.
- They are not yet good enough to **execute** unsupervised on a line with a fixed cycle time.
- So the architecture is: propose → verify → human approves → deterministic execution.
- Where variability is the job (kitting, handling), VLAs execute, under supervision and outside safety-critical zones.

---

## 5. Critical analysis

For each objection below: why it bites, our working answer, and what would prove us wrong.

**1. Platform risk.**
- **Why it bites:** NVIDIA (Omniverse, Isaac, Cosmos, GR00T), Siemens (Xcelerator, Process Simulate, Industrial Copilot) and the robot makers each build a piece of the brain. Humanoid makers ship their own fleet software (to verify). Any horizontal infrastructure, they will bundle or give away.
- **Working answer:** stand where they are conflicted.
  - Vendor neutrality: an OEM's brain won't run a rival's robots well.
  - Plant-specific knowledge: no platform owns a plant's change history.
  - Be an app on their platforms, not a rival platform.
- **Proves us wrong:** an OEM opens real multi-vendor support, or Siemens ships change-impact analysis inside its simulation tools.

**2. Closed controllers.**
- **Why it bites:** reading state is fairly easy (OPC UA, vendor APIs). Uploading programs or streaming commands is vendor-specific, sometimes licence-gated, and guarded by integrators (to verify).
- **Working answer:**
  - Start read-only: diagnosis, change impact, verification.
  - Write later, in each vendor's own language through post-processors (as RoboDK does), with deployment approved by a person.
- **Proves us wrong:** integrators or plants refuse any third-party write access, even with sign-off.

**3. The reliability gap.**
- **Why it bites:** production lines expect very high first-pass yield at a fixed cycle time (est.). Learned policies don't deliver that yet.
- **Working answer:** *learned at design time, deterministic at run time.*
  - Models generate and adapt programs offline; deterministic programs run.
  - VLAs run online only where variability is the job.
- **Proves us wrong:** VLA reliability reaches line standards soon, so the compile step stops mattering. The verifier would still matter.

**4. Safety and certification.**
- **Why it bites:** industrial robots fall under ISO 10218, collaborative operation under ISO/TS 15066, and control-system safety under ISO 13849. Humanoids have no mature standard yet. The EU Machinery Regulation (2023/1230) applies from early 2027 and covers machines whose behaviour evolves. The EU AI Act adds duties for high-risk AI. (All to verify.)
- **Working answer:** the brain is never in the safety loop.
  - Safety PLCs, zones and speed limits stay in certified hardware.
  - The brain can only propose changes to them, through human sign-off.
- **Proves us wrong:** regulators require the planning layer itself to be certified. That could also become an advantage for W5.

**5. No pooled data.**
- **Why it bites:** plants won't share data across customers (IP), so learning across customers is limited.
- **Working answer:**
  - The moat is per-plant memory, plus methods that transfer (verification, adapters, capability schemas), not a pooled dataset.
  - Use sim and synthetic data. Deploy on-prem.
- **Proves us wrong:** a competitor with an OEM's installed-base data learns faster than any per-plant approach can.

**6. Humanoid timing.**
- **Why it bites:** humanoids in factories look like pilots, not fleets (to verify). A brain built for humanoid fleets in 2030 has no buyer in 2027.
- **Working answer:** every plant is already multi-vendor (arms, AMRs, PLCs, machines, people). Build for that. Humanoids plug in later as one more vendor.
- **Proves us wrong:** nobody pays for multi-vendor reasoning until humanoids arrive in numbers.

**7. Where the reprogramming pain really sits.**
- **Why it bites:** high-volume automotive body and paint shops are highly automated. They use mature offline programming and plan model changes years ahead (est.). The pain per change may be larger elsewhere:
  - high-mix, low-volume plants (job shops, aerospace, furniture, contract and electronics manufacturing), where every new part needs programming and robots often don't pay off
  - automotive final assembly, the least automated area and where humanoid pilots happen (to verify)
- **Working answer:** door → hood is a good demo, but possibly the wrong first market. Measure what a change costs, how often it happens, and who pays.
- **Proves us wrong:** interviews show changes are rare or cheap everywhere we look.

**8. Buyers buy outcomes, not brains.**
- **Why it bites:** no budget line is called "factory brain". The real ones are new-product introduction (NPI) and launch, integration and commissioning, maintenance and downtime, and quality.
- **Working answer:** sell one measured outcome. Examples: hours from engineering change to validated programs, commissioning days, downtime hours.
- **Proves us wrong:** the outcome is too small, or split across too many teams to own.

**9. The integrators.**
- **Why it bites:** system integrators do most robot programming. Integration, not the robot, is most of a cell's cost (est., to verify). Integrators are at once channel, competitor and customer.
- **Working answer:** decide early.
  - Sell to integrators: a tool that makes them faster, which matters if they're short of capacity.
  - Or sell to plants: fewer integrator hours.
- **Proves us wrong:** integrators bill by the hour and block anything that cuts hours.

**10. The do-it-yourself version.**
- **Why it bites:** as in direction A, an engineer with a frontier LLM, RoboDK and the CAD might get 70% of change impact or intent-to-program for free.
- **Working answer:** a DIY setup lacks the plant context (knowledge layer), the vendor adapters, the independent verification and the citations.
- **Status:** untested; see E5 below.

---

## 6. Candidate wedges and scorecard

A **wedge** is a first product that sells on its own today and grows into the brain.

| ID | Wedge | What it does | First buyer (hypothesis) | Path to the brain | Capital needed |
|---|---|---|---|---|---|
| W1 | **Cited diagnosis across a mixed fleet** | The current idea, widened from one machine to a multi-vendor cell. When a cell misbehaves, maps symptom → cause → fix, with citations | Maintenance and production engineering | Builds plant state (layer 4) and memory (7), read-only | Low |
| W2 | **Change-impact analysis** | Given an engineering change (new part, variant, spec or robot), produces a cited report of everything it touches: programs, fixtures, reach, cycle time, safety zones, quality checks, documents. Read-only | Manufacturing engineering, NPI and launch teams; integrators | Builds the links between product data, robot programs and the plant model: the core of "understand what a change means" | Low–medium |
| W3 | **Intent-to-program across vendors** | From CAD, spec and plain-language intent: generates vendor programs, verifies them in sim, deploys after sign-off. The door → hood demo | Integrators; high-mix plants; finishing processes (paint, seal, sand, weld) | The brain's action layer | Medium–high: a robot cell, process physics. Crowded (to verify) |
| W4 | **Cross-vendor coordination** | Real-time task allocation and traffic among arms, AMRs, humanoids and people | Intralogistics and plant operations | The "communicate" capability | Medium. Crowded around AMR fleets (to verify) |
| W5 | **Verifier for robot programs and learned policies** | An independent check before any new program, VLA skill or vendor update goes live: simulates it, tests it against requirements and safety constraints, and issues a cited sign-off. Then monitors it in production. This is the "doctor of agents" note in `SUMMARY.md` §4 | Quality, safety and validation leads; teams deploying humanoids and VLAs that need evidence for their customers; integrators at acceptance tests (FAT/SAT: factory and site acceptance tests) | The "critique" capability, from a neutral position across vendors. Also bridges to direction A (requirement-based testing) | Medium |
| W6 | **Plant world model** | A learned, predictive model of the plant (throughput, quality, what-if) | Operations leadership | The "understand" capability | High. Needs a lot of data; competes with NVIDIA and Siemens twins |
| W7 | **Own cross-embodiment skill model** | Trains a factory-task VLA that runs on many vendors' robots | Robot makers, integrators | The skill layer | Very high. Competes with well-funded labs |

**Scorecard.** These are the fixed criteria from `CLAUDE.md`, scored 1–5 with half points, as in `Research/ICP.md`. All scores are first-pass estimates before any interview (est.). Founder fit is scored for Gawtam's current base (Stockholm, part-time, solo).

| Criterion | W1 | W2 | W3 | W4 | W5 | W6 | W7 |
|---|---|---|---|---|---|---|---|
| Pain intensity | 3.5 | 3.5 | 4.5 | 3 | 3.5 | 2.5 | 4 |
| Willingness to pay | 3 | 3 | 4 | 3 | 3.5 | 2.5 | 3 |
| Market size | 4 | 3 | 4.5 | 3.5 | 3 | 4 | 5 |
| Reachability for a solo founder | 3 | 3 | 2.5 | 2 | 3 | 1.5 | 1 |
| Competitive whitespace | 2.5 | 4 | 2 | 2 | 4 | 2 | 1.5 |
| Integration ease | 3.5 | 3 | 2 | 2 | 3 | 2 | 2 |
| Founder fit | 3 | 4 | 5 | 4 | 5 | 4.5 | 4.5 |
| **Total (/35)** | **22.5** | **23.5** | **24.5** | **19.5** | **25** | **19** | **21** |

**Reading the scores (est.):**
- **W5, the verifier, leads.**
  - It is neutral across vendors, and few players hold that position (to verify).
  - It uses Gawtam's full depth: control, RL, world models, sim.
  - Its pain grows as learned policies reach factories.
  - The open PhD topic at EPFL's IMOS lab, "Trustworthy AI for Autonomous Plant Operations", suggests that verifiable plant agents are still an open problem (see `Research/Academic_EPFL_IMOS.md`).
  - **Risk:** the market is small today.
- **W3, intent-to-program, has the most pain and the best founder fit.**
  - But it scores low on whitespace, reach and integration. That makes it a deep-tech bet, not a solo first sale.
- **W2, change impact, is the most open space.**
  - It is read-only, so it is easy to trial. Its budget owner is unclear.
- **W1, the current idea, is solid but crowded.**
  - It uses the least of Gawtam's physical AI depth.
- **W4, W6 and W7 are platform territory** for a solo founder.

**One engine, three moments:**
- **W2 (before the change):** what does it touch?
- **W5 (at the change):** does the new plan work?
- **W1 (after the change):** why did something drift?

All three need the same plant model, knowledge links and citations. Run as a loop, they become the brain. Hypothesis: start at one moment and expand along the loop.

---

## 7. Two company paths

| | Deep tech (venture-scale) | Capital-light (sell first) | Hybrid |
|---|---|---|---|
| **Thesis** | Build the hard core of the brain (intent-to-program plus verifier on world models) and raise on the demo | Sell a read-only wedge to engineers now; grow into the brain on data and trust | Sell W5 or W2 as software while building the W3 demo as the fundraising asset |
| **First wedge** | W3 + W5 | W2 or W5 (W1 as fallback) | W5 sold, W3 demoed |
| **Team** | A technical cofounder (ML and sim, or robot systems) plus 2–4 engineers early | Solo, with one design partner; cofounder later | Solo now; a cofounder by the raise |
| **Capital** | Pre-seed of about €1–3M for team, compute and a robot cell (est.) | Under about €50k: founder time, cloud, travel (est.) | Angels or grants, e.g. Swedish innovation grants (est., to verify) |
| **Robot or lab access** | Own cell, or a partner lab (university, research institute or integrator; to verify) | Customers' cells, read-only; sim | Lab access for the demo only |
| **First 12 months** | Door → hood across two vendors in sim, then on real robots; 2–3 design partners; raise | 10–20 interviews; 1–2 paid pilots; one repeatable outcome metric | One paid W5 or W2 pilot plus the sim demo; raise on both |
| **Proof point** | Generated programs pass verification and run on real robots for a new part, with no hand coding | A customer pays and renews for a measured outcome (e.g. hours saved per change) | Both |
| **Main risk** | Crowded and capital-hungry, against well-funded labs. Hard to raise as a part-time solo founder | The wedge is too small, turns into consultancy and never reaches the brain | Split focus |
| **Fit with today (part-time, solo, Stockholm)** | Low, until a cofounder joins and Gawtam goes full-time | High | Medium |

**Working view:** the hybrid looks right on paper. Decide on interview evidence, not on this table.

---

## 8. Design principles

**Kept from the current idea** (see `CLAUDE.md`):
- **Symptom ≠ root cause.** Classifiers emit symptoms; the reasoning step cites the cause.
- **Citation is the product.** Engineers, operators and auditors won't act on an uncited answer.
- **Reason from the signal.** No shortcuts through names. In the PoC, the fault injector is named like a production ECU.
- **On-prem or self-hosted** is likely mandatory because of IP.

**New, as hypotheses:**
- **Change is the unit of value.** Measure the brain by the time and risk each change takes.
- **Robots as tools.** Every asset exposes typed capabilities through an adapter. The brain reasons over capabilities, not vendors.
- **Planner and verifier stay separate.** The verifier must be able to say no, and must not share the planner's blind spots: use a different model, sim or rule set.
- **The brain is never in the safety loop.** Certified controllers and safety PLCs have the final say.
- **Learned at design time, deterministic at run time** for fixed-cycle work. Learned policies run online only where variability is the job, and under supervision.
- **Humanoids are just another vendor.** Design for today's mixed fleets.
- **People sign off on changes.** Every sign-off is cited and logged.

---

## 9. Experiments

| # | Experiment | Tests | Cost (est.) | Continue if… |
|---|---|---|---|---|
| E1 | **Interviews:** 10–15 manufacturing and NPI engineers, robot programmers and integrators, starting in Sweden. Ask about their last change: what it touched, how long it took, who did it, what broke. Guide: `Research/Interviews_Factory_Brain.md` | Where the pain sits (objection 7), the buyer (8), the integrators' role (9) | Time only | Changes cost days or more, recur often, and have an owner with budget |
| E2 | **Sim spike, door → hood:** two CAD parts; generate paint paths with an LLM plus a planner; check coverage and reach in sim; emit programs for two vendor languages; time it against a manual baseline | W3 feasibility; the DIY threat (10) | 2–3 weeks | Verifiable programs in hours, not days |
| E3 | **Change-impact spike:** an open ROS 2 / MoveIt cell with two different arms; apply a change (new part, moved fixture); the agent writes a cited impact report; compare it with an engineer's list | W2 | 1–2 weeks | The report catches what the engineer catches, and more |
| E4 | **Verifier spike:** an open VLA in sim (check licences); write requirements; the verifier runs scenarios and reports violations with citations. Reuses the PoC's classifier and citation pattern | W5 | 2–3 weeks | It finds real failures the policy's own evaluation misses |
| E5 | **DIY baseline:** give a frontier LLM the same inputs as E2 and E3, without the system | Objection 10 | Days | The gap is large and visible |
| E6 | **Targeted research** (this agent, when asked): verify the "(to verify)" claims and map who builds each layer | Sections 3–5 | Days | n/a |

---

## 10. Open questions

**For Gawtam:**
- Which industry anchors the vision: automotive (the door → hood example), high-mix low-volume, electronics, or still open?
- What year is the "futuristic factory"? That decides how much to bet on humanoids.
- Is a cofounder in the picture? The choice of path depends on it.
- What robot or lab access is there for demos (e.g. through KTH)?
- A neutral brain over other vendors' robots, or one that also provides the skills (its own VLA)?
- Does direction A (robot and vehicle testing) fold into W5, the verifier?
- What would bring direction B back, or fit the Hindustan Pencils lead into the factory brain story?

**For research** (when asked):
- What does a typical product change cost in robot reprogramming and commissioning time, by industry?
- How open are the main controllers to third-party program upload and command streaming?
- Who sells change-impact analysis today (PLM and simulation vendors)?
- Humanoids in factories: pilots or paid fleets? How many, and where?
- What will the EU Machinery Regulation and the AI Act require of AI that changes robot behaviour?
- Integrator economics: what share of a cell's cost is integration, and are integrators short of capacity?

---

## Sources

**Internal:**
- `CLAUDE.md` (product constraints)
- `SUMMARY.md` §4 (Gawtam's "doctor of agents" note)
- `Research/Academic_EPFL_IMOS.md` (the open PhD on trustworthy plant-operation agents)
- the founder's brainstorm answers, 28 Oct 2026

**External:** none yet. Every external claim above is from memory and marked "(to verify)".

---

## Change log

- 28 Oct 2026: created. A seeded draft from the founder's brainstorm answers; no web research.
- 28 Oct 2026: E1 now links to its interview guide, `Research/Interviews_Factory_Brain.md`.
