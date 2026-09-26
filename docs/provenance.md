# Provenance and known gaps

For each observation, follow `event_id` to `events.csv` and `source_id` to `sources.csv`. The source row gives publisher, title, URL, retrieval time, upstream version labels, rights basis, and any source snapshot SHA-256. The observation gives its source version, statement locator, and normalized record hash. The event-source table makes every included relationship explicit; filenames are not the provenance mechanism.

The source metadata and factual action fields were checked against one another during initial curation. All selected records had a publisher, title, retrieval time, original URL, and no-PII flag. Available source snapshot hashes refer to earlier captures; this release did not republish or rehash original documents. The new CSV and schema files have independently computed SHA-256 values in `metadata/`.

## Open issues

- Eleven of 88 source rows have no verified source snapshot hash. Their URLs, retrieval times, and statement locators remain available, but byte-for-byte replay of those source pages is not possible from this release.
- Publisher URLs may change or disappear. A link and retrieval timestamp prove the recorded locator, not current reachability or current page content.
- The included 76 events are the source-supported response subset, not a complete Taiwan disaster inventory. Forty-six inspected event identities were left out because no action fact passed this release's source and rights screen; some might later be merged with included events after independent identity review.
- Event windows sometimes describe the period covered by a report. They do not prove the exact onset or end of the weather system, and some events have no reported end date.
- Area labels come from reports and have no released geometry. Location completeness varies, and road segments cannot be treated as point coordinates.
- The source site reuse declarations have exceptions for specially marked third-party works and personal information. This release uses only normalized non-personal facts; any later attempt to distribute source documents requires a separate source-specific rights check.
- NCDR aggregate impact and other excluded sources need separate rights and provenance qualification before release. No absent aggregate was converted to zero or to a negative observation.

The published tables include source URLs, statement locators, and normalized record hashes so each included observation can be reviewed independently. Their use does not require an application, database, or project-specific runtime.
