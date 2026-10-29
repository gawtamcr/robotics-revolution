# Factory brain: interview guide (E1)

**Date:** 28 Oct 2026 · **Owner:** `factory-brain-strategist` · **Purpose:** run experiment E1 from `Research/Factory_Brain.md`. Learn what a real change on a robot line costs before building anything · **Status:** ready to use; 0 interviews done

---

## TL;DR

- **Goal:** find out where a change really hurts:
  - working out what it touches
  - writing the programs
  - proving it works
  - fixing what breaks after go-live
- **Who:** 10–15 people. Mostly manufacturing and NPI engineers, robot programmers and integrators; a few quality, safety or AI-robot people. Sweden first.
- **Method:** walk through **their last change**, step by step. Ask about past facts, not opinions about the future. Don't pitch.
- **Decision it feeds:**
  - which wedge to start with (W1, W2, W3 or W5)
  - which industry (high-volume or high-mix)
  - who pays
  - whether integrators are a channel, a customer or a competitor
- **Checkpoint:** pause after 5 interviews to check that the questions work. Decide after 10–15.

---

## 1. What we're testing

Each hypothesis links to an objection (§5) or a wedge (§6) in `Research/Factory_Brain.md`.

| # | Hypothesis | Links to | Confirms it | Kills it |
|---|---|---|---|---|
| H1 | Changes that touch robots are frequent and costly | Objection 7 | Monthly or more per line; days of skilled time each (est. thresholds) | Rare, or hours of work |
| H2 | The pain per change is bigger in high-mix plants than on high-volume automotive lines | Objection 7 | High-mix interviewees describe worse, more frequent changes | High-volume lines hurt as much, or more |
| H3 | Working out what a change touches is itself painful | W2 | Things broke after a change because an impact was missed | Impact is obvious, or a checklist covers it |
| H4 | Writing and touching up robot programs is the bottleneck | W3 | Programming dominates the timeline, or waiting for a programmer does | Programming is quick; other steps dominate |
| H5 | Proving a change is correct and safe before go-live is painful, and AI-made changes make it worse | W5 | Long acceptance tests, unclear sign-off, repeated validation; no way to trust AI output | Sign-off is routine and fast |
| H6 | Diagnosing drift after a change is painful | W1 | Weeks of teething problems; causes are found slowly | The line stabilises fast |
| H7 | Someone owns a budget for faster changes | Objection 8 | A named role with budget, and a cost they track | Cost is spread out, and nobody owns it |
| H8 | Integrators are short of capacity and would use tools that cut hours | Objection 9 | Turned-down projects, programmer shortage | They bill hours and would resist |
| H9 | Mixed-vendor fleets are normal today | Objection 6 | 2+ robot vendors plus AMRs and PLCs at one site | Single-vendor sites everywhere |
| H10 | Third-party software may read robot data; writing programs is restricted | Objection 2 | Read allowed; write needs sign-off or is blocked | Neither allowed, or both freely allowed |
| H11 | People already patch this themselves with LLMs or scripts | Objection 10 | Home-made tools exist, showing demand and a DIY threat | No one has tried |

---

## 2. Who to interview

| Role | Why | Target | Company type |
|---|---|---|---|
| Manufacturing, NPI or launch engineer (Swedish: *produktionstekniker*) | Owns the change end to end; may own a budget | 3–4 | Automotive and truck OEMs, tier-1 suppliers, industrial-equipment makers |
| Robot programmer or automation engineer (*robotprogrammerare*, *automationsingenjör*) | Does the hands-on work; knows what breaks | 3–4 | The same plants, ideally a high-mix one |
| System integrator: project lead or programmer (*systemintegratör*) | Programs most cells; channel, customer or competitor | 3–4 | Robot-cell integrators, small and mid-size |
| Quality, validation or safety lead | Owns the sign-off; the W5 buyer | 1–2 | OEMs or tier-1 suppliers |
| Team deploying humanoids or AI-driven robots | The future buyer of a verifier; tells us if humanoid timing is real | 1–2 | Robotics startups, or OEMs running pilots |

**Mix to aim for:**
- at least 3 high-volume and at least 3 high-mix sites
- at least 3 multi-vendor sites
- at least 2 integrators

**Candidate companies in Sweden** (from memory, all to verify; contact people by role, never cold-mass-mail):
- **Automotive and trucks:** Volvo Cars, Volvo Group, Scania
- **Industrial equipment:** Atlas Copco, Epiroc, Sandvik, SKF, Alfa Laval
- **Consumer goods:** Electrolux, Husqvarna
- **Robots:** ABB Robotics, Västerås (sees many customers' changes)
- **Integrators:** find through the robot makers' partner directories (ABB, FANUC, KUKA, Universal Robots)

**Where to find people:**
- Your own network: KTH and RPL alumni, IIT Madras alumni in Sweden.
- LinkedIn: search the Swedish titles above, and "NPI engineer", "launch engineer", "commissioning" (*driftsättning*).
- Robotics and automation clusters and events around Mälardalen and Gothenburg, e.g. Robotdalen (to verify).
- Ask every interviewee for two more names. Referrals are the main channel after the first 5.

### Outreach message

Keep it short. You're asking to learn, not to sell.

> Hi [name], I'm a robotics engineer (KTH) researching how factories handle changes on robot lines: a new part, a variant, a moved fixture. I'm not selling anything. I'd value 30 minutes to hear how your last change went: what it touched, how long it took, what broke. Happy to share what I learn across the interviews. Would [two time options] work?

---

## 3. Interview rules

- **Past, not future.** Ask "Last time, what did you do?", not "Would you use…?". Opinions about the future are cheap; past behaviour is evidence.
- **Get numbers:** hours, days, people, cost, how often.
- **Don't pitch.** Don't mention AI, the factory brain or any product until the last 3 minutes, and only if it helps.
- **Follow the pain.** When they sigh, laugh or swear, dig: "Tell me more about that."
- **Ask for artefacts:** a change order, a checklist, a sign-off form, a redacted program diff. Where they exist, the real process is written down.
- **Let silence work.** Don't fill pauses.
- **Length:** 30–40 minutes. Record only with consent; otherwise take notes.
- **Privacy:** in this repo, describe people by role and company type only. Keep names and contact details out of the markdown files.

---

## 4. Script

### Opening (2 min)
- Thank them. Say why: you're learning how changes on robot lines work, and you aren't selling anything.
- Ask whether you may take notes or record.

### Context (5 min)
1. What's your role? Which lines or cells are you responsible for?
2. What robots and automation do you have? How many robots, from which vendors? AMRs, PLCs, vision? Any humanoid or AI pilots?
3. How often do things change on your lines? What kinds of change: a new part or variant, model year, process, robot or tool swap, layout?

### The last change (15–20 min): the core
**"Walk me through the last change that touched your robots. Start from when you first heard about it."**

Let them tell the story, then probe each stage.

| Stage | Probes | Tests |
|---|---|---|
| **1. Trigger** | What changed and why? Who decided? What arrived: a change order, CAD, a spec, an email? | Context |
| **2. Impact** | How did you work out what it would touch? What did it touch (programs, grippers, fixtures, PLC logic, safety zones, AMR routes, vision, documents, training)? Did anything get missed? How did you find out? | H3 (W2) |
| **3. Doing it** | Who did the work: in-house, an integrator, the robot maker? Which tools: offline programming (RobotStudio, Process Simulate, RoboDK…) or teach pendant? How many people, for how many hours or days? What did you wait for? | H4 (W3), H8, H9 |
| **4. Proving it** | How did you show it was right and safe before production? Test parts, FAT/SAT (factory and site acceptance tests)? Who signed off, and what did they need to see? How long did that take? | H5 (W5) |
| **5. Go-live** | What broke in the first days or weeks? How did you find the cause? How long until the line was stable? | H6 (W1) |
| **6. Cost** | Total time from decision to stable production? Downtime, scrap, overtime? What did the integrator invoice? | H1, H7 |
| **7. Memory** | Where is this change recorded? Next time, will someone know what was done and why? | W1, W2 |

### Zoom out (5 min)
1. Was that change typical? Tell me about the worst change in the last year.
2. If you could delete one step of that process, which would it be?
3. What have you tried to make changes faster? Tools, templates, scripts, ChatGPT or another LLM? (H11)

### Money and access (5 min)
1. Whose budget pays for a change? Who would decide on a tool that made changes faster?
2. *(Plants)* What does an integrator charge for a typical change? *(Integrators)* How do you price changes? Are you short of programmers? Do you turn work down? (H8)
3. Could outside software read data from your robots and PLCs? Write programs to them? What would IT or security require: on-prem, cloud, approval? (H10)

### The future (3 min, last)
1. Any pilots of humanoids, or of AI that generates or runs robot motions?
2. Before you let an AI-generated program or a learned policy run on your line, what would you need to see? Who would sign it off? (H5)

### Close (2 min)
- What should I have asked but didn't?
- Who else should I talk to? Could you introduce me?
- May I follow up with one or two questions later?

### Add-ons by role
- **Integrators:**
  - What share of a cell project is programming and commissioning, compared with hardware? (est. check for objection 9)
  - Which vendors do you program most?
  - Do customers ask you for changes after handover? How do you charge for them?
- **Quality, validation or safety:**
  - Which standards do your sign-offs follow? What evidence counts?
  - What fails audits?
  - How do you validate software changes on robots today?
- **Humanoid or AI-robot teams:**
  - How do you prove to a customer that your robot will do the job reliably?
  - What do customers ask for before go-live?
  - Who tests your models, and against what?

---

## 5. Note template

Copy one block per interview into your private notes (outside the repo). Add only the anonymised log row in §6 here.

```
ID:              I01
Date:
Role:
Company type:    (e.g. truck OEM, tier-1 supplier, small integrator)
Industry:
Volume / mix:    high-volume | high-mix | both
Fleet:           robot vendors, # robots, AMRs, PLCs, humanoid/AI pilots

THE LAST CHANGE
Trigger:
What it touched:
Missed impacts:
Who did it:      in-house | integrator | OEM — # people
Tools:
Time:            hours/days per stage, total to stable production
How proven:      tests, FAT/SAT, who signed off
What broke:
Cost:            downtime, scrap, invoice
Where recorded:

PAIN BY STAGE (1 = fine, 5 = hurts; mark where they sighed)
Impact __ | Programming __ | Proving __ | Go-live/diagnosis __ | Memory __

Budget owner:
Integrator role: channel | customer | competitor
Access:          read? write? on-prem required?
DIY / tools tried:
Best quotes (verbatim, anonymised):

HYPOTHESES (+ supports, - weakens, ? unclear)
H1 _ H2 _ H3 _ H4 _ H5 _ H6 _ H7 _ H8 _ H9 _ H10 _ H11 _

Referrals:
Follow-up:
```

---

## 6. Interview log

Anonymised: role and company type only.

| ID | Date | Role | Company type | Mix | Vendors | Change type | Time to stable | Worst stage | Budget owner | Points to |
|---|---|---|---|---|---|---|---|---|---|---|
| I01 | | | | | | | | | | |
| I02 | | | | | | | | | | |
| I03 | | | | | | | | | | |
| I04 | | | | | | | | | | |
| I05 | | | | | | | | | | |

"Points to" is the wedge the interview supports most: W1, W2, W3, W5 or none.

---

## 7. Synthesis: how the answers change the plan

**After 5 interviews:**
- Check the questions. Are people telling real stories with numbers?
- Cut what doesn't work and sharpen the probes that produce sighs.

**After 10–15, decide:**

| Question | How to read the answers |
|---|---|
| **Is "change" the right thesis?** | Continue if changes cost days or more, recur often, and have an owner with budget (the E1 rule in `Factory_Brain.md`). If changes are rare or cheap everywhere, rethink the thesis before building |
| **Which wedge?** | Count the most painful stage across interviews: impact → W2; programming → W3; proving → W5; go-live diagnosis → W1 |
| **Which industry?** | Compare the high-volume and high-mix answers on frequency, time per change and who does the work |
| **Who pays?** | The role that owned the budget most often. If nobody owns it, objection 8 holds |
| **Integrators?** | If they're short of capacity: a channel or customer. If they're protective of billed hours: a competitor; sell to plants |
| **Access?** | If read is allowed and write is blocked, start read-only (W1, W2, W5) |
| **DIY threat?** | If people already use LLMs or scripts, note how far they get. That's the bar to beat |

**Then:**
- Ask `factory-brain-strategist` to update the scores in `Research/Factory_Brain.md`, mainly pain, willingness to pay, integration ease and reachability.
- Flag buyer findings to `icp-analyst`, and tools people name to `competitors-analyst`.

---

## Change log

- 28 Oct 2026: created. Interview guide for E1: hypotheses, targets, outreach, script, note template, log, synthesis rules. No research; company names to verify.
