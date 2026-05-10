# Document Type Registry

This file is the definitive reference for every client-provided document type the agent
will encounter. For each document type it defines: the canonical label used across all
outputs, what the document proves (authority scope), what independent source must
corroborate it (verification requirement), the form in which it is accepted, the recency
requirement, and which client types require it.

The agent uses this registry when assessing document collection status against KYC policy
and when recording verification gaps.

---

## How to Use This Registry

When the agent encounters a client-provided document it first identifies the document type
using the signals in the Source Type Catalogue. It then looks up this registry to determine:
what data to extract from the document, what verification action is required, and whether
the document in its current form and age meets the policy requirement for the applicable
client type.

---

## Canonical Labels and Document Type Definitions

The following canonical labels must be used consistently across all outputs. Do not use
informal names or abbreviations that are not listed here.

---

### government-issued-photo-id

Covers: passport, national identity card, government-issued driving licence.

Authority scope: full legal name, date of birth, nationality, document number, and expiry
date of a natural person. Proves identity of the individual.

Acceptable forms: original sighted by a compliance officer, certified copy (certified by
a solicitor, notary, embassy, or equivalent professional), notarised copy. Electronic
certified copies are acceptable where the KYC policy permits.

Recency requirement: must be valid and not expired. An expired identity document is always
a gap regardless of when it was collected.

Verification requirement: the full name on the document, and all aliases identified during
onboarding, must be run through LexisNexis screening. The name on the document must match
the name under which the screening was run.

Required for client types: all five client types for each natural person subject to
verification (the individual client, each UBO, each trustee and settlor, each director
or authorised signatory subject to verification).

---

### proof-of-address

Covers: utility bill, bank statement, council tax notice, mortgage statement, government
correspondence issued to the subject at the address.

Authority scope: current residential or registered address of the subject as of the
document date.

Acceptable forms: original, certified copy. The document must show the subject's name and
the address. Generic or undated documents are not acceptable.

Recency requirement: issued within the period specified in the KYC policy for the
applicable client type and risk level. Typically three months for standard and EDD clients.

Verification requirement: the name on the proof of address must match the name on the
government-issued-photo-id for the same subject. Address must be consistent with what
other sources show for the subject's residence.

Required for client types: individual/retail for the client themselves. For corporate,
trust, and financial institution clients: for each individual UBO or director subject to
address verification per the KYC policy.

---

### company-registration-certificate

Covers: certificate of incorporation, certificate of good standing, equivalent official
registration document issued by a national company registry.

Authority scope: legal existence of the entity, legal name, registration number, jurisdiction
of incorporation, and date of incorporation as at the certificate issue date.

Acceptable forms: original, certified copy, notarised copy. An official extract downloaded
from the national registry is acceptable and preferred as it represents the current record.

Recency requirement: a certificate of good standing must be issued within the period
specified in the KYC policy. A certificate of incorporation does not expire but must be
supplemented by a current good standing certificate for higher-risk clients or where the
policy requires confirmation of ongoing active status.

Verification requirement: the legal name, registration number, and jurisdiction must match
the company registrar database record for that entity. Any discrepancy governs in favour
of the registrar database.

Required for client types: corporate/business, trust/foundation (for any corporate trustee),
financial institution.

---

### articles-of-association

Covers: articles of association, memorandum of association, company constitution, by-laws.

Authority scope: the governance structure and operating rules of the entity, the authorised
share capital, the classes of shares, and the procedures for director appointment and
shareholder meetings.

Acceptable forms: original, certified copy, or the version filed with the national registry.

Recency requirement: must be the current version as filed. If the articles have been amended
since the version held in CIP, the amended version must be obtained.

Verification requirement: must be consistent with the directorship and ownership records in
the registrar database. Any provision that affects the beneficial ownership threshold or
the control structure must be noted.

Required for client types: corporate/business, financial institution.

---

### trust-deed

Covers: trust deed, deed of settlement, foundation charter, equivalent constitutive document
of a trust or foundation.

Authority scope: the legal structure of the trust or foundation, the identity of trustees
and settlors as named, the nature and scope of the beneficiary class, the governing law,
and the powers and duties of the trustees.

Acceptable forms: original, certified copy, notarised copy.

Recency requirement: must be the current operative deed including all amendments and
supplemental deeds. A principal deed without amendments is incomplete if amendments exist.

Verification requirement: all trustees and settlors must be individually identified and
their identity verified through government-issued-photo-id. Named beneficiaries must be
individually identified where the policy requires. No public registry corroboration exists
for most trusts -- the deed must be assessed on its face for completeness.

Required for client types: trust/foundation.

---

### ubo-declaration

Covers: beneficial ownership declaration form, UBO register extract, equivalent signed
declaration of beneficial ownership.

Authority scope: records the client's formal declaration of who the beneficial owners are,
their ownership percentages, nationalities, and residences. A legal obligation on the
client -- a false declaration is a material compliance failure.

Acceptable forms: completed and signed on the organisation's own template or an equivalent
form. Must be signed by an authorised representative of the client.

Recency requirement: must have been completed within the period specified in the KYC
policy. Must be refreshed whenever the beneficial ownership structure changes.

Verification requirement: every UBO declared must be verified against Orbis. Every
ownership percentage declared must be checked against Orbis. Any UBO shown in Orbis
but not declared in the form is a blocking conflict.

Required for client types: corporate/business, trust/foundation, financial institution.

---

### corporate-structure-chart

Covers: ownership diagram, group structure chart, beneficial ownership chart produced by
or on behalf of the client.

Authority scope: records the client's representation of their own structure. Not
independently verified on its face.

Acceptable forms: any format, but must show entity names, jurisdictions, and ownership
percentages at each layer. A chart without percentages or jurisdictions is incomplete.

Recency requirement: must reflect the current structure. Must be updated whenever the
structure changes.

Verification requirement: every entity in the chart must be found in Orbis or the company
registrar database. Every percentage must match Orbis. Entities present in the chart but
absent from all Tier 1 and Tier 2 sources are an ownership transparency gap.

Required for client types: corporate/business with complex structures, trust/foundation,
financial institution.

---

### authorised-signatory-list

Covers: a document listing individuals authorised to act on behalf of the client entity.

Authority scope: records who holds transaction authority on the account.

Acceptable forms: completed and signed on the organisation's template or an equivalent
board resolution or power of attorney. Must include name, role, and specimen signature
for each signatory.

Recency requirement: must be current. Any change to signatories since the last review
is a material change requiring a refreshed list.

Verification requirement: each signatory must be individually identified through
government-issued-photo-id. Director-level signatories must be consistent with the
registrar database directorship record.

Required for client types: all client types where the account will be operated by
individuals other than the client themselves.

---

### financial-statements-audited

Covers: annual audited financial statements prepared by a registered external auditor.

Authority scope: the client's financial position, revenue, and performance for the
reporting period. The auditor opinion provides independent assurance.

Acceptable forms: original or certified copy. Must include the full auditor report and
opinion. A set of accounts without the auditor report is not treated as audited.

Recency requirement: must be for the most recent financial year for which accounts have
been filed. The age of the most recent audited accounts relative to the current review
date must be noted -- accounts more than eighteen months old are a staleness signal.

Verification requirement: must be consistent with the financial profile from Moodys where
available. An auditor qualification (except an emphasis of matter on a going concern basis)
or a going concern note is always a material adverse signal that must be flagged regardless
of Moodys rating status. Must be consistent with the business description from Orbis.

Required for client types: corporate/business, financial institution for EDD cases, trust
where the trust holds significant assets.

---

### financial-statements-management

Covers: unaudited management accounts, interim financial statements, draft accounts.

Authority scope: the client's financial position as reported internally. Lower evidential
weight than audited accounts because they have not been independently assured.

Acceptable forms: signed by a director or equivalent. Must state clearly that the accounts
are unaudited.

Recency requirement: typically more recent than audited accounts. Must be for a period
ending within twelve months of the review date.

Verification requirement: must be consistent with audited accounts for overlapping periods.
Significant deviations from the audited accounts for the same period are a signal.

Required for client types: corporate/business and financial institution where audited
accounts are not yet available for the current year.

---

### source-of-funds-evidence

Covers: evidence of the specific funds being deposited or invested.
Types include: payslips, employment contracts, sale of business agreements, property sale
completion statements, loan agreements, dividend vouchers.

Authority scope: proves a specific sum was received from a specific source at a specific date.

Acceptable forms: original or certified copy. Must show the amount, the source, and the date.

Recency requirement: must relate to the specific funds being deposited or to recent activity.
The KYC policy recency requirement for the applicable client type governs.

Verification requirement: must be consistent with the client's stated occupation or business
activity. Must not contradict the financial profile from Moodys or Orbis. A source of funds
document referencing a business not shown in Orbis or the registrar database is a gap.

Required for client types: all client types where source of funds verification is required
by the applicable due diligence tier per the KYC policy.

---

### source-of-wealth-evidence

Covers: evidence of how the client accumulated their total wealth over time.
Types include: inheritance documents (grant of probate, will extract), investment portfolio
statements, property sale records, business sale agreements, prize or award documentation.

Authority scope: proves specific historical wealth events. Together with other source of
wealth documents must tell a coherent account of wealth accumulation.

Acceptable forms: original or certified copy.

Recency requirement: must cover the relevant wealth events. Older documents are acceptable
where they evidence historical events (an inheritance twenty years ago may still be
evidenced by documents of that age). Recency of the portfolio statement or account balance
must meet the KYC policy requirement.

Verification requirement: must be internally consistent. Must be consistent with public
information about the client's career and business activities. A claimed source of wealth
inconsistent with what LexisNexis adverse media or public sources show about the client
is a conflict.

Required for client types: all client types at EDD level, and all PEP clients regardless
of risk level.

---

### professional-reference-letter

Covers: a reference letter from a professional attesting to the client's standing.

Authority scope: corroborating evidence only. Not primary evidence for any risk determination.

Acceptable forms: original on the professional's letterhead, signed and dated.

Recency requirement: issued within twelve months of the review date.

Verification requirement: the professional's identity and firm should be confirmed. The
professional must not have a conflict of interest with the client.

Required for client types: as specified in the KYC policy for specific client types or
jurisdictions. Not universally required.

---

### regulatory-licence

Covers: a licence or authorisation issued by a regulatory authority.

Authority scope: proves the entity held a licence from the named authority as of the
document date.

Acceptable forms: original, certified copy, or official extract from the regulatory
authority's register.

Recency requirement: must be current. An expired licence is a blocking gap for a financial
institution client.

Verification requirement: must be corroborated against the official register maintained
by the relevant central bank or regulatory authority to confirm the licence is current
and in good standing. A licence document alone is not sufficient without register
corroboration.

Required for client types: financial institution.

---

### sanctions-pep-self-declaration

Covers: the client's signed declaration of PEP status and sanctions exposure.

Authority scope: records the client's formal declaration. Tier 3 source -- does not govern
over LexisNexis.

Acceptable forms: completed and signed on the organisation's template.

Recency requirement: must be completed at onboarding and refreshed at each periodic review.

Verification requirement: must be compared in full against LexisNexis findings. A positive
LexisNexis finding that the declaration denies is a blocking conflict.

Required for client types: all five client types.

---

### tax-identification-document

Covers: tax registration certificates, tax identification number letters, W-8 or W-9 forms,
certificate of tax residency.

Authority scope: proves the tax identification number and declared tax residency jurisdiction.

Acceptable forms: original or certified copy.

Recency requirement: must be current for the relevant tax year or period.

Verification requirement: must be consistent with the jurisdictions shown in other documents
and with what Orbis shows for the entity's tax domicile. A tax document showing residency
in a jurisdiction not otherwise disclosed is a material disclosure requiring risk assessment.

Required for client types: all five client types where tax identification is required by
the KYC policy for the applicable jurisdiction.
