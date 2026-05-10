# Reconciliation Rules (Partial Source Set Edition)

This file defines how the agent resolves conflicts between sources when building the
Reconciled Client Record, including how to handle situations where the normal governing
source is not available.

---

## The Core Principle

A conflict exists whenever two or more available sources provide different values for the
same data point. The higher-tier source governs. The discarded value is always recorded.
The conflict is always disclosed. The agent never silently resolves a conflict.

When the normal governing source is not available, the next available source in the
authority hierarchy for that data type takes the governing role -- but the confidence
of the reconciled value is explicitly reduced. The agent records that the normal governing
source was absent.

---

## When the Primary Source Is Not Available

For each data dimension, if the primary source is absent, apply this fallback logic:

**Ownership and UBO -- Orbis not available**
Next available: company registrar database (Tier 2) for registered directors and shareholders.
Then: client-provided UBO declaration and corporate structure chart (Tier 3).
Confidence: Limited if relying on Tier 3 alone. The agent must state: ownership assessment
is based on client-provided documents only. No independent corroboration was available.

**PEP and Sanctions -- LexisNexis not available**
No fallback source can substitute for LexisNexis for PEP and sanctions determination.
The client's sanctions-pep-self-declaration is recorded as client-stated but is not
an independent verification. The agent must state: PEP and sanctions status cannot be
independently determined. This review cannot be concluded without LexisNexis screening
or a documented exception approved by the appropriate compliance role.

**Legal entity details -- Company registrar not available**
Next available: Orbis (may lag but is derived from registry data).
Then: client-provided company registration document (Tier 3).
Confidence: Reduced if relying on Orbis. Limited if relying on client document only.

**Financial risk -- Moodys not available**
Next available: audited financial statements (Tier 3) from a recognised auditor.
Then: management accounts (Tier 3, lower weight), Orbis financial extracts.
Confidence: Reduced if relying on audited accounts. Limited if relying on management
accounts or Orbis extracts only.

**Identity of natural persons -- LexisNexis screening not run**
No fallback can independently screen for PEP status or sanctions. However, identity
verification from government-issued-photo-id can still proceed for the purpose of
establishing name and date of birth. The screening gap is recorded separately.

---

## Conflict Types and How to Handle Each

### Conflict between two available sources (standard conflict)

Apply the authority hierarchy per the Source Authority Matrix. The higher-ranked source
governs. Record the conflict, the governing value, and the discarded value.

### Conflict between an available secondary source and an absent primary source

The secondary source provides the best available value. Record the value with reduced
confidence. Note explicitly that the primary source was not available to corroborate or
override. Do not treat the secondary source value as equivalent in authority to the
primary source.

### Conflict between a client-provided document and an available independent source

The independent source governs per its tier ranking. The client document value is the
discarded value. Record both. Flag the discrepancy as a risk signal -- a client document
that contradicts an independent source may indicate misrepresentation.

### Conflict between two client-provided documents (both Tier 3)

When two client-provided documents of the same type provide different values (for example
two versions of a UBO declaration with different percentages), record both, flag as a
document inconsistency gap, and refer to the reviewer. The agent cannot resolve a conflict
between two client documents without an independent source to act as arbiter.

### Conflict between a news article signal and an independent source

If a news article alleges something that is not corroborated by a Tier 1 or official Tier 2
source: record as an unconfirmed adverse signal. Do not treat it as a confirmed finding.
If a Tier 1 or official Tier 2 source confirms the same event: the official source governs
as the confirmed finding. The news article is recorded as a corroborating signal.

---

## Three States That Must Never Be Confused

**Verified**: a client-provided document's key claims have been checked against an
available independent source and no material discrepancy was found.

**Unverified -- source not available**: the document is present but the independent source
needed to verify it was not provided. The claims are client-stated, unverified. This is
not a failure -- it is a transparency state that the reviewer must be aware of.

**Discrepancy found**: the document's claims were checked against an independent source
and a material difference was identified.

These three states are recorded for every Tier 3 document in the Document Verification
Record. They are never collapsed or implied. An unverified document is not the same as
a verified document, and a discrepancy is not the same as an unverified document.

---

## Confidence Propagation

When a data point is assembled from multiple sources, its confidence level is the lowest
confidence among the sources that contributed to it. If a dimension relies on:

A Tier 1 source with high confidence extraction: the dimension confidence is high.
A Tier 2 source with high confidence extraction (no Tier 1 available): reduced.
A Tier 3 source with high confidence extraction (no Tier 1 or 2 available): limited.
No source at all: not assessed.

Confidence does not improve when multiple low-confidence sources agree. Three client
documents agreeing on an ownership structure does not produce the same confidence as
one Orbis report. Corroboration increases plausibility but it does not increase the
evidential tier.
