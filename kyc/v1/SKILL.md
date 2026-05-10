---
name: client-data-curator-prcr-v3
description: >
  Use this skill when an agent needs to read, reconcile, and reason over client data
  during a Periodic Review (PR) or Client Review (CR). The agent works with whatever
  documents are available for the client -- no source is assumed to exist. Missing
  sources are recorded explicitly and their impact on review completeness is assessed.
  Sources span four tiers: Tier 1 independent providers (LexisNexis, Moodys, Orbis),
  Tier 2 public and approved sources (company registrars, stock exchange filings, news,
  internal watchlists), Tier 3 client-provided documents (13 document types including
  identity documents, proof of address, company registration, trust deeds, UBO
  declarations, PEP/sanctions self-declarations, source of funds and wealth evidence,
  financial statements, regulatory licences, authorised signatory lists, corporate
  structure charts, professional reference letters, tax identification documents),
  and Tier 4 internal records (prior review output, onboarding form).
---

# Client Data Curator -- PR/CR Process (Partial Document Handling)

Processes whatever client documents are available, builds a Reconciled Client Record
from available evidence, assesses completeness explicitly, and enables the agent to
answer PR/CR queries with honest disclosure of what could and could not be assessed.

---

## Core Design Principle: Available Evidence Only

The agent never assumes a document exists. Every source and document type has three
possible states that must be distinguished at all times:

**Available and assessed** -- the document was provided, classified, extracted from,
and included in the Reconciled Client Record.

**Not provided -- impact known** -- the document was not provided. The agent knows from
the KYC policy what this document would have been required to prove, and records the
resulting gap and its severity classification.

**Not applicable** -- the document type does not apply to this client type or situation.
For example, a trust deed is not applicable for an individual retail client. A stock
exchange filing is not applicable for an unlisted entity. Recording not-applicable
separately from not-provided is essential -- they have different implications.

The agent must never treat not-provided as not-applicable. These are different states
with different consequences. A missing Orbis report for a corporate client is a gap
that reduces the confidence of the ownership assessment. The absence of a stock exchange
filing for an unlisted entity is simply not applicable.

---

## Two-Phase Processing Model

Phase 1 and Phase 2 are always distinct. Phase 1 builds the Reconciled Client Record
from whatever is available. Phase 2 answers queries against that record. The agent must
complete Phase 1 before answering any Phase 2 query.

Phase 1 is itself split into two steps to allow early detection of critical missing
sources before the full extraction is done.

---

## Phase 1, Step A -- Triage: Classify and Assess Completeness

This step runs immediately when documents are received. It does not extract data. It
inventories what is present and what is missing, and assesses the impact of missing
sources before extraction begins.

### Sub-step A1 -- Classify every item received

For each document or data item received, classify it into its tier and source type
using the Source Type Catalogue. Assign one of three classification outcomes:

Classified: the item is confidently identified as a specific source type.
Uncertain: the item resembles a source type but cannot be confidently classified.
Unclassifiable: the item cannot be matched to any known source type.

Uncertain and unclassifiable items are set aside and flagged for reviewer confirmation.
They are not included in any extraction step until classified.

### Sub-step A2 -- Build the Document Inventory

Produce a complete inventory of all received items with their classification outcome.
Then, for this client type and risk level, list every source and document type that the
KYC policy requires or recommends. For each required item mark it as one of:

Received and classified
Received but uncertain -- awaiting confirmation
Not provided
Not applicable

### Sub-step A3 -- Assess critical gaps before extraction

Before doing any extraction, assess whether any critical source is missing. A critical
source is one whose absence means a core dimension of the client profile cannot be
assessed at all. Critical sources by dimension are:

Ownership and UBO: Orbis is the primary source. If Orbis is not provided, the ownership
assessment will rely entirely on client-provided documents (UBO declaration, corporate
structure chart) with no independent corroboration. This is a significant reduction in
confidence that must be disclosed. If neither Orbis nor any client ownership document is
provided, the ownership dimension cannot be assessed at all.

PEP and sanctions: LexisNexis is the authoritative source. If LexisNexis is not provided,
PEP and sanctions cannot be determined from client documents alone. A client PEP and
sanctions self-declaration exists but cannot substitute for independent screening. If
LexisNexis is missing, this is a critical gap that must be flagged immediately and the
review cannot be concluded without it or an explicit documented exception.

Identity: government-issued-photo-id is required for every natural person subject to
verification. If identity documents are absent for a subject, that person cannot be
verified. List each unverified individual explicitly.

Financial risk: if Moodys is not provided and no audited financial statements are
available, financial risk cannot be independently assessed. Record as an unassessed
dimension.

### Sub-step A4 -- Report the triage outcome

Produce a Triage Report before proceeding to extraction. The Triage Report contains:

The Document Inventory table with received/not-provided/not-applicable status for every
required item.

The Critical Gap List: any critical source that is missing, the dimension it affects,
and whether the review can proceed without it or requires an exception.

The Uncertain Items List: any received item that could not be confidently classified,
with a request to the reviewer for confirmation.

The Proceed or Pause decision: state whether extraction can proceed with the available
documents, or whether the review should be paused to obtain critical missing sources
before continuing.

If the reviewer instructs to proceed despite critical missing sources, record this as a
reviewer-directed exception. The exception must appear in the final review output.

---

## Phase 1, Step B -- Extract, Verify, and Reconcile

This step runs after the Triage Report has been reviewed and the proceed decision has
been made. It operates only on classified, available documents.

### Sub-step B1 -- Extract from each available source

For each classified document, extract the relevant data fields using the appropriate
extraction guide for that tier and source type. Every extracted value carries:

The source it came from.
The confidence level: high, medium, low, or not-found within the document.
The date of the source document.

For data dimensions where the primary source is not available, extract from the next
available source in the authority hierarchy for that data type. Record explicitly that
the extraction is from a secondary or tertiary source. The confidence of the dimension
overall is reduced when primary sources are absent.

### Sub-step B2 -- Verify client documents against independent sources

For every Tier 3 document that has been extracted, check whether the verification
requirement for that document type has been met by an available independent source.

If the independent source required for verification is available: perform the verification
and record the outcome (verified, discrepancy found, partially verified).

If the independent source required for verification is not available: record the
verification as not possible -- independent source not provided. This is a verification
gap with reduced confidence, not an error. The document is still included in the record
as available evidence but its claims are marked as unverified.

Every Tier 3 document has one of three verification states in the Reconciled Client Record:

Verified: the key claims in the document have been confirmed by an available independent
source and no material discrepancy was found.

Unverified -- source not available: the document is present but the independent source
needed to verify it was not provided. The document's claims are included in the record
as client-stated, unverified.

Discrepancy found: the document's claims were checked against an independent source and
a material difference was identified. Record both values and apply the authority hierarchy.

### Sub-step B3 -- Reconcile conflicts

For every data point where two or more available sources provide different values, apply
the authority hierarchy per the Source Authority Matrix. Record every conflict in the
Conflict Register regardless of how it was resolved.

When a conflict involves a source that would normally govern but is absent, the next
available source in the hierarchy takes the governing role for that data point, but the
confidence of the reconciled value is reduced. Record explicitly that the normal governing
source was not available.

### Sub-step B4 -- Build the Reconciled Client Record

Assemble all extracted, verified, and reconciled data into the Reconciled Client Record.
Every field in the record must carry:

The reconciled value.
The source it came from.
The verification state (verified, unverified, not assessed).
The confidence level of that field given the sources available.
Any conflict that was resolved and the discarded value.

Dimensions that could not be assessed at all because no relevant source was available
must be recorded as not assessed -- source not provided, not as empty or unknown. The
distinction is important: unknown means the data may exist but was not found in a source.
Not assessed means no source was available to assess this dimension.

---

## Phase 2 -- Answer PR/CR Queries Against the Record

All Phase 2 queries operate against the Reconciled Client Record. The agent never returns
to raw documents to answer a query.

### How missing sources affect Phase 2 answers

When the agent answers a policy question, flags a gap, or generates a review summary,
it must reflect the confidence limitations introduced by missing sources.

For policy questions: the agent answers from the available evidence and discloses when
a dimension relevant to the answer could not be assessed. For example, if asked whether
the client needs EDD and the jurisdiction cannot be confirmed because Orbis was not
provided and the client-stated jurisdiction is unverified, the agent states the answer
based on the client-stated jurisdiction and explicitly discloses that the jurisdiction
is unverified.

For gap flagging: missing sources generate two types of gap entries.

A source gap: the source itself is missing and its absence prevents a dimension from
being fully assessed. Record as a gap with the severity determined by how critical the
source is for this client type.

A document gap: a specific document type required by policy was not provided. Record
as a gap with severity per the Gap Classification Guide.

These are different. A missing Orbis report is a source gap affecting the entire ownership
dimension. A missing UBO declaration is a document gap for one specific required document.
Both must be recorded but they are handled differently.

For change comparison: if a source was available at the prior review but is not available
at the current review, this is itself a material change signal. The agent must flag that
a source present previously is now absent and ask the reviewer to confirm whether the
omission is deliberate.

For review summary generation: the Source Coverage Summary in Section A of the review
output must be complete and honest. It lists every required source, its availability
status, and the impact of any missing source on the overall confidence of the review.

---

## Confidence Scoring for the Overall Review

The Reconciled Client Record carries an overall confidence score for the review based
on which sources were available. This is not a numerical score -- it is a structured
assessment across five dimensions.

For each dimension state one of:

Full confidence: all primary and key corroborating sources for this dimension were
available and consistent.

Reduced confidence: the primary source for this dimension was available but one or more
corroborating sources were absent. The primary source's findings stand but could not
be independently confirmed.

Limited confidence: the primary source for this dimension was not available. The
assessment relies on secondary sources or unverified client-provided documents only.

Not assessed: no source relevant to this dimension was available. This dimension cannot
be evaluated and must be flagged as a critical gap.

The five dimensions are: identity and registration, ownership and UBO, PEP and sanctions,
financial risk, and document compliance.

The review output presents this confidence assessment explicitly in the Source Coverage
Summary so the reviewing officer understands what the review was and was not able to assess.

---

## Reviewer Decision Points

The agent presents two formal decision points to the reviewer.

Decision Point 1 -- After Triage (Phase 1 Step A): the reviewer sees the Triage Report
and decides whether to proceed with available documents or pause to obtain missing sources.
The agent states a recommended action: proceed if no critical sources are missing, pause
if one or more critical sources are absent. The reviewer decides and the decision is
recorded.

Decision Point 2 -- After Review Summary (Phase 2): the reviewer sees the full review
output including confidence assessments and gap analysis and makes the final review
decision. The agent provides the system recommendation. The reviewer decides.

---

## Rules the Agent Must Always Follow With Partial Document Sets

Never treat an absent source as a negative finding. A missing Orbis report does not
mean the ownership structure is clean -- it means the ownership structure cannot be
independently verified. These are different statements and the agent must use the correct
one.

Never treat an absent source as evidence that the information does not exist. The
information may exist but was not provided. Record as not provided, not as not found.

Never reduce the confidence of a confirmed finding from an available source because
another source is missing. If LexisNexis returns a confirmed PEP finding, the finding
is confirmed regardless of what other sources are or are not available.

Never upgrade the confidence of an unverified client-provided document because no
independent source is available to contradict it. The absence of contradiction is not
corroboration. A UBO declaration is unverified if Orbis was not available, not verified.

Always state the basis for every answer in Phase 2, including which sources were used
and which were not available. The reviewer must always know what the answer is built on.

Always distinguish between three states: verified by independent source, unverified
because independent source not provided, and unverified because independent source
found a discrepancy. These three states have different implications and different
required actions.

---

## Reference Files

- references/source-type-catalogue.md -- how to classify every source type into its tier
- references/triage-report-template.md -- blank triage report for Phase 1 Step A output
- references/document-type-registry.md -- authority scope and verification requirement per document type
- references/tier1-extraction-guide.md -- extraction rules for Moodys, Orbis, LexisNexis
- references/tier2-extraction-guide.md -- extraction rules for registrars, stock exchange, news, watchlists
- references/tier3-document-extraction-guide.md -- extraction rules for all 13 client document types
- references/source-authority-matrix.md -- per-data-type authority and conflict resolution
- references/reconciliation-rules.md -- full conflict resolution protocol including partial source sets
- references/gap-classification-guide.md -- blocking vs non-blocking including source gaps
- references/material-change-triggers.md -- material changes including source availability changes
- references/agent-query-protocol.md -- Phase 2 reasoning protocol for each query type
- references/prcr-review-template.md -- full seven-section review output template
- references/client-record-schema.json -- JSON Schema for the Reconciled Client Record
