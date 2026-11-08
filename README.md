# urn:aibn registration package

Working documents for the `aibn` URN namespace registration (RFC 8141,
Expert Review), prepared for submission to urn@ietf.org.

## Documents

- `AIBN_URN_Registration_v2_draft.txt` — the filled-in RFC 8141 Appendix A
  registration template (Purpose, Syntax, Assignment, Security and Privacy,
  Interoperability, Resolution, Documentation, Additional Information,
  Revision Information). Version 2, incorporating the reviewer's items;
  editorial notes removed and registrant values completed.
- `AIBN_Registration_Rules_v1_draft.txt` — companion operational rules
  (assignment of reg-segments, recording, lifecycle, abuse removal, privacy,
  escrow/succession, fees, changes, appeals), cited as [AIBN-RULES];
  editorial notes removed and registrant values completed.
- `AIBN_Metadata_Schema_v1.1.0.json` — the machine-readable [AIBN-SCHEMA]
  document (current): JSON Schema (draft 2020-12) for the public record
  (root), the holder submission payload (`#/$defs/submission`), the
  controlled vocabularies (work types, degree of AI involvement), the
  tombstone minimum, related-record associations, `x-visibility`
  annotations, and the companion JSON-LD context (`x-jsonld-context`).
  The degree of AI involvement is mandatory and always public; the
  `visibility` election (`#/$defs/visibility`) is scoped to `description`
  and `aiSystem` (Registration Rules 6.1, 6.5). Version 1.1.0 adds the
  optional, always-public `subjects` field (work-level classification in a
  named scheme — Thema, the registry's example scheme, with BISAC codes
  equally accepted) with scheme-aware validation (Rules 6.4): Thema codes
  are verified against the registry's embedded snapshot of the list
  published by EDItEUR (free to use); BISAC codes are validated for format
  only, because the BISAC Subject Headings List is licensed by BISG and is
  not embedded.
- `AIBN_Metadata_Schema_v1.0.0.json` — the initial schema version; kept in
  the package (and hosted at its own canonical URL) because versions
  already cited stay available: additive changes are minor versions,
  removals or semantic changes are major versions, per the schema's
  versioning note.
- `AIBN_Context_v1.1.0.jsonld` — the standalone JSON-LD `@context` document
  (current), identical to the 1.1.0 schema's embedded `x-jsonld-context`
  (adds `subjects` -> `dcterms:subject`); intended to be published at
  https://aibn.viloocity.press/schema/aibn-context-1.1.0.jsonld and
  referenced by the lookup API's default (JSON-LD) representation.
- `AIBN_Context_v1.0.0.jsonld` — the initial context version, kept for
  persistence at https://aibn.viloocity.press/schema/aibn-context-1.0.0.jsonld.
- `record-example.json` — a complete public record as returned by the lookup
  API (JSON-LD default representation), validating against the schema root;
  uses only documentation-reserved reg-segments and checksum-valid example
  identifiers; carries two Thema subject codes (`FL`, `1D` — both present in
  the registry's embedded Thema snapshot).
- `submission-example.json` — the holder submission that produced the record
  example (holder-minted `pubSegment`, private `contact`, visibility
  election, same subjects), validating against `#/$defs/submission`.
- `AIBN_URN_Review_Action_Items.xlsx` — reviewer action-item workbook
  (24 items, Draft Texts blocks R1a-R9b, status tracking).

## Before submission

1. The drafts are complete: every operational value (dates, emails, URLs,
   legal name, postal address) is filled in, all `[EDITORIAL NOTE ...]`
   blocks have been removed, and no bracketed placeholders remain. Confirm
   the hosting commitment: the 1.1.0 schema's `$id` URL is the intended
   [AIBN-SCHEMA] stable URL and must be hosted there, together with the
   JSON-LD context at
   https://aibn.viloocity.press/schema/aibn-context-1.1.0.jsonld (the 1.0.0
   schema and context stay hosted at their own URLs — versions already
   cited persist).
2. Run the verifiers in `scripts/`: `verify_workbook.py` and
   `verify_schema.py` (both fully applicable), and `verify_v2_draft2.py`
   and `verify_rules.py` (their structural, promise, and subject-code
   checks apply; the editorial-note and open-placeholder checks target
   the earlier working state and will report those as missing by
   design).
3. Send the completed template to urn@ietf.org.
