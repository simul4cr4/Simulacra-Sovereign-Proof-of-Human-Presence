# Simulacra

*The simulacrum is a copy with no original. This paper proposes a way to define the original.*

---

## Abstract

**Simulacra** proposes an authentication primitive that proves a living human body was present during a bounded interval without exporting readable body-derived evidence or requiring institutional memory of the user. A body-worn device evaluates multi-domain sensor consistency inside a protected hardware boundary, accumulates continuity state that decays without ongoing evidence, and emits anonymous expiring claims. The architecture is designed to raise the cost of forgery from software replay to coordinated physical reality staging across multiple independent evidence domains, contingent on the three invariants holding in practice. Three invariants govern the design: raw evidence stays inside the boundary (secrecy), only the boundary advances state (integrity), and authority weakens with absence (progress). The primitive is narrow by design. It proves one thing only: human presence. Uniqueness, identity, and institutional trust are deliberately excluded. The primitive is stated precisely enough to critique, falsify, prototype, and improve.

---

## 1 Introduction

The cost of fabricating a convincing human presence online is approaching the cost of electricity. Autonomous agents already open accounts, post content, execute transactions, and hold conversations indistinguishable from the real thing. Every platform on earth will shortly face a choice it cannot defer. Mandate identity verification for every interaction, in which case the internet becomes a surveillance apparatus and anonymity dies. Or let the agents through, and accept that nothing online can be trusted as human-originated ever again. Surveillance internet or dead internet. The verification industry offers behavioral heuristics that AI erodes faster than they are patched. The identity industry offers biometric enrollment that converts the proof of humanity into a permanent record of the human. One fails on security. The other fails on sovereignty. Neither asks whether a third option exists.

The current proof-of-personhood field tends to collapse three questions into one:

1. **Is this a human?**
2. **Which human is it?**
3. **Can an institution remember that answer forever?**

The third question is where the trouble begins. Many existing systems answer the first by hardening the second and warehousing the result in a form that is persistent, linkable, or both. A registry knows your face. A social graph knows your neighbors. A ceremony knows where you stood. A biometric issuer knows the template even when it promises not to.

The contamination is easiest to see in concrete cases. When an iris is enrolled into a durable registry, the system does not merely answer whether a human appeared; it answers which human and stores the answer in a form designed to outlive the session. When a face video enters a persistent personhood registry, the registry learns a reusable representation even if the interface talks in the softer language of attestation or community vouching.

Put more bluntly: the field keeps smuggling surveillance in through the back door of verification.

A user climbs a stairwell, passes through a cold doorway, pauses at a locked entrance, and continues walking. A humane system could ask only whether one living continuity moved through that interval. Most deployed systems insist on asking who that continuity belongs to and whether the answer can be stored forever. The third question corrupts the first two.

That is the wrong compromise for a world in which synthetic activity is growing, identity systems are increasingly coercive, and many users need to prove humanness without consenting to durable disclosure.

The missing option is a different primitive entirely, not a better enrollment ceremony.

If proving humanness requires permanent custody of the proof, the proof has already been weaponized against the user. And if human presence can be authenticated without durable identity custody, platforms gain a third option between surveillance-backed verification and unverified synthetic chaos. This paper defines that primitive and states the conditions under which it could survive contact with the world.

---

## 2 The primitive

### 2.1 Definition

The primitive proposed here is:

> **anonymous, expiring, body-bound evidence of live embodied continuity, with no routine export of raw body-derived evidence**

A more operational restatement:

A body-adjacent sensing module, operating inside a protected hardware boundary, evaluates multi-domain bodily consistency over time. If that consistency is sufficient, it mints a narrow claim that a live human continuity was present during a bounded interval. The claim decays. It can be re-earned. It is not a durable identity.

The primitive proves less than "personhood" in the legal or philosophical sense. It proves less than "identity." It proves less than "uniqueness." It proves something narrower and, for the coming internet, potentially more useful: that a live embodied process remained physically coherent long enough to accumulate bounded authority without routinely exporting readable raw evidence to outside systems.

Scope exclusions are explicit: uniqueness, institutional trust, traffic analysis, and consciousness testing all fall outside the primitive. One human can wear multiple devices and accumulate multiple continuity states; optional anti-Sybil layers including proximity-based collision penalties can pressure that surface without collapsing into biometric deduplication (Section 9). The manufacturer remains in the trust path, and the political claim is narrower: that less of the body needs to be surrendered to institutions in order to demonstrate humanness. Decay limits durable credential accumulation but leaves real-time observation and verifier-side logging unaffected. Simulacra is deliberately silent on the moral status of digital entities that may reason or even suffer without possessing a body that can satisfy this primitive. The primitive protects a tributary, and embodied continuity deserves its own authentication path, one that allows digital entities to exist without exclusion as the price of human recognition.

### 2.2 The three-boundary invariant

Any realization of this primitive has to satisfy three boundaries. Violate any one of them and the system has become something else.

| Boundary | Requirement | What fails if it is violated |
|---|---|---|
| **Secrecy** | Raw body-derived evidence is not routinely exported in readable form outside the trusted boundary. | The system becomes another biometric custody apparatus. |
| **Integrity** | Only the protected boundary, in a known state, can advance continuity state or mint claims about it. | Claims become forgeable or contingent on untrusted software. |
| **Progress** | Authority must be meaningfully forward-evolving: earned by ongoing embodied evidence, weakened by absence, and not freely replayable. | The system collapses into a reusable token rather than a time-bound continuity primitive. |

Secrecy is an architectural requirement, not a guarantee. The protocol should never require raw evidence to leave the boundary, but a compromised manufacturer could still subvert that through firmware or provisioning. Integrity says trust stays where you declared it. It says nothing about whether the silicon can survive a bench attack. Progress says authority accumulates in ongoing body-worn time, which is something software alone cannot produce cheaply. It says nothing about whether a sophisticated attacker with physical access might find cheaper paths.

The simplest way to see why these matter: break secrecy and you have built a biometric warehouse. Break integrity and your claims are worth whatever the weakest link in the trust path is worth. Break progress and you have a reusable token. Most deployed proof-of-personhood systems have broken at least one. Many have broken all three.

### 2.3 Privacy as architecture

Simulacra is a privacy architecture designed to reduce the ordinary mechanisms by which authentication becomes coercive: body-derived evidence stays local and unreadable by default; biometric warehousing, global identity, persistent proof, and verifier memory of the body are all structurally absent, replaced by bounded claims that expire.

This falls short of total privacy. What it offers is authentication by local evidence custody and controlled disclosure rather than durable exposure.

---

## 3 Evidence-family architecture

The key question for any authentication architecture is what the attacker has to fake. If the answer is one signal, the attacker's job is bounded, and it gets cheaper every year as synthesis improves. If the answer is the coordinated physical behavior of a living body moving through a changing environment over real elapsed time, the job is categorically harder. That is what this section is about.

Simulacra decomposes the evidence for embodied continuity into four evidence families. Each derives from a different physical measurement domain. Each provides constraints the others cannot substitute for.

**Body-coupled evidence** comes from the organism itself: pulse timing, motion, posture change, contact impedance. It answers whether a living body is producing this signal.

**World-coupled evidence** comes from the environment interacting with that body: pressure shifting across altitude, light changing through a doorway, temperature dropping in a stairwell. It answers whether this body is moving through a real, changing world or through a recording.

**Time/progression evidence** comes from the passage of real time: oscillator drift, session continuity, external time references, decay. It answers whether this continuity is unfolding at the speed of lived experience or has been compressed, frozen, or rewound.

**Secure-state evidence** comes from the protected device itself: monotonic counters, ratchets, sealed logs, bounded presentation state. It answers whether this continuity has advanced honestly or has been branched, cloned, or rolled back.

The first three produce physical evidence. The fourth makes that evidence trustworthy over time. This decomposition is the paper's current explanatory frame, not a permanent partition.

The contribution is what happens when these families are required to agree.

### 3.1 Cross-licensing and analytical redundancy

No single family is sacred. The power comes from **cross-licensing**: a forged body family should have to survive the world family; a forged world family should have to survive elapsed-time and secure-state checks; a cloned state should have to survive disagreement with the lived world and the body that is supposedly carrying it. This is why Simulacra should be read less as a biometric classifier and more as a privacy-preserving instrument cluster.

The closer engineering ancestry is **analytical redundancy** in the Willsky 1976 and Chow-Willsky 1984 sense [21, 22], not biometric enrollment: heterogeneous sensors can constrain one another because the world itself supplies expected relationships and exposes residuals when those relationships break.

Simulacra does not need aerospace-grade sensors to borrow that logic. It needs evidence-family diversity. Independence here is in the physics (different laws governing different measurements), not merely in the geography of sensor placement. A second accelerometer on the same board may still help, but it does not buy the same attacker-cost increase as a pressure trace, an oscillator check, or an externally observed timing context governed by different physical or protocol rules. Agreement raises confidence. Disagreement is not just noise; it is information.

The stronger claim is therefore not "more sensors mean more security." It is this: **each additional independent physical domain can raise fabrication cost if it adds a meaningful constraint that must agree with the others.**

### 3.2 Attack economics of cross-domain coherence

The architecture does not claim that forgery is impossible. It claims that forgery becomes a different kind of problem.

An attacker who can synthesize a plausible heartbeat (and BioForge shows that cross-modal cardiac synthesis is real [8]) still has to stage the pressure change, the motion trajectory, the thermal transition, and the elapsed time that would accompany that heartbeat in the physical world. The current scoring package (Section 7.2) concretely exercises body×world and body×body pairings; thermal and elapsed-time cross-checks remain architectural targets, not currently scored constraints. But the argument holds for whatever subset is active: BioForge's published CycleGAN operates within cardiovascular families; it has not demonstrated cross-domain synthesis from cardiac signals to inertial measurement unit (IMU) or barometric traces, though future generative work may attempt that bridge. The architecture bets on this gap: physically dissimilar evidence families should be harder to forge jointly than any single biological channel.

The attacker must stage this coherence continuously, not once. Under a sync design with unpredictable challenge selection (Section 6.4, construction still open), they must do it without knowing which committed relationship will be tested. And they must do it at scale if they want to maintain more than one live credential. Each additional independent evidence family raises the cost of coherent fabrication, not because any single domain is unspoofable, but because jointly satisfying multiple independent physical constraints in real time is fundamentally more expensive than replaying a packet.

The system does not claim impossibility against a state-level adversary with physical laboratory access. If the three boundaries hold and the sync boundary achieves genuinely unpredictable challenge selection, the cheapest successful attack should move from "laptop running a replay script" to "physical laboratory staging coordinated multi-domain reality." That cost shift is the security hypothesis.

One implication should be stated directly. The same cross-modal coupling that makes the architecture work is the coupling an attacker will eventually learn to model. BioForge already bridges within the cardiovascular family. Future generative work will attempt broader bridges. The defense rests on the difficulty of jointly synthesizing coupling across physically dissimilar domains, not on the secrecy of the coupling itself. Coupling across such domains is harder to synthesize jointly, harder still to sustain over time, and hardest of all under a sync design where the scoring challenge is not known in advance (Section 6.4, construction still open). The architecture survives not by hiding the physics but by requiring more of it than a generator can cheaply produce. If that requirement ceases to hold, falsification condition F7 (Section 8.3) has been met, and the scoring package must be rebuilt.

### 3.3 Motion artifact as evidence

In much of the photoplethysmography (PPG) literature, accelerometer-coupled motion artifact is treated as contamination to remove. Asada et al. [32] introduced adaptive noise cancellation using collocated MEMS accelerometers as noise references for motion-tolerant wearable PPG. Kim and Yoo [33] applied independent component analysis to separate the motion component from the cardiac signal. These represent a broader literature in which the accelerometer-PPG coupling is consistently characterized as a corruption mechanism to be filtered, cancelled, or decomposed away. From the perspective of identity-free embodied continuity, that "contamination" may also be evidence. It is a sign that two domains are reacting to the same moving body at the same time. No group in the surveyed literature has proposed scoring that coupling as same-body evidence rather than removing it.

That does not make the signal secure by itself. It does make it worth scoring rather than merely denoising.

---

## 4 Prior art and the novelty perimeter

### 4.1 Same-body sensing and continuous wearable authentication

Foundational same-body work showed that accelerometer coherence can distinguish whether two devices are on the same body rather than merely near each other. Lester et al. [3] produced a striking early result, but under a tiny and highly constrained same-placement setup; that result should never be quoted without the caveat attached. Cornelius and Kotz [4] pushed the problem into more realistic cross-position settings and obtained lower, more honest performance. ZEBRA [5] and adjacent continuous-authentication systems then showed that same-body and same-user inference can be maintained over time rather than only at login. Pistis [17] addressed the complementary problem of replay and liveness in gait-based wearable authentication using vibration, which matters here because any continuous body-worn system must eventually answer not just "is this the same body?" but "is this body live and present right now?"

Cornelius et al. [27, 34] demonstrated that bioimpedance can passively recognize the wearer of a device, progressing from household-scale recognition [27] to 98\% balanced accuracy on day-long data from 8 subjects [34]. That work is the closest published ancestor to Simulacra's body-coupled evidence family, and the distinction is instructive: it answers *who is wearing this device*, while Simulacra deliberately refuses to ask that question.

Fusion-ID [9] used wrist-worn PPG plus motion sensors in a 247-user biometric-authentication study, which is precisely why it must be treated as adjacent rather than identical prior art. Liu et al.'s 2026 PPGTransID preprint [7] extends the cross-device story by asking whether physiological signals can transfer authentication status between a phone and nearby wearables. It is promising, recent, and still too pre-publication to carry more argumentative weight than the evidence supports.

This lineage proves that body-worn cross-sensor consistency is real and clarifies what Simulacra is not doing. Those systems predominantly answer some version of: *is this the enrolled user?* Simulacra asks a different question: *can a live human continuity be established and refreshed without default identity disclosure?*

### 4.2 Personhood credentials and anti-Sybil systems

The 2024 *Personhood Credentials* paper [1] is the best current systems map of the field. It surveys the dominant approaches (social graph, general-hardware biometric, specialized biometric hardware, and institution-mediated issuance) and exposes the tradeoffs those systems accept. Buterin's earlier analysis [2] maps the same terrain from a different angle, weighing biometric and social-graph systems against each other and concluding that no ideal form exists.

Eden [10] uses external observation and on-chain analysis to produce a personhood score. Its logic is explicitly anti-Sybil and explicitly identity adjacent.

IOST's PayPIN / Signet Ring [11] is a public wearable precedent with published documentation. Its own materials describe secure elements, heartbeat-based proofs, continuous verification, and a financialized identity-payment stack. The contrast is architectural: IOST couples physical presence to a persistent wallet and incentive layer. Simulacra aims for the opposite: narrow, expiring, default-anonymous claims.

Buterin's June 2025 post on ZK-wrapped digital identity [29] argues that zero-knowledge wrapping alone does not eliminate the coercion and correlation risks of one-person-one-credential systems, and proposes pluralistic identity structures instead. Simulacra's continuous, expiring, non-unique primitive is compatible with that pluralistic direction: it provides a humanity signal without requiring the single-identity binding that Buterin identifies as the core risk.

### 4.3 The composition claim

The novelty claim must be narrow enough to survive a hostile reader.

Every component here exists independently. Wearables exist. PPG-motion fusion exists. Hardware authentication exists. Bot detection is a multi-billion dollar industry running on heuristics that weaken by the quarter. The novelty concerns composition, not ingredients:

> **Within the literature cited here, there is no peer-reviewed system that combines continuous body-worn evidence, local protected-boundary evaluation, and anonymous expiring humanity claims while explicitly refusing to collapse that primitive into durable identity or global uniqueness.**

That is the perimeter. Stronger claims are unnecessary.

---

## 5 Evidence base

The question underneath the architecture is simple enough to say in one sentence: **does reality agree with itself?**

Simulacra does not ask one biometric to answer that question alone. It asks multiple partially independent evidence families (Section 3) to answer it together. The architecture succeeds to the extent that forgery stops being a cheap software exercise and becomes a problem of staging coherent reality across more than one domain at once.

### 5.1 Same-body, colocation, and the larger question

The key physical distinction is not mere colocation.

Two devices in the same room experience the same Wi-Fi environment, similar temperature, and similar radio conditions. Those are colocation signals.

Two sensors on the same living body experience something stricter: a coupled physical process whose domains are related but not identical. Acceleration, pressure change, pulse timing, motion artifact, contact quality, posture change, and environmental transition are not redundant copies of the same number. They are consequences of one body moving through one environment under one temporal progression.

A concrete interval makes the point better than abstraction. A wearer climbs a short stairwell, pushes through a doorway into colder air, pauses, then walks on. The IMU sees vertical motion and gait change. The barometer sees pressure shift. Light and temperature change across the threshold. PPG reflects exertion rising and then settling. The local state machine records an interval that cannot be advanced for free. None of those signals is decisive alone. Their agreement is the signal.

### 5.2 Current evidence perimeter

The literature currently supports four lower-level claims.

**First**, same-body accelerometer correlation is real. Lester [3] and Cornelius/Kotz [4] jointly establish that coherence between motion streams can discriminate same-body from different-body situations, although the best numbers live under constrained conditions and must not be inflated.

**Second**, large-scale cross-modal wearable alignment is real enough to matter. Apple's accelerometry-distillation work [6] reports strong alignment between accelerometry and PPG representations using approximately 20 million minutes of data from approximately 172,000 participants, including 99.2% top-1 retrieval of PPG embeddings from accelerometry embeddings. That is powerful evidence that motion and cardiovascular traces share structured latent information at scale. It is evidence of coupling, not proof of same-body authentication security.

**Third**, cross-device cardiac consistency is plausible enough to warrant serious attention. Liu et al.'s 2026 PPGTransID preprint [7], submitted to the Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies (IMWUT), reports 95.5% balanced accuracy in a 33-participant study for transferring authentication status between a phone's remote PPG signal and nearby wearable PPG sensors. That is strong enough to support same-body transfer plausibility. It is not enough to carry anonymity, issuer trust, or full primitive viability.

**Fourth**, cardiovascular biosignals are copyable. BioForge [8] demonstrates that an attacker who observes one cardiac modality can synthesize another strongly enough to fool multiple authentication systems, many of them more than 50% of the time in 10 or fewer attempts. That matters because it destroys any lazy argument that "the body is secret." The body is an open channel. Security has to come from requiring joint consistency under bounded trust, earned through architecture rather than assumed from physiology.

The literature does not yet establish the main security claim this paper needs: that multi-domain coherence, scored over time on body-worn hardware, is robust against adversaries who can jointly fabricate or replay multiple channels while targeting the exact features the system uses. The present evidence is strongest in the body family, prototype-thin in the world family, and still mostly candidate logic in the time/progression and secure-state families. The current scoring package should be treated as the **minimum viable cluster**, not the ceiling of the design.

| Evidence source | What it supports | What it does **not** support |
|---|---|---|
| Lester / Cornelius-Kotz [3, 4] | same-body motion discrimination under specific placements and activities | universal same-body performance, sedentary validity, or adversarial robustness |
| Apple accelerometry-distillation work [6] | large-scale cross-modal coupling and representation alignment | same-body authentication security or claim object design |
| PPGTransID [7] | physiological consistency across devices/positions may be useful | anonymity, issuer trust, or full primitive viability |
| BioForge [8] | biosignal spoofing is real and multi-modal threat models must be taken seriously | that Simulacra is broken; it instead raises the bar on what must be tested |

---

## 6 Realization

### 6.1 Why band-first

The current strongest hypothesis is a **band-class trust anchor** worn on the body.

The band is a working hypothesis, chosen as the best current compromise among sensor surface, power budget, wear time, mechanical stability, and the possibility of tightly controlling ingress and computation inside one body-adjacent boundary.

A ring may be more socially acceptable in some contexts and less stable in others. A chest strap may give better signal quality and worse daily adoption. A hardened smartwatch may offer convenience at the cost of inheriting platform assumptions.

### 6.2 Trust distribution

The band is the trust anchor. Companion devices are not.

A phone can provide networking, UI, challenge relay, wallet functions, or public-key custody. A watch can provide auxiliary corroboration. Neither should be treated as the moral or technical center of the system. If they are compromised, the design should degrade but not silently invert itself.

The **band owns the body-coupled and secure-state evidence families**, while companions may contribute auxiliary testimony to the **world-coupled** and **time/progression families**. A phone can report network time, radio context, or displacement deltas. A watch can report environmental conditions or co-wear anomalies. The point is not to trust those sources blindly. The point is to ask whether their testimony remains consistent with the band's own instruments.

At sync, a companion may provide the latest public beacon value it observed, its current network or cell-derived time, and, when available, a coarse displacement or environmental report since the previous sync. The band compares that testimony against its own oscillator state, inertial estimate, and world-family traces. Consistency can add time or world confidence. Inconsistency can discount or ignore the companion entirely. The companion never learns family-level summaries, continuity state, or the result of the comparison.

### 6.3 Compatibility without capitulation

Interoperability with legacy systems is not the same thing as submission to them.

A future Simulacra device may need to speak to iOS or Android, may need to present to web services, and may need to fit inside current relying-party systems. None of that requires treating Apple, Google, carrier public-key infrastructure (PKI), or vendor trusted execution environments (TEEs) as the moral center of the design. The right design stance is: compatible where useful, dependent only where unavoidable, and architecturally pointed toward less custody, less persistence, and less central memory over time.

Operationally, that means a future band may speak ordinary transport layers such as Bluetooth Low Energy (BLE) and present proofs through standard verifier-facing channels, including CTAP-style roaming-authenticator bindings [25] where they are useful, while the phone remains only a relay, display, challenge broker, or reporting source. The phone may carry packets, contribute time or world testimony, and help route challenges. It must not become the place where continuity state lives or where the decisive signing authority quietly migrates.

### 6.4 The sync boundary

The four evidence families are not yet a protocol. They become a protocol only when the scoring paths are specified (Section 7) and when the paper states **where** provisional local continuity state is tested, ratcheted, and made claimable.

The strongest current candidate is a **hybrid sync boundary**. The band accumulates sealed provisional continuity state locally. That state can include family-level summaries, residuals, and modality-specific provisional outputs from any measurement channel, whether body-coupled, world-coupled, temporal, or secure-state in nature. No single channel proves much on its own. The question is whether committed provisional outputs can later remain mutually consistent.

The architectural principle is that broad score advancement should depend on the intersection of **sealed local evidence** and **unpredictable external context**. The context might come from a distributed randomness beacon [23, 24], an append-only public log, a committee-issued challenge family, or a hybrid that mixes global public input with device-local derivation. The paper does not choose an implementation. It names the required properties: the context should be public enough to verify, unpredictable enough to prevent perfect precomputation, forward-moving enough to ground progress, and difficult for any single party to bias without detection.

This changes the attacker's position. A compromised phone or watch may relay packets, falsify companion testimony, or try to shape the sync surface. It still does not get to read the band's sealed evidence directly. If the challenge space is not known in advance, then fabrication becomes partly blind: the attacker must stage coherence across evidence families without knowing exactly which committed relation will be opened or tested at sync.

The sync boundary can unify three functions that might otherwise be treated separately: **secure progress**, **checkpointing**, and **claim issuance**. A successful sync can ratchet freshness, confirm that continuity state was not silently rewound, and mint a new bounded claim. A failed sync can force decay, loss, or probation for the disputed epoch. The sync event itself is also a privacy risk: BLE advertising payloads and MAC addresses change asynchronously, enabling passive tracking across address rotations [28], and checkpoint timing can become a stable correlation surface between issuance and presentation. Any eventual protocol must treat the companion communication channel as observable to surveillance and constrain sync-event metadata accordingly.

#### 6.4.1 One epoch, in order

A coherent epoch looks like this. Sensors sample continuously. Over a bounded window, each active measurement channel produces an **atomic modality yield**: the irreducible provisional output of a single sensing modality over one epoch window. The barometer's pressure summary is one atomic modality yield. The IMU's motion summary is another. The PPG's optical summary is another. Evidence families are the higher-order groupings (body-coupled, world-coupled, temporal, secure-state) within which those modality-level outputs are interpreted and cross-licensed. Each atomic modality yield is domain-specific, bounded in time, and insufficient on its own. Nothing in the scoring architecture works without her. Atomic modality yields feed scoring paths. Scoring paths update the local continuity state. The sync boundary tests that state against external context. Only then can claim eligibility advance. Atomic modality yields do not become public claims. They exist only long enough to be cross-licensed against one another through the scoring checks and then to update the band's provisional local continuity state through the decay-aware accumulation rule. Raw evidence is purged after summarization.

Periodically, the band commits to the current epoch state. That commitment may be computed over raw windows, extracted features, rolling digests, or some more careful hybrid; the present paper leaves that choice open. What matters at this stage is that the band can carry provisional continuity forward without routinely exporting readable raw evidence.

At sync, the band encounters forward-moving external context. A companion may relay that context and offer its own statements, but the companion does not decide the result. The band checks whether the committed local state remains consistent with the new context and with any companion testimony it chooses to consider. If the check succeeds, the continuity state ratchets forward and bounded claim eligibility may advance. If the check fails, the disputed epoch decays, is discounted, or is placed under a stricter penalty regime. If sync does not happen, the band may continue to accumulate state locally, but broader claim issuance remains gated by the missing checkpoint.

Without a lifecycle like this, the evidence families remain a taxonomy rather than a system.

### 6.5 Claim surfaces

The primitive can support several **claim modes** without changing the underlying invariant.

**Mode 1: Anonymous verification.** A relying party learns only that sufficient embodied continuity was present during a bounded interval and that the proof is fresh enough for the context. In the strongest current reading of this mode, bounded anonymous presentation is baseline: some ARC-like or equivalent mechanism [12, 13, 14] must prevent a single freshly minted proof from being replayed or spent without limit even before any higher anti-Sybil overlay is considered.

**Mode 2: Relying-party-scoped continuity.** A relying party can re-encounter the same pseudonymous continuity without learning who the user is globally. This proves same-key-plus-fresh-evidence, not biological identity. The relying party knows the same pseudonymous continuity returned with fresh evidence. It does not know whose body produced it.

**Mode 3: Public commitment.** A user may choose to attach ongoing embodied continuity to a public persona. This is the least private mode and should not be the default assumption of the architecture.

Mode 1 is the design center, and stronger linkage belongs only as explicit opt-in layers. These modes are political positions about how much a user discloses, not product tiers in a pricing table.

### 6.6 Two realization families

The same primitive can be realized under two different trust philosophies.

**Realization A: boundary-trusted scoring.** Sensor data stays local to the band. The band scores coherence internally and emits narrow claims. This is the buildable baseline. Its trustworthiness depends on the boundary, firmware integrity, and the physical limits of the hardware.

**Realization B: externally verifiable scoring.** Parts of the computation become cryptographically auditable outside the device. This is attractive in principle and significantly less mature in practice.

This draft treats Realization A as the baseline and Realization B as a frontier, not a promise.

---

## 7 Provisional state and scoring

### 7.1 Impermanence as security economics

Decay is part of the security economics, not an implementation detail.

A continuity state that never weakens becomes a durable identity. A continuity state that must be renewed by ongoing embodied evidence remains closer to a session than a passport.

The design therefore uses a leaky accumulation model:

$$
\mathrm{score}_{t+1}=\alpha\cdot\mathrm{score}_t+(1-\alpha)\cdot g(\mathrm{consistency}(W_t))
$$

where $W_t$ is the current evidence window, $g$ maps consistency into a bounded contribution, and $\alpha$ controls the decay rate.

The exact half-life is a deployment parameter. A short half-life increases the cost of maintaining many live credentials. A long half-life increases convenience and decreases anti-Sybil pressure. **Decay is a tradeoff surface, not a moral absolute.**

Claim eligibility requires crossing a minimum viable score:

$$
\mathrm{score}_t \geq A, \quad A \geq 0
$$

where $A$ is a deployment parameter, not a protocol constant. The constraint $A \geq 0$ is structural: negative thresholds are meaningless. At $A = 0$ the system imposes no accumulation requirement; accumulation alone no longer constrains claim eligibility. Practical deployments that require embodied evidence choose $A > 0$. At $A > 0$, the interaction of $A$ with $\alpha$ and the epoch interval determines the **rebuild window**: the time a new or reset device must be continuously worn before claims become mintable.

When the device is removed or no body is present, the consistency contribution drops to zero and the score reduces to pure exponential decay:

$$
\mathrm{score}_{t+n}=\alpha^n\cdot\mathrm{score}_t
$$

This decay is steep. At representative parameters ($\alpha \approx 0.99$, epoch interval $\approx 30$ minutes), one day of absence costs roughly 38\% of accumulated score. Three days costs roughly 77\%. A week of non-wear reduces the score to below 4\% of its peak regardless of prior history. There is no reservoir of stored authority. Accumulated authority decays exponentially without evidence.

Sync amplifies the pressure. The sync boundary gates broader claim advancement, so a device that is worn but never syncs accumulates local state that cannot be spent. A device that syncs but is not worn has nothing to spend. Maintaining a live credential requires both: continuous body-worn evidence production and periodic sync against external context. Pure score accumulation converges within days at $\alpha = 0.99$. But claim eligibility depends on more than raw score. The sync boundary must be cleared, challenges must be met, and failed or missing syncs can impose penalties or probation. The effective rebuild window, the time from a cold start to mintable claims, is a function of the accumulation rate, the sync cadence, and the threshold $A$. A representative design target places the effective rebuild window at approximately 27 days, less than one full month. This figure is not derivable from the accumulator equation alone; it reflects the combined effect of score accumulation, sync cadence, missed-sync penalties, and threshold selection. It is long enough that maintaining multiple live credentials is expensive in body-worn time, short enough that device loss or replacement does not permanently exclude a legitimate user. A higher threshold increases Sybil cost but also increases recovery time. That tradeoff is a deployment decision, not a protocol constant. The representative wearing pattern is waking hours, not 24/7. Eight hours of sleep costs roughly 15\% of accumulated score at $\alpha = 0.99$. For a wearer already above threshold $A$, this overnight loss will often leave the score above the claim boundary; it does not reset the credential.

The base primitive does not enforce one-credential-per-body. One human can wear multiple bands and accumulate multiple continuity states; this is the explicit price of refusing biometric deduplication (Section 2.1). What the base primitive does enforce is that each credential costs body-worn time to build and maintain. The stronger claim, that $k$ credentials require $k$ separate bodies, holds only when optional anti-Sybil overlays such as co-wear penalties or encounter-based friction are active (Section 9). Without those overlays, a single body can farm multiple credentials in parallel at the cost of multiplied hardware, device-hours, and sync overhead. With them, the cost becomes physical and multiplicative.

The local continuity state authorizes claim issuance but never becomes the claim object. No raw state information leaves the protected boundary during presentation. The continuity state is the engine; the claim is the exhaust.

### 7.2 Scoring paths

The current scoring package is **designed and preliminarily tested on proxy data, not validated under the project's own hardware or adversarial conditions**. It is the **minimum viable scoring package**, not the ceiling of the architecture. Its job is to make the first experiments legible. No parameter in this section has been tuned against data. The formulas exist to make the hypotheses specific enough to test and falsify. Each scoring path asks whether two provisional outputs agree. S1 pairs outputs from different evidence families (body × world). S2 and S3 pair distinct modalities within the body family, where agreement across different physical transduction pathways is still informative even without cross-family diversity. The evaluator does not ask one channel to settle the matter. It asks whether multiple atomic modality yields remain mutually consistent enough to advance the provisional continuity state.

| Candidate | Sensor domains | Intended regime | Concrete statistic | Plausible default window | Current status |
|---|---|---|---|---|---|
| **S1** | IMU + barometer | active vertical motion | windowed cross-correlation between altitude change and integrated vertical acceleration | 10-30 s on stairs / distinct elevation changes; up to 60 s in mixed walking | prototype-grade hypothesis |
| **S2** | IMU + PPG | active movement and motion-artifact regimes | magnitude-squared coherence between optical and inertial streams over candidate motion/cardiac bands | 8-20 s during active motion; 30-60 s under weaker movement | prototype-grade hypothesis |
| **S3** | optical + mechanical cardiac timing (PPG + micro-motion / BCG-like timing) | sedentary or low-motion fallback | correlation or agreement between inter-beat interval sequences from optical and mechanical traces | 30-120 s, likely longer than S1/S2 because of lower signal-to-noise | open and weakest current pathway |

For **S1**, one natural statistic is

$$
\rho_{ah}(\tau)=\operatorname{corr}\!\left(\Delta h(t),\int a_z(t-\tau)\,dt\right)
$$

computed over a bounded window and summarized over small lags $\tau$. Here $\Delta h(t)$ is first-differenced barometric altitude and $a_z(t)$ is vertical acceleration after frame alignment.

For **S2**, one natural statistic is band-limited magnitude-squared coherence

$$
C_{xa}(f)=\frac{|S_{xa}(f)|^2}{S_{xx}(f)S_{aa}(f)}
$$

where $x$ is the optical stream and $a$ is the inertial stream. A practical implementation could aggregate coherence over candidate cardiac bands (roughly $0.7-3$ Hz) and motion-artifact or movement sidebands (roughly $2.5-8$ Hz), while treating those band choices as tunable rather than canon.

For **S3**, the simplest candidate is agreement between beat-to-beat interval sequences inferred through two pathways,

$$
\rho_{IBI}=\operatorname{corr}(IBI_{PPG}, IBI_{mech})
$$

possibly augmented by lag consistency, beat-detection agreement, or short-window timing residuals. S3 is the weakest current pathway precisely because extracting stable mechanical cardiac timing at the wrist under real-world low-motion conditions remains hard.

Preliminary S2 testing on public datasets (WESAD, N=15; PPG-DaLiA, N=15) shows that single-window magnitude-squared coherence produces modest but consistent same-body versus different-body separation in both cardiac and motion bands. Sequential accumulation over 20 windows lifts discrimination substantially. Full methods, effect sizes, and caveats are reported in the companion empirical note [31].

These sketches do not make the package validated. They make it specific enough that a sensor-fusion researcher can implement and test it. The current package exercises body×world (S1) and body×body (S2, S3) pairings. The remaining two evidence families, time/progression and secure-state, participate through different mechanisms rather than through pairwise coherence statistics. Time contributes through the decay rule (score must be renewed by ongoing evidence and cannot be banked indefinitely) and through sync boundary freshness (Section 6.4) (external time references such as beacon values or network time must agree with the band's internal oscillator state). Secure state contributes through the progress invariant (monotonic ratchets, anti-rollback, and the requirement that continuity advance rather than branch freely). These are architectural constraints that make the S-numbered scoring paths trustworthy over time, not additional scoring paths of the same kind. World×time and body×time cross-checks, which would produce S-numbered statistics, remain future work.

---

## 8 Threat model and falsification conditions

### 8.1 Non-goals

The following are outside the scope of the primitive by design:

- **Not institution free.** The manufacturer remains in the trust path. The goal is to narrow institutional custody, not abolish it.
- **Not a deployable protocol.** The sync boundary is architecturally specified (Section 6.4), not construction complete.
- **Not general anti-surveillance.** Decay limits credential accumulation but does not prevent traffic analysis, real-time observation, or verifier-side logging.

### 8.2 Adversary classes

| Class | Typical capability | Rough budget / access model | Why it matters |
|---|---|---|---|
| **A1: remote or companion-level attacker** | compromised phone, watch, relay channel, app layer, or verifier-facing client stack | ~$0-100 plus software effort | tests whether the band remains meaningful when companions are hostile |
| **A2: hands-on attacker** | physical possession, debug access attempts, rollback, probing, fault injection, side-channel extraction, simple signal injection | ~$100-1,000 and bench access | tests whether the protected boundary is more than a software fiction |
| **A3: lab-grade physical attacker** | PCB rework, sustained probing, custom fixtures, invasive extraction, sophisticated side-channel and firmware attacks | ~$1,000-10,000+ and specialist time | tests the difference between tamper-evident consumer hardware and serious hardware security |
| **A4: supply-chain or manufacturer-level attacker** | altered firmware, altered provisioning, modified components, coerced updates, state-level or vendor-level control before the user ever wears the device | structural, not reducible to a simple budget | the manufacturer remains an institution in the trust path; open specifications, reproducible firmware, manufacturer diversity, and conformance criteria are the best available constraints |

A fifth pressure cuts across all four classes: **model-assisted fabrication**. BioForge-style work [8] means the attacker need not steal the exact sensor stream; they may only need access to one physiological modality and a generative model good enough to synthesize another.

### 8.3 Falsification conditions

The primitive should be stated in a way that makes failure recognizable.

| ID | Falsification condition | Example attack | What failure would mean |
|---|---|---|---|
| **F1** | A cheap bench rig can jointly spoof IMU-PPG coherence at operationally meaningful acceptance rates | ~$30-100 in phone, actuator, LED driver, or replay hardware | the core coupling thesis is weaker than claimed |
| **F2** | Barometric-motion agreement can be cheaply fabricated under realistic scoring windows | ~$30-100 in pressure manipulation | active-motion same-body evidence is easier to fake than hoped |
| **F3** | Low-motion windows remain operationally weak for same-body discrimination (AUC below ~0.6 at 60s windows across realistic cohorts) | standard dataset evaluation | the primitive fails too many bodies to be called a general humanity primitive |
| **F4** | Rollback or state cloning yields reusable continuity without detectable score collapse | battery pull, flash clone, firmware rollback | the progress boundary is not meaningful |
| **F5** | Claim presentation is linkable across relying parties or sessions | passive observation, verifier correlation, metadata inspection | the anonymous mode degrades into a tracking token |
| **F6** | Key extraction or secret compromise is cheap under modest physical attack | ~$100-1,000 with probes, logic analyzers, fault tools | the boundary offers less protection than the paper implies |
| **F7** | Multi-domain generative synthesis defeats the scoring package quickly (>50% success in 10 or fewer attempts) | model-assisted fabrication using one observed modality | designed scoring is not enough |
| **F8** | Performance collapses across skin tone, loose wear, disability, sweat, edema, or tremor | normal cohort diversity and basic fairness evaluation | the primitive is inequitable or too brittle for serious adoption |

---

## 9 Anti-Sybil integration

The primitive does not solve uniqueness. That is not the end of the story.

The core primitive proves human presence, not one-person-one-credential. But that leaves open a second design space: **privacy-preserving anti-Sybil pressure layered above the primitive without collapsing it into readable identity.**

The middle ground is narrow: the option space is alive, and every candidate inside it still has real failure modes. One distinction matters immediately: bounded anonymous presentation (Privacy Pass / ARC-like [12, 13, 14]) inside Mode 1 is baseline protocol hygiene, not an anti-Sybil overlay. It prevents a single proof from being replayed without limit, but it does not pressure uniqueness. The families below go further, adding physical, economic, or issuance friction above that baseline.

| Candidate family | What it tries to add | Privacy posture | Current judgment |
|---|---|---|---|
| **Threshold or split-trust issuance** (threshold BBS+ [15], pairing-free blind-threshold [16]) | no single issuer learns or controls the whole issuance act | stronger than single-issuer models | serious research direction, hardware and governance still open |
| **Encounter or co-wear friction** | penalize improbable multi-band proximity or suspicious co-wear patterns | potentially privacy-preserving if carefully local and ephemeral | candidate mitigation only; false positives and graph leakage remain risks |
| **Decay economics and issuance caps** | raise the cost of keeping many live credentials warm (Section 7.1) | privacy-preserving if implemented locally or via blinded bounded issuance | useful pressure, not uniqueness proof |

These should be described as **anti-Sybil layers above the primitive**, not as hidden guarantees already provided by it.

---

## 10 Open engineering problems

### 10.1 The sync boundary (protocol layer)

The next protocol task is to turn the sync boundary principle into a finished construction. That construction must preserve secrecy, resist rollback, tolerate offline accumulation, limit censorship damage, and avoid making checkpointing into a new tracking surface. A deployable design must answer five questions: what exactly gets committed, when the challenge is determined, how much failure is tolerable, what public context is acceptable, and what remains private at issuance.

### 10.2 Trusted sensor provenance

The first hardware task is to establish that scored streams originate from the band's own sensors and have not been rewritten in transit.

| Sub-problem | What has to be protected | Candidate mechanism families | Current judgment |
|---|---|---|---|
| **bus authenticity** | sensor samples should not be trivially rewritten between sensor and scorer | authenticated or constrained ingress, protected peripheral paths | partially understood, not closed |
| **driver / DMA discipline** | untrusted software should not silently copy or alter samples before scoring | protected peripheral access, memory isolation, trusted driver placement | serious engineering task |
| **physical trace vulnerability** | exposed board traces should not make logical isolation irrelevant | shorter trace surface, tamper evidence, shielding | still the hardest practical gap |
| **debug / update abuse** | maintenance paths should not become sensor forgery paths | debug lock, secure boot, anti-rollback | necessary but not sufficient |
| **proof that the body is actually there** | even authentic sensors can still be fooled by replay or staged environments | device-controlled challenge-response, cross-domain consistency checks | strongest current defense |

### 10.3 Unlinkable claim objects

The central cryptographic task is to make claims anonymous without recreating an institutional chokepoint.

If a band signs claims with a stable device identity, the proof becomes a tracker. If a central issuer blinds and reissues claims, the design reintroduces the institutional dependency it was built to avoid. Privacy Pass and ARC [12, 13, 14] remain the most relevant current protocol family because they make unlinkable, bounded, rate-limited presentation legible. They do not by themselves solve the issuer problem for a decentralized hardware architecture.

| Claim-object family | Why it is attractive | Why it remains hard | Near-term role |
|---|---|---|---|
| **Central issuer + Privacy Pass / ARC** | clean bounded anonymous presentation, mature standards | recentralizes issuer trust | comparator and fallback family |
| **Device-self-issued credentials** | no outside issuer required | stable device key becomes a tracking surface | unacceptable as anonymous baseline |
| **Threshold or split-trust issuance** (threshold BBS+ [15], Snowblind [16]) | distributes trust, improves privacy | hardware cost, governance, verifier trust remain open | strongest current innovation direction |
| **Batch / cohort / manufacturer-mediated issuance** | may enlarge anonymity sets | risks vendor capture, weak revocation | candidate family only |

Pairing-free threshold blind signatures such as Snowblind [16] require only standard elliptic curve operations, making anonymous issuance on Cortex-M-class hardware materially more plausible than pairing-heavy credential families. This undercuts the assumption that privacy-preserving issuance is computationally out of reach for constrained devices. Issuer governance and verifier trust remain open.

### 10.4 Low-motion and accessibility sufficiency

The scoring package is strongest during movement. The next sensing task is to extend it to rest.

Ballistocardiography/seismocardiography (BCG/SCG)-style mechanical sensing [18] and electrical bioimpedance [19, 27] both materially improve the option space for sedentary and low-motion regimes. Electrical bioimpedance [19, 27, 34] is one of the strongest current candidates for low-motion fallback. It also has a practical advantage: wrist-worn bioimpedance analysis already ships in commercial wearables.

If low-motion fallback fails under adversarial testing, the primitive narrows from proof of humanity to proof of ambulatory capacity. That consequence is serious enough to make this one of the highest-priority research paths.

### 10.5 Secure progress and device lifecycle

The next systems task is to make continuity state survive real life: decay, charging, removal, replacement, loss, and seizure.

Candidate time/progression sources include oscillator and real-time clock (RTC) behavior, external time references such as network or beacon time, session-continuity receipts from companions, and any local secure-state ratchet that makes rollback produce inconsistency rather than silent success. The device does not need one perfect clock. It needs enough partially independent progression sources that rollback becomes increasingly difficult to stage coherently.

One consequence of decay-based progress deserves separate attention. If a device is seized or disabled, authority collapses. The rebuild window (Section 7.1) is not only a usability cost. For a refugee, a disaster survivor, or a person fleeing violence, the rebuild interval may coincide with the exact period when proving humanness matters most. Any deployment that ignores this has failed a population it claimed to serve.

### 10.6 Research directions

**For hardware security engineers:** define a band security profile. Ingress assumptions, physical attack classes, tamper-evidence budget, secure state progression, and challenge-response feasibility.

**For embedded systems engineers:** build the reference prototype. Synchronized acquisition, protected local state, replay harnesses, and a testing framework for attack injection.

**For sensor-fusion researchers:** implement and test S1/S2/S3 and candidate low-motion modalities on public and newly collected datasets. Report negative results. A failed scoring package is valuable information.

**For cryptographers:** attack the claim object problem directly. Issuer models, unlinkability, presentation limits, verifier trust, threshold issuance feasibility, and computational cost on constrained hardware.

**For accessibility, HCI, and public-interest researchers:** test the human conditions that could make the primitive unjust. Low motion, disability, loose wear, low perfusion, atypical physiology, climate and sweat, and coercive use contexts.

**For governance and civil-liberties experts:** draft conformance language that keeps the system from silently becoming the opposite of what it claims to be.

---

## 11 Governance and deployment constraints

The political value of a system like this, if it has one, is reducing how much institutional custody is required to prove humanness. The manufacturer still remains in the trust path. The goal is to narrow that dependency, not to pretend it can be eliminated.

The best governance response is constraint: open specifications, reproducible firmware where feasible, public transparency about roots of trust and update models, manufacturer diversity across jurisdictions, and conformance criteria that make anti-user deviations visible.

Open-root-of-trust work matters as precedent. At datacenter and laptop scale, projects such as Caliptra [20] and OpenTitan [30] show that silicon trust stories can be opened for audit. At wearable scale, TROPIC01 [26] is a more relevant precedent: an open-architecture RISC-V secure element with published RTL that has reached commercial deployment. The right long-term question is not "which vendor should we trust?" but "how much of the trust story can be opened, measured, inspected, and contested?"

Any system that can prove "a live human is here" can be captured and turned into a gate. Compliance requires five constraints: no permanent identity binding, no export of raw body-derived evidence, no public or persistent modes as default, no unquestioned legacy platform roots, and no silent degradation of the primitive into a tracking layer. If those constraints are absent from the standardization path early, someone else will write the opposite rules later.

The architecture's political claim requires openness to be credible. A proprietary humanity primitive is a contradiction in terms. Specifications, firmware, scoring algorithms, and claim object constructions should be open-source and open-specification, so that a system which asks users to trust a sealed boundary lets those users verify what the boundary contains.

---

## 12 Conclusion

Simulacra does not detect reality, cure propaganda, kill AI activity, or settle proof of personhood. The proposition is narrower than any of those, and for that reason, more serious.

The proposition is that **live embodied continuity** can become a usable authentication primitive without default identity surrender and without routine export of raw body-derived evidence.

The argument for that proposition is no longer empty. There is enough same-body literature, enough wearable signal evidence, enough adversarial biosignal work, enough prototype-grade engineering detail, and now enough instrument-cluster logic to state the primitive responsibly. The hardest problems have names.

If the scoring package fails, the paper should fail with it. If low-motion fallback fails, the claim to general humanity should narrow. If claim objects cannot be made unlinkable without recreating an issuer, the anonymous mode should remain explicitly incomplete. If the band-first hypothesis is surpassed by a cleaner trust anchor, the architecture should move. If privacy-preserving anti-Sybil optionalities fail, the paper should say that too rather than pretending the field has only two choices: surveillance or surrender.

Authentication has spent too long asking whether one credential, one issuer, or one biometric can settle the matter. Simulacra asks a harder question: can authentication be rebuilt around the local coherence of body, world, time, and secure state, around evidence families whose agreement is the signal and whose disagreement is the alarm, so that successful forgery becomes less a software trick and more a costly act of staged reality?

**Can humanness be proven as expiring embodied continuity rather than durable identity?**

This paper argues that the question is now precise enough to test, precise enough to falsify, and important enough that some future portion of digital user sovereignty may depend on whether the answer is yes.

---

## Thank yous

"Even if the software layer is perfect and fully decentralized, the Foundation still has the ability to insert a backdoor into the system, letting it create arbitrarily many fake human identities." - Vitalik Buterin [2]

"Arguing that you don't care about the right to privacy because you have nothing to hide is no different than saying you don't care about free speech because you have nothing to say." - Edward Snowden

"The internet, our greatest tool of emancipation, has been transformed into the most dangerous facilitator of totalitarianism we have ever seen." - Julian Assange

"You're expelled from your mother's uterus as if shot from a cannon towards a barn door studded with old nail files and rusty hooks. It's a matter of how you use up the intervening time in an intelligent and ironic way; and try not to do anything ghastly to your fellow creatures." - Christopher Hitchens

To those who treated this project as real before we could guarantee the real inside each other.

And to those we lost, who were here o7 *A* ≥ 0.

🖤 Care until it breaks you. It's the greatest thing a thing can do. 🖤

---

## Appendix A. Candidate presentation and anti-Sybil families

This appendix is partly speculative. None of the following should be read as solved. The first row is a baseline presentation mechanism, not an anti-Sybil overlay; it is included as the comparator against which higher-friction families are measured.

| Candidate family | Intended effect | Privacy posture | Current maturity |
|---|---|---|---|
| **ARC / bounded anonymous presentation** | limit how often one continuity state can be spent in a context/epoch | strong if issuer trust is acceptable | strongest near-term candidate |
| **Threshold issuance (e.g., threshold BBS+)** | reduce single-issuer concentration | potentially strong | cryptographically credible, deployment-open |
| **Pairing-free threshold blind signatures (e.g., Snowblind)** | lower-weight distributed blind issuance | potentially strong | frontier candidate |
| **Co-wear / collision penalties** | reduce gain from wearing many devices in suspicious proximity | privacy-sensitive, must be local or narrowly disclosed | open candidate |
| **Encounter friction / local contact evidence** | make farming many anonymous credentials physically expensive | privacy-sensitive, false-positive prone | appendix-only candidate |
| **Optional higher-friction overlays** | allow applications to demand more than base human presence | depends on overlay design | outside base primitive |

---

## Appendix B. Representative cross-licensing relations

| Family combination | What it can corroborate | What disagreement may reveal | Current status |
|---|---|---|---|
| **Body x World** | motion through a changing environment rather than isolated replay | staged motion without matching environmental transition | physically grounded, only partly validated |
| **Body x Time** | exertion, recovery, and continuity unfolding over real elapsed intervals | accelerated clocks, replayed intervals, or continuity farming | conceptually strong, implementation open |
| **World x Time** | transitions between environments across a plausible temporal sequence | bench emulation, frozen traces, or impossible timing | promising, under-tested |
| **Body x Secure State** | one body carrying one advancing continuity state through an epoch | replayed biosignals attached to cloned or rolled-back local state | foundational target, unresolved at deployment grade |
| **World x Secure State** | one instrument moving through an environment while local state advances honestly | fabrication that does not survive protected progression | promising, engineering-heavy |
| **Body x World x Time x Secure State** | embodied continuity inside a changing world over real elapsed time with advancing protected state | cheap software forgery and single-family replay attacks | architectural goal, not validated result |

The current prototype path only exercises body-world through S1 and body-body through S2 and S3. The remaining pairings are architectural targets.

---

## Appendix C. Candidate sync boundary topologies

| Topology | What the band computes locally | Role of external context | Main strength | Main weakness | Current status |
|---|---|---|---|---|---|
| **Local provisional scoring + external ratchet** | provisional family-level summaries and continuity state | freshness checkpoint only | strongest local secrecy | rollback risk if local state can be cloned | conceptually coherent |
| **External-context-dependent evaluation** | retained commitments or summaries only | determines the evaluation challenge and advancement condition | strongest blind-attack intuition | higher availability and censorship risk | interesting, privacy delicate |
| **Hybrid local + sync** | provisional continuity state, local residuals, and partial scoring | selects or authorizes higher-order checks, ratchets progress | best current balance of secrecy, progress, and freshness | protocol not yet source-hardened | strongest current candidate |

---

## References

1. S. Adler, Z. Hitzig, S. Jain, et al., "Personhood credentials: Artificial intelligence and the value of privacy-preserving tools to distinguish who is real online," arXiv:2408.07892, 2024.
2. V. Buterin, "What do I think about biometric proof of personhood?", https://vitalik.eth.limo/general/2023/07/24/biometric.html, July 2023, accessed March 2026.
3. J. Lester, B. Hannaford, and G. Borriello, "Are You With Me? Using Accelerometers to Determine If Two Devices Are Carried by the Same Person," in *Pervasive Computing*, 2004.
4. C. Cornelius and D. Kotz, "Recognizing Whether Sensors Are on the Same Body," in *Pervasive Computing*, 2011.
5. S. Mare et al., "ZEBRA: Zero-Effort Bilateral Recurring Authentication," in *IEEE Symposium on Security and Privacy*, 2014.
6. S. Abbaspourazad, A. Mishra, J. Futoma, A. C. Miller, and I. Shapiro, "Wearable Accelerometer Foundation Models for Health via Knowledge Distillation," arXiv:2412.11276, 2024.
7. J. Liu, J. Tang, G. Zhao, R. Gui, S. Cheng, T. Lu, J. Liu, W. Wang, M. Gowda, Y. Shi, and Y. Wang, "PPG as a Bridge: Cross-Device Authentication for Smart Wearables with Photoplethysmography," arXiv:2602.08972, submitted to IMWUT 2026.
8. V. Krish, N. Paoletti, M. Kazemi, S. Smolka, and A. Rahmati, "Biosignal Authentication Considered Harmful Today," in *33rd USENIX Security Symposium*, 2024.
9. H. Kumar, H. S. Mousavi, and B. Shahsavari, "Fusion-ID: A Photoplethysmography and Motion Sensor Fusion Biometric Authenticator With Few-Shot On-Boarding," in *ICASSP*, 2022.
10. Y. Cao, J. Cao, H. Liu, Z. Cui, and L. Wen, "Eden: An Edge Computing Empowered Proof-of-Personhood Protocol for Anti-Sybil in Blockchain-based Metaverse," in *2nd International Conference on Intelligent Metaverse Technologies & Applications (iMETA)*, 2024.
11. IOST, "PayPIN Ring: Continuous Identity Verification," product documentation, https://docs.iost.io/payment-solutions/paypin/ring, accessed March 2026.
12. A. Davidson et al., "The Privacy Pass Architecture," RFC 9576, 2024.
13. S. Celi et al., "Privacy Pass Issuance Protocols," RFC 9578, 2024.
14. IETF Privacy Pass Working Group, "Privacy Pass Issuance Protocol for Anonymous Rate-Limited Credentials," draft-ietf-privacypass-arc-protocol-01, and "Anonymous Rate-Limited Credentials Cryptography," draft-ietf-privacypass-arc-crypto-01, March 2026.
15. J. Doerner, Y. Kondi, E. Lee, abhi shelat, and L. Tyner, "Threshold BBS+ Signatures for Distributed Anonymous Credential Issuance," in *IEEE Symposium on Security and Privacy*, 2023; IACR ePrint 2023/602.
16. E. Crites, C. Komlo, M. Maller, S. Tessaro, and C. Zhu, "Snowblind: A Threshold Blind Signature in Pairing-Free Groups," in *CRYPTO*, 2023; IACR ePrint 2023/1228.
17. W. Song et al., "Pistis: Replay Attack and Liveness Detection for Gait-Based User Authentication System on Wearable Devices Using Vibration," *IEEE Internet of Things Journal*, 2023.
18. A. D. Wiens, A. Johnson, and O. T. Inan, "Wearable Sensing of Cardiac Timing Intervals from Cardiogenic Limb Vibration Signals," *IEEE Sensors Journal*, 2017.
19. K. Sel, D. Osman, and R. Jafari, "Non-Invasive Cardiac and Respiratory Activity Assessment From Various Human Body Locations Using Bioimpedance," *IEEE Open Journal of Engineering in Medicine and Biology*, 2021.
20. Open Compute Project, "Caliptra: Silicon-Level Root of Trust for Datacenter Infrastructure," specification and reference implementation, https://chipsalliance.github.io/Caliptra/, accessed March 2026.
21. A. S. Willsky, "A Survey of Design Methods for Failure Detection in Dynamic Systems," *Automatica*, vol. 12, no. 6, pp. 601-611, 1976. DOI: 10.1016/0005-1098(76)90041-8.
22. E. Y. Chow and A. S. Willsky, "Analytical Redundancy and the Design of Robust Failure Detection Systems," *IEEE Transactions on Automatic Control*, vol. 29, no. 7, pp. 603-614, 1984. DOI: 10.1109/TAC.1984.1103593.
23. drand, "Distributed Randomness Beacon: Protocol Specification and League of Entropy," https://docs.drand.love, accessed March 2026.
24. NIST, "Randomness Beacon, Version 2.0: Interoperable Randomness Beacons," https://csrc.nist.gov/projects/interoperable-randomness-beacons, accessed March 2026.
25. FIDO Alliance, "Client to Authenticator Protocol (CTAP), v2.2," Proposed Standard, specification for external/roaming authenticators over USB, NFC, and BLE, https://fidoalliance.org/specifications/, July 2025.
26. Tropic Square, "TROPIC01: Open-Architecture RISC-V Secure Element," open-source RTL at https://github.com/tropicsquare/tropic01, general availability announced 2025, accessed March 2026.
27. C. Cornelius, J. Sorber, R. Peterson, J. Skinner, R. Halter, and D. Kotz, "Who Wears Me? Bioimpedance as a Passive Biometric," in *USENIX Workshop on Health Security and Privacy (HealthSec)*, 2012.
28. J. K. Becker, D. Li, and D. Starobinski, "Tracking Anonymized Bluetooth Devices," in *Proceedings on Privacy Enhancing Technologies (PoPETs)*, 2019(3):50-65.
29. V. Buterin, "Does digital ID have risks even if it's ZK-wrapped?", https://vitalik.eth.limo/general/2025/06/28/zkid.html, June 2025, accessed March 2026.
30. lowRISC and Google, "OpenTitan: Open Source Silicon Root of Trust," https://opentitan.org, accessed March 2026.
31. Simulacra Project, "Companion Empirical Note: S2 Proxy Testing on WESAD and PPG-DaLiA," project repository, 2026.
32. H. H. Asada, H.-H. Jiang, and P. Gibbs, "Active Noise Cancellation Using MEMS Accelerometers for Motion-Tolerant Wearable Bio-Sensors," in *Proc. IEEE Engineering in Medicine and Biology Society (EMBS)*, 2004.
33. B. S. Kim and S. K. Yoo, "Motion Artifact Reduction in Photoplethysmography Using Independent Component Analysis," *IEEE Transactions on Biomedical Engineering*, vol. 53, no. 3, pp. 566-568, 2006.
34. C. Cornelius, R. Peterson, J. Skinner, R. Halter, and D. Kotz, "A Wearable System That Knows Who Wears It," in *Proc. ACM MobiSys*, 2014.
