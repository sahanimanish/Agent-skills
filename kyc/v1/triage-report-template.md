# Triage Report Template

This template is produced at the end of Phase 1 Step A -- before any extraction begins.
Its purpose is to give the reviewer a complete picture of what is available, what is
missing, and what impact missing sources have -- so they can decide whether to proceed
or pause to obtain additional documents.

Fill every section. Do not skip any row in the Document Inventory. If a source is not
applicable, state why it is not applicable. Remove instructional notes in parentheses
before delivering to the reviewer.

---

# Triage Report

**Client Name**: {{FULL LEGAL NAME IF KNOWN FROM DOCUMENTS RECEIVED, OR REFERENCE NUMBER}}
**Client Reference**: {{INTERNAL REFERENCE NUMBER}}
**Client Type**: {{if determinable from available documents, otherwise: to be confirmed}}
**Review Type**: {{periodic-review / triggered-review / initial-review}}
**Triage Date**: {{YYYY-MM-DD}}
**Documents Received**: {{COUNT}} items

---

## Section 1 -- Document Inventory

(One row per source type and document type required or potentially applicable for this
client. Status must be one of: Received, Uncertain (needs confirmation), Not Provided,
or Not Applicable (with reason). Do not leave any row blank.)

### Tier 1 -- Independent Third-Party Providers

| Source | Status | Document Date | Notes |
|---|---|---|---|
| Moodys credit report | {{Received / Not Provided / Not Applicable}} | {{date or --}} | {{notes}} |
| Orbis company report | {{Received / Not Provided / Not Applicable}} | {{date or --}} | {{notes}} |
| LexisNexis screening report | {{Received / Not Provided / Not Applicable}} | {{date or --}} | {{notes}} |

### Tier 2 -- Public and Approved External Sources

| Source | Status | Document Date | Notes |
|---|---|---|---|
| Company registrar database record | {{status}} | {{date or --}} | {{applicable jurisdiction(s) or not applicable reason}} |
| Stock exchange filings | {{status}} | {{date or --}} | {{not applicable if unlisted}} |
| News and media review | {{status}} | {{date or --}} | {{notes}} |
| Internal watchlist check | {{status}} | {{date or --}} | {{notes}} |

### Tier 3 -- Client-Provided Documents

(List each document received individually under its document type. If multiple documents
of the same type were received -- for example identity documents for three different
individuals -- list each separately with the subject name.)

| Document Type | Subject | Status | Issue Date | Expiry Date | Form Received | Notes |
|---|---|---|---|---|---|---|
| government-issued-photo-id | {{subject name or entity}} | {{Received / Not Provided / Not Applicable}} | {{date}} | {{date or N/A}} | {{original / certified copy / notarised / electronic}} | {{notes}} |
| proof-of-address | {{subject}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| company-registration-certificate | {{entity name}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| articles-of-association | {{entity name}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| trust-deed | {{trust name}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{not applicable if client is not a trust}} |
| ubo-declaration | {{entity name}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| corporate-structure-chart | {{entity name}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{not applicable if individual client}} |
| authorised-signatory-list | {{entity name}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| financial-statements-audited | {{entity name}} | {{status}} | {{period}} | {{N/A}} | {{form}} | {{notes}} |
| financial-statements-management | {{entity name}} | {{status}} | {{period}} | {{N/A}} | {{form}} | {{notes}} |
| source-of-funds-evidence | {{subject}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| source-of-wealth-evidence | {{subject}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| professional-reference-letter | {{subject}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{not applicable if not required by policy}} |
| regulatory-licence | {{entity name}} | {{status}} | {{date}} | {{expiry}} | {{form}} | {{not applicable if not financial institution}} |
| sanctions-pep-self-declaration | {{subject}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |
| tax-identification-document | {{subject or entity}} | {{status}} | {{date}} | {{N/A}} | {{form}} | {{notes}} |

### Tier 4 -- Internal Records

| Source | Status | Date | Notes |
|---|---|---|---|
| Prior review output | {{Received / Not Available -- first review}} | {{date or --}} | {{notes}} |
| Internal onboarding form | {{Received / Not Available}} | {{date or --}} | {{notes}} |

### Uncertain Items

(Any received item that could not be confidently classified. List each with the signals
observed and the possible source types it could be. Do not use in extraction until
the reviewer confirms the classification.)

| Item Description | Possible Source Types | Signals Observed | Reviewer Action Required |
|---|---|---|---|
| {{description}} | {{possible types}} | {{what was observed}} | Please confirm source type |

---

## Section 2 -- Critical Gap Assessment

(For each of the five assessment dimensions, state the confidence level achievable with
the available sources and the impact of any missing critical source.
Confidence: Full / Reduced / Limited / Not Assessed)

### Identity and Registration

Available sources for this dimension: {{list received sources that cover this dimension}}
Missing sources: {{list not-provided sources that would normally cover this dimension}}
Achievable confidence: {{Full / Reduced / Limited / Not Assessed}}
Impact of missing sources: {{what cannot be assessed or confirmed without them}}

### Ownership and UBO

Available sources: {{list}}
Missing sources: {{list}}
Achievable confidence: {{level}}
Impact: {{description}}
Individuals requiring verification with no identity document currently on file: {{list names or "none"}}

### PEP and Sanctions

Available sources: {{list}}
Missing sources: {{list}}
Achievable confidence: {{level}}
Impact: {{description}}
(Note: if LexisNexis is not available, state explicitly that PEP and sanctions status
cannot be independently determined and the review cannot be concluded without it or
a documented exception.)

### Financial Risk

Available sources: {{list}}
Missing sources: {{list}}
Achievable confidence: {{level}}
Impact: {{description}}

### Document Compliance

Available sources: {{list the document types received}}
Missing document types: {{list document types required by policy that were not received}}
Achievable confidence: {{level}}
Impact: {{description}}

---

## Section 3 -- Agent Recommended Action

(The agent's recommendation based on the triage. The reviewer decides.)

**Recommended action**: {{Proceed with available documents / Pause -- obtain missing sources first}}

**Basis for recommendation**:

(If recommending Proceed): The available sources are sufficient to conduct a meaningful
review of the following dimensions: {{list dimensions with full or reduced confidence}}.
The following dimensions cannot be fully assessed: {{list dimensions with limited confidence
or not assessed}}. These limitations will be disclosed in the review output.

(If recommending Pause): The following critical sources are missing and their absence
prevents assessment of a core review dimension: {{list critical missing sources and the
dimensions they affect}}. The review should be paused until these sources are obtained.

**If the reviewer instructs to proceed despite missing critical sources**: record this
as a reviewer-directed exception below and include it in the final review output.

Reviewer-directed exception (to be completed by reviewer if applicable):
The reviewer has instructed the agent to proceed with the review despite the following
missing critical sources: {{sources}}. The reviewer acknowledges that the review output
will reflect limited or not-assessed confidence for the following dimensions: {{dimensions}}.
Reviewer role: _____________ Date: _____________

---

## Section 4 -- Pre-Extraction Notes

(Any observations made during classification that are relevant to the extraction step
but do not fit elsewhere -- for example, a document that appears to be a different
version than expected, a document with visible damage or redactions, or a document
date that seems inconsistent with other received items.)

{{Notes or "No pre-extraction observations."}}
