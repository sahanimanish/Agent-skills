# Client Classification Framework

This file defines the three independent classification systems used to describe a client
and explains precisely what each system controls during PR/CR processing. The agent must
understand the boundaries between these systems to avoid applying the wrong classification
to the wrong decision.

---

## The Three Classification Systems

### System 1 -- KYC Client Type

Values: individual-retail, corporate-business, trust-foundation, financial-institution, pep

What it controls: everything related to due diligence obligations. Which documents the
client must provide. Which screening checks are required. Which approval roles must sign
off. Which rule atoms in the KYC Policy KnowledgePack apply. Which verification actions
are triggered by each client document.

When the agent looks up policy requirements, it filters by KYC client type. Size and
segment are never used to filter rule atoms.

How it is determined: from the nature of the client entity itself. A natural person is
individual-retail. A legal entity is corporate-business, trust-foundation, or
financial-institution depending on its legal form. PEP is an overlay applied on top
of any of the other four types when PEP status is identified.

Can it change: yes. A client can be reclassified if the nature of their entity changes
or if a PEP overlay is newly identified. A reclassification is always a blocking material
change.

---

### System 2 -- Segment

Values: smb, services, markets, banking

What it controls: the internal business segment that owns the client relationship. Segment
drives the periodic review cycle frequency through its contribution to the client risk
rating. A segment change over time is a material change trigger because it may change the
risk rating and therefore the review cycle.

Segment does not control: document requirements, screening obligations, approval chains,
or rule atom selection. None of these are filtered by segment.

How it is determined: assigned at onboarding based on the type of products and services
the client uses and the business unit that manages the relationship. Banking segment
clients are typically the most complex and most regulated. SMB segment clients are
typically simpler with lower transaction volumes.

Can it change: yes. A client can move between segments as their business grows or as
their product usage changes. A segment change must be recorded and assessed for its
impact on the risk rating and review cycle.

---

### System 3 -- Size

Values: large, medium, small

What it controls: the size classification of the client, which together with segment
determines the client risk rating. The risk rating determines the PR/CR cycle frequency.

Size does not control: document requirements, screening obligations, or rule atom
selection independently.

How it is determined: from financial metrics or turnover thresholds defined internally.
The specific thresholds for each size band (what revenue or asset size qualifies a client
as large, medium, or small) are defined in the organisation's internal policy and are
referenced in the KYC Policy KnowledgePack. The agent reads the applicable thresholds
from the policy rather than applying hardcoded values.

Can it change: yes. A client's size classification changes as their financials change.
A size reclassification is a material change if it results in a change to the risk rating.

---

## How the Three Systems Combine During PR/CR

### Step 1 -- Determine all three classifications

At the start of every review the agent must determine the current value of all three
classifications from the available evidence:

KYC client type: from the nature of the entity (Orbis, registrar, trust deed).
Segment: from the onboarding form and internal records. Corroborated against the
relationship manager's current assignment if that information is available.
Size: from the most recent financial data available -- Moodys where available, then
audited financial statements, then Orbis financial extracts.

For each classification, record its source and confidence level. An unverified size
or segment classification is flagged but does not block the review unless it produces
a risk rating that differs materially from the prior review.

### Step 2 -- Derive the risk rating

The risk rating is derived from the combination of segment and size. The derivation
logic is defined in the KYC Policy KnowledgePack under the risk rating matrix. The
agent reads the risk rating matrix and applies it to the current segment and size values.

The risk rating has values: low, medium, high, or EDD-mandatory.

Record the derived risk rating and compare it against the prior review risk rating.
A change in risk rating is always a material change regardless of its direction.

### Step 3 -- Determine the PR/CR cycle from the risk rating

The PR/CR cycle frequency is determined by the risk rating. The cycle definitions
are in the KYC Policy KnowledgePack. The agent reads the cycle for the current risk
rating and records:

The current cycle frequency (for example: annually, every two years, every three years).
The date the last review was conducted.
The date the next review is due based on the current cycle.
Whether the current review is on time, overdue, or early.

An overdue review is flagged in the Triage Report. The reviewing officer must note
the reason for the delay.

### Step 4 -- Use KYC client type for all rule atom lookups

All policy questions, gap analysis, and document requirement checks use KYC client type
only. The agent never filters rule atoms by segment or size. This is a firm boundary.

If a reviewer asks a policy question that seems segment-specific (for example: "what
does a Banking segment client need?"), the agent clarifies that document and screening
requirements are determined by KYC client type, not segment, and asks which KYC client
type the client is before answering.

---

## Classification Change Detection During Change Comparison

During the change comparison step (Phase 2, Query Type 3), the agent must explicitly
check for changes in all three classifications, not just KYC client type.

### KYC client type change

Always a blocking material change. The applicable rule atoms change entirely. The gap
analysis must be rerun under the new type before the review can be concluded.

### Segment change

A material change that must be assessed for risk rating impact. Steps:
1. Record the prior segment and the current segment.
2. Derive the risk rating under the new segment (holding size constant).
3. Compare the new risk rating against the prior risk rating.
4. If the risk rating has changed: record as a risk rating material change and determine
   the new PR/CR cycle frequency.
5. If the risk rating has not changed despite the segment change: record the segment
   change as a non-blocking material change for documentation purposes.

### Size change

A material change that must be assessed for risk rating impact. Same steps as segment
change above, holding segment constant and varying size.

### Simultaneous segment and size change

If both have changed, derive the new risk rating from the new segment and size combination
together. Do not assess each independently if the combined effect is what matters.

---

## Recording Classifications in the Client Record

The Reconciled Client Record must carry all three classifications with their sources
and confidence levels. See the client-record-schema.json for the field structure.

The review output must show all three classifications in the Client Summary section
and must explicitly state whether any classification has changed since the prior review.

The risk rating derived from segment and size must be shown separately from the effective
due diligence tier derived from KYC client type and jurisdiction. These are two different
risk concepts and must not be conflated:

The segment-and-size risk rating determines the review cycle frequency.
The KYC due diligence tier (SDD, standard, EDD) determines what the review must assess.

Both are recorded. Both are compared against the prior review. Both are shown to the
reviewer. They are never merged into a single risk label.
