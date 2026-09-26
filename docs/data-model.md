# Data model

The four UTF-8 CSV tables form the complete canonical dataset. Each row has a stable `TWD-` identifier assigned at the initial release; IDs are opaque, never encode paths or release dates, and must never be renumbered when rows are added. JSON Schemas in `schema/` list exact column order, allowed values, and key relationships. The `_json` cells are JSON embedded in CSV text, not a second editable data store.

| Entity | Key | Meaning |
| --- | --- | --- |
| Event | `events.event_id` | One source-supported historical event identity in this release |
| Observation | `observations.observation_id` | One source-supported factual response record |
| Source | `sources.source_id` | One public source URL and captured byte identity where a hash exists |
| Event-source | `(event_sources.event_id, event_sources.source_id)` | A source that supports at least one included observation for the event |

`events.name` and `aliases_json` retain historically used names. `start_date` is the earliest source-reported start date among included reports, and `end_date` is the latest reported end date where provided; the pair is a compiled report window, not a precise event onset or cessation. `reported_areas_json` lists administrative areas mentioned in included observations. It is not a polygon, a complete affected-area list, or proof of damage in every listed area.

All current observations have `category=response_action`. `observation_type` says what kind of action the source records, while `state` preserves the source's status: `ordered`, `planned`, `reported_closed`, and `completed` are different claims. `attributes_json` holds source-supported quantities, units, and qualifiers; inspect its keys before aggregation. A cumulative evacuation count, a current shelter count, and a planned count must not be summed as though they had the same meaning.

Observation, action, report, publication, and availability times have separate columns and precision fields. An empty time means the source does not establish it; `unknown` precision reinforces that state. Day precision uses a date without a fabricated clock time. Where a time is known, the ISO 8601 offset is retained. `available_at` is never inferred from report or publication time. Source retrieval and dataset release time are metadata in `sources.csv` and `metadata/dataset.json`, not event or action times.

`area_name` is source wording normalized as a location label, and `spatial_precision` states the supported scale: `event`, `county`, `township`, `village`, or `road_segment`. A road segment is a named stretch, not a surveyed geometry. There is no geometry in this release and no implied 20 m grid location. Empty location is unknown, not nationwide.

`source_locator` identifies the page, section, or record within the original source. `source_version` distinguishes curated views of a document. `source_record_sha256` identifies the earlier normalized record used during initial curation; `sources.snapshot_sha256`, when present, identifies original source bytes. Neither hash establishes rights or factual accuracy on its own. `versions_json` lists version labels that were found to refer to the same URL and source snapshot. A missing source hash is explicit, not a string of zeroes.

Empty CSV cells mean unknown or unsupported. `[]` in array cells means no entries recorded; `{}` in `attributes_json` means no extra attributes recorded. These are not negative observations. There are no weak signals, inferred priority preferences, candidate eligibility flags, model features, or split labels in the canonical tables.
