# Source Type Catalogue

This file is the agent's classification guide for every source it will encounter during
a PR/CR. Before extracting any data the agent must classify each item into its tier and
source type. Classification determines authority scope, what the source can prove, and
how conflicts involving it are resolved.

---

## How to Classify a Source

Read the item received. Apply the signals below to identify its type. If the item matches
signals from more than one type, use the primary purpose of the document to determine its
type. If classification is uncertain, flag as unclassified and do not use as an
authoritative source until the reviewer confirms it.

---

## Tier 1 -- Independent Third-Party Providers

### Moodys Credit Report or Rating Opinion

Signals: Moodys branding or letterhead, credit opinion or rating action header, probability
of default table, loss given default, rating rationale and constraints sections, industry
and country outlook, analyst name and contact. Typically covers one rated entity.

Authority scope: credit rating, rating outlook, probability of default, key rating drivers
and constraints, industry risk classification, country risk commentary.

Cannot be authoritative for: ownership structure, individual identity, document collection
status, legal registration details.

### Orbis / Bureau van Dijk Company Report

Signals: Bureau van Dijk or Orbis branding, BvD ID number, shareholder structure table or
diagram, UBO section, subsidiary list, standardised financial statement extract, national
registry data fields. Typically covers one legal entity and its ownership chain.

Authority scope: ownership structure, UBO identification and percentage, subsidiary mapping,
registered entity details, legal form, operational status, industry classification.

Cannot be authoritative for: PEP status, sanctions status, individual screening outcomes,
credit ratings.

### LexisNexis Screening Report

Signals: LexisNexis branding, WorldCompliance or similar product name, screening result
summary, PEP match section, sanctions list hit section, adverse media findings, match
basis field (exact, alias, phonetic), overall outcome field. Typically covers one individual
or entity name searched.

Authority scope: PEP status and category, sanctions list matches, adverse media findings,
identity screening outcomes, watchlist matches.

Cannot be authoritative for: ownership structure, financial ratings, document collection.

---

## Tier 2 -- Public and Approved External Sources

### Company Registrar Database Record

Signals: output from Companies House, SEC EDGAR, a national business registry, or
equivalent official authority. Contains the official registered name, registration number,
registered address, filing history, current directors, charges registered, and confirmation
statement status. May be a printed extract, a PDF download from the registry, or a
screenshot with the registry URL visible.

Authority scope: official legal name and any changes, registration number, registered
address as filed, current and historical directors and their appointment and resignation
dates, charges and mortgages registered, confirmation statement filing status, dissolution
notices or insolvency filings.

Note: this is the official legal record. When Orbis and the registrar conflict, the
registrar governs for legal entity details because it is the primary source Orbis
aggregates from. Orbis may lag by days or weeks; the registrar is the current record.

### Stock Exchange Filing or Announcement

Signals: filed with a named stock exchange (London Stock Exchange, NYSE, NASDAQ, etc.)
or downloaded from an exchange regulatory news service (RNS, SEC EDGAR EDGAR filings,
etc.). Contains a filing date, a filing category (major shareholding notice, profit
warning, director change, regulatory investigation, auditor change, etc.), and the
exchange or regulatory authority the filing was made to.

Authority scope: material ownership changes crossing mandatory disclosure thresholds,
director appointments and resignations as disclosed to the market, profit warnings and
financial guidance revisions, disclosed regulatory investigations or enforcement actions,
auditor changes and auditor qualifications referenced in filings, going concern disclosures.

Note: applies only to publicly listed entities. For unlisted entities this source type
will not be present. Its absence for an unlisted entity is not a gap.

### News and Media Site Article

Signals: an article from a named news publication or media site, with a publication date,
author or publication name, and a URL or publication reference. May be a printed article,
a PDF of a webpage, or an extract.

Authority scope: signal source only. News and media findings are not confirmed facts for
compliance purposes -- they are signals that prompt further investigation. A news article
reporting an allegation against a client must be recorded as an adverse signal and
investigated further through Tier 1 or official Tier 2 sources before being treated as
a confirmed finding.

Exception: a news article reporting a regulatory action that has been officially confirmed
(a regulator's own press release, a court judgment, a stock exchange filing) may be used
to corroborate that official finding. The official source remains primary.

### Internal Watchlist or Approved Database Match

Signals: output from an internally maintained watchlist, an approved third-party database
not otherwise classified in this catalogue, or an internal risk flag system. Will typically
show the matched name, the list the match was found on, the date of the match, and the
nature of the match.

Authority scope: any match on an internal watchlist always triggers further investigation
regardless of what Tier 1 sources show. Internal watchlists represent the organisation's
own risk determinations and must be treated seriously even when no external source
corroborates the match.

---

## Tier 3 -- Client-Provided Onboarding Documents

### Identity Document

What it is: a government-issued document proving the identity of a natural person.
Types include: passport, national identity card, driving licence.
Signals: government issuing authority, photograph of the holder, name, date of birth,
document number, expiry date, machine-readable zone or chip indicator.
Authority scope: proves the full legal name, date of birth, nationality, and document
number of the individual. Does not prove current address. Does not prove PEP status.
Verification requirement: LexisNexis screening must be run on the full name and all
aliases as shown in the document.

### Proof of Address

What it is: a document proving the current residential or registered address of the subject.
Types include: utility bill, bank statement, council tax notice, mortgage statement,
government correspondence.
Signals: the subject's name, a residential or registered address, an issue date, and the
issuing organisation (utility company, bank, local authority, etc.).
Authority scope: proves the address of the subject as of the document date, subject to the
recency requirement in the KYC policy. Does not prove identity or ownership.
Verification requirement: the name on the proof of address must match the name on the
identity document. The recency requirement from the KYC policy must be met.

### Company Registration Document

What it is: official documentation of a legal entity's incorporation and governing rules.
Types include: certificate of incorporation, certificate of good standing, articles of
association, memorandum of association, company constitution.
Signals: issuing authority (a national registry or notary), the entity's legal name,
registration number, date of incorporation, jurisdiction of incorporation, and the
governing rules of the entity.
Authority scope: proves the legal existence of the entity, its name, and its registration
details at the date of issue. Articles of association prove the governance structure
and rules of the entity.
Verification requirement: key details (name, number, jurisdiction, active status) must be
corroborated against the company registrar database record for that jurisdiction.

### Trust Deed or Foundation Charter

What it is: the founding document of a trust or foundation, establishing its terms,
trustees, settlors, and beneficiaries.
Signals: legal language establishing the trust or foundation, names of trustees and
settlors, description of beneficiaries (named or class), governing law, date of execution,
and signatures of the parties.
Authority scope: proves the structure and terms of the trust, the identity of trustees
and settlors as named, and the nature of the beneficiary class. There is typically no
public registry corroboration for most trusts.
Verification requirement: the trustees and settlors named must be individually verified
through identity documents and LexisNexis screening. The trust deed must be complete --
a partial deed or a deed with blank fields is a gap.

### Source of Funds Evidence

What it is: documents proving the origin of the specific funds being deposited or invested.
Types include: payslips, employment contracts, business sale agreements, loan agreements,
property sale completion statements, dividend vouchers.
Signals: the amount received, the date received, the source of the payment, and the
subject who received it.
Authority scope: proves that a specific sum was received from a specific source at a
specific date. Does not prove the ultimate origin of the wealth.
Verification requirement: must be consistent with the client's stated occupation or business
and with the financial profile from Moodys or Orbis. A source of funds document that
describes a business activity inconsistent with what Orbis shows for that entity is a
conflict.

### Source of Wealth Evidence

What it is: documents proving how the client accumulated their total wealth over time.
Types include: inheritance documents (grant of probate, will), investment portfolio
statements, property sale and purchase records, business sale agreements, audited accounts
of a business owned by the client.
Signals: the nature of the wealth event (inheritance, investment growth, business sale),
the amounts involved, the dates, and the subject.
Authority scope: proves specific wealth events. Together with other source of wealth
documents must tell a coherent account of how the client's wealth was accumulated.
Verification requirement: must be internally consistent across documents. Must be
consistent with what public sources show about the client's career and business activities.
A source of wealth claim inconsistent with what LexisNexis or news sources show about
the client is a conflict.

### Beneficial Ownership Declaration or UBO Form

What it is: the client's formal signed declaration of who the ultimate beneficial owners
of the entity are, their ownership percentages, and their nationalities and residences.
Signals: a signed form on the organisation's template or equivalent, naming each UBO with
their ownership percentage, nationality, and date of birth.
Authority scope: records what the client has formally declared under legal obligation.
Verification requirement: must be verified in full against Orbis. Any UBO shown in Orbis
but absent from the declaration is a conflict. Any UBO shown in the declaration but absent
from Orbis must be flagged -- Orbis not corroborating the declared UBO is a verification
gap even if the declaration is signed.

### Authorised Signatory List

What it is: a document listing the individuals authorised to act on behalf of the client
entity, typically with specimen signatures.
Signals: names, roles, and specimen signatures or signature panels of each authorised
signatory.
Authority scope: records who is authorised to transact on the account. Changes to this
list since the last review are a material change signal.
Verification requirement: each signatory must be individually verified through identity
documents. Director-level signatories must be consistent with the registrar database
directorship record.

### Financial Statements

What it is: the client's own financial reporting documents.
Types include: audited annual accounts, management accounts, interim financial statements.
Signals: the entity name, the reporting period, the financial figures (revenue, assets,
profit), and for audited accounts the auditor name and audit opinion.
Authority scope: provides the client's own financial picture. Audited accounts carry
higher evidential weight than management accounts. Where Moodys is available it governs
for financial risk assessment. Where not available, audited accounts are the best available
financial evidence.
Verification requirement: must be consistent with the financial profile from Moodys and
Orbis where those are available. An auditor qualification or a going concern note is always
flagged as a material adverse signal.

### Professional Reference Letter

What it is: a letter from a professional (solicitor, accountant, banker) attesting to the
client's standing.
Signals: the professional's name, firm, and professional registration or letterhead; the
subject of the reference; and the nature of the attestation.
Authority scope: corroborating source only. A professional reference letter is not primary
evidence for any risk determination. It supports but does not replace independent
verification.
Verification requirement: the professional's identity and firm should be confirmed where
possible. The professional must not have a conflict of interest with the client.

### Regulatory Licence

What it is: a licence or authorisation document issued by a regulatory authority to a
financial institution client.
Signals: the issuing regulatory authority, the entity to which the licence is granted, the
type of licence or authorisation, the licence number, and the expiry date or ongoing
status.
Authority scope: proves that the entity held a licence from the named authority as of the
document date.
Verification requirement: must be corroborated against the register maintained by the
relevant central bank or regulatory authority to confirm the licence is current and in good
standing. A licence document that is not corroborated by the official register is not
sufficient.

### Sanctions and PEP Self-Declaration Form

What it is: the client's own signed declaration of their PEP status and whether they or
any associated persons are subject to sanctions.
Signals: the organisation's own form template, signed by the client or an authorised
representative, with responses to PEP and sanctions questions.
Authority scope: records what the client has formally declared. This is a Tier 3 source
and does not govern over LexisNexis findings.
Verification requirement: must be compared in full against LexisNexis. A positive LexisNexis
finding that contradicts a negative self-declaration is a blocking conflict.

### Tax Identification Document

What it is: a document proving the client's tax residency and tax identification number.
Types include: tax registration certificates, tax identification number letters, W-8 or
W-9 forms, certificate of tax residency.
Signals: the issuing tax authority, the entity or individual name, the tax identification
number, and the jurisdiction of tax residency.
Authority scope: proves the tax identification number and declared tax residency.
Verification requirement: must be consistent with the jurisdictions shown in other documents
and with what Orbis shows for the entity's tax domicile. A tax document showing residency
in a jurisdiction not otherwise disclosed is a material disclosure.

### Corporate Structure Chart

What it is: a client-produced diagram or document showing the ownership and group structure
of the client entity.
Signals: a visual or tabular representation of entities, ownership percentages, and the
relationships between them, produced by or on behalf of the client.
Authority scope: records what the client declares their structure to be. Every entity and
percentage shown in the chart must be independently verifiable.
Verification requirement: every entity in the chart must appear in Orbis or the company
registrar database. Every ownership percentage must match what Orbis shows. Entities shown
in the chart that cannot be found in any Tier 1 or Tier 2 source are an ownership
transparency gap requiring escalation.

---

## Tier 4 -- Internal Records

### Internal Onboarding Form

The organisation's own form completed at onboarding capturing client-stated information.
Contains client type classification, risk rating, due diligence tier, relationship manager
details, and client-stated purpose, source of funds, and anticipated activity.
Authority scope: records prior determinations and client-stated information as a baseline
for change comparison. Not an independent source. Cannot corroborate client documents.

### Prior Review Output

The structured review output from the most recent prior PR/CR. Contains the prior risk
rating, prior gap list, and prior material changes. Used exclusively as the baseline for
the change comparison step.
Authority scope: records prior determinations only. Does not constitute evidence for the
current review.
