# Copy Learning Hub — LIGHT Governance v1.0 (Design Reference)

> **Status: PROPOSAL / NON-OPERATIVE.** This document is a reference for Codex investigation and implementation planning, **not** an effective policy, approval, or permission to merge, deploy, modify repository settings, or override existing rules.
>
> Repository: `myaiwouldbemine/myaiwouldbemine-Copy-Learning-Hub`  
> Date: 2026-11-05  
> Inspiration: `reconstruction-core` SLIM Governance; **independent project authority**.

## 1. Purpose

LIGHT Governance aims for **minimum governance, sufficient assurance** in a multi-subject, Code-First, Evidence-Driven learning platform. The product is reproducible learning, not governance paperwork.

**Good governance is not maximum governance.** Do not add mandatory ceremony without evidence of material benefit.

## 2. LIGHT principles

- **L — Learning First:** prioritize accurate, understandable, reproducible learning.
- **I — Issue & Intent:** record goal, WHY, scope, boundary, and acceptance; trivial changes may use a PR without a separate Issue.
- **G — Guardrails:** preserve Human authority, source integrity, security, PR/CI/merge safeguards.
- **H — Human-Guided Autonomy:** Human decides objectives and material boundaries; Builder owns HOW within authorization.
- **T — Traceable Delivery:** use GitHub Issues, PRs, commits, checks, and source evidence as primary records.
- **Verification:** proportionate to actual risk and claims; never confuse tests with learning assessment.

## 3. Roles and authority

| Actor | Responsibility |
| --- | --- |
| Human Owner | Goal / WHY / Scope / Boundary, material direction, exceptional approval, merge authorization |
| ChatGPT | Optional goal framing, comparison, teaching design, review support; not a second authority |
| Claude Code / Codex | Peer Builders/Reviewers; investigation, plan, implementation, tests, evidence, readback |
| GitHub | Durable Issue/PR/commit/check record and actual repository controls |

No Agent role, review, or plan implies GitHub formal approval, merge permission, or authority to change security settings. Respect actual permissions and current policy.

## 4. Lifecycle

**Define → Plan (proportional) → Build → Verify → PR/Review → Authorized Merge → Delivery/Closure.**

One coherent work item should normally complete its authorized investigation, implementation, correction, and verification without a new Issue for every stage. Do not add routine Human approval checkpoints within authorized scope. Escalate when scope, material direction, safety, licensing, or authority requires it.

An interrupted session resumes from actual GitHub state, outstanding obligations, and current branch/head. Do not declare closure with in-scope acceptance criteria unfinished; state blockers and leave the work open. A reopened issue resumes the remaining obligation, not a fictional fresh success.

## 5. Risk model — **DEFAULT L0**

**Default risk classification for a newly proposed CLH work item is L0 (lightweight intake).** This is a starting assumption **only**; the Builder must inspect affected surfaces, impact, reversibility, and current authorization **before acting**. Reclassify immediately when the work is not genuinely low-risk. Uncertainty about material impact must not be treated as L0.

| Level | Examples | Planning | Verification / Review |
| --- | --- | --- | --- |
| **L0 Default / Low** | typo, formatting, nonsemantic text/link maintenance, clearly reversible low-impact change | concise PR description | self-review + applicable checks |
| **L1 Standard** | substantive new lesson, code example, website feature, routine code changes | brief plan in Issue or PR | tests, source review, optional cross-review |
| **L2 Material** | curriculum restructuring, governance semantics, cross-subject architecture, substantial workflow changes | Human-approved plan | cross-review preferred; decision and impact recorded |
| **L3 Critical** | bulk deletion, source-evidence rewriting, permissions/secrets/rulesets/deployment identity, irreversible migration | case-specific Human confirmation **before action** | enhanced verification, rollback and explicit authorization |

**Default L0 ≠ automatic authorization, exemption from PR, bypass of CI, or merge permission.** L0 cannot override an existing higher-risk category or operative governance. A seemingly small edit that changes a source claim, public publishing rights, CI security, or governance obligations is not L0. Classify by actual consequences, not file size. If unsure, investigate first and conservatively elevate.

## 6. Existing CLH safeguards to preserve

The proposed `GOVERNANCE.md` v1.1 and `AGENTS.md` on `feat/CLH-001-project-bootstrap` remain the current implementation reference until their actual adoption status is verified. This proposal does **not** amend them.

- Keep `main` stable: topic branch → PR → applicable CI/review → authorized merge. No routine direct push, force-push, or bypass.
- `mkdocs build --strict` for affected site/navigation work; run actual relevant checks and report results truthfully.
- Verify current PR head, blocking review conversations, required checks, and applicable GitHub rules immediately before merge.
- No implicit Agent merge authorization. Explicit Human authorization for the specific PR or clearly scoped class is required; high-risk operations additionally require case-specific confirmation.
- PR checks must not deploy unmerged code. Pages deployment is main-only or individually authorized under operative rules.
- Separate policy document changes from actual GitHub Settings/Rulesets changes; Markdown alone does not configure enforcement.
- For solo maintenance, do not invent mandatory external reviewer approval; prefer peer-Agent review for material work, allow recorded self-review for truly low-risk work.
- Respect confidentiality, licensing, source provenance, and immutable historical evidence.

If LIGHT conflicts with operative CLH governance, **do not silently replace the operative rule**: identify the exact difference in the proposed Plan and obtain the required Human decision.

## 7. Verification: three separate claims

1. **Build verified**: actual tests, CI, MkDocs build, links and affected render checks.
2. **Content verified**: exact checked PDF pages, source paths, code, formulas, explanations, provenance and permissions.
3. **Learning verified**: a learner actually performed and passed a relevant exercise, trace or understanding assessment.

A build PASS never implies content or learning PASS. Use `PASS`, `FAIL`, `NOT RUN`, `N/A` accurately. Identify `PDF SOURCE`, `VERIFIED SOURCE CODE`, `TEACHING EXAMPLE`, `EXTERNAL VERIFIED`, `UNVERIFIED` as applicable. Never invent line numbers, screenshots, test results, or learning outcomes.

Substantial courses may use `README.md`, `EVIDENCE.md`, and `TERMINOLOGY.md`; minor edits do not require empty templates. Apply the OS v3.1 Code-First standard to OS lessons where relevant, not automatically to other subjects.

## 8. Minimum durable evidence

Normally the Issue/PR, commits, and CI provide sufficient traceability. Record goal/scope, changed surfaces, actual tests, content evidence where applicable, review, risk, unresolved gaps, and next steps. No mandatory per-Issue standalone plan/execution files or parallel decision ledger in v1.0. Preserve existing records; do not rewrite historical evidence to make a later claim appear true.

**Claim ≤ actual evidence.** Authorization is not proof of effectiveness; a green CI check is not proof of semantic completeness.

## 9. Exceptions, closure, and governance stop condition

Escalate before unauthorized scope expansion, destructive or high-risk action, material policy conflict, or new Human decision. Within authorized scope, the Builder should investigate and fix issues without repeatedly seeking permission. Report unresolved blockers rather than claiming completion.

Closure requires the authorized acceptance criteria to be met, evidence linked, applicable review/CI/merge conditions satisfied, and remaining limitations stated. If merge/deployment is not authorized or not complete, report the precise partial state; do not imply delivery.

Do not introduce additional QA actors, gates, hooks, registries, decision-loading machinery, or governance documents by default. Revisit governance only on material recurring defects, new material risk, or new operating requirements, with an explicit cost/benefit case.

## 10. Codex implementation assignment (not authorization)

Codex should: (1) read the current `main`, CLH-001 Issue/PR, feature-branch `GOVERNANCE.md` v1.1 and `AGENTS.md`; (2) compare them with this proposal and `reconstruction-core` SLIM principles; (3) propose a minimal effective LIGHT mechanism, preserving security and merge controls; (4) present a Human-reviewable Plan and policy delta; (5) implement only within authorized scope on a separate feature branch/PR; (6) verify claims and leave merge/deploy/settings changes untouched absent explicit authorization.

**This document is a reference, not an approved Plan or an operative policy.**

## References

- [reconstruction-core SLIM baseline Issue #39](https://github.com/myaiwouldbemine/reconstruction-core/issues/39)
- [reconstruction-core governance simplification Issue #119](https://github.com/myaiwouldbemine/reconstruction-core/issues/119)
- [Copy Learning Hub bootstrap Issue #2](https://github.com/myaiwouldbemine/myaiwouldbemine-Copy-Learning-Hub/issues/2)
- [Copy Learning Hub bootstrap PR #1](https://github.com/myaiwouldbemine/myaiwouldbemine-Copy-Learning-Hub/pull/1)
