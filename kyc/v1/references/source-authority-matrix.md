# Source Authority Matrix

This is the quick-reference conflict resolution table for the agent. For any data point,
it states: which source is authoritative, which sources corroborate, and what a conflict
between sources means. This matrix now covers all four tiers.

---

## How to Read This Matrix

For each data type: identify which tier and source type is listed as governing. When two
sources conflict, the governing source determines the reconciled value. The discarded
value is recorded in the Conflict Register. The conflict itself is always disclosed.

When a conflict cannot be resolved by this matrix, apply the full reconciliation rules
in references/reconciliation-rules.md.

---

## Legal Identity and Registered Name

Governing source: Tier 2 company registrar database (the official legal record).
Corroborating: Orbis (aggregates from registrar but may lag), company registration
certificate (Tier 3 client document), onboarding form.
Conflict signal: when Orbis and the registrar show different names, the registrar governs.
When the client document shows a name different from the registrar, the registrar governs
and the discrepancy may indicate the client used a previous name or trading name.

---

## Jurisdiction of Incorporation

Governing source: Tier 2 company registrar database.
Corroborating: Orbis, company registration certificate, tax identification document.
Conflict signal: a tax document showing a different jurisdiction of tax residency than the
jurisdiction of incorporation is not a conflict -- these are different concepts. Both must
be recorded. A client-stated jurisdiction on the onboarding form that differs from the
registrar record is a discrepancy.

---

## Director and Officer Records

Governing source: Tier 2 company registrar database for the current official record.
Corroborating: Orbis (may lag), articles of association (governance structure), authorised
signatory list (operational authority, which may differ from legal directors).
Conflict signal: a person shown as a director in Orbis or on the client's authorised
signatory list who is not shown as a current director in the registrar is a discrepancy
requiring explanation. They may have resigned or not have been officially filed.

---

## Ownership Structure and UBO

Governing source: Orbis for ownership structure.
Corroborating: Tier 2 registrar database (direct shareholder filings where available),
stock exchange major shareholding notices for listed entities, client-provided UBO
declaration and corporate structure chart (Tier 3, verified against Orbis).
Conflict signals:
- Orbis shows a UBO not in the client declaration: blocking gap.
- Client declaration shows a UBO Orbis does not: Orbis governs; verification gap.
- Stock exchange filing shows a shareholding change Orbis has not yet reflected: the
  filing governs as it is the official disclosure. Orbis may lag.
- Corporate structure chart shows an entity not in Orbis or any registrar: ownership
  transparency gap, escalate.

---

## PEP Status

Governing source: LexisNexis. Absolute. No exceptions.
Corroborating: client sanctions-pep-self-declaration (Tier 3).
Conflict signal: any positive LexisNexis PEP finding that the client declaration denies
is a blocking conflict. The self-declaration does not override LexisNexis under any
circumstances.

---

## Sanctions Status

Governing source: LexisNexis. Absolute. No exceptions.
Corroborating: UN, OFAC, EU sanctions lists if checked directly (Tier 2 approved sources
where applicable), client sanctions-pep-self-declaration (Tier 3).
Conflict signal: a positive LexisNexis sanctions finding is a blocking gap regardless of
what any other source shows. A client declaration of no sanctions exposure does not clear
a LexisNexis positive finding.

---

## Adverse Events and Reputational Risk

Governing source: LexisNexis for structured adverse media findings.
Corroborating: Tier 2 news and media sites (signal source), stock exchange regulatory
disclosures (official source for listed entities), internal watchlist matches.
Conflict resolution:
- A LexisNexis adverse media finding governs as a confirmed finding.
- A news article adverse signal that is not yet reflected in LexisNexis is a signal
  requiring investigation. Record as an adverse signal, not a confirmed finding.
- An official regulatory disclosure (stock exchange filing, regulator announcement) is
  a confirmed adverse finding and is corroborated by the LexisNexis check. If LexisNexis
  has not yet reflected the official disclosure, both are recorded and the official
  disclosure governs.
- An internal watchlist match always triggers investigation regardless of LexisNexis status.

---

## Credit Rating and Financial Risk

Governing source: Moodys.
Corroborating: audited financial statements (Tier 3), stock exchange profit warnings and
financial guidance disclosures (Tier 2 for listed entities), management accounts (Tier 3,
lower weight).
Conflict signal: an auditor going concern note or qualification in audited financial
statements is always flagged as a material adverse signal even if it is not yet reflected
in the Moodys rating. Both findings are recorded.

---

## Financial Performance and Position

Governing source: Moodys where available. Where not: audited financial statements.
Corroborating: Orbis financial extracts, management accounts (lower weight), stock exchange
financial announcements.
Conflict signal: a significant difference between audited accounts and what Moodys
references may reflect different reporting periods or accounting standards. Record both
and note the basis of the difference.

---

## Regulatory Licence Status

Governing source: Tier 2 official register maintained by the relevant central bank or
regulatory authority.
Corroborating: the client-provided regulatory-licence document (Tier 3).
Conflict signal: a licence document held in CIP that is not corroborated by the official
register, or that shows a different status (expired, suspended, revoked) than what the
register shows, is a gap. The register governs.

---

## Document Collection Status

Governing source: CIP records for what has been physically collected.
Corroborating: the onboarding form may list expected documents.
Conflict signal: a document listed on the onboarding form as collected but absent from
the CIP record is not held. CIP governs. This is a collection gap.

---

## Address and Residence

Governing source: proof-of-address document (Tier 3) for residential address, subject to
recency requirement. Company registrar database for registered address.
Corroborating: onboarding form (client-stated), Orbis (registered address field).
Conflict signal: a registered address in Orbis that differs from the registrar database
is an Orbis lag signal -- the registrar governs. A residential address that differs from
what public sources show for the individual is a signal.

---

## Source of Funds and Wealth

Governing source: the collection of client-provided evidence documents (Tier 3), assessed
for internal consistency and for consistency with independent sources.
Corroborating: Moodys and Orbis (financial profile consistency), LexisNexis (adverse
media that contradicts stated wealth origin), public sources (career and business history
consistency).
Conflict signal: a source of funds or wealth narrative that is inconsistent with what
independent sources show about the client's career, business activities, or financial
profile is a conflict requiring escalation.

---

## Tax Identification and Residency

Governing source: the tax-identification-document (Tier 3) for declared tax residency,
corroborated against Orbis.
Conflict signal: a tax document showing residency in a jurisdiction not otherwise disclosed
in any other source is a material disclosure. A discrepancy between declared tax residency
and what Orbis shows for the entity's domicile must be flagged.
