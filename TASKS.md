# Civics-Exam-Prep — TASKS.md

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

Backlog for **Civics-Exam-Prep** (slug: `civics-exam-prep`): open, accuracy-reviewed practice items
for free high-stakes exams — the **U.S. naturalization civics test** first (clean public-domain
license), then **HSE-aligned** subject practice (gated on IP/legal review). See `PLAN.md` for full
context.

Two gates are hard product requirements and the first build items: the **item schema + "no source,
no item" validation/CI gate** and the **accuracy + non-partisan + sensitivity rubric**. This is a
**MEDIUM risk-tier** project — items need accuracy-reviewer sign-off before shipping; any drift into
individualized legal/immigration advice escalates the item to HIGH and out of scope. **No partner is
yet secured**, so all delivery-dependent tasks carry `requestor: TO BE SECURED` and
`verifiedNeed: false`.

## How these tasks map to Elyos

Each task below becomes an Elyos **Task JSON** validated against `packages/schema/src/schemas.ts`.
Field mapping:

- **id** — stable slug `civics-exam-prep-<area>-NNN` (e.g. `civics-exam-prep-schema-001`).
- **title** — the task title in the milestone table.
- **project** — `civics-exam-prep`.
- **type** — one of `code | research | writing | data | design-spec | maintenance`.
- **lane** — `donated` (default; no funded tasks planned. Any `funded` task must add
  `fundedBudgetUsd` with a hard cap).
- **priority** — `high | medium | low`.
- **domain** — array, e.g. `["education","civic","exam-prep","content"]`.
- **riskTier** — `low | medium | high`. Items asserting exam-correct answers or civic facts are
  `medium`; pure schema/tooling/app/infra is `low`; the project has no `high` tasks unless content
  drifts into individualized legal/immigration advice (out of scope).
- **urgent** — boolean (no urgent tasks at cold-start; reserved for a known official-question-set or
  officeholder change requiring fast re-verification).
- **deliverable** — `pr | dataset | document | translation`.
- **tokenEstimate** — `small | medium | large` (maps to the Size column).
- **status** — `open | in-progress | review | delivered | done` (all start `open`).
- **context / objective / acceptanceCriteria[] / resources[] / output** — per task.
- **requestor** — partner/steward/reviewer; `TO BE SECURED` where unknown.
- **verifiedNeed** — `true` only once a specific partner/need is confirmed; otherwise `false`
  (currently `false` everywhere — no partner secured).
- **outputLicense** — code: **MIT**; content/data/docs: **CC-BY-4.0**.

Size legend: small ≈ `small`, med ≈ `medium`, large ≈ `large`.
Reviewer "Accuracy reviewer" = qualified civics/government educator or naturalization-prep
instructor (MEDIUM-tier sign-off, **TO BE SECURED**); "IP/legal reviewer" gates the HSE lane
(**TO BE SECURED**).

---

## Milestone M0 — Foundation, schema & accuracy/IP gates (cold-start)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-exam-000 | Pilot-exam + licensing decision (citizenship first; HSE trademark/source framing) — gates content | research | small | medium | document | — | Maintainer + IP/legal reviewer |
| civics-exam-prep-schema-001 | Item-bank schema (stem/options/answer/rationale/sources/dynamicAnswer/lastVerified/validUntil/lang/license) | design-spec | medium | low | document | — | Maintainer |
| civics-exam-prep-repo-002 | Monorepo + pnpm + TS/ESM + CI (build/test/lint + content-schema validation) skeleton | code | small | low | pr | — | Maintainer |
| civics-exam-prep-rubric-003 | Accuracy-review + non-partisan + sensitivity rubric + "not official/not advice" framing + dynamic-answer policy | design-spec | medium | medium | document | — | Accuracy reviewer |
| civics-exam-prep-validate-004 | Validation tooling: "no source, no item", single-correct, distractor sanity, readability, staleness — wired into CI | code | medium | low | pr | 001, 002 | Maintainer |

**Acceptance criteria — key tasks**

- **civics-exam-prep-exam-000** (pilot-exam + licensing decision)
  - Locks **citizenship as the first exam** on the public-domain (17 U.S.C. § 105) USCIS footing, with
    rationale recorded.
  - Records the **HSE posture**: no proprietary/trademarked content (GED®/HiSET®/TASC); original items
    aligned to **publicly available standards**; non-affiliation disclaimer; HSE lane **gated on the
    M3 IP/legal review** (`hse-legal-013`) before any HSE content.
  - States the decision rule + dates: pilot exam/licensing by 2026-07-31; accuracy reviewer by
    2026-09-30; partner by 2026-12-31; build-vs-pivot decision by ~2027-03-31.
  - The specific partner remains `TO BE SECURED`; the **decision rule and deadlines are fixed**.

- **civics-exam-prep-schema-001** (item schema)
  - Defines every field incl. `sources[]` (official citation + URL + retrieval date + version +
    legal-status note), `dynamicAnswer` (`static | officeholder | state-dependent`), `correctAnswer`
    (forbidden for dynamic items — they reference a lookup/method instead), `lastVerified`/
    `validUntil`, `language`, `outputLicense`, `reviewedBy`/`signoffVersion`.
  - Requires **≥ 1 source per item** and exactly one correct answer for static items.
  - Items stored as version-controlled files so provenance + review are visible in history.

- **civics-exam-prep-rubric-003** (review rubric + policies)
  - Specifies the **accuracy** check (every claim traceable to an official source), the
    **non-partisan** check (only what official sources state; no opinion/advocacy/party-candidate
    framing), and the **sensitivity** check (no demeaning/exclusionary framing of immigrants/groups).
  - Mandates persistent **"Study material — not an official test; not legal/immigration advice;
    verify current answers with the official source"** labeling.
  - Defines the **dynamic-answer policy** (never serve a stale static answer for officeholder/state
    items; show the "verify current" affordance + official pointer; short re-verification cadence).
  - Defines version-scoped sign-off, the reviewer veto, and the HIGH-escalation rule for advice-drift.
  - Reviewed + signed off by the accuracy reviewer (recorded in the reviewers ledger).

- **civics-exam-prep-validate-004** (validation + CI gate)
  - CI **fails the build** on any item missing a source, lacking a single correct answer (static),
    containing duplicate/contradictory options, exceeding the readability target, or past `validUntil`
    without a flag.
  - Reports citation coverage (target 100%) and a staleness report per run.

**M0 Definition of Done:** schema + validator merged enforcing "no source, no item," single-correct,
readability, and staleness in CI; accuracy + non-partisan + sensitivity rubric published and
expert-reviewed; TS/ESM/pnpm skeleton + green CI; **pilot-exam + licensing decision locked**
(citizenship first; HSE framing + gate defined); non-official/non-advice framing wired into item +
app templates.

---

## Milestone M1 — Citizenship content (accuracy-reviewed)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-sources-005 | USCIS source vetting + provenance recording (2008 + 2020 questions/answers + reading/writing vocab) | data | medium | medium | dataset | 000, 004 | Accuracy reviewer + Maintainer |
| civics-exam-prep-items-006 | Draft original citizenship practice items (MC + flashcard) covering all civics topics, cited to USCIS | writing | large | medium | dataset | 001, 003, 005 | Accuracy reviewer |
| civics-exam-prep-dynamic-007 | Dynamic-answer subsystem (officeholder/state items) + "verify current" affordance + lookup | code | medium | medium | pr | 004, 005 | Maintainer + Content reviewer |
| civics-exam-prep-review-008 | Accuracy + non-partisan + sensitivity review of citizenship items (sign-off recorded) | research | medium | medium | document | 006, 007 | Accuracy reviewer |
| civics-exam-prep-a11y-009 | Plain-language + reading/writing-vocab study support + initial a11y pass on items | writing | medium | low | document | 006 | Maintainer |

**Acceptance criteria — key tasks**

- **civics-exam-prep-sources-005** (USCIS source vetting)
  - Confirms + records public-domain status for each source; captures **both** the 2008 and 2020
    civics question/answer sets and the reading/writing vocabulary, noting which applies by filing
    date.
  - Provenance recorded per source (document, citation, URL, retrieval date, version, legal-status).
  - Accuracy reviewer confirms the official answers before items are authored.

- **civics-exam-prep-items-006** (citizenship items)
  - Original stems, distractors, and rationales (we do **not** copy any third-party question set);
    every item cites an official USCIS answer (100% citation coverage; validator passes).
  - Covers all official civics topics (principles of democracy, system of government, rights/
    responsibilities, American history, geography, symbols, holidays) at the plain-language target.
  - Dynamic items reference the dynamic-answer subsystem, **not** a static key.

- **civics-exam-prep-dynamic-007** (dynamic-answer subsystem)
  - Officeholder/state-dependent items (e.g., current President/senators/governor/representative) are
    **never** shipped as a single static correct answer.
  - App renders a **"verify the current answer for your state/today"** affordance with an official-
    source pointer; a maintained lookup keyed by state/date backs it; short re-verification cadence +
    on-change refresh; staleness test passes.

- **civics-exam-prep-review-008** (accuracy/non-partisan review)
  - Independent ≥ 10% spot-check finds **0** factual errors (any found → block + root-cause); **0**
    items flagged as partisan/opinion or insensitive.
  - Version-scoped sign-off recorded in the reviewers ledger before ship.

**M1 Definition of Done:** USCIS sources vetted + provenance recorded; original citizenship items
covering all topics drafted, 100% cited, and **accuracy/non-partisan-reviewed (sign-off recorded)**;
dynamic-answer subsystem live (no stale static answers); reading/writing-vocab support + plain-
language pass done. **Kill-gate:** if no accuracy reviewer is secured, content does not ship —
platform/schema hold.

---

## Milestone M2 — Delivery (app + exports + i18n scaffolding)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-app-010 | No-account offline PWA: practice / mock-test / flashcard modes + persistent non-official labels | code | large | low | pr | 006, 007 | Maintainer |
| civics-exam-prep-export-011 | Exporters: printable PDF study sheets + spaced-repetition (CSV/Anki) deck + open JSON dataset | code | medium | low | pr | 006 | Maintainer |
| civics-exam-prep-i18n-012 | Multilingual study scaffolding (UI + rationale + glossary; test items kept in official language) | writing | medium | medium | translation | 006, 010 | Accuracy reviewer (per language) |

**Acceptance criteria — key tasks**

- **civics-exam-prep-app-010** (practice PWA)
  - Requires **no account**, collects **no PII**, stores progress **local-device only**, works
    **offline**, runs **no ads**.
  - Practice mode gives immediate feedback + cited rationale; mock-test mode labels its score
    "practice-only, not an official score"; persistent "not official / not advice / verify with
    USCIS" labeling on every screen.
  - Meets initial WCAG 2.2 AA (keyboard + screen-reader usable).

- **civics-exam-prep-i18n-012** (multilingual scaffolding)
  - Translates UI, instructions, rationales, and glossary; **keeps the test items themselves in the
    official test language** (does not translate the answer surface a learner is tested on).
  - Each translated rationale/glossary set is reviewed for accuracy per language; Spanish first.

**M2 Definition of Done:** no-account offline PWA (practice/mock/flashcard) with persistent
non-official labels shipped; PDF + spaced-repetition + JSON exporters working with license +
non-official labels; multilingual scaffolding (≥ Spanish) live with test items in the official
language; WCAG 2.2 AA initial pass.

---

## Milestone M3 — HSE-aligned content (gated on IP/legal review)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-hse-legal-013 | HSE IP/legal review: trademark posture + public-standard source set + non-affiliation framing — GATE | research | medium | medium | document | 000 | IP/legal reviewer + Maintainer |
| civics-exam-prep-hse-items-014 | Original HSE-aligned practice items (RLA/Math/Science/Social Studies) cited to public standards | writing | large | medium | dataset | 013, 001, 004 | Accuracy reviewer (subject) |
| civics-exam-prep-hse-review-015 | Subject-matter accuracy + sensitivity review of HSE items (sign-off recorded) | research | medium | medium | document | 014 | Accuracy reviewer (subject) |

**Acceptance criteria — key tasks**

- **civics-exam-prep-hse-legal-013** (IP/legal gate)
  - Confirms **no proprietary/trademarked content** is reproduced; **nominative trademark use only**;
    a clear **non-affiliation disclaimer** ("not GED®/HiSET® test content; not affiliated/endorsed").
  - Approves the **public-standard source set** (e.g., CCR Standards for Adult Education + openly-
    licensed descriptors) with provenance + reuse terms recorded.
  - **No HSE content task starts until this review clears** (recorded in governance).

- **civics-exam-prep-hse-items-014** (HSE items)
  - Original items across RLA/Math/Science/Social Studies aligned to the approved public standards;
    each cited; 100% citation coverage; validator passes.
  - Carries the non-affiliation disclaimer and the non-official/non-advice labels.

**M3 Definition of Done:** IP/legal review cleared and recorded; original HSE-aligned items across the
four subjects drafted, cited to public standards, subject-matter-reviewed (sign-off recorded), and
labeled non-affiliated/non-official. *(Branch does not start until `hse-legal-013` clears.)*

---

## Milestone M4 — Eval, hardening & pilot readiness

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-eval-016 | Item-quality eval (single-correct, distractor plausibility, readability, bias scan) + defect report | code | medium | medium | pr | 006, 014 | Maintainer + Accuracy reviewer |
| civics-exam-prep-hardening-017 | Full WCAG 2.2 AA + offline verification + independent ≥10% accuracy spot-check + learner-pilot runbook | code | medium | medium | document | 008, 010, 016 | Accuracy reviewer + Maintainer |

**Acceptance criteria — key tasks**

- **civics-exam-prep-eval-016** (item-quality eval)
  - Automated checks confirm exactly one correct answer (static), plausible non-overlapping
    distractors, reading level within target, and a basic bias/sensitivity scan; an LLM-judge pass
    **flags for human review, never auto-publishes**.
  - Defects reported per release and resolved before ship.

- **civics-exam-prep-hardening-017** (hardening + readiness)
  - Practice surface + exports meet **WCAG 2.2 AA**; offline verified end-to-end.
  - Independent **≥ 10% accuracy spot-check** passes (0 errors; any found blocks release); learner-
    pilot onboarding runbook written (how a partner runs a cohort, anonymous outcome survey included).

**M4 Definition of Done:** item-quality eval green with defects resolved; WCAG 2.2 AA + offline
verified; independent accuracy spot-check clean; learner-pilot runbook ready.

---

## Milestone M5 — Partner adoption & handoff (the deed)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-pilot-018 | Secure delivery partner + steward + independent accuracy/non-partisan audit of shipped content | research | medium | medium | document | 008, 010, 011, 017 | Steward + Accuracy reviewer |
| civics-exam-prep-handoff-019 | Pilot cohort uses the bank; readiness/pass outcomes recorded (anonymous, voluntary, aggregate) | maintenance | medium | medium | document | 018 | Steward + Maintainer |

**Acceptance criteria — key tasks**

- **civics-exam-prep-pilot-018** (secure partner + audit)
  - A real adult-ed program / library / literacy council / community college / immigrant-serving
    nonprofit is secured as pilot; steward assigned; `verifiedNeed` flips to `true`.
  - Independent accuracy + non-partisan audit of shipped content passes; citation/staleness gates
    confirmed in force.
  - Driven by the dated partner-acquisition plan; if no partner by **~2027-03-31**, apply the
    **build-vs-pivot decision rule** (donate the vetted bank + app to an OER home, or mothball to
    maintenance-only) — recorded in governance — rather than ship to no real beneficiary.

- **civics-exam-prep-handoff-019** (closed loop — the deed)
  - A pilot cohort (≥ 50 learners target) uses the bank; an **anonymous, opt-in** pre/post survey
    records readiness improvement (≥ 60% target); voluntary, anonymous pass reports collected where
    ethically possible (**never** touching immigration status or PII).
  - Outcomes recorded with the partner's confirmation; non-official/non-advice labeling upheld.

**M5 Definition of Done:** project-level **Definition of Shipped** met — a real partner adopts the
bank, real learners use it to prepare, accuracy/non-partisanship independently verified, citation/
staleness gates in force, and the readiness-improvement outcome recorded. *(Gated on a secured
partner — TO BE SECURED.)*

---

## Milestone M6 — Sustain & scale (post-delivery)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| civics-exam-prep-ops-020 | Ops runbook + content review cadence (dynamic-answer refresh + official-change re-verification) + outcomes dashboard + maintenance rotation | maintenance | medium | medium | document | 019 | Maintainer + Steward |

**Acceptance criteria — civics-exam-prep-ops-020**
- Runbook covers deploy, content updates, source re-verification, and partner support.
- **Content review cadence** defined + scheduled: dynamic/officeholder items on a short cadence and
  on known changes (elections, official-question-set revisions); static civics facts on a longer
  cadence; HSE standards re-checked on revision — all driving the staleness fail-safe.
- Outcomes dashboard tracks learners reached, readiness improvement, and voluntary pass reports (not
  engagement metrics); named maintenance rotation; documented, reviewer-gated process for adding
  languages/exams.

**M6 Definition of Done:** project sustainably maintained with outcomes tracked, a rotation owning
it, a runtime-enforced review cadence for content, and a gated expansion process.

---

## Backlog / future

| ID | Title | Type | Size | Risk | Deliverable | Notes |
|---|---|---|---|---|---|---|
| civics-exam-prep-langs-021 | Additional languages for study scaffolding (beyond Spanish) | translation | medium | medium | translation | Per partner demand; per-language accuracy review; test items stay in official language |
| civics-exam-prep-audio-022 | Read-aloud audio for items + rationales (low-literacy / low-vision support) | code | medium | low | pr | Accessibility win; aligns with read-aloud-audio sibling |
| civics-exam-prep-srs-023 | In-app spaced-repetition scheduling (local-only, no accounts) | code | medium | low | pr | Builds on export deck; keep PII-free |
| civics-exam-prep-hiset-024 | HiSET/TASC-aligned practice (additional HSE exams) | writing | large | medium | dataset | Only after HSE IP/legal review extended to these brands |
| civics-exam-prep-naturalization-english-025 | Naturalization English reading/writing practice module | writing | medium | medium | dataset | Original items from USCIS vocab; keep in official language |
| civics-exam-prep-partner-dashboard-026 | Optional privacy-preserving partner cohort dashboard (aggregate only) | code | medium | medium | pr | Aggregate counts only; no individual learner records |

---

## Example task JSON

Complete, schema-valid Task JSON for the first M0 task (`civics-exam-prep-exam-000`):

```json
{
  "id": "civics-exam-prep-exam-000",
  "title": "Pilot-exam + licensing decision (citizenship first; HSE trademark/source framing)",
  "project": "civics-exam-prep",
  "type": "research",
  "lane": "donated",
  "priority": "high",
  "domain": ["education", "civic", "exam-prep", "licensing", "content"],
  "riskTier": "medium",
  "urgent": false,
  "deliverable": "document",
  "tokenEstimate": "small",
  "status": "open",
  "context": "Civics-Exam-Prep produces open, accuracy-reviewed practice questions for free high-stakes exams (U.S. naturalization civics test and high-school-equivalency subjects), each item cited to official study materials. The two exams have very different licensing footings: USCIS naturalization materials are U.S. Government works in the public domain (17 U.S.C. section 105), while 'GED' is a registered trademark of GED Testing Service LLC with proprietary, copyright-protected test content. Sequencing and legal posture therefore depend on this decision, which gates all content work. No delivery partner or accuracy reviewer is yet secured.",
  "objective": "Lock the pilot exam and the project's licensing posture: citizenship first on the clean public-domain footing; HSE reframed as original practice aligned to publicly available standards (no proprietary/trademarked content, nominative trademark use only, non-affiliation disclaimer) and gated behind the M3 IP/legal review. Record the decision rule and the dated partner-acquisition plan.",
  "acceptanceCriteria": [
    "Selects citizenship (U.S. naturalization civics test) as the first exam, with rationale recorded (public-domain USCIS sources per 17 U.S.C. 105)",
    "Records the HSE posture: no proprietary/trademarked content (GED, HiSET, TASC); original items aligned to publicly available standards (e.g., CCR Standards for Adult Education); nominative trademark use only; prominent non-affiliation disclaimer; HSE content gated on the M3 IP/legal review (hse-legal-013)",
    "States the dated plan and decision rule: pilot exam/licensing by 2026-07-31; accuracy reviewer by 2026-09-30; delivery partner by 2026-12-31; build-vs-pivot decision by ~2027-03-31 (donate vetted bank to an OER home or mothball rather than ship to no beneficiary)",
    "Confirms output licensing: MIT for code, CC-BY-4.0 for content/data, with attribution to official sources preserved on redistribution",
    "Notes that the specific delivery partner remains TO BE SECURED (verifiedNeed=false) while the decision rule and deadlines are fixed"
  ],
  "resources": [
    "planning/projects/civics-exam-prep/PLAN.md",
    "planning/ROADMAP.md",
    "CLAUDE.md",
    "docs/good-deed-definition.md",
    "packages/schema/src/schemas.ts"
  ],
  "output": "A recorded decision document fixing citizenship as the pilot exam, the HSE trademark/source framing and IP/legal gate, the dated partner-acquisition plan with a build-vs-pivot rule, and the licensing posture (MIT code / CC-BY-4.0 content) - the decision that gates all downstream content tasks.",
  "requestor": "TO BE SECURED",
  "verifiedNeed": false,
  "outputLicense": "CC-BY-4.0"
}
```
