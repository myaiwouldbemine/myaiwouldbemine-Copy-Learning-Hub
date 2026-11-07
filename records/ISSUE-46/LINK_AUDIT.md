# Issue 46 Phase 0 — Five-class Link Audit (read-only)

Issue: https://github.com/myaiwouldbemine/myaiwouldbemine-Copy-Learning-Hub/issues/46

| Class | v5 state | Status |
|---|---|---|
| Source (PDF page) | 78 + 55 in-page anchors present; one `#page=` occurrence is explanatory text only; no PDF is public | In-page PASS; deep links NOT RUN (rights unconfirmed) |
| Code | 3 GitHub links per lesson, all `blob/main`, none commit-pinned. Blob SHAs match QA report (translate.cc 969203b8, addrspace.cc cd995514, scheduler.cc 0a8170cd; nycu-os main aa8a5fa8 on 2026-11-07). Line ranges vs source: RestoreState L257-261 correct; Translate stated L185-249, actual L185-250; Load stated L106-166, actual L106-174; Run stated L104-148, actual L104-150 | FAIL until pinned and corrected |
| Knowledge | LEC08 3, LEC09 4 WikiLinks with WHY text; LEC08 line 159 anchor does not exist in v5 | FAIL (build breaks) |
| Evidence | Few derivations (EMAT); traces labelled teaching examples; no runtime evidence | PENDING |
| Relearning | Points to RELEARNING_SUPPLEMENTS/ISSUE-26 and Issue 41 only; no per-concept links | PENDING |

Representations: MkDocs generation fails on v5 (above). Flat-root Obsidian note equals the docs copy in the ZIP; Obsidian desktop rendering NOT RUN.
