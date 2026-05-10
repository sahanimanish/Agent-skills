# Tier 3 Document Extraction Guide

This file defines what to extract from each client-provided document type and what to
record as the basis for the verification step. For the authority scope, acceptable forms,
recency requirements, and verification requirements for each document type, see
references/document-type-registry.md. This file focuses on what data to pull from the
document itself.

---

## Universal Rules for Tier 3 Documents

For every client-provided document record: the document type using the canonical label
from the Document Type Registry, the subject the document relates to (individual name or
entity name), the issuing authority, the issue date, the expiry date if applicable, the
form in which it was received, the key data points the document contains, and the
verification action the document creates against a Tier 1 or Tier 2 source.

Never treat a client-provided document as verified simply because it is present. Collection
and verification are two separate states. A document is collected when CIP records it as
held. It is verified when an independent source has confirmed the key claims in it.

---

## government-issued-photo-id

Extract: full legal name exactly as shown on the document. Date of birth. Nationality.
Document type (passport, national ID, driving licence). Document number. Issue date.
Expiry date. Issuing authority (country and issuing body). All name fields including any
maiden name or alternative name shown. Machine-readable zone data if legible.

Verification action created: run LexisNexis on the full name as shown, including any
alternative names on the document. Record whether this has been done. If not done, record
a verification gap.

---

## proof-of-address

Extract: the subject's full name as shown. The address. The issue date. The issuing
organisation. The document type (utility bill, bank statement, etc.).

Verification action created: confirm the name matches the government-issued-photo-id for
the same subject. Check the issue date against the KYC policy recency requirement.

---

## company-registration-certificate and articles-of-association

Extract: the entity's full legal name. The registration number. The jurisdiction of
incorporation. The date of incorporation. For articles: the share structure, classes of
shares, quorum requirements for decisions, any provisions affecting control or ownership
thresholds.

Verification action created: check the legal name, registration number, and active status
against the company registrar database. Record whether done and the outcome.

---

## trust-deed

Extract: the name of the trust or foundation. The governing law. The date of execution.
The full names of all trustees. The full names of all settlors. The description of the
beneficiary class (named beneficiaries with full names, or class description such as
"the children of the settlor"). The powers and duties of the trustees including any
power to appoint or remove trustees. Any protector or enforcer and their powers.
All amendments and supplemental deeds -- note whether the deed is complete.

Verification action created: each trustee and settlor must have a government-issued-photo-id
on file and LexisNexis screening completed. Record which individuals are verified and which
are outstanding.

---

## ubo-declaration

Extract: each UBO's full name. Nationality. Country of residence. Ownership percentage.
The nature of the ownership (direct shareholding, indirect through named intermediaries,
control through other means). The date the declaration was signed. The signatory's name
and role.

Verification action created: compare every declared UBO against Orbis. Record any UBO
in Orbis not declared in the form and any declared UBO not found in Orbis.

---

## corporate-structure-chart

Extract: every entity shown in the chart with its legal name, jurisdiction, and ownership
percentage at each layer. Note whether percentages are shown and whether jurisdictions
are shown. A chart without both is incomplete.

Verification action created: check every entity in the chart against Orbis and the
company registrar database. Record entities present in the chart but not found in any
independent source as ownership transparency gaps.

---

## authorised-signatory-list

Extract: each signatory's full name, role or title, and whether their signature specimen
is included. The date the list was prepared or approved. The authorisation scope (whether
signatories can act individually or must act jointly).

Verification action created: each signatory must have a government-issued-photo-id on file.
Director-level signatories must be consistent with the registrar database directorship
record.

---

## financial-statements-audited and financial-statements-management

Extract: the entity name. The reporting period. Total revenue. Total assets. Net profit or
loss. For audited accounts: the auditor name and firm, the audit opinion type (unqualified,
qualified, adverse, disclaimer), whether a going concern paragraph is included. For
management accounts: the preparer and whether they are signed by a director.

Verification action created: check for consistency with Moodys where available. Flag any
auditor qualification or going concern note as a material adverse signal.

---

## source-of-funds-evidence and source-of-wealth-evidence

Extract: the amount. The date received or the date of the event. The source (who paid,
what was sold, what was inherited). The subject who received the funds or benefited from
the wealth event. For each document, whether it forms part of a coherent narrative with
the other source of funds or wealth documents provided.

Verification action created: assess internal consistency across all source of funds and
wealth documents provided. Check for consistency with the client's stated occupation or
business and with Moodys, Orbis, and public source findings.

---

## professional-reference-letter

Extract: the professional's name and firm. The professional's role or qualification. The
date of the letter. The subject of the reference. The nature of the attestation. Whether
the professional discloses any relationship with the client beyond the professional
relationship.

Verification action created: confirm the professional's identity and firm where possible.
Note any conflict of interest indicators.

---

## regulatory-licence

Extract: the issuing regulatory authority. The entity to which the licence is granted.
The type of licence or authorisation. The licence number. The issue date. The expiry date
or ongoing status. Any conditions attached to the licence.

Verification action created: check the licence against the official register maintained
by the relevant regulatory authority to confirm it is current and in good standing.

---

## sanctions-pep-self-declaration

Extract: whether the client declares PEP status (yes or no) for themselves. Whether the
client declares that any UBO, director, trustee, or associated person is a PEP. Whether
the client declares any sanctions exposure. The date signed. The signatory.

Verification action created: compare the declaration in full against LexisNexis findings.
Record any discrepancy as a conflict -- a positive LexisNexis finding contradicting a
negative declaration is always a blocking conflict.

---

## tax-identification-document

Extract: the issuing tax authority. The entity or individual name. The tax identification
number. The jurisdiction of tax residency. The period or date of validity.

Verification action created: check the declared jurisdiction against what Orbis shows for
the entity's tax domicile. A new jurisdiction of tax residency not previously disclosed
is a material change.
