# TWDisaster

[![Latest release](https://img.shields.io/github/v/release/KageRyo/TWDisaster?style=flat-square)](https://github.com/KageRyo/TWDisaster/releases/latest) [![License](https://img.shields.io/github/license/KageRyo/TWDisaster?style=flat-square)](LICENSE) [![Dataset gate](https://github.com/KageRyo/TWDisaster/actions/workflows/dataset-gate.yml/badge.svg?branch=main)](https://github.com/KageRyo/TWDisaster/actions/workflows/dataset-gate.yml) 

The initial release provides a curated set of source-supported historical disaster response observations from official public sources in Taiwan. The dataset currently covers 76 weather-related disaster events from 2001 to 2025 and includes observations of evacuation, shelter operations, road conditions, emergency response activities, rescue, and resource deployment.

The dataset reflects the coverage and granularity of the included source material and is intended as a reusable historical record rather than an exhaustive catalogue of disaster events or response activities. [[正體中文]](README_ZH.md)

## Files

| Path | Contents |
| --- | --- |
| [`data/events.csv`](data/events.csv) | Stable event identities and source-reported date windows |
| [`data/observations.csv`](data/observations.csv) | Factual response observations with time, area, source, and locator |
| [`data/sources.csv`](data/sources.csv) | Publisher, original URL, retrieval time, integrity, and rights basis |
| [`data/event_sources.csv`](data/event_sources.csv) | Explicit event-source relationships |
| `schema/*.schema.json` | JSON Schemas for rows read from the four CSV files |
| `metadata/dataset.json` | Dataset description, scope, counts, and versions |
| [`metadata/manifest.json`](metadata/manifest.json) and [`metadata/checksums.sha256`](metadata/checksums.sha256) | Canonical artifact counts and SHA-256 hashes |

Read CSV files as UTF-8 with a header row. A spreadsheet can open each file directly; R can use `read.csv("data/events.csv", fileEncoding = "UTF-8")`, and Python's standard `csv.DictReader` can read it without installing a package. Cells ending in `_json` contain ordinary JSON arrays or objects. Join `observations.event_id` to `events.event_id`, `observations.source_id` to `sources.source_id`, and use `event_sources.csv` for all distinct event-source links.

Empty CSV cells mean unknown, unsupported, or unavailable, according to the field definition; they never mean zero or false. A literal `0` inside `attributes_json` is an explicitly recorded value. `[]` means an empty recorded list. Dates and timestamps retain their documented precision: a day-level action is represented as `YYYY-MM-DD`, while a known time retains its original ISO 8601 offset. Source-reported event windows are not exact meteorological onset or end times. Locations retain the source's scale and are not geocoded to a finer unit.

See [data model](docs/data-model.md), [methodology](docs/methodology.md), [provenance](docs/provenance.md), and [source and rights details](docs/sources.md). Original source documents are not included. Some source URLs may move, and 11 source records lack a verified snapshot hash; these and other known gaps are listed in [provenance](docs/provenance.md).

## Rights and citation

The original repository prose, schema definitions, and dataset selection and arrangement use the [CC BY 4.0 license](LICENSE). Individual source-backed facts and source materials remain subject to the rights described in [DATA_LICENSE.md](DATA_LICENSE.md), each `sources.csv` row, and the linked official reuse declarations. Attribute the original publisher when using a source-backed row. This license does not replace upstream rights or grant rights to absent PDFs, HTML archives, images, or logos.

Cite this release using [CITATION.cff](CITATION.cff), and cite the corresponding original publisher and URL for specific observations.

## Maintenance

See [maintenance conventions](docs/maintenance.md) for dependency updates, required CI, Action pinning and release validation.
