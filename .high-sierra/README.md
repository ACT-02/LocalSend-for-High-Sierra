# High Sierra maintenance metadata

These files are maintained by the upstream-release synchronization workflow.

- `last-synced-release.txt` records the latest official LocalSend release that this repository has intentionally processed.
- `source-base.txt` records the upstream commit used for the current source snapshot.
- `source-kind.txt` is `upstream-main-baseline` for the historical first-working snapshot and `official-release` after an exact official release has been synchronized.

Automatic GitHub Release publication is allowed only when `source-kind.txt` is `official-release`. This prevents the historical post-release baseline from being mislabeled as an exact official-release backport.
