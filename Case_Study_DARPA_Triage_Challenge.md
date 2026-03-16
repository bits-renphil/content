# Case Study: The DARPA Triage Challenge — Designing a Grand Challenge for a Data-Scarce, Life-Critical Domain

---

## Overview

The DARPA Triage Challenge (DTC) is a three-year open competition launched in 2022, currently running through Fall 2026, that is attempting to do for mass casualty triage what the Grand Challenge did for autonomous vehicles: force a fragmented field to produce integrated, working systems under real-world conditions, while generating the data infrastructure and human capital network that the field has always lacked.

It is relevant to the BiTS community for a specific reason: **Commander Jean-Paul Chretien**, one of BiTS's co-directors and a former DARPA Program Manager in the Biological Technologies Office, was the original program manager for RITMO — the foundational data collection initiative that underpins the DTC. The DTC is, in part, his intellectual fingerprint. Understanding its design logic is a direct window into how an experienced ARPA PM thinks about challenge construction in a domain where the usual challenge prerequisites — abundant labeled training data, well-established evaluation protocols, a community of technical talent ready to engage — do not yet exist.

---

## The Problem the Challenge Was Designed to Solve

### Mass Casualty Incidents and the Triage Bottleneck

In mass casualty incidents (MCIs) — whether military engagements, terrorist attacks, natural disasters, or large-scale accidents — the central bottleneck is not treatment capability. It is identification: figuring out, faster than human assessment can accomplish, which casualties need immediate life-saving intervention and which can wait. The clinical term for this is triage, and it has been performed by human medics using visual assessment and basic vital signs since the Napoleonic Wars.

The problem with human triage under MCI conditions is well-documented. When the number of casualties exceeds the number of medics, assessments become rapid and error-prone. Critically injured casualties who appear stable can be misclassified. The casualties who appear most distressed are not always the ones whose lives are most immediately at risk. And in military contexts, the first medic on scene may be operating under fire, at night, in environments where physical access to casualties is itself dangerous.

The field has known this problem existed for decades. Progress had been slow for structural reasons that the DTC was specifically designed to address.

### The Three Structural Barriers

**First: fragmented, low-quality data.** Developing algorithms that can identify the physiological signatures of critical injury requires high-resolution, multimodal sensor data from real trauma patients in field conditions — not clean hospital records. This data is extraordinarily difficult to collect, proprietary to the institutions that hold it, and rarely labeled consistently across collection sites. No team trying to build a triage algorithm could access enough data to validate their approach.

**Second: no evaluation standard.** There was no agreed-upon protocol for testing whether a triage algorithm actually worked in a realistic scenario. Teams published results using incompatible metrics, on incompatible datasets, in incompatible environments. Progress was essentially unmeasurable at the field level.

**Third: disciplinary fragmentation.** The people best positioned to build triage algorithms — roboticists, sensor engineers, machine learning researchers — had little interaction with the clinicians and prehospital care providers who understood the domain. The domain experts had little interaction with the technology developers. Military medical research was largely siloed from academic research. No forcing function existed to bring these communities together around a shared concrete problem.

The DTC was designed to address all three simultaneously.

---

## Program Architecture

### RITMO: Building the Foundation Before the Competition

The first decision Chretien made was not to launch the competition directly. Before teams could compete on triage algorithms, the field needed the data those algorithms would require. He first designed RITMO — Research Infrastructure for Trauma with Medical Observations — as a pre-competition data collection program.

RITMO funded teams to instrument real trauma patients across the full care pathway: from field care through helicopter transport, trauma center reception, resuscitation, and stabilization. The sensor suite was comprehensive: continuous non-invasive vital signs, brain and tissue oxygenation, pupillometry, respiratory dynamics, advanced airway data, and in-flight video. The University of Maryland School of Medicine received up to $7.3 million for a 3.5-year RITMO award; the University of Pittsburgh contributed trauma transport data.

The RITMO output was a publicly accessible, standardized dataset that competition teams could use for algorithm development — the equivalent of a training corpus for the challenge's machine learning components.

This sequencing reflects a design principle visible across ARPA programs: **pull the prerequisite work to the front**. JoeAnna Arthur's UP TEMPO program used a "Phase Zero" concept for the same reason — she needed ground-truth team performance metrics before she could test team readiness sensors, and she built that infrastructure during the BAA period rather than leaving it to performers. Chretien applied the same logic at the field level: the competition infrastructure needed to exist before the competition could be meaningful.

### Competition Structure: Three Events, Increasing Complexity

The DTC runs as a three-year competition with annual events of escalating difficulty:

**Event 1 (September-October 2024, Guardian Centers, Perry, Georgia):** Teams competed in simulated mass casualty scenarios — airplane crashes, convoy ambushes — in which casualties with realistic injuries (moulage, simulated physiological data) were distributed across a mock environment. Teams deployed sensor platforms to detect, localize, and assess casualties without initial physical access.

**Event 2 (September-October 2025):** Scenarios incorporated degraded and obstructed environments — conditions where line-of-sight access to casualties was restricted, ambient noise and visual interference increased, and the physical challenges of sensor deployment were amplified.

**Event 3 (Fall 2026):** The most complex scenarios yet. The specific parameters for Event 3 were announced to registered teams in advance; the qualification deadline was February 5, 2026.

### Five Tracks

The competition runs five parallel tracks:

**Systems Competition — Real World:** Teams deploy physical systems (typically UAVs/drones and ground robots) in live scenarios. Sensors gather data; algorithms assess casualties in real time.

**Systems Competition — Virtual:** Teams compete in simulated environments using identical sensor modalities and scenario structures. Enables participation from teams without hardware development capacity.

**Data Competition:** Teams develop algorithms that perform secondary triage — predicting which casualties require specific life-saving interventions — using the RITMO dataset and standardized vital sign waveforms.

**Special Events:** Including medic collaboration events where human-machine teaming is evaluated.

This multi-track structure reflects a deliberate design choice: different communities have different strengths. Hardware teams and software teams have different barrier-to-entry profiles. Running real and virtual competitions in parallel maximizes the talent pool while ensuring that the highest-stakes evaluation happens against real physics.

### Prize Structure

Prize amounts for Event 2 included $300,000 for the Systems Real World winner, $150,000 for second place, and comparable amounts in the Data competition. Total DTC prize funding across the full three-year program has not been publicly disclosed in full, but the RITMO infrastructure investment alone was $7.3 million.

---

## Notable Results

### Event 1 (2024)

**DART** (Battelle's Drone-Assisted Rapid Triage) won the Systems Real World competition. **Coordinated Robotics** won both the Virtual and Data competitions.

The field's performance in Event 1 established baseline capability — how well existing approaches could detect, localize, and assess casualties in a structured scenario — and identified specific failure modes that teams could target for Event 2.

### Event 2 (2025)

**DART** retained the Systems Real World title. **MSAI** won the Data competition, and **Coordinated Robotics** placed second in the Systems Real World track. Notably, UAS-DTU (Delhi Technological University) placed second in the Real World competition — a non-US team demonstrating one of the open participation benefits: the challenge attracted international capability that a US government-directed program would not have prioritized.

The transition from Event 1 to Event 2 showed improvement across the field in the basic detection and localization tasks, while the more complex secondary triage prediction tasks — where algorithms need to identify which physiological waveform signatures predict need for transfusion, airway management, or other specific interventions — remained harder. This is precisely the kind of granular, public benchmark that the field had previously lacked.

---

## Program Design Lessons — Extracted

### 1. Infrastructure Investment Must Precede Competition

The DTC's most distinctive architectural choice was RITMO. Without RITMO, the competition would have been a demonstration of who could collect the best data under competition conditions — not a test of who had built the best algorithms. By publicly providing training data before competition launch, DARPA lowered the barrier to participation for pure software teams, attracted machine learning researchers who would otherwise have had no entry point, and ensured that teams with the best algorithms won rather than teams with the best data collection infrastructure.

This is a broadly applicable principle for challenges in data-scarce domains. A challenge that requires participants to build data collection capability as well as algorithmic capability is not testing the right thing — unless data collection is itself the capability you're trying to develop. In most domains, the appropriate challenge design separates infrastructure provision (the funder's job) from capability development (the competitor's job).

### 2. Multi-Track Design Maximizes Talent Coverage

The real-world, virtual, and data competition tracks are not redundant — they are complements. Real-world teams tend to be hardware-oriented, with systems integration expertise and field deployment experience. Data competition teams tend to be algorithmically sophisticated but lack hardware. Virtual teams may be in either category. Running all three in parallel means the competition captures the best of each community while creating natural collaboration incentives: real-world teams know that the winning data competition algorithm might make their system better; data teams know that real-world results will validate their approach.

This architecture echoes Brad Ringeisen's "parallel TAs beat serial programs" principle. If DARPA had run a sequential program — first the data collection, then the algorithm development, then the hardware deployment — the insights from each stage would flow only to the next team, not to the whole field. Running in parallel means the field learns everything simultaneously.

### 3. Scenarios Are Program Management Instruments

The scenario design choices — airplane crash, convoy ambush, degraded/obstructed environments — are not merely test cases. Each scenario tests a specific capability hypothesis. The shift from Event 1 to Event 2 scenarios (degraded environments, obstructed access) was a deliberate escalation designed to stress capabilities that performed adequately under favorable conditions. The willingness to design scenarios that most teams will partially fail at is what makes the competition informative.

This is the challenge-design equivalent of JoeAnna Arthur's "pull the hardest part to the front" principle. If the scenarios are too easy, you only learn that the hardest part was the scenario design, not the technology. Event 3's "most complex scenarios yet" structure maintains pressure on teams to continue developing rather than optimizing to a static evaluation target.

### 4. Biological and Medical Domains Require End-User Integration by Design

Renee Wegrzyn's addition to the Heilmeier Questions at ARPA-H — "How are you addressing customer experience and making sure end users are partners in program design?" — is essential in medical domains. The DTC's "special medic collaboration events" are not peripheral. They test the most important question about any triage technology: will a medic actually use it, trust its output, and integrate it into their decision-making under field conditions?

The failure mode in medical technology programs is almost always sociotechnical rather than purely technical. A triage algorithm that performs well against a benchmark dataset can still fail to improve outcomes if medics don't understand how to interpret its outputs, don't trust its confidence estimates, or find the physical hardware too cumbersome for field use. The DTC builds this test into the competition rather than deferring it to post-program transition.

### 5. Open Participation Finds Non-Obvious Expertise Clusters

The appearance of Delhi Technological University in the top rankings for Event 2 illustrates a consistent pattern across open competitions: the communities most capable of advancing a problem are not always in the places traditional funders look. DTU's performance reflected strong UAV and autonomy research capacity that DARPA would not have prioritized in a directed program. Open competitions find these capacity clusters passively — teams self-select in based on their own assessment of where their expertise applies.

SPRIND operates in a European context where cross-national talent mobilization is both possible and strategically valuable. A challenge that attracts top teams from universities across the EU — and potentially outside it — is doing field development that no single national program can replicate.

### 6. The Founding PM's Intellectual Fingerprint Persists

An underappreciated aspect of challenge design is that the founding program manager's choices — data infrastructure, track structure, scenario sequencing, evaluation metrics — set the field's agenda for years. The RITMO-first architecture was Chretien's decision. The five-track structure was established before his successor Col. Jeremy Pamplin took over as DTC program manager in 2025. The choices that shape what the field learns from the competition were made in the design phase, not the execution phase.

This means that challenge programs are high-leverage moments for program managers in a way that contracted programs are not. A contracted program has ongoing PM influence throughout its life. A challenge program has outsized PM influence at design time, and then runs largely on the infrastructure those early decisions created. The implication for SPRIND is that the design phase of a challenge program deserves proportionally more PM time and deliberation than the execution phase.

---

## Connections to the BiTS Curriculum

The DTC sits at the intersection of several frameworks the BiTS curriculum emphasizes:

**The "Why Now" question.** The convergence of high-quality drone sensor payloads, miniaturized vital sign monitors, and transformer-based anomaly detection algorithms made the DTC technically feasible in 2022 in a way it was not in 2012. Chretien's timing was not arbitrary — it reflected a genuine assessment that the enabling technologies had crossed a threshold.

**Transition as a design parameter.** The DTC's end-user was always the military medic and the civilian first responder, not an abstract "DoD customer." The medic collaboration events and the emphasis on stand-off and non-invasive sensor modalities reflect design choices made with deployment constraints in mind from the beginning, not retrofitted at the transition phase.

**Parallel TAs prevent single points of failure.** The five tracks mean no single technical failure — a hardware team that can't get their drone to function in degraded conditions, a data team whose algorithm overfits — kills the program's learning value. Something always advances.

**The champion hunt has a clinical dimension.** In medical technology programs, the physician-champion who will advocate for adoption within a clinical or military system is as important as the funder who will provide resources. The DTC's clinical track record from RITMO data collection — built before the competition — gives early clinical advocates something concrete to defend when acquisition conversations begin.

---

## Implications for the SPRIND Challenge Model

### Identify Your RITMO Equivalent

If SPRIND pursues a challenge in a data-scarce domain — clinical outcomes, industrial safety, ecological monitoring — the first question is whether the training data required for algorithmic competition exists at sufficient quality and accessibility. If it does not, the challenge program should begin with a RITMO-equivalent infrastructure investment, and the challenge design should separate data provision from algorithm development.

The cost of this step is real (RITMO was a $7.3M investment before the first competitive event). But a competition launched without it will produce one or two well-resourced teams that happen to have better data access, rather than a true field-wide benchmark.

### Build Multi-Track Structure Into the Initial Design

SPRIND challenges should run real-world, virtual, and algorithmic tracks simultaneously rather than sequentially. The communities that excel at each are different; reaching all of them requires parallel entry points. The virtual track in particular is valuable for attracting academic ML and AI researchers who would not otherwise engage with a hardware-heavy competition.

### Design Scenario Escalation as a Curriculum

The three-event, escalating-complexity structure of the DTC is not just a competitive format. It is a curriculum for the field — each event teaches the community what it doesn't yet know how to do, and the difficulty escalation directs where development effort should go next. SPRIND challenges should build scenario escalation ladders explicitly and publish them in advance, so teams can plan 18-month development arcs rather than optimizing to the next single event.

### Take the Sociotechnical Dimension Seriously From Day One

Any SPRIND challenge in a domain with human operators — clinical, manufacturing, infrastructure, public services — needs an end-user evaluation track built into the competition structure, not added later. The DTC's medic collaboration events cost DARPA coordination overhead but provide data that no algorithmic benchmark can capture. This is especially important for EU contexts where regulatory requirements and user adoption dynamics may be the binding constraint on technology deployment.

### Count Human Capital as a Primary Output

The DTC is creating a community of researchers with shared vocabulary, shared benchmark data, shared evaluation standards, and demonstrated track records against each other. SPRIND should track where DTC-model challenge alumni go — which ones found companies, which ones join procurement programs, which ones publish field-shaping papers — to capture the full value of the challenge investment. The $7 million RITMO investment should be evaluated not against the triage algorithms it produced but against the field infrastructure it created.

---

## Key Lessons in Summary

**Build infrastructure before competition.** In data-scarce domains, the single most valuable thing a challenge funder can do is create the training data and evaluation standards that let algorithmic teams compete on algorithm quality rather than data collection capacity.

**Multi-track maximizes field coverage.** Hardware teams, software teams, and pure algorithm developers are different communities with different barrier-to-entry profiles. Run tracks for all of them in parallel.

**Scenario design is program management.** The choice of what scenarios to run, in what order, at what complexity level, determines what the field learns from the competition. These choices should receive as much deliberate attention as prize structure and eligibility rules.

**End-user integration is non-negotiable in life-critical domains.** Competitions that only test technical performance miss the adoption question. Build user evaluation into the competition structure rather than deferring it to transition.

**The founding PM's design choices set the field's agenda.** Challenge programs have their highest-leverage PM moment at design time. More deliberation in the design phase produces better downstream outcomes than more oversight during execution.

---

*Sources: DARPA Triage Challenge official site (triagechallenge.darpa.mil); DARPA research program description; DARPA news releases on Event 1 and Event 2 results; University of Maryland School of Medicine RITMO award announcement; Carnegie Mellon / Pitt DTC participation coverage; TechBriefs "Inside DARPA's Push to Reinvent Battlefield Triage"; DARPA profile of Jeremy Pamplin.*
