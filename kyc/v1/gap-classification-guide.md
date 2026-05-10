# Gap Classification Guide (Partial Source Set Edition)

This file defines how to classify every gap identified during PR/CR, including gaps
that arise specifically because sources were not available. Three gap types now exist:
document gaps, verification gaps, and source gaps.

---

## The Three Gap Types

**Document gap**: a document type required by the KYC policy for this client type,
jurisdiction, and risk level was not provided. The document is absent from the client
file.

**Verification gap**: a document was provided and is present in the CIP record, but
the independent source required to verify its claims was not available. The document
exists but its claims are unverified.

**Source gap**: a data source (Tier 1 or Tier 2) that the KYC policy or the review
process depends on was not provided. Its absence reduces the confidence of one or more
assessment dimensions. Source gaps are broader than document gaps -- they affect entire
dimensions rather than individual document requirements.

These three types are distinct and must be recorded separately. A source gap and a
document gap can exist simultaneously for related requirements. Record both.

---

## Blocking Gap Triggers (Updated for Partial Source Sets)

The following gaps are always blocking regardless of source availability:

All blocking triggers from the prior version apply unchanged: prohibited jurisdiction,
confirmed sanctions match, PEP without EDD, UBO not identified, UBO not verified, client
type reclassification required, required approval not obtained, chronic outstanding core
identity document.

Additional blocking trigger -- LexisNexis not provided:
If LexisNexis has not been provided and no prior review record with a current LexisNexis
result exists, PEP and sanctions status cannot be independently determined. This is a
blocking source gap. The review cannot be concluded without LexisNexis or a documented
exception approved by the appropriate compliance role.

Additional blocking trigger -- No ownership evidence of any kind:
If neither Orbis nor any client-provided ownership document (UBO declaration, corporate
structure chart) is available for a corporate, trust, or financial institution client,
the beneficial ownership dimension is entirely unassessed. This is a blocking source gap.

Additional blocking trigger -- Two conflicting client documents without an arbiter:
If two Tier 3 documents of the same type provide materially different values (for example
two UBO declarations with different ownership structures) and no independent source is
available to resolve the conflict, the conflict is unresolvable by the agent. This is
a blocking gap requiring reviewer resolution before the record can be used.

---

## Non-Blocking Gap Triggers (Updated for Partial Source Sets)

Source gap -- Moodys not provided:
If Moodys is not available but audited financial statements are present, the financial
risk dimension has limited confidence. Non-blocking provided audited accounts are recent
and unqualified. Blocking if the client is a financial institution or is rated as
high-risk and financial risk assessment is a mandatory EDD component.

Source gap -- Orbis not provided but client ownership documents are present:
The ownership assessment proceeds on the basis of client-provided documents with limited
confidence. Non-blocking for low-risk clients. Escalates to blocking if the client is
high-risk or EDD and independent ownership verification is a mandatory requirement.

Source gap -- Company registrar not checked:
If the registrar database was not consulted and Orbis is available, Orbis provides a
reasonable proxy. Non-blocking. If neither Orbis nor the registrar was checked, escalates
per the ownership source gap rule above.

Verification gap -- document present but independent source not available:
A client document is held but could not be verified because the independent source was
not provided. Classification depends on the document type:
- government-issued-photo-id unverified (LexisNexis not run on that name): blocking if
  this is the only identity document for a subject who is a UBO or PEP. Non-blocking for
  lower-risk subjects with other corroborating evidence.
- UBO declaration unverified (Orbis not available): see ownership source gap above.
- Company registration document unverified (registrar not checked): non-blocking if Orbis
  corroborates. Blocking if neither Orbis nor registrar was available.
- Regulatory licence unverified (official register not checked): blocking for financial
  institution clients.
- Sanctions-pep-self-declaration unverified (LexisNexis not run): blocking -- see
  LexisNexis blocking trigger above.

---

## How to Record Source Gaps in the Review Output

Source gaps appear in two places in the review output:

In the Source Coverage Summary (Section A): the overall availability assessment for each
dimension with its confidence level.

In the Compliance Gap Analysis (Section C): as individual gap entries of type source-gap,
with the dimension affected, the source that was not available, the confidence impact,
and the required action (obtain the source before concluding, or document a reviewer
exception).

Source gaps are labelled distinctly from document gaps and verification gaps so the
reviewer can immediately identify whether the issue is a missing client document, an
unverified client document, or an absent independent source.

---

## Gap Severity Ranking With Source Gaps Integrated

Blocking gaps in order of urgency:

1. Prohibited jurisdiction or confirmed sanctions match
2. LexisNexis not provided -- PEP and sanctions cannot be determined
3. PEP identified without EDD
4. No ownership evidence of any kind (source gap)
5. UBO not identified or not verified
6. Two conflicting client documents without arbiter (source gap)
7. Client type reclassification required
8. Required approval not obtained
9. Chronic outstanding core identity document

Non-blocking gaps in order of remediation priority:

1. Moodys not provided for high-risk or EDD client (source gap)
2. UBO declaration unverified -- Orbis not available (verification gap)
3. Document approaching expiry
4. Expired non-core document
5. Regulatory licence unverified -- official register not checked (verification gap)
6. Orbis not provided -- ownership assessed from client documents only (source gap, low-risk)
7. Screening not refreshed
8. Adverse media finding requiring assessment
9. Outstanding non-core document (first occurrence)
10. Minor onboarding form discrepancy
