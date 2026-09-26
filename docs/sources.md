# Sources and rights review

Version 0.1.1 includes 88 physical source records from four publisher website families. Each source has an original URL and a linked official reuse declaration in `data/sources.csv`. The source rows require attribution to the original publisher. The declarations concern material on the relevant official sites and include exceptions; TWDisaster publishes normalized non-personal facts only.

| Website family | Sources | Observations | Rights basis |
| --- | ---: | ---: | --- |
| Highway Bureau (`thb.gov.tw`) | 39 | 182 | [Official website data reuse statement](https://www.thb.gov.tw/cp.aspx?n=439) |
| National Fire Agency (`nfa.gov.tw`) | 13 | 98 | [Official website information publication statement](https://www.nfa.gov.tw/eng/index.php?code=list&ids=634) |
| Water Resources Agency (`wra.gov.tw`) | 26 | 96 | [Official WRA website data reuse statement](https://www.wra.gov.tw/wra02/cp.aspx?n=9884) |
| Executive Yuan (`ey.gov.tw`) | 10 | 19 | [Official website data reuse statement](https://www.ey.gov.tw/Page/2EADDBFEDDB6357E) |

These counts are source rows after same-URL, same-snapshot deduplication, not a count of original PDFs or distinct reports on the internet. One source can support more than one event, so `event_sources.csv` has 89 rows. Some pages had no archived source hash and are identified by empty `snapshot_sha256`; this is a provenance gap, not a license conclusion.

The upstream source registry used during initial curation marked records as public references and did not qualify its internal event export. TWDisaster separately reviewed the official website declarations above for this narrower factual publication. No general permission is asserted for content from `bear.emic.gov.tw`, `246.ardswc.gov.tw`, `dra.ncdr.nat.gov.tw`, municipal sites, or remote-sensing products in this version. Their facts and documents remain outside the public canonical tables pending review.

A source-specific notice or third-party right can limit reuse even when a general website declaration exists. Users should cite the publisher and URL listed on the specific source row, and should not treat the presence of a link or SHA-256 as a grant to copy the original document. See [DATA_LICENSE.md](../DATA_LICENSE.md) for the dataset rights boundary.
