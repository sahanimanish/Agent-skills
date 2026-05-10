# Tier 1 Source Extraction Guide

This file defines what to extract from each Tier 1 independent third-party provider.
See references/source-extraction-guide.md from the prior version of this skill for the
full field list. This file records the additions and clarifications specific to this
expanded source framework.

---

## Moodys

Extract all fields defined in the prior source-extraction-guide.md under the Moodys section.

Additional field: note whether the entity being rated is the same legal entity as the
client, a parent entity, or a subsidiary. A rating for a parent entity is informative but
is not the same as a rating for the client entity itself. Record the relationship.

---

## Orbis

Extract all fields defined in the prior source-extraction-guide.md under the Orbis section.

Additional cross-check: after extraction, compare the Orbis legal name and registration
number against the company registrar database record for the same entity. If Orbis and
the registrar show different directors or different ownership percentages, record the
conflict. The registrar governs for legal entity details.

---

## LexisNexis

Extract all fields defined in the prior source-extraction-guide.md under the LexisNexis section.

Additional field: record which names and aliases were searched and which were not. An alias
identified in a client-provided document (such as a maiden name on an identity document or
a trading name on the onboarding form) that was not included in the LexisNexis search is
a verification gap. The screening must cover all known names.
