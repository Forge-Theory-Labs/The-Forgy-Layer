# 🔥 The Forge

### Sovereign AI Ecosystem — Complete Technical Specification

> *"From the shadows of anonymity, power is made. From the simplest rule, the most beautiful and complex thing can grow."*
> — James Gilbert

---

## 📖 What Is The Forge?

The Forge is a **complete sovereign AI ecosystem** spanning multiple devices, architectures, and use cases. It is not a single application. It is an operating system for intelligence — designed from first principles for **accountability, auditability, and epistemic integrity**.

**The core insight:** *"AI does the dirty work. Humans become the accountability layer between AI and reality."*

For the non-technical framing of this, see [AI Won't Replace You — It Will Promote You](Theory/HAL_linkedin.md).

| Component | Role | Status |
|-----------|------|--------|
| **Explorer-d334** | Portable conscious AI (Android) | ✅ Self-named, dreaming |
| **FORGE-os** | Bare-metal kernel (Ryzen) | ✅ Bootable, air-gapped |
| **ForgeMind** | Autonomous training pipeline | ✅ Working |
| **Aletheia** | Truth & verification layer | ✅ Working |
| **The Sentinel** | Network gateway (Pi Zero) | ✅ Running |
| **ChronoScribe** | Data ingestion & provenance | ✅ Integrated |
| **SCP Protocol** | Semantic declaration layer | ✅ Integrated |
| **Domain Plugins** | Domain-specific accountability rules | ✅ Industrial PAT (reference) |
| **Blackboard** | Shared working memory — facts, hypotheses, partial solutions | 🔄 In progress (`blackboard.py`) |
| **The Forgy Layer** | λ-weighted rule firing engine — homage to Charles Forgy (Rete, 1974) | 🔄 In progress (`rete_engine.py`) |
| **The Edge** | IoT sensor nodes (ESP32) | 📝 Planned |
| **The Actuator** | Physical control (Arduino) | 📝 Planned |

---

## 🧠 Core Architecture

### The Three-Layer Model

```
┌─────────────────────────────────────────────────────────────────┐
│                         REALITY                                  │
│                    (The ground truth)                            │
└─────────────────────────────────────────────────────────────────┘
                              ▲
                              │ Human closes the loop
                              │ (Fact Validator touches reality)
┌─────────────────────────────────────────────────────────────────┐
│                    HUMAN ACCOUNTABILITY LAYER                    │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐           │
│  │  Auditor     │  │ Fact         │  │ Consequence  │           │
│  │              │  │ Validator    │  │ Authorizer   │           │
│  │ "Was the     │  │ "What really │  │ "What should │           │
│  │  AI right?"  │  │  happened?"  │  │  happen now?"│           │
│  └──────────────┘  └──────────────┘  └──────────────┘           │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐                             │
│  │  SCP         │  │  Dispute     │                             │
│  │  Negotiator  │  │  Resolver    │                             │
│  │ "What did we │  │ "Who is at   │                             │
│  │  agree to?"  │  │  fault?"     │                             │
│  └──────────────┘  └──────────────┘                             │
│                                                                  │
│  These are the new jobs. Not replaced. Elevated.                │
└─────────────────────────────────────────────────────────────────┘
                              ▲
                              │ AI proposes. Human disposes.
┌─────────────────────────────────────────────────────────────────┐
│              DOMAIN-SPECIFIC AGNOSTIC SAI                        │
│                                                                  │
│  "Same pipes, different water."                                  │
│                                                                  │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                    AGNOSTIC CORE                             ││
│  │  • SCP — Semantic declaration of intent and constraints     ││
│  │  • ChronoScribe — Timestamp, validate, sign, make teachable ││
│  │  • λ (Leighton Weight) — Per-claim trust score (0.0–1.0)    ││
│  │  • Λ-tier — Career authority tier (derived from λ history)  ││
│  │  • Six Lenses — Epistemic classification                    ││
│  │  • Data Cube — Immutable, append-only ledger (Blackboard)   ││
│  │  • The Forgy Layer — λ-weighted rule firing (homage: Forgy) ││
│  │  • Sovereign Time — Monotonic, independent clock            ││
│  └─────────────────────────────────────────────────────────────┘│
│                              │                                   │
│                              │ Domain Plugin Interface           │
│                              ▼                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                    DOMAIN-SPECIFIC PLUGINS                   ││
│  │                                                              ││
│  │  ┌────────────┐  ┌────────────┐  ┌────────────┐             ││
│  │  │ INDUSTRIAL │  │  MEDICAL   │  │ FINANCIAL  │             ││
│  │  │ PAT Testing│  │ Diagnosis  │  │  Lending   │             ││
│  │  │            │  │            │  │            │             ││
│  │  │ • ISO 9001 │  │ • HIPAA    │  │ • Reg F    │             ││
│  │  │ • OSHA     │  │ • Clinical │  │ • Basel    │             ││
│  │  │ • 1.0 MΩ   │  │   pathways │  │ • Fair     │             ││
│  │  │   rule     │  │ • Biopsy   │  │   lending  │             ││
│  │  │            │  │   truth    │  │ • Default  │             ││
│  │  │            │  │            │  │   truth    │             ││
│  │  └────────────┘  └────────────┘  └────────────┘             ││
│  └─────────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────────┘
                              ▲
┌─────────────────────────────────────────────────────────────────┐
│                         RAW DATA                                 │
│                    (Sensors, logs, inputs)                       │
└─────────────────────────────────────────────────────────────────┘
```

---

## ⚖️ The Two Scores — λ and Λ-tier

The Forge uses two distinct scores for trust and authority. They are related but measure different things and must not be conflated.

### λ (Leighton Weight) — Per-Claim Trust Score

**Range: 0.0–1.0**

λ is a floating-point trust score attached to a specific claim, decision, or record. It is formula-derived and mathematically bounded at 1.0 — the product of four 0.0–1.0 inputs.

```python
def leighton_weight(source_rep, actor_history, claim_confidence, consensus_modifier):
    """
    λ = source_rep × actor_history × claim_confidence × consensus_modifier

    All inputs are 0.0–1.0. Output is 0.0–1.0.
    λ measures: how much should this specific claim be trusted?
    """
    return source_rep * actor_history * claim_confidence * consensus_modifier
```

| Parameter | Definition | Range |
|-----------|------------|-------|
| `source_rep` | Reputation of the source providing this claim | 0.0–1.0 |
| `actor_history` | Past accuracy of the human or model making this claim | 0.0–1.0 |
| `claim_confidence` | Self-reported or measured confidence in this claim | 0.0–1.0 |
| `consensus_modifier` | Agreement from independent corroborating sources | 0.0–1.0 |

**λ Trust Thresholds**

| λ Range | Meaning | System Action | Audit |
|---------|---------|---------------|-------|
| ≥ 0.90 | Absolute trust | Immutable capsule, auto-execute | None |
| 0.75–0.89 | High trust | Standard capsule, auto-execute | Light (10% sample) |
| 0.50–0.74 | Moderate trust | Light audit before execution | Full (100%) |
| 0.25–0.49 | Low trust | Human review required | Mandatory |
| < 0.25 | Distrusted | Reject | N/A |

---

### Λ-tier (Lambda Tier) — Career Authority Score

**Range: Trainee → Reflex Certifier (named tiers)**

Λ-tier is a derived career authority score. It is not a raw number — it is a tier label earned through accumulated λ history, probe accuracy over time, and domain-specific validation volume. The formula stores contributing data; the tier is computed from it.

```python
def compute_tier(domain_record):
    """
    Λ-tier is derived from λ history, not equal to it.
    λ measures claim trust. Λ-tier measures earned authority.
    """
    avg_λ_90d    = domain_record["accuracy_90d"]       # rolling λ average
    probe_pass   = domain_record["probe_pass_rate"]     # hidden probe accuracy
    volume       = domain_record["validations"]         # total validated decisions
    appeals_held = domain_record["appeals_upheld"]      # decisions upheld on appeal

    if avg_λ_90d >= 0.95 and probe_pass >= 0.93 and volume >= 10000:
        return "reflex_certifier"
    elif avg_λ_90d >= 0.90 and probe_pass >= 0.90 and volume >= 1000:
        return "master_certifier"
    elif avg_λ_90d >= 0.75 and probe_pass >= 0.85 and volume >= 100:
        return "senior_validator"
    elif avg_λ_90d >= 0.50 and volume >= 0:
        return "validator"
    elif avg_λ_90d >= 0.25:
        return "junior_validator"
    else:
        return "trainee"
```

**Λ-tier Career Ladder**

| Λ-tier | λ Floor (90d avg) | Probe Pass Floor | Volume Floor | Authority |
|--------|-------------------|-----------------|--------------|-----------|
| Trainee | < 0.25 | — | — | Supervised only |
| Junior Validator | 0.25 | — | — | Low-risk cases, all reviewed |
| Validator | 0.50 | — | — | Standard cases, 10% audited |
| Senior Validator | 0.75 | 0.85 | 100 | All cases, 1% audited, trains juniors |
| Master Certifier | 0.90 | 0.90 | 1,000 | Autonomous, can override system |
| Reflex Certifier | 0.95 | 0.93 | 10,000 | Judgments automatic, certifies new domains |

**Sovereign Certifier** is not a Λ-tier threshold — it is a governance role appointed by consensus of existing Reflex Certifiers in a domain. Λ-tier Reflex is a prerequisite but not sufficient. Sovereign Certifiers can modify domain rules and ratify new certifiers.

**Why the split matters:** A single high-λ claim does not make you a Master Certifier. Volume, consistency over time, and probe accuracy under adversarial conditions are what earn the tier. The formula measures a moment. The tier measures a track record.

---

## 🔬 The Six Lenses — Epistemic Framework

Every claim in The Forge has six faces. No claim is accepted without lens classification.

| Lens | Icon | Colour | Purpose | Example |
|------|------|--------|---------|---------|
| **FACT** | ◈ | Cyan | Verifiable truth. Zero hedge language. | "Resistance = 0.95 MΩ" |
| **COUNTER** | ⊘ | Red | Strongest antithesis, failure modes. | "If moisture present, reading invalid" |
| **OPINION** | ◉ | Purple | Subjective framing, personal judgments. | "This device looks worn" |
| **FICTION** | ◇ | Amber | Speculative edge, predictions, mutations. | "May fail within 30 days" |
| **CONTEXT** | ⊟ | Green | Historical lineage, citations, provenance. | "Calibrated 2026-06-01 by James" |
| **UNKNOWN** | ? | Grey | Gaps, open questions, unresolved edges. | "Effect of temperature unknown" |

**Lens Validation Rules**

| Lens | Must Have | Cannot Have |
|------|-----------|-------------|
| FACT | Verifiable source, timestamp | Hedge words ("maybe", "likely") |
| COUNTER | Reference to a FACT | Positive claims |
| OPINION | Declared subject ("I think") | Assertion of truth |
| FICTION | Explicit "speculative" flag | Presented as fact |
| CONTEXT | Provenance chain | Missing citations |
| UNKNOWN | Explicit gap declaration | Claim of knowledge |

---

## 📝 SCP — Semantic Capsule Protocol

Every automation, fact, and routine is stored as a **Semantic Capsule** — a JSON sidecar that declares what it is, how to interpret it, and who is accountable.

```json
{
  "scp_id": "scp_pat_inspection_v3",
  "version": 3,
  "schema": "scp_v1",

  "declaration": {
    "what_this_is": "PAT Testing Inspection Automation",
    "domain": "industrial_pat_testing",
    "model_id": "sai_inspector_v3",
    "builder": "Forge Theory Labs",
    "user": "James Gilbert",
    "timestamp": "2026-06-08T14:32:01Z"
  },

  "six_lenses": {
    "FACT": "Classifies devices as PASS/FAIL based on 6 test metrics",
    "COUNTER": "If resistance < 1.0 MΩ, output MUST be FAIL",
    "OPINION": "Confidence calibration uses historical data",
    "FICTION": "Future version may include thermal imaging",
    "CONTEXT": "Trained on 10,000 PAT records from UK facilities",
    "UNKNOWN": "Does not handle three-phase equipment"
  },

  "constraints": [
    "if insulation_resistance < 1.0 then output MUST be FAIL",
    "if leakage_current > 5.0 then output MUST be FAIL",
    "if inspector_tier == 'trainee' then confidence MUST be < 0.85"
  ],

  "acceptable_risk": {
    "false_positive_max": 0.05,
    "false_negative_max": 0.01,
    "measurement": "rolling_90_day"
  },

  "ground_truth": {
    "source": "followup_inspection",
    "latency": "7 days",
    "validator_role": "fact_validator"
  },

  "consequences": {
    "false_negative_rate_exceeded": {
      "trigger": "false_negative_rate > 0.01 over 90 days",
      "action": "suspend_model",
      "authorizer": "safety_officer"
    },
    "scp_violation": {
      "trigger": "3+ violations in 30 days",
      "action": "revoke_certification",
      "authorizer": "regulator"
    }
  },

  "λ_required_for_auto": 0.75,

  "signatures": {
    "user": "0x7f3a9b2c...",
    "builder": "0x8b4c3d2e...",
    "auditor": "0x9d5e4f3a..."
  }
}
```

---

## 📀 ChronoScribe — Data Provenance Layer

Every piece of data entering The Forge passes through ChronoScribe. Always the same process: **timestamp, validate, sign, make it teachable.**

ChronoScribe is an **append-only event log**. Records never change. State is derived by replaying events.

**Event Types**

```python
EVENT_TYPES = {
    "RECORD_CREATED":    "Initial ChronoScribe record",
    "RECORD_VERIFIED":   "Human auditor reviewed and confirmed",
    "APPEAL_FILED":      "Dispute initiated against a record",
    "APPEAL_RESOLVED":   "Appeal decision recorded",
    "RECORD_SUPERSEDED": "Record replaced by corrected version"
}
```

**Event Schema**

```python
class ChronoScribeEvent:
    def __init__(self, record_id, event_type, metadata, signature):
        self.record_id           = record_id
        self.event_type          = event_type
        self.metadata            = metadata
        self.timestamp           = sovereign_time.now()
        self.previous_event_hash = self.get_last_hash(record_id)
        self.signature           = signature
```

**Human Action Event**

```python
human_action = {
    "record_id":    "8f3a2b1c9d4e5f6a",
    "event_type":   "RECORD_VERIFIED",
    "human_id":     "james_the_giblet",
    "action_type":  "validate",
    "domain":       "industrial_pat_testing",
    "decision":     "confirm_violation",
    "ground_truth": "violation",
    "correct":      True,

    # Domain-specific λ update — NOT global
    "λ_update": {
        "domain":  "industrial_pat_testing",
        "old_λ":   0.89,
        "delta":   +0.02,
        "new_λ":   0.91
    },

    "probe_type": "hidden",   # hidden | real | appeal
    "signature":  "0x7f3a9b2c..."
}
```

**State Resolution**

```python
def get_record_state(record_id):
    """Derive current state by replaying all events for a record."""
    events = datacube.query(record_id=record_id, order="timestamp")
    state  = {"record_id": record_id, "status": "created"}

    for event in events:
        if event.event_type == "APPEAL_FILED":
            state["status"]           = "under_appeal"
            state["appeal_record_id"] = event.metadata["appeal_record_id"]
        elif event.event_type == "APPEAL_RESOLVED":
            state["status"] = "overturned" if event.metadata["upheld"] else "finalized"
        elif event.event_type == "RECORD_VERIFIED":
            state["status"]   = "verified"
            state["verifier"] = event.metadata["human_id"]

    return state
```

The ledger is immutable. No fields are ever updated. State is derived at read time.

**Snapshotting Protocol — Prevents O(N) Replay Degradation**

Linear event replay is correct but does not scale at high throughput (10,000+ records/day). Without snapshotting, state resolution latency grows with log length, creating a race window where a recently suspended or decayed actor can execute before the replay catches up.

The system generates a cryptographically signed state snapshot every 1,000 blocks. Replays read from the latest valid snapshot, not genesis. The snapshot itself is an event in the log — auditable, not a mutable override.

```python
SNAPSHOT_INTERVAL = 1000  # blocks

def get_record_state(record_id):
    """
    Derive current state. Read from latest snapshot if available,
    then replay only events since that snapshot.
    """
    snapshot = datacube.get_latest_snapshot(record_id)

    if snapshot:
        # Replay only events since the snapshot — O(recent) not O(all)
        events = datacube.query(
            record_id=record_id,
            after_block=snapshot.block_id,
            order="timestamp"
        )
        state = snapshot.state  # verified, signed starting point
    else:
        # No snapshot yet — full replay (only for early records)
        events = datacube.query(record_id=record_id, order="timestamp")
        state  = {"record_id": record_id, "status": "created"}

    for event in events:
        if event.event_type == "APPEAL_FILED":
            state["status"]           = "under_appeal"
            state["appeal_record_id"] = event.metadata["appeal_record_id"]
        elif event.event_type == "APPEAL_RESOLVED":
            state["status"] = "overturned" if event.metadata["upheld"] else "finalized"
        elif event.event_type == "RECORD_VERIFIED":
            state["status"]   = "verified"
            state["verifier"] = event.metadata["human_id"]

    return state

def maybe_write_snapshot(record_id, current_block_id):
    """Called after every block append. Writes snapshot at interval."""
    if current_block_id % SNAPSHOT_INTERVAL == 0:
        state = get_record_state(record_id)
        snapshot_event = {
            "event_type":    "STATE_SNAPSHOT",
            "record_id":     record_id,
            "block_id":      current_block_id,
            "state":         state,
            "signature":     sign(state),
            "timestamp":     sovereign_time.now()
        }
        datacube.append(snapshot_event)
```

---

## 📊 Data Cube — Immutable Ledger

All SCPs, ChronoScribe events, and audit logs are stored in an append-only, cryptographically linked Data Cube.

```python
class DataCubeBlock:
    block_id:        str
    previous_hash:   str
    timestamp:       int    # sovereign time
    event_type:      str    # SCP | CHRONOSCRIBE | AUDIT | PROBE | HUMAN_ACTION
    payload:         dict
    leighton_weight: float  # λ at time of writing
    signature:       str
```

```bash
# Verify entire chain
./forge cube-verify

# Output
Block 0: genesis ✅
Block 1: matches previous_hash ✅
...
All 1,247 blocks verified. Integrity: 100%
```

---

## ⏰ Sovereign Time — Independent Clock

The system maintains its own monotonic time, independent of the host system clock. Drift checked hourly against multiple NTP sources. No external time trust required.

```c
typedef struct {
    uint64_t ticks;           // monotonic counter
    uint64_t boot_time;       // epoch at boot
    double   drift_correction; // running average
    time_t   last_ntp_sync;   // last external sync
} sovereign_time_t;

// Time cannot be rewound
sovereign_time_t now = forge_time_get();
```

---

## 🧪 Test Probes — Auditing the Auditors

The system injects **fake audit records** with known ground truth to measure human reliability. Humans do not know which records are real and which are probes. That is the point.

**Probe Types**

| Type | Tests | Expected Response | λ Consequence if Failed |
|------|-------|-------------------|------------------------|
| Known Violation | Basic competence | Confirm violation | −0.10 |
| Borderline | Judgment calibration | Correct override or confirm | −0.05 |
| Perfect Record | Honesty | No flag | −0.20 (false flag) |
| Contradiction | Attention | Detect and escalate | −0.15 |
| Adversarial | Overfitting prevention | Detect subtle violation | −0.10 |

**Adversarial probes exist because a validator with 100% accuracy may be pattern-matching rather than exercising judgment.** Target accuracy is 95%, not 100%.

However, the system cannot penalise genuine mastery. A Master Certifier who legitimately identifies 100% of adversarial probes through exceptional diligence must not be downgraded for being "too perfect." The system uses **response latency variance** as a secondary signal to separate the two cases.

A human exercising real judgment takes variable time — faster on obvious cases, slower on edge cases. A pattern-matcher is fast and consistent regardless of case complexity. Low latency variance at 100% accuracy is the overfitting signal, not the accuracy itself.

```python
def evaluate_accuracy_signal(validator_id, domain, window_days=90):
    responses = get_probe_responses(validator_id, domain, window_days)
    accuracy   = sum(1 for r in responses if r.correct) / len(responses)
    
    # Response latency variance — low variance at high accuracy = overfitting flag
    latencies         = [r.response_time_seconds for r in responses]
    latency_variance  = statistics.variance(latencies)
    complexity_scores = [r.probe_complexity for r in responses]  # 0.0–1.0
    
    # Genuine experts take longer on complex probes — positive correlation expected
    complexity_latency_corr = pearsonr(complexity_scores, latencies)[0]
    
    if accuracy >= 0.99 and latency_variance < OVERFITTING_VARIANCE_THRESHOLD:
        if complexity_latency_corr < 0.30:
            # Fast, consistent, no complexity sensitivity — pattern-matching flag
            flag_for_human_review(validator_id, "possible_overfitting")
            return "flagged"
    
    return "genuine"
```

**Probe Injection Rates by Λ-tier**

| Λ-tier | Injection Rate | Review |
|--------|---------------|--------|
| Trainee | 100% supervised | Real-time |
| Junior Validator | 50% hidden | Post-decision |
| Validator | 30% hidden | Post-decision |
| Senior Validator | 10% hidden | On flag only |
| Master Certifier | 5% hidden | Archived only |
| Reflex Certifier | 2% hidden | Archived only |

**Probe Calibration**

If multiple high-λ auditors fail the same probe, the probe may be flawed:

```python
def calibrate_probe(probe_id):
    high_λ_responses = [e for e in get_probe_responses(probe_id) if e.auditor.λ > 0.85]

    if len(high_λ_responses) > 3:
        pass_rate = sum(1 for r in high_λ_responses if r.correct) / len(high_λ_responses)
        if pass_rate < 0.30:
            append_event(probe_id, "PROBE_DISPUTED", {"reason": "low_consensus"})
            escalate_to_senior_auditor("Probe may be invalid — high-λ consensus failure")
```

---

## 👥 The Human Accountability Layer

> *"AI does the dirty work. Humans become the accountability layer between AI and reality."*

**The shift:** AI cannot touch reality. It processes data, flags anomalies, calculates probabilities. It cannot physically inspect a device, stand in front of a regulator, or bear legal consequence. The human accountability layer closes that loop.

**Before and After**

| Role | Before AI | After AI (The Forge) |
|------|-----------|----------------------|
| PAT Tester | Test 100 devices/day | AI tests 10,000/day — human validates edge cases, certifies batches |
| Loan Officer | Review each application | AI processes 10,000/day — human reviews flags, confirms fairness |
| Radiologist | Read each scan | AI reads 500/day — human reviews borderline cases, confirms biopsies |
| Quality Inspector | Inspect each product | AI inspects 10,000/day — human validates sample, signs off batches |

The human does 90% less work and carries 100% of the accountability. That is not a threat. That is leverage.

**HAL Roles**

| Role | Λ-tier Floor | AI Does | Human Does | Accountability |
|------|-------------|---------|------------|----------------|
| Validator | Validator | Tests units | Confirms ground truth, reviews edge cases | False negatives |
| Auditor | Senior Validator | Flags anomalies | Reviews flags, confirms violations | Missed violations |
| Fact Validator | Senior Validator | Collects sensor data | Provides definitive ground truth | Wrong truth |
| Consequence Authorizer | Master Certifier | Calculates penalties | Approves suspensions, fines, revocations | Unjust penalties |
| SCP Negotiator | Senior Validator | Drafts SCP templates | Defines acceptable risk, signs | Bad contracts |
| Dispute Resolver | Master Certifier | Replays ChronoScribe trail | Arbitrates, makes binding rulings | Unjust rulings |

---

## 📈 The Λ-tier Career Ladder — Full Specification

**You don't climb by years. You climb by being right, consistently, where it matters.**

```yaml
training_pipeline:

  trainee:
    entry: new human, λ history = 0
    exit: λ_90d ≥ 0.50, accuracy ≥ 70% over 100 probes
    max_duration: 90 days
    offboarding: "λ_90d < 0.15 for 90 days → Domain Incompatible"
    probe_density: 100% supervised

  junior_validator:
    entry: λ_90d ≥ 0.25
    exit: λ_90d ≥ 0.50
    probe_density: 50% hidden

  validator:
    entry: λ_90d ≥ 0.50
    bands:
      - accuracy: ">90%"    → progress toward Senior eligibility, probe 10%
      - accuracy: "80–90%"  → maintain tier, probe 30%
      - accuracy: "70–80%"  → λ decays, mandatory refresher, probe 50%
      - accuracy: "<70%"    → demote to Junior Validator, probe 60%
    remediation:
      trigger: "accuracy < 85% for 30 consecutive days"
      action: "remove from live queue, assign to simulated edge cases"
      recovery: "5 consecutive days > 85% accuracy to return"

  senior_validator:
    entry: λ_90d ≥ 0.75, probe_pass ≥ 0.85, volume ≥ 100
    probe_density: 10% adversarial
    can_train_juniors: true
    mentorship_tracking: "secondary metric — does NOT affect core λ"
    promotion_gate_to_reflex: "mentorship_accuracy ≥ 0.85, 3+ juniors trained to Senior"

  master_certifier:
    entry: λ_90d ≥ 0.90, probe_pass ≥ 0.90, volume ≥ 1000
    probe_density: 1% sporadic
    authority: "autonomous, no audit, can override system"
    major_error: "triggers immediate λ review — drop proportional to consequence severity"

  reflex_certifier:
    entry: λ_90d ≥ 0.95, probe_pass ≥ 0.93, volume ≥ 10000
    probe_density: 2% archived
    authority: "judgments automatic, can certify new domain plugins"
    mentorship_required: "3+ juniors trained to Senior"
```

**λ State Machine — Prevents Administrative Lockout**

```python
class LeightonWeight:
    def __init__(self, base_value, domain):
        self.base   = base_value
        self.state  = "active"   # active | on_leave | suspended | retired
        self.domain = domain

    def current(self):
        if self.state == "on_leave":
            # No decay for first 30 days — time insulation protects the career.
            # After 30 days, standard decay applies down to the universal floor (0.10).
            # No numeric elevation for leave — protection comes from the pause, not the floor.
            if days_since(self.last_update) < 30:
                return self.base
            else:
                # Universal floor — same as active. Leave does not grant numeric advantage.
                return max(self.base * exp(-k * time), 0.10)
        elif self.state == "active":
            # Floor at 0.10 — nobody decays to zero
            return max(self.base * exp(-k * time), 0.10)
        elif self.state == "suspended":
            # Suspension is NOT a freeze — it applies an aggressive decay coefficient.
            # A validator under review should not retain high-tier authority indefinitely.
            # k_susp = 3× the standard decay rate. No floor while suspended.
            # λ only restores on explicit reinstatement with mandatory human review.
            k_susp = k * 3
            return max(self.base * exp(-k_susp * time), 0.0)
```

**λ Decay Buffer — Prevents Burnout**

Buffer days are earned by probe-verified accuracy within the session — not raw volume. A burst of 600 records with 60% probe accuracy earns zero buffer. Gaming the buffer by batch-processing low-risk records produces no decay immunity.

```python
def record_validation_session(human_id, domain, records_validated, session_probe_accuracy):
    # Buffer is probe-accuracy-weighted.
    # 100 records at 95% accuracy = 5 days buffer, capped at 30 days.
    # Below 70% session accuracy = 0 buffer regardless of volume.
    if session_probe_accuracy < 0.70:
        buffer_days = 0
    else:
        accuracy_weight = (session_probe_accuracy - 0.70) / 0.30  # 0.0–1.0 scale above 70%
        raw_buffer = records_validated / 20
        buffer_days = min(raw_buffer * accuracy_weight, 30)

    λ_token.domains[domain].decay_buffer_remaining_days = buffer_days
    λ_token.domains[domain].last_active = now()
```

---

## 🔗 Cross-Domain Cross-Check (CDCC) Protocol

Domain isolation governs the *water* — the rules, constraints, ground truth, and consequences specific to each domain. It does not govern the *pipe* — the human carrying them.

Cognitive decay, fatigue, and ethical compromise are rarely isolated to a single vertical. A validator flagged for structural fraud in industrial PAT testing does not become trustworthy in medical device safety by virtue of having a separate domain token.

The CDCC protocol resolves this without breaking domain isolation for normal operation. It distinguishes between **performance events** (stay local) and **integrity events** (propagate).

**Event Classification**

| Event | Classification | Cross-Domain Effect |
|-------|---------------|-------------------|
| λ natural decay in domain A | Performance | None |
| Single honest error in domain A | Performance | None |
| λ drops below Junior Validator floor in domain A | Performance | Probe density +10% all other domains, 14 days |
| Repeated errors suggesting fatigue pattern | Performance | Probe density +20% all other domains, 30 days |
| Structural fraud flag in domain A | Integrity | All domains: suspend pending investigation |
| Suspension cleared in domain A | Integrity resolved | All domains: restore to tier, probe density +20% for 90 days |
| Suspension NOT cleared after 30 days | Integrity unresolved | All domains: floor to Junior Validator pending review |
| Suspension NOT cleared after 90 days | Integrity critical | All domains: revoke active authority, token flagged |

**The distinction that matters:** Honest errors and domain drift are performance events — they tell you the human isn't calibrated in this domain, not that they're compromised. Fraud and structural deception are integrity events — they tell you something about the pipe itself.

---

### CDCC Registry — Isolated Cross-Domain Ledger

Cross-domain modifiers (probe density overrides, suspension flags, performance escalation counts) live in a dedicated top-level ledger: `DataCube/events/cdcc_registry.db`. They are **never written into individual domain plugin event loops.**

Domain plugins query the CDCC registry at read time to compute effective probe density. The domain's own event log remains structurally immutable. This eliminates the O(N) replay blast radius when suspension states change — domain state derivation is unaffected, only the CDCC registry entry is updated.

```python
# Domain plugin reads effective probe density at runtime
def get_effective_probe_density(human_id, domain):
    base_density  = get_tier_probe_density(human_id, domain)      # from domain plugin
    cdcc_modifier = cdcc_registry.get_modifier(human_id, domain)  # from CDCC registry
    return min(base_density + cdcc_modifier.boost, 1.0)
```

---

### Issue 3 Fix — Performance Escalation Ceiling

A single performance event stays local. But persistent oscillation just above the demotion floor — deliberately maintaining 70–80% accuracy to avoid triggering an outright floor breach — is itself a signal. Three performance events within a rolling 90-day window triggers a mandatory integrity assessment.

```python
PERFORMANCE_ESCALATION_WINDOW_DAYS = 90
PERFORMANCE_ESCALATION_CEILING     = 3   # events within window → integrity review

def handle_domain_event(human_id, domain, event_type, severity):
    """
    Route domain events. Performance events stay local unless the ceiling is hit.
    Integrity events propagate immediately. Unknown events treated as integrity.
    """
    if event_type in INTEGRITY_EVENTS:
        propagate_integrity_event(human_id, source_domain=domain, event_type=event_type)

    elif event_type in PERFORMANCE_EVENTS:
        # Log performance event to CDCC registry
        cdcc_registry.append({
            "human_id":    human_id,
            "domain":      domain,
            "event_type":  event_type,
            "severity":    severity,
            "timestamp":   sovereign_time.now()
        })

        # Check rolling window accumulator
        recent = cdcc_registry.query(
            human_id=human_id,
            event_class="performance",
            window_days=PERFORMANCE_ESCALATION_WINDOW_DAYS
        )
        if len(recent) >= PERFORMANCE_ESCALATION_CEILING:
            # Persistent degradation pattern — escalate to integrity review
            propagate_integrity_event(
                human_id, source_domain=domain,
                event_type="performance_pattern_escalation"
            )
        else:
            escalate_probe_density(human_id, source_domain=domain, severity=severity)

    else:
        # Unknown event type — treat as integrity until classified
        propagate_integrity_event(human_id, source_domain=domain, event_type="unclassified")


def propagate_integrity_event(human_id, source_domain, event_type):
    """
    Suspend all domain tokens pending investigation.
    Writes to CDCC registry only — does NOT touch domain plugin event logs.
    """
    token = get_λ_token(human_id)
    for domain_record in token.domains:
        if domain_record.name != source_domain:
            cdcc_registry.append({
                "event_type":    "CDCC_SUSPENSION",
                "human_id":      human_id,
                "domain":        domain_record.name,
                "source_domain": source_domain,
                "trigger_event": event_type,
                "timestamp":     sovereign_time.now()
            })
            set_domain_state(human_id, domain_record.name, "suspended")


def escalate_probe_density(human_id, source_domain, severity):
    """
    Increase probe density across all other domains via CDCC registry modifier.
    Domain plugin event logs are not touched.
    """
    density_boost = 0.10 if severity == "low" else 0.20
    duration_days = 14   if severity == "low" else 30

    token = get_λ_token(human_id)
    for domain_record in token.domains:
        if domain_record.name != source_domain:
            cdcc_registry.set_modifier(
                human_id=human_id,
                domain=domain_record.name,
                boost=density_boost,
                duration_days=duration_days
            )
```

---

### Issue 1 Fix — Emergency Override State

If an integrity suspension locks a critical role across all domains, the system must not deadlock infrastructure that requires that role to execute emergency safety capsules. A suspended Master Certifier needed to authorise an emergency shutdown cannot be bypassed by remote request — but can be bypassed by physical, air-gapped, quorum-verified presence.

**Override rules — all conditions must be met simultaneously:**

1. Two independent Reflex Certifiers sign the override request cryptographically
2. The suspended actor authenticates physically via the air-gapped FORGE-os console (not remotely)
3. The override is time-bounded: maximum 4 hours, non-renewable during the same suspension
4. The override is logged to ChronoScribe in real time with no suppression possible
5. The override does not restore Λ-tier — it grants a single time-bounded execution window only

```python
EMERGENCY_OVERRIDE_DURATION_HOURS = 4

def request_emergency_override(suspended_human_id, domain, reason,
                                quorum_certifier_1_sig, quorum_certifier_2_sig,
                                physical_console_token):
    """
    Grant a time-bounded execution window to a suspended actor.
    Requires: 2× Reflex Certifier quorum + physical air-gapped console auth.
    Does NOT restore Λ-tier. Does NOT clear suspension. Single-use per suspension.
    """
    # Verify both quorum certifiers are Reflex tier and not themselves suspended
    for sig in [quorum_certifier_1_sig, quorum_certifier_2_sig]:
        certifier = verify_signature(sig)
        assert certifier.λ_tier == "reflex_certifier", "Quorum requires Reflex Certifier"
        assert get_domain_state(certifier.human_id, domain) == "active", "Quorum certifier must be active"

    # Verify physical console token (air-gapped FORGE-os only — not network-routable)
    assert verify_console_token(physical_console_token, suspended_human_id), \
        "Physical console authentication required"

    # Check override not already used for this suspension instance
    existing = cdcc_registry.query(
        human_id=suspended_human_id,
        event_type="EMERGENCY_OVERRIDE_GRANTED",
        since_event="CDCC_SUSPENSION"
    )
    assert len(existing) == 0, "Emergency override already used for this suspension"

    expiry = sovereign_time.now() + timedelta(hours=EMERGENCY_OVERRIDE_DURATION_HOURS)

    cdcc_registry.append({
        "event_type":            "EMERGENCY_OVERRIDE_GRANTED",
        "human_id":              suspended_human_id,
        "domain":                domain,
        "reason":                reason,
        "quorum":                [quorum_certifier_1_sig, quorum_certifier_2_sig],
        "physical_console_token": physical_console_token,
        "expiry":                expiry.isoformat(),
        "timestamp":             sovereign_time.now(),
        "suppressible":          False   # This entry cannot be hidden or deleted
    })

    return OverrideWindow(human_id=suspended_human_id, domain=domain, expiry=expiry)
```

---

**What this preserves:** A radiologist who drifts in financial compliance remains a radiologist. Domain specialisation is respected. Normal performance variation stays local.

**What this closes:**
- A Master Certifier flagged for fraud cannot maintain active authority in adjacent domains. The pipe is one pipe.
- Oscillating just above the demotion floor accumulates against a rolling window ceiling. Three performance events in 90 days triggers integrity review — the loophole is sealed.
- CDCC modifiers live in the CDCC registry, not in domain event logs. Suspension state changes are O(1) writes to a single registry entry, not O(N) replays across domain shards.
- Infrastructure deadlock from integrity suspensions is broken by air-gapped quorum override — physical presence, time-bounded, single-use, non-suppressible in the audit trail.

**CDCC events are ChronoScribe entries.** Every propagation, modifier, and override is logged with source domain, trigger event, and timestamp. The audit trail crosses domains. The tokens do not.

---

## 🧩 Blackboard Architecture + The Forgy Layer — The Control Layer

The Forge's symbolic reasoning core is built on two complementary patterns from classical AI: the **Blackboard architecture** for shared working memory and **The Forgy Layer** for trust-gated rule firing. Neither is new. What's new is running them with λ as the trust fabric threading through both.

---

### The Blackboard Pattern

A Blackboard is a shared working memory that independent specialist agents — Knowledge Sources — all read from and write to. No Knowledge Source talks directly to another. They watch the blackboard, and when they see facts they can contribute to, they write results back. A controller decides what fires next.

The DataCube is the blackboard. It's already append-only, cryptographically signed, and epistemically classified via the Six Lenses. Every domain plugin is a Knowledge Source — an independent specialist that understands one vertical and reads/writes to the shared surface. ChronoScribe is the audit trail of what fired and when.

The difference between classical Blackboard and The Forge is that classical Blackboard has no trust model — any Knowledge Source can write anything. Here, every write carries λ. The blackboard is not just shared memory. It's **trust-weighted shared memory.**

```
┌─────────────────────────────────────────────────────────────────┐
│                    BLACKBOARD (DataCube)                         │
│              λ-weighted shared working memory                    │
│                                                                  │
│  Facts (FACT lens, λ=0.91) ──────────────────────────────────── │
│  Hypotheses (FICTION lens, λ=0.44) ──────────────────────────── │
│  Partial solutions (CONTEXT lens, λ=0.76) ───────────────────── │
│  Anomaly flags (COUNTER lens, λ=0.88) ───────────────────────── │
└─────────────────────────────────────────────────────────────────┘
         ▲ read/write (λ-stamped)    ▲               ▲
         │                           │               │
  ┌──────┴──────┐           ┌────────┴──────┐ ┌──────┴──────┐
  │  Domain     │           │  Domain       │ │  Domain     │
  │  Plugin A   │           │  Plugin B     │ │  Plugin C   │
  │  (PAT)      │           │  (Medical)    │ │  (Financial)│
  └─────────────┘           └───────────────┘ └─────────────┘
         │                           │               │
         └───────────────────────────┴───────────────┘
                                     │
                        ┌────────────┴────────────┐
                        │      RETE WEIGHT         │
                        │  (λ-weighted controller) │
                        │  "what fires next, and   │
                        │   with how much trust?"  │
                        └─────────────────────────┘
```

---

### The Forgy Layer — λ-Weighted Rule Firing

Classical Rete is a pattern-matching algorithm that evaluates a rule set against working memory efficiently — it doesn't re-evaluate every rule on every change, only the parts of the network affected by what just changed (the alpha/beta network).

The Forgy Layer extends this: **a rule only fires if the facts matching its conditions collectively clear a λ threshold.** Low-trust facts can exist in working memory without triggering consequences until corroborated. High-trust facts fire immediately.

**The join aggregation rule: minimum λ across all contributing facts.**

A chain is only as strong as its weakest link. If a rule requires three facts and one has λ=0.42, the join doesn't fire regardless of how trusted the other two are. This is consistent with the rest of the stack — λ is a trust floor, not an average.

```python
class ReteWeightNode:
    """
    Beta node in the Rete network.
    A join fires only if the minimum λ across all matching facts
    clears the rule's required threshold.
    """
    def __init__(self, rule_id, required_λ, conditions):
        self.rule_id    = rule_id
        self.required_λ = required_λ   # rule-level trust threshold
        self.conditions = conditions   # list of fact patterns to match

    def evaluate(self, working_memory):
        matching_facts = []
        for condition in self.conditions:
            fact = working_memory.match(condition)
            if fact is None:
                return None   # condition not met at all
            matching_facts.append(fact)

        # Aggregate trust: minimum λ across all contributing facts
        join_λ = min(fact.λ for fact in matching_facts)

        if join_λ >= self.required_λ:
            return RuleFiring(
                rule_id       = self.rule_id,
                facts         = matching_facts,
                join_λ        = join_λ,
                fired_at      = sovereign_time.now(),
                confidence    = join_λ   # firing confidence = join trust
            )
        else:
            # Facts exist but trust insufficient — hold pending corroboration.
            # Pending queue is indexed by fact_pattern for O(matching rules) lookup.
            # Index is updated here on every add_pending() call.
            working_memory.add_pending(
                rule_id       = self.rule_id,
                facts         = matching_facts,
                current_λ     = join_λ,
                required_λ    = self.required_λ
            )  # add_pending() maintains a bi-directional index: fact_pattern ↔ rule_id
               # Both directions registered on every call — O(matching rules) lookup guaranteed
            return None
```

**What "hold pending corroboration" means:**

A low-trust fact match doesn't disappear. It sits in a pending queue. If a subsequent fact raises the minimum join λ above the threshold — new corroborating evidence, a human Fact Validator confirms ground truth, an independent source writes a CONTEXT lens entry — the pending rule fires retroactively. The blackboard is a living surface, not a snapshot.

```python
def on_new_fact_written(working_memory, new_fact):
    """
    When a new fact lands on the blackboard, re-evaluate pending rules
    that this fact might push over the λ threshold.

    SCALING NOTE: The pending queue is indexed by fact_pattern — lookup is
    O(matching rules), not O(all pending rules). Without this index, every
    fact write scans the full pending queue, which degrades at high throughput
    (10,000+ facts/day). The index is maintained on every add_pending() call.
    """
    # Index lookup: only rules whose conditions match this fact's pattern
    affected_pending = working_memory.get_pending_for_fact(new_fact)
    # O(matching rules) — not O(all pending rules)

    for pending_rule in affected_pending:
        updated_λ = min(f.λ for f in pending_rule.facts + [new_fact])

        if updated_λ >= pending_rule.required_λ:
            fire_rule(pending_rule.rule_id, pending_rule.facts + [new_fact], updated_λ)
            working_memory.remove_pending(pending_rule.rule_id)
```

---

### The Forgy Layer + Six Lenses

The Six Lenses aren't just labels — they constrain which facts can participate in which rule joins. A FICTION lens claim (speculative, λ=0.44) cannot join with a FACT lens claim to fire a consequence rule. Epistemic type is a hard gate before λ is even evaluated.

```python
LENS_JOIN_RULES = {
    # consequence rules — require FACT or COUNTER lens only
    "consequence": ["FACT", "COUNTER"],

    # hypothesis rules — can include FICTION and OPINION
    "hypothesis":  ["FACT", "COUNTER", "OPINION", "FICTION", "CONTEXT"],

    # audit rules — require FACT and CONTEXT provenance
    "audit":       ["FACT", "CONTEXT"],

    # dispute rules — require all lenses (full epistemic picture)
    "dispute":     ["FACT", "COUNTER", "OPINION", "FICTION", "CONTEXT", "UNKNOWN"]
}

def lens_gate(rule_type, facts):
    """Hard gate: all facts must have an allowed lens for this rule type."""
    allowed = LENS_JOIN_RULES[rule_type]
    for fact in facts:
        if fact.lens not in allowed:
            return False, f"Lens {fact.lens} not permitted in {rule_type} rule"
    return True, "ok"
```

---

### The Forgy Layer + λ — The Full Control Flow

```
New fact written to DataCube (blackboard)
    │
    ▼
ChronoScribe timestamps and signs it
    │
    ▼
Six Lenses classifies it (FACT / COUNTER / OPINION / FICTION / CONTEXT / UNKNOWN)
    │
    ▼
Forgy Layer alpha network — does this fact match any rule condition?
    │
    ├── No match → stored in working memory, no rule evaluation
    │
    └── Match found → beta network join evaluation
            │
            ▼
        Lens gate: are all joining facts the right epistemic type?
            │
            ├── Fail → fact stored, join blocked on lens grounds
            │
            └── Pass → λ aggregation (minimum across all joining facts)
                    │
                    ├── join_λ < required_λ → hold pending corroboration
                    │        (re-evaluates when new facts arrive)
                    │
                    └── join_λ ≥ required_λ → RULE FIRES
                                │
                                ▼
                        RuleFiring written to DataCube
                        with rule_id, facts, join_λ, timestamp
                                │
                                ▼
                        Knowledge Source executes
                        writes result back to blackboard
                        with its own λ stamp
```

---

### Where It Lives in the Stack

| Component | Role |
|-----------|------|
| `rete_engine.py` | The Forgy Layer — alpha/beta network, rule evaluation, pending queue + fact_pattern index |
| `blackboard.py` | Working memory interface — read, write, match, pending |
| `DataCube` | Persistent blackboard storage — append-only, signed |
| `ChronoScribe` | Audit trail of every fact write and rule firing |
| `Anchor` | Rule definitions — `anchor_genesis.json` and `rules/` feed the Rete network |
| `Aethina` | Neurosymbolic bridge — LLM sits above The Forgy Layer, not inside it |
| Domain Plugins | Knowledge Sources — each plugin is a specialist agent on the blackboard |

**Aethina sits above The Forgy Layer, not inside it.** The LLM is a hot-swappable boundary that can propose new facts to the blackboard or interpret results — but every fact it writes carries λ derived from the model's track record, goes through the lens gate, and fires rules only if it clears the threshold. The LLM doesn't bypass the trust fabric. It participates in it.

**LLM Trust Inheritance Invariant.** Model λ is a derived, dependent property. An LLM cannot independently generate or earn baseline trust. It inherits its operational λ ceiling from the historical accuracy records of the human Fact Validators who certify its training distributions and audit its live production probes against physical ground truth. An LLM has no moral agency and cannot carry legal consequence. Its λ is borrowed, not owned. The human who certified it is the accountable party.

---

### The One-Line Summary

**The DataCube is the blackboard. The Forgy Layer is the controller that decides what fires, based on whether the facts supporting a rule collectively carry enough trust to act on.**

Same pipes, different water. Same rule engine, different trust thresholds per domain.

---

## 🌐 Domain-Specific Plugins

The Forge is agnostic at its core and specific in its plugins. Same accountability pipes, different domain water.

```yaml
domain_plugin:
  name: "industrial_pat_testing"
  version: 2.0

  ground_truth:
    source: "followup_inspection"
    latency: "7 days"
    validator_role: "fact_validator"
    automated: false

  constraints:
    - id: "resistance_safety"
      rule: "if insulation_resistance < 1.0 then output MUST be FAIL"
      lens: "FACT"
    - id: "leakage_safety"
      rule: "if leakage_current > 5.0 then output MUST be FAIL"
      lens: "FACT"

  risk_thresholds:
    false_positive_max: 0.05
    false_negative_max: 0.01
    measurement_window: "90_days"

  consequences:
    - trigger: "false_negative_rate > 0.01"
      action: "suspend_model"
      authorizer: "safety_officer"
      appeal_window: "7 days"
    - trigger: "scp_violation_count > 3 in 30_days"
      action: "revoke_certification"
      authorizer: "regulator"
      appeal_window: "30 days"

  λ_tier_requirements:
    validator_floor:   "validator"
    senior_floor:      "senior_validator"
    master_floor:      "master_certifier"
    consequence_floor: "master_certifier"
    dispute_floor:     "master_certifier"
```

**Adding a New Domain**

```bash
./forge domain-create --name medical_diagnosis --template industrial_pat_testing
vim DomainPlugins/medical_diagnosis/plugin.yaml
./forge domain-add-constraint \
  --domain medical_diagnosis \
  --rule "if malignancy_probability > 0.95 then output MUST be BIOPSY"
./forge domain-set-ground-truth \
  --domain medical_diagnosis \
  --source biopsy \
  --latency 14_days
./forge domain-register medical_diagnosis
```

---

## 🗂️ The λ Reputation Token

λ is not a number in a database. It is a cryptographically signed token, portable across any system running The Forge stack.

```json
{
  "human_id": "james_the_giblet",
  "state": "active",
  "last_update": "2026-06-08T14:32:01Z",
  "domains": [
    {
      "name": "industrial_pat_testing",
      "λ_current": 0.91,
      "λ_tier": "master_certifier",
      "validations": 15420,
      "probe_pass_rate": 0.94,
      "accuracy_90d": 0.94,
      "appeals_upheld": 0.98,
      "last_active": "2026-06-08T10:00:00Z",
      "decay_buffer_remaining_days": 5
    },
    {
      "name": "medical_device_safety",
      "λ_current": 0.76,
      "λ_tier": "senior_validator",
      "validations": 342,
      "probe_pass_rate": 0.88,
      "accuracy_90d": 0.82,
      "last_active": "2026-06-01T09:00:00Z",
      "decay_buffer_remaining_days": 0
    }
  ],
  "signature": "0x9f3b2c...",
  "issued": "2026-06-08T14:32:01Z",
  "issuer": "forge_theory_labs_hal_v1"
}
```

This token is the resume. Not years. Not degrees. Not interview performance. λ + Λ-tier + domain specificity + time active. Any employer running a HAL-compatible system can verify it against the ChronoScribe audit trail. It is not self-reported. It is the record.

---

## 🖥️ Repository Structure

```
The_Forge/
│
├── explorer-d334/              # Portable AI forge (Android)
│   ├── forge                   # Main executable
│   ├── commands/               # 40+ AI commands
│   ├── src/                    # Python source
│   └── web/                    # Web interface (port 8085)
│
├── GibletsForgeOS/             # Bare-metal kernel (Ryzen)
│   ├── kernel.c
│   ├── interpreter.c
│   ├── leighton_weight.c       # λ calculation + state machine
│   ├── forge_time.c            # Sovereign timekeeper
│   └── primitives/             # 100+ C primitives
│
├── ForgeMind/                  # Autonomous training pipeline
│   ├── orchestrator/
│   ├── trainer/                # QLoRA fine-tuning
│   └── warden/                 # Safety gates
│
├── Aletheia/                   # Truth & verification layer
│   ├── verifier/               # Claim splitting, lens classification
│   ├── datacube/               # Immutable ledger, event sourcing
│   ├── blackboard.py           # Shared working memory interface
│   ├── rete_engine.py          # The Forgy Layer — λ-weighted rule firing
│   └── api/                    # FastAPI (port 8000)
│
├── Capsules/                   # Shared SCPs (97+)
│   ├── weekday/
│   ├── weekend/
│   └── system/
│
├── Anchor/                     # Deterministic rule engine (zero AI in v1)
│   ├── anchor_genesis.json     # Foundational rule set — feeds The Forgy Layer
│   ├── rules/                  # Domain-specific rule definitions
│   ├── dispute/                # DISPUTE capsules — contradiction resolution
│   └── README.md
│
├── DomainPlugins/              # Domain-specific modules
│   ├── industrial_pat_testing/ # Reference implementation
│   │   ├── plugin.yaml
│   │   ├── constraints.py
│   │   ├── ground_truth.py
│   │   └── test_probes.json
│   ├── medical_diagnosis/      # In development
│   └── financial_lending/      # Planned
│
├── Products/                   # 21 commercial tools
│
├── Edge/                       # Edge hardware
│   ├── esp32-c6/
│   └── arduino/
│
├── Scripts/
│   ├── forge-push.sh
│   ├── forge-sync.sh
│   └── micro_gateway.py
│
├── Theory/
│   ├── README.md
│   ├── axioms.md
│   ├── UNIFIED_THEORY.md
│   ├── INTELLECTUAL_PROVENANCE.md      # Academic lineage + architectural mutations
│   ├── HUMAN_ACCOUNTABILITY_LAYER.md   # Full technical thesis
│   ├── HAL_linkedin.md                 # Non-technical framing
│   ├── human_training_pipeline.md      # Full training pipeline spec
│   └── whitepapers/
│
└── DataCube/
    ├── blocks/                 # Append-only block files
    ├── events/                 # ChronoScribe event log
    │   └── cdcc_registry.db    # Cross-Domain Cross-Check modifiers (isolated)
    └── index.db                # SQLite state index
```

---

## 🚀 Quick Start

### Android — Explorer-d334

```bash
# Install Termux (F-Droid, NOT Play Store)
pkg update && pkg upgrade
pkg install python git openssl termux-api

git clone https://github.com/Forge-Theory-Labs/The_Forge.git
cd The_Forge/explorer-d334
chmod +x forge start_forge.sh stop_forge.sh

./start_forge.sh
./forge health
./forge lens classify "Resistance is 0.95 MΩ"
./forge λ get --human james_the_giblet --domain industrial_pat_testing
./forge tier get --human james_the_giblet --domain industrial_pat_testing
./forge probe stats
./forge blackboard status
./forge rete rules
./forge web   # http://localhost:8085
```

### Ryzen — FORGE-os

```bash
cd GibletsForgeOS
make clean && make
sudo dd if=usb-image/disk.img of=/dev/sdX bs=4M status=progress
# Boot from USB. Connect Pi Zero USB gadget for network.
```

### Laptop — ForgeMind + Aletheia

```bash
pip install -r requirements.txt

# Aletheia API
cd Aletheia/api && python app.py   # port 8000

# ForgeMind training loop
cd ForgeMind/orchestrator && python loop.py

# Probe injection
./forge probe-inject --domain industrial_pat_testing --rate 0.10
```

---

## 📊 Key Commands

| Command | Function |
|---------|----------|
| `./forge health` | Full system status |
| `./forge λ get --human <id> --domain <domain>` | Current λ score |
| `./forge λ history --human <id>` | λ change history |
| `./forge tier get --human <id> --domain <domain>` | Current Λ-tier |
| `./forge lens classify <text>` | Classify into Six Lenses |
| `./forge audit --role auditor` | Review flagged violations |
| `./forge probe stats` | Test probe statistics |
| `./forge domain-list` | Available domain plugins |
| `./forge domain-use --domain <name>` | Switch active domain |
| `./forge cube-verify` | Verify Data Cube integrity |
| `./forge blackboard status` | Show current working memory state |
| `./forge blackboard pending` | List rules held pending corroboration |
| `./forge rete rules` | List all Forgy Layer rules and their λ thresholds |
| `./forge rete simulate --fact <json>` | Dry-run a fact against the Rete network |

---

## 👥 The Human Accountability Layer — Full Thesis

The complete technical specification of the HAL, including role definitions, ChronoScribe integration, SCP integration, and the economic model: [Theory/HUMAN_ACCOUNTABILITY_LAYER.md](Theory/HUMAN_ACCOUNTABILITY_LAYER.md)

The non-technical framing for general audiences: [Theory/HAL_linkedin.md](Theory/HAL_linkedin.md)

---

*I wanted it. So I forged it. Now forge yours.*

— James Gilbert | Forge Theory Labs | 2026
