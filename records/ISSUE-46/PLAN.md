# Issue 46 plan — LEC08/LEC09 v5.0 full-rebuild integration (Umbrella for #42 and #45)

Issue: https://github.com/myaiwouldbemine/myaiwouldbemine-Copy-Learning-Hub/issues/46
Related: #42 (v4.1 preview, foundation), #45 (PDF deep links, to be superseded), Learning Records #26 (LEC08) and #41 (LEC09) stay OPEN and are not owned here.
Accountable Builder: Claude Code (sole). Base: origin/main bc19fef (PR #44 merge) at branch creation.
Companion records (same commit): `COVERAGE_GAP_REPORT.md`, `LINK_AUDIT.md`.
Human decisions applied (Issue 46 comments): v5.0 is the integration base; v4.1 is not; PDFs are not published; #42/#45 closure is authorized after evidence transfer.

## Goal
Integrate the v5.0 DRAFT rebuild of LEC08 (78 PDF pages) and LEC09 (55 PDF pages) as one canonical Markdown per lesson, derive the MkDocs preview and the flat-root Obsidian note from it without independent body edits, and add Link-First connections (Source, Code, Knowledge, Evidence, Relearning) through a shared PDF page mapping and switchable Source Resolver. Track #42 and #45 remaining work in this Issue.

## Why
Phase 0 audit (see companion reports): the v5.0 ZIPs are intact and page-complete (133/133 anchored), but (a) the v5 teaching body is much thinner than v4.1 (about 3.8 KB and 3.3 KB of concept text, 1 code block, 0 Mermaid, 5 one-line Review answers), (b) `scripts/build_preview_pages.py` fails on v5 (WikiLink anchor `4.1 Demand Paging ... (PDF pp.8-14)` does not exist in v5), (c) code permalinks use `blob/main` and three line ranges are off, (d) no usable PDF page links exist, and (e) figure/formula visual QA is incomplete. Merging without resolving these would ship a regression or a broken build.

## Scope
1. Canonical files: `OBSIDIAN_VAULT/NYCU_OS_LEC08.md`, `NYCU_OS_LEC09.md`, `_attachments/` (v5 base). Generated: `docs/preview/lec0{8,9}/` via `scripts/build_preview_pages.py` (extended). Obsidian and MkDocs are both derived or validated from the same canonical file.
2. Shared PDF page mapping data (PDF physical page numbers 1-78 and 1-55, per-concept page ranges) plus a build-time Source Resolver with three modes:
   - Public: emits `<authorized-pdf-url>#page=N` only when a rights-confirmation flag and an authorized URL are configured. Default OFF.
   - Private/Local: no public URL; local-viewer link pattern or instruction for a legitimately held local/private PDF. Nothing is uploaded.
   - Unavailable: shows "PDF p.N" as plain text with source location; no link is generated, so no dead links.
3. Source evidence: recheck every cited NachOS range against the actual source and pin permalinks to a commit SHA (candidate: nycu-os `aa8a5fa8...`, to be re-resolved at implementation time). Correct line ranges (Load L106-174, Run L104-150, Translate L185-250 as observed).
4. Generator fixes: WikiLink anchors against v5 headings; drift check (`--check`) extended to cover resolver output and PDF mapping.
5. Tests, QA and records under `records/ISSUE-46/`.
6. Umbrella tracking of #42 and #45 (Dependency & Closure Matrix below).

## Boundary
- No original PDF, RAW_DATA or exported lesson PDF is committed, pushed or deployed. RAW_DATA stays ignored. Public mode stays disabled until the Human confirms redistribution rights.
- Content authorship stays with ChatGPT + Human (AGENTS.md 03). The Builder imports v5 faithfully and fixes mechanical links and anchors only. Gaps against v4.1 (see Coverage Gap Report) are reported and marked PENDING for Human/ChatGPT decision; the Builder does not write teaching content, new Review answers, derivations or Knowledge Connections. v4.1 text may be cited only as a comparison baseline or reference, and may be re-used only if the Human approves specific passages after re-verification; it is never the body that v5 is stitched onto.
- DRAFT label retained. Existing `docs/subjects/` content, GOVERNANCE.md, AGENTS.md, workflows and the verifier are unchanged. The live v4.1 preview is replaced only through the governed PR and only after explicit Human authorization at that stage.
- No direct push to main, no force push, no merge or Pages deployment without a separate authorization. Learning Records #26/#41 stay OPEN.

## Dependency & Closure Matrix
| Issue | Role | State at plan time | Transfer to #46 | Closure condition |
|---|---|---|---|---|
| #42 | Foundation (generator, `/preview/` paths, DRAFT banner, drift check) | Preview live: PR #43 merge 52e64c0, PR #44 merge bc19fef, Pages readback SHA bc19fef, both URLs HTTP 200 | Accessibility audit: NOT RUN. Obsidian desktop rendering: NOT RUN. Five candidate Knowledge Connections: PENDING, handed to #26/#41. | Add the post-PR-44 deployment SHA readback record; post transfer comment; then close per Governance, stating the two QA items are transferred, not passed. |
| #45 | Superseded by #46 | OPEN, no Plan, PR or implementation | All five acceptance criteria and details (next section) | After transfer evidence is recorded in #46, mark Superseded and close with the statement that the feature is NOT complete and nothing is marked PASS. |
| #46 | Umbrella | Phase 0 / Plan | Tracks all of the above; PLAN and RESULT preserve each Issue's acceptance state | Close only after implementation, deployment readback, archive readback. |
| #26, #41 | Learning Records | OPEN | none | Remain OPEN; engineering success is not content approval. |

## #45 acceptance transferred in full
1. Rights gate: no full PDF is published until the Human confirms ownership/permission or license; otherwise a rights-safe alternative (Private/Local or Unavailable mode) is documented and used. Status: PENDING (Human has not confirmed); this plan implements the rights-safe alternative.
2. Page-cell links: leftmost cell of each page-index row is a keyboard-accessible, descriptive link to the correct PDF physical page (not the printed slide number), 78/78 and 55/55, opening in a new tab with `rel="noopener noreferrer"`, where a permitted source exists; otherwise Unavailable-mode text. Status: NOT RUN.
3. Concept deep links only where the page mapping is evidenced; never invented. Status: NOT RUN.
4. Verification: desktop and mobile, link accessibility, PDF link 200 and Content-Type (Public mode only), first/middle/last representative pages, browser-native page navigation, fallback for viewers that ignore `#page=`, `mkdocs build --strict`. Status: NOT RUN.
5. No unrelated content changes; DRAFT label, SVG/Mermaid and existing knowledge links preserved; #26/#41 remain OPEN. Status: to verify.
Also: canonical Markdown stays single-source and the generator stays in sync; the rights decision is recorded in `records/ISSUE-46/`; Issue #45 owns no separate engineering after supersession.

## Implementation plan
1. Commit this Plan alone (records only) as the first commit; run the Plan field check.
2. Import v5 canonical notes and SVGs byte-faithfully from the local ZIPs (not committed ZIPs); record ZIP and PDF SHA-256 values in RESULT.
3. Fix mechanical link/anchor defects against actual v5 headings; fix and pin NachOS permalinks after re-reading the sources.
4. Add the PDF page mapping data and the Source Resolver (three modes), emitting page-cell and concept links; default Unavailable/Private, Public gated by the rights flag.
5. Extend `build_preview_pages.py` and its tests: drift, anchors, WikiLinks, resolver modes (including that Public emits nothing without the flag), no PDF in the tree.
6. Visual QA of figure/formula pages (LEC08 p.36; LEC09 pp.10, 11, 23, 53 have no text layer) from the local PDF; unchecked pages stay flagged, not guessed.
7. Draft PR, tests, browser desktop/mobile, accessibility audit, Obsidian desktop rendering (or NOT RUN with reason), RESULT.md with per-Issue acceptance status, Self-Review, Ready, governed merge, Pages SHA readback, archive readback, then #42/#45 closure and #46 closure each with its own evidence.

## Acceptance criteria
- v5 is the base; regression report vs v4.1 is resolved or explicitly PENDING with Human decision recorded.
- `build_preview_pages.py --check` passes; no raw WikiLinks; all page anchors 133/133 resolve.
- Five link classes present and audited; code links pinned to a commit with verified line ranges.
- Resolver verified in all three modes; no PDF in Git, site or deployment.
- `mkdocs build --strict`, unit/governance tests, required CI all succeed; browser, accessibility and Obsidian results reported separately as PASS/FAIL/BLOCKED/PENDING/NOT RUN.
- #42 and #45 acceptance status preserved in RESULT.md; #26/#41 OPEN.

## Verification strategy
`git diff --check`; `python -m unittest discover -s scripts -p 'test_*.py'`; `scripts/build_preview_pages.py --check`; `mkdocs build --strict`; `scripts/validate_preview_site.py site`; PDF-absence check on repo and built site; permalink line-range recheck against the pinned commit; Chromium desktop 1366 and mobile 390; accessibility audit; Obsidian desktop; `scripts/verify_plan_records.py <base> <head> 46` once RESULT.md exists; post-deploy SHA readback. Mocks are never reported as live E2E.

## Risks
Content thinness of v5 (human decision needed); generator incompatibility; rights uncertainty (mitigated by default-off Public mode); stale line numbers; unverified figures; replacing the live v4.1 preview (needs separate authorization); Mermaid depends on the theme CDN.

## Rollback
Revert PR of the merge commit, tested; no history rewrite. The v4.1 preview remains recoverable from main history (bc19fef).

## Evidence archive
`records/ISSUE-46/RESULT.md`: source hashes, coverage and link audit results, resolver evidence, per-Issue acceptance table, PR, commit, CI, deployment SHA, browser/a11y/Obsidian results, deviations, unfinished.

## Revision history
- r0: initial Plan (Phase 0 audit plus Human approvals of 2026-11-07).
