# Maintenance

Dependency and GitHub Actions updates are proposed weekly by Dependabot, with grouped updates and a small open-PR limit. Review behavior changes and merge only after required CI passes; automatic merging and mandatory human approvals are not configured.

External Actions are pinned to verified full commit SHAs with readable version comments. Update the SHA and comment together. Pinning an Action implementation does not freeze its transitive dependencies.

Main should reject force pushes and deletion and require a pull request with the always-running CI checks listed below. No human approval is required. Required checks must not use workflow-level PR path filters, which can leave documentation or dependency PRs pending indefinitely. Keep check names stable or migrate the ruleset when changing them.

Release tags must match `release.yaml`, `metadata/dataset.json` and `CITATION.cff`. Validate dataset checks and metadata before publishing. Publishing a GitHub release archives it on Zenodo, which assigns a version DOI; never replace assets on an already published release.

Required CI: `ReleaseGuard` and `LineageGuard`, on every pull request. These independently validate dataset structure and local provenance/hash integrity. Root lineage.yaml is not included in the frozen dataset manifest; a CI-only change needs no new dataset release. TWDisaster and TAG-Twin internal Evidence Release have independent event sets and release histories.
