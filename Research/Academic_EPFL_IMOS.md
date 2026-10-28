# Academic: EPFL IMOS lab (Prof. Olga Fink)

**Date:** 27 Oct 2026 · **Purpose:** the technical state of the art in machine fault detection and diagnosis, and what it means for the product · **Status:** desk research; papers read at abstract level only

---

## TL;DR

- **Who:** the Intelligent Maintenance and Operations Systems (IMOS) lab at EPFL, led by Prof. Olga Fink since March 2022 (previously at ETH Zurich, 2018–2022). About 20 people: 2 postdocs and 10 PhD students ([lab people page](https://www.epfl.ch/labs/imos/people/)). It is one of the leading academic groups in prognostics and health management (PHM): fault detection, diagnosis and remaining-useful-life prediction.
- **Why it matters:** the lab works on exactly the hard parts the hackathon PDF left open:
  - Classifiers that don't need rebuilding for every machine (domain adaptation).
  - Learning from machines that have almost no recorded failures (unsupervised and contrastive health indicators, synthetic fault generation).
  - Estimating what you can't measure on old machines (virtual sensing).
  - Making diagnoses trustworthy (explainable AI, uncertainty).
- **Signal:** the lab is hiring a PhD student in "Trustworthy AI for Autonomous Plant Operations": AI agents that monitor plants, diagnose faults and recommend actions, with verifiable decisions ([open positions](https://www.epfl.ch/labs/imos/open-positions/)). Academia treats trustworthy diagnostic agents as an open problem. That supports the "citation is the product" thesis, and suggests nobody has solved it yet.
- **Gap:** I found no work from the lab on language models, capturing technicians' knowledge, or citing sources for a diagnosis. Their strength is the signal side; the product's proposed edge is the knowledge side.

---

## 1. Lab profile

| | |
|---|---|
| Lab | Intelligent Maintenance and Operations Systems (IMOS), EPFL, School of Architecture, Civil and Environmental Engineering ([lab page](https://www.epfl.ch/labs/imos)) |
| Head | Prof. Olga Fink. PHM Society Fellow, 2023 ([EPFL news](https://actu.epfl.ch/news/olga-fink-awarded-fellow-of-phm-society)) |
| Funding | ERC Consolidator Grant 2025 for HEROES, "Longevity-focused health management of complex engineered systems", about €2M over 5 years ([EPFL news](https://actu.epfl.ch/news/erc-consolidator-grants-awarded-to-five-epfl-aca-3), [ERC list](https://erc.europa.eu/system/files/2025-12/erc-2025-cog-results-all-domains.pdf)). Project details aren't public yet |
| Themes | Physics-informed deep learning; graph neural networks (GNNs); time-series analysis; transfer learning and domain adaptation; explainable AI; self-supervised learning; reinforcement learning and multi-agent systems |
| Teaching | CIVIL-426, Machine learning for predictive maintenance applications ([EPFL Moodle](https://moodle.epfl.ch/course/info.php?id=17052)) |
| Industry contact | Runs the Intelligent Maintenance Conference. Recent panels included SBB, SNCF, Alstom and CSEM ([IMC page](https://www.epfl.ch/labs/imos/8th-intelligent-maintenance-conference-workshop)). These are conference contacts, not confirmed projects |
| Open roles (Oct 2026) | PhD: Trustworthy AI for Autonomous Plant Operations. Postdoc: tabular foundation models for building energy systems, joint with EMPA |

---

## 2. Work most relevant to the product

| Work | What it does | Why it matters for us |
|---|---|---|
| **Controlled generation of unseen faults** (Rombach, Michau, Fink; *Reliability Engineering & System Safety* 230, 2023; [arXiv](https://arxiv.org/abs/2204.14068)) | Generates fault signatures for a new machine or operating condition, using only *healthy* data from that machine plus *faulty* data from another. Can control fault type and severity. Tested on two bearing datasets | Directly addresses the hackathon's "classifier scaling" question. A fault library from one plant might transfer to another plant's machines without waiting for them to fail. Unproven beyond bearings |
| **Unsupervised health indicators via contrastive learning** (Rombach, Michau, Fink et al.; [arXiv 2208.13288](https://arxiv.org/abs/2208.13288v2)) | Learns a health indicator without labels, using operating time as a stand-in for wear. Tested on real railway-wheel data and milling-tool wear | Legacy plants have few labelled failures. This lets a model learn "drifting from healthy" from normal operation alone |
| **Transfer learning across operating conditions** (Michau et al., *Knowledge-Based Systems*, 2021; the group's line of work, verify authorship) | Anomaly detection that transfers between complementary operating conditions | Pencil lines run different products and speeds. The model must not mistake a change of product for a fault |
| **Virtual sensing with GNNs** (PHME 2024 best paper, from the lab: real-time bearing load prediction) | Estimates quantities you can't measure directly from the sensors you have | 20-year-old machines have no built-in sensors. Infer more from a few cheap retrofit sensors |
| **Physics-informed GNNs** (e.g. Dynami-CAL GraphNet, which builds conservation laws into the model; [MPI talk](https://www.mpi-magdeburg.mpg.de/events/44561/2316)) | Models that obey physical laws, so they generalise with less data | Longer-term: more reliable models with little data. Further from a first product |
| **Test-time domain adaptation** ([alphaXiv profile](https://www.alphaxiv.org/@olga-fink)) | Models adapt to shifting data during use, without the original training data | Handles machines that age and drift after deployment, which old machines do |

---

## 3. What this means for the product

| Open question (hackathon PDF / pencil plant) | State of the art (this lab) | Implication |
|---|---|---|
| Classifier scaling: rebuilt per customer and per subsystem? | Domain adaptation and synthetic fault generation reduce per-machine labelling | Plausible to reuse fault knowledge across machines and plants. Test it, don't assume it |
| Few or no recorded failures on legacy machines | Unsupervised, contrastive health indicators trained on healthy data | Start with anomaly detection ("this isn't normal") before diagnosis ("this is bearing wear") |
| No sensors on old machines | Virtual sensing from a few sensors | Keep the retrofit cheap: 1–2 sensors per machine plus inference |
| Changing products and speeds | Transfer across operating conditions | Feed the operating mode (product, speed) to the model, or false alarms will kill trust |
| Trust: why should an engineer act on it? | Explainable AI; the open PhD on verifiable agent decisions | Still open in research. **Citations to past cases and to the person who fixed it** are a practical, product-level answer the lab isn't working on (as far as found) |
| Knowledge held by retiring staff | Not covered in what I found | Whitespace: combine signal-level methods with a captured-knowledge layer |

**Caveat:** academic results are mostly on benchmark bearing datasets and rail data. Expect a gap between paper accuracy and a dusty pencil factory.

---

## 4. How to use this

- **Reading list:** the unseen-faults paper and the contrastive health-indicator paper first. Both speak to the two biggest technical risks: classifier scaling and lack of failure labels.
- **Benchmarks:** test any classifier on public bearing datasets the lab uses before trying it on customer data.
- **Track:** the HEROES project and the open PhD topic, for where the field is heading on trustworthy diagnostic agents.

---

## Sources

[IMOS lab](https://www.epfl.ch/labs/imos) · [IMOS people](https://www.epfl.ch/labs/imos/people/) · [IMOS open positions](https://www.epfl.ch/labs/imos/open-positions/) · [PHM Society fellow](https://actu.epfl.ch/news/olga-fink-awarded-fellow-of-phm-society) · [ERC CoG news](https://actu.epfl.ch/news/erc-consolidator-grants-awarded-to-five-epfl-aca-3) · [ERC 2025 CoG list](https://erc.europa.eu/system/files/2025-12/erc-2025-cog-results-all-domains.pdf) · [IMC conference](https://www.epfl.ch/labs/imos/8th-intelligent-maintenance-conference-workshop) · [CIVIL-426](https://moodle.epfl.ch/course/info.php?id=17052) · [Unseen faults, arXiv 2204.14068](https://arxiv.org/abs/2204.14068) · [Contrastive health indicators, arXiv 2208.13288](https://arxiv.org/abs/2208.13288v2) · [MPI talk](https://www.mpi-magdeburg.mpg.de/events/44561/2316) · [alphaXiv profile](https://www.alphaxiv.org/@olga-fink)

---

## Change log

- 27 Oct 2026: created. Lab profile and relevant work, framed as technical state of the art.
