# PR/CR Review Output Template (Partial Source Set Edition)

This template defines the structure every PR/CR review output must follow. Seven sections
are always present. Remove instructional notes in parentheses before delivering.
Replace every placeholder in double curly braces with the actual value.

---

# PR/CR Review Output

**Client Legal Name**: {{FULL LEGAL NAME -- state source: Orbis / registrar / client-stated}}
**Client Reference**: {{INTERNAL REFERENCE NUMBER}}
**Client Type**: {{type -- state if confirmed by independent source or client-stated only}}
**Review Type**: {{periodic-review / triggered-review / initial-review}}
**Review Date**: {{YYYY-MM-DD}}
**Prior Review Date**: {{YYYY-MM-DD or "no prior review on record"}}
**Reviewing Officer**: {{ROLE}}
**Effective Risk Level**: {{sdd / standard / edd -- state confidence level}}
**Prior Risk Level**: {{level or "not recorded"}}

**Sources Provided**:

Tier 1:
- Moodys: {{received -- report date: DATE / not provided}}
- Orbis: {{received -- report date: DATE / not provided}}
- LexisNexis: {{received -- search date: DATE / not provided}}

Tier 2:
- Company registrar: {{received -- jurisdiction: X, date: DATE / not provided / not applicable}}
- Stock exchange filings: {{received / not provided / not applicable -- unlisted entity}}
- News and media review: {{received / not provided}}
- Internal watchlist: {{received / not provided}}

Tier 3 -- Client Documents:
(List each document type with status: received / not provided / not applicable)
- government-issued-photo-id: {{status}} -- subject(s): {{names}}
- proof-of-address: {{status}} -- subject(s): {{names}}
- company-registration-certificate: {{status}}
- articles-of-association: {{status}}
- trust-deed: {{status / not applicable}}
- ubo-declaration: {{status}}
- corporate-structure-chart: {{status}}
- authorised-signatory-list: {{status}}
- financial-statements-audited: {{status}} -- period: {{period}}
- financial-statements-management: {{status}} -- period: {{period}}
- source-of-funds-evidence: {{status}}
- source-of-wealth-evidence: {{status}}
- professional-reference-letter: {{status / not applicable}}
- regulatory-licence: {{status / not applicable}}
- sanctions-pep-self-declaration: {{status}}
- tax-identification-document: {{status}}

Tier 4:
- Prior review output: {{received -- date: DATE / not available -- first review}}
- Internal onboarding form: {{received / not available}}

**Reviewer-directed exceptions (if any)**:
{{List any exceptions where the reviewer directed the agent to proceed despite missing
critical sources. State the missing source and the dimension affected. Or: "None."}}

**Segment**: {{smb / services / markets / banking}} -- source: {{source}}, confidence: {{confirmed / uncertain}}
**Size**: {{large / medium / small}} -- source: {{source}}, confidence: {{confirmed / uncertain}}
**Segment-Size Risk Rating**: {{low / medium / high / edd-mandatory}} -- change from prior: {{same / increased / decreased}}
**PR/CR Cycle Frequency**: {{annually / every-2-years / every-3-years}} -- status: {{on-time / overdue by X months / early}}
**Next Review Due**: {{YYYY-MM-DD}}
**Effective DD Tier**: {{sdd / standard / edd}} (governed by KYC client type and jurisdiction -- separate from risk rating)

**System Recommendation**: {{continue-relationship / escalate-for-review / refer-to-senior-compliance / pause--obtain-missing-sources}}
**Basis**: {{one sentence}}

---

## Section A -- Client Summary and Source Coverage

### Client Summary

### Classification Summary

KYC client type: {{type}} -- source: {{source}}, confidence: {{level}}
Segment: {{segment}} -- {{same as prior / changed from X}}
Size: {{size}} -- source: {{source}}, confidence: {{level}}
Derived risk rating: {{rating}} -- {{same as prior / changed: prior was X}}
PR/CR cycle: {{frequency}} -- {{on time / overdue by X months}}
Effective due diligence tier: {{tier}}

(Note: the risk rating and the due diligence tier are two separate assessments.
The risk rating comes from segment + size and governs review frequency.
The due diligence tier comes from KYC client type + jurisdiction and governs
what the review must assess.)


(Factual summary of who the client is, what risk level applies, and the headline findings.)

Legal identity: {{legal name, aliases, jurisdiction, registration number, operational status}}
State source and confidence: {{e.g. "from Orbis -- full confidence" or "client-stated, unverified"}}

Ownership summary: {{describe the ownership structure in 2-3 sentences}}
State confidence: {{full / reduced / limited / not assessed -- reason}}

Risk level determination:
- Jurisdiction risk tier: {{tier}} -- source: {{source and confidence}}
- Client type default tier: {{from KYC policy}}
- PEP overlay: {{applies / does not apply / could not be determined -- LexisNexis not available}}
- Effective risk level: {{level}} -- confidence: {{level}}

Financial risk summary:
- Moodys rating: {{rating and date / not available}}
- Audited accounts: {{period and auditor opinion / not available}}
- Overall financial risk confidence: {{full / reduced / limited / not assessed}}

Screening summary:
- LexisNexis outcome: {{overall result / not available -- PEP and sanctions not independently determined}}
- Adverse signals: {{none / list findings by type}}

### Source Coverage Summary

(For each of the five assessment dimensions state the confidence level and the reason.)

| Dimension | Confidence | Available Sources Used | Missing Sources | Impact |
|---|---|---|---|---|
| Identity and registration | {{full/reduced/limited/not assessed}} | {{list}} | {{list or none}} | {{impact of missing sources}} |
| Ownership and UBO | {{level}} | {{list}} | {{list or none}} | {{impact}} |
| PEP and sanctions | {{level}} | {{list}} | {{list or none}} | {{impact}} |
| Financial risk | {{level}} | {{list}} | {{list or none}} | {{impact}} |
| Document compliance | {{level}} | {{list}} | {{list or none}} | {{impact}} |

---

## Section B -- Material Changes Since Last Review

(If no prior review: write "No prior review record. Full baseline assessment performed.")
(If no material changes: write "No material changes identified.")

For each material change:

**Change {{ID}} -- {{Dimension}}**
Prior value: {{value at last review -- source: X}}
Current value: {{value at current review -- source: X, confidence: level}}
Source confidence: {{full / reduced / limited}}
Verification status: {{verified by independent source / unverified -- source not available}}
Policy consequence: rule_id {{ID}} -- {{brief description}}
Required action: {{specific instruction}}
Immediately blocking: {{yes / no}}

---

## Section C -- Compliance Gap Analysis

(Organised into three subsections: source gaps, document gaps, verification gaps.
If none in a subsection: write "None identified.")

### C1 -- Source Gaps
(Entire assessment dimensions affected by absent independent sources)

**Gap {{ID}} -- Source Gap**
Gap class: {{blocking / non-blocking}}
Severity rank: {{1-9 per Gap Classification Guide}}
Missing source: {{source name and tier}}
Dimension affected: {{which of the five dimensions}}
Confidence impact: {{what this source would have provided}}
Required action: {{obtain source / document exception}}
Remediation owner: {{role}}
Deadline: {{date or "immediate"}}
Present at prior review: {{yes / no / not applicable}}

### C2 -- Document Gaps
(Specific documents required by policy that are not held)

**Gap {{ID}} -- Document Gap**
Gap class: {{blocking / non-blocking}}
Severity rank: {{1-9}}
Policy rule: rule_id {{ID}} -- {{description}}
Document type: {{canonical label}}
Subject: {{individual or entity the document relates to}}
Nature: {{not provided / expired / outstanding / waived without authority}}
Required action: {{specific instruction}}
Remediation owner: {{role}}
Deadline: {{date or "immediate"}}
Chronic (present at prior review unremediated): {{yes / no}}

### C3 -- Verification Gaps
(Documents held but not independently verified because the independent source was absent)

**Gap {{ID}} -- Verification Gap**
Gap class: {{blocking / non-blocking}}
Severity rank: {{1-9}}
Document type: {{canonical label}}
Subject: {{individual or entity}}
Document status: {{collected and held}}
Independent source required: {{which Tier 1 or Tier 2 source would verify it}}
Reason not verified: {{independent source not provided}}
Risk implication: {{what remains unconfirmed}}
Required action: {{obtain independent source / document exception}}
Remediation owner: {{role}}
Deadline: {{date or "immediate"}}

---

## Section D -- Source Conflict Register

(Every data point where two available sources provided different values.
If none: write "No source conflicts identified.")

**Conflict {{ID}}**
Data point: {{what the conflict is about}}
Source A -- {{name}}: {{value}}
Source B -- {{name}}: {{value}}
Governing source: {{higher-tier source}}
Governing value: {{value applied in the record}}
Discarded value: {{value not applied}}
Confidence of governing source: {{full / reduced / limited}}
Risk implication: {{does the discrepancy itself carry a risk signal}}
Reviewer confirmation required: yes -- reviewer must confirm the governing value is correct

---

## Section E -- Data Quality Flags

(Unclassified documents, low-confidence extractions, illegible sections, sources that
could not be searched. If none: write "No data quality issues identified.")

**Flag {{ID}}**
Flag type: {{unclassified-document / low-extraction-confidence / illegible-section / source-not-searchable / uncertain-classification}}
Affected source: {{document or source}}
Affected field: {{what data is affected}}
Impact: {{how this affects the review}}
Required resolution: {{what the reviewer must do}}

---

## Section F -- Document Verification Record

(Every client-provided Tier 3 document and its verification status. Always present.
One row per document received.)

| Document Type | Subject | Held in CIP | Independent Source Used | Verification State | Outcome or Gap |
|---|---|---|---|---|---|
| {{canonical label}} | {{name}} | {{yes/no}} | {{source name or "not available"}} | {{verified / unverified-source-not-available / discrepancy-found}} | {{outcome description or gap ID}} |

---

## Section G -- Reconciled Client Profile

(The full structured client record as the auditable evidence base. Always attached.)

### Identity and Registration

| Field | Value | Source | Confidence | Conflict Resolved |
|---|---|---|---|---|
| Full legal name | {{value}} | {{source}} | {{high/medium/low}} | {{yes/no}} |
| Aliases | {{value}} | {{source}} | {{level}} | |
| Jurisdiction | {{value}} | {{source}} | {{level}} | |
| Registration number | {{value}} | {{source}} | {{level}} | |
| Legal form | {{value}} | {{source}} | {{level}} | |
| Operational status | {{value}} | {{source}} | {{level}} | |

### Ownership Structure

(Describe the ownership chain. For each layer state the source and confidence.
If ownership is based on client documents only with no independent corroboration,
state this explicitly in the description.)

### UBO Records

(One record per UBO. State source and confidence for each field.)

**UBO {{n}}**
- Name: {{value}} -- source: {{source}}, confidence: {{level}}
- Nationality: {{value}} -- source: {{source}}, confidence: {{level}}
- Ownership percentage: {{value}} -- source: {{source}}, confidence: {{level}}
- Ownership path: {{chain}}
- PEP status: {{clear / PEP category / not determined -- LexisNexis not available}}
- Sanctions status: {{clear / match / not determined -- LexisNexis not available}}
- Identity documents: {{document types held, verification state}}

### Screening Results

| Finding ID | Category | Matched Name | Match Basis | Status | New Since Last Review | Source |
|---|---|---|---|---|---|---|
| {{id}} | {{type}} | {{name}} | {{basis}} | {{confirmed/potential}} | {{yes/no}} | LexisNexis |

If LexisNexis not available: "Screening not performed -- LexisNexis not provided.
PEP and sanctions status not independently determined."

### Financial Risk

| Field | Value | Source | Confidence | Change Since Last Review |
|---|---|---|---|---|
| Credit rating | {{value / not available}} | {{Moodys / audited accounts / not assessed}} | {{level}} | {{direction/unchanged}} |
| Rating outlook | {{value / not available}} | {{source}} | {{level}} | |
| Probability of default | {{value / not available}} | {{source}} | {{level}} | |
| Auditor opinion | {{unqualified / qualified / going concern / not available}} | {{audited accounts}} | {{level}} | |

### Document Collection Status

| Document Type | Subject | Status | Form | Issue Date | Expiry | Recency Met | Verified | Verification Source |
|---|---|---|---|---|---|---|---|---|
| {{type}} | {{name}} | {{collected/outstanding/expired/waived/not-provided}} | {{form}} | {{date}} | {{date/NA}} | {{yes/no/expired}} | {{yes/no/na}} | {{source or "not available"}} |

### Client-Stated Information

| Field | Stated Value | Source | Corroborated By | Discrepancy | Confidence |
|---|---|---|---|---|---|
| Purpose of relationship | {{value}} | onboarding form | {{source or "not corroborated"}} | {{yes/no}} | {{level}} |
| Source of funds | {{value}} | {{source}} | {{source or "not corroborated"}} | {{yes/no}} | {{level}} |
| Source of wealth | {{value}} | {{source}} | {{source or "not corroborated"}} | {{yes/no}} | {{level}} |
| Anticipated activity | {{value}} | {{source}} | {{source or "not corroborated"}} | {{yes/no}} | {{level}} |

---

## Reviewer Sign-Off

(Completed by reviewing officer -- not by the agent)

Review decision: {{continue / continue with conditions / escalate / pause / exit relationship}}
Conditions (if any): {{remediation actions required}}
Reviewer role: _______________
Date: _______________
Next review due: _______________
Notes: _______________
