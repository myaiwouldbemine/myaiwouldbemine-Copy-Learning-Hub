# Issue 46 Phase 0 — v4.1 to v5.0 Coverage Gap Report (read-only audit)

Issue: https://github.com/myaiwouldbemine/myaiwouldbemine-Copy-Learning-Hub/issues/46
Method: pypdf text extraction of lec08.pdf (78 pages) and lec09.pdf (55 pages); structural counts of `docs/preview/*/index.md` (v4.1) and the v5 ZIP `docs/preview/*/index.md`. Visual figure QA: NOT RUN.

Inputs: lec08.pdf sha256 2088ee05ba8252286b6b25649e8ef6396f2ffa6b4c46842ccd715209af7c2284; lec09.pdf db416d27d80f638c7ce18163086b54a4676e01545443165831151c7976c32f42; CLH_Lec08_v5_fresh_20261107.zip c241d1b259298341bf0dc379ed4b5c9445e2560317c9bfa5e6e9dc32d01dbf11; CLH_Lec09_v5_fresh_20261107.zip 1890d842934eadf048b253c748162e5e0c92e90bd763fd7e7a983998fbac3f90. ZIP integrity PASS. Pages without text layer: LEC08 p.36; LEC09 pp.10, 11, 23, 53.

| Metric | v4.1 LEC08 / LEC09 | v5 LEC08 / LEC09 |
|---|---|---|
| Lines | 724 / 594 | 560 / 434 |
| Headings | 59 / 46 | 21 / 20 |
| Code blocks | 14 / 10 | 1 / 1 |
| Mermaid | 3 / 3 | 0 / 0 |
| SVG refs (files identical) | 4 / 4 | 4 / 4 |
| Concept body (section 3) | large | about 3.8 KB / 3.3 KB |
| NachOS traces | V3-A to V3-G, REPO-VERIFIED additions, call-flow matrix | one pseudocode flow, 3 permalinks |
| Review Slides (5 per lesson) | full Q&A | one line each |
| Page map | LEC08 78/78 p.N; LEC09 27/55 | 78/78 and 55/55 with anchors |

Concept coverage by PDF range (v5 3.x sections): LEC08 pp.4-11, 12-18, 19-29, 30-38, 39-43, 44-47, 48-59, 60-76; LEC09 pp.4-12, 12-14, 15-16, 17-23, 25-38, 39-42, 43-51. LEC08 pp.1-3, 77-78 and LEC09 pp.1-3, 24, 52-55 have index entries only.

Regressions v5 vs v4.1 (decision owner: ChatGPT + Human): page-by-page lecture explanations; worked derivations (binding, contiguous, paging, hierarchical, segmentation); Review answers; V3-A..G code traces; Mermaid diagrams; Knowledge Connection depth. v5 gains: thematic structure, complete page anchors, source-boundary wording.

Spot checks: LEC08 p.42 EMAT (150 ns at 70%, 122 ns at 98%) matches PDF text PASS. Figures, formulas on image-only pages: NOT RUN. v5 own QA report says figure QA incomplete and Browser/Obsidian/CI/Pages NOT RUN.

Defects found: generator raises `WikiLink anchor not found in NYCU_OS_LEC09: 4.1 Demand Paging 與 Page Fault（PDF pp.8–14）` (LEC08 line 159); `--check` fails likewise.
