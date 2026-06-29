# Civics-Exam-Prep — PLAN.md

> Status: Draft · Version: 0.2.0 · Last updated: 2026-06-29 · Owner: TBD (maintainer) · Lane: donated

Open, accuracy-reviewed practice questions for **free, high-stakes equivalency and citizenship
exams** — beginning with the **U.S. naturalization civics test** and expanding to **high-school-
equivalency (HSE)** subject practice — built as original items sourced and cited to **official study
materials**, delivered for free, offline-capable, and accessible. The product is the **vetted item
bank + its provenance + a no-account practice surface**, handed to learners through adult-education,
library, and immigrant-serving partners. It is **study material, not legal/immigration advice and
not an official test**, and it is **non-partisan** on all civic content.

---

## Executive summary

Passing a high-stakes exam is often the single gate between a person and citizenship, a diploma, a
job, or college. The two exams in scope are *gateways for exactly the people least able to pay for
prep*: prospective citizens (many with limited English and limited income) and adults without a
high-school credential. Free, trustworthy, accurate practice is scarce; the web is full of
ad-laden, unsourced, sometimes-wrong "practice tests," and the good material is fragmented across
official PDFs that are hard to study from. Civics-Exam-Prep produces **original practice items whose
every answer is cited to an official source**, reviewed for accuracy and non-partisanship, and
delivered free, offline, and accessibly.

The single most important design fact is **provenance + accuracy as a gate, not a footnote**. A
wrong practice answer on a naturalization or HSE exam actively harms the beneficiary — they study
the wrong thing and fail a life-changing test. So **no item ships without (a) a citation to an
official source and (b) recorded accuracy review**, and the bank is engineered so that an item
without a verified source literally cannot be published (CI-enforced). This is a **MEDIUM risk-tier**
project (domain-accuracy critical; civic neutrality required) — not HIGH, because it offers no
individualized legal/medical/financial advice — but the accuracy and licensing gates are treated as
safety-critical.

The **second** design fact is the **licensing split**, which dictates sequencing. The
naturalization civics materials are **U.S. Government works in the public domain** (USCIS), giving a
clean legal footing — so **citizenship is built first**. "GED®" by contrast is a **registered
trademark of GED Testing Service LLC (a commercial joint venture)** with proprietary,
copyright-protected test content; we will **not** reproduce GED items or imply affiliation. The HSE
lane is therefore reframed as **original practice aligned to publicly available skill standards**
(e.g., the College & Career Readiness Standards underpinning HSE exams), shipped with a clear
non-affiliation disclaimer, and **gated behind an explicit IP/legal review** (M3) before any HSE
content work begins.

The **third** design fact is **test-version currency**, which is itself the project's hardest live
problem and the strongest validation of its own thesis. The naturalization civics test is **not a
single static exam**. As of this plan, the live split is **2008** (for N-400s filed before **October
20, 2025**) vs the **new 2025 USCIS civics test** (for N-400s filed **on or after October 20, 2025**);
the **2020 redesign is historical only** (administered Dec 1 2020 – Apr 30 2021, then reverted). The
two live versions differ **structurally**: **2008 = 100-question bank, 10 asked, 6 to pass**; **2025
= 128-question bank, 20 asked, 12 to pass**; plus a **65/20 special-consideration** reduced (starred)
bank for applicants aged 65+ with 20+ years as a lawful permanent resident. The bank therefore carries
a first-class **`testVersion`** dimension (`2008 | 2025 | senior-65-20`) and **parametrizes question
count and pass threshold per version** — every mock-test, metric, and source-vetting task is
version-scoped. Because **which version applies to a person is eligibility-adjacent**, version
selection is presented as **neutral, USCIS-sourced information with a link to USCIS, never as a
determination** (see §8); and because the **2025 redesign is politically charged**, any "the test
changed" copy uses a **reviewer-vetted, strictly factual, non-causal** framing (§7–8).

Honesty note: **no partner organization or requestor is yet secured.** Every delivery-dependent task
is marked `TO BE SECURED` with `verifiedNeed: false` until a real adult-education program, library
system, literacy council, or immigrant-/refugee-serving organization adopts the bank for its
learners. The project is **not "shipped" on merge**; it is shipped only when real learners use it to
prepare and we record genuine readiness/pass outcomes.

**Partner-acquisition plan (dated) and build-vs-pivot decision rule.** Outreach is time-boxed
against the build, not left open-ended: by **2026-07-31** the pilot exam + licensing posture is
locked (citizenship first; HSE framing decided); by **2026-09-30** a credentialed accuracy reviewer
is secured (civics/government educator or naturalization-prep instructor) and ≥ 3 candidate delivery
partners are in active conversation; by **2026-12-31** a pilot partner + steward is secured (M5
gate). **Decision rule:** if no accuracy reviewer is secured by the M1 content date, M1 content does
not ship (platform + schema hold). If no delivery partner is secured by **2027-03-31** (≈ M4
completion), the project does **not** dump content to no one: it either (a) **pivots** the last mile
(donate the vetted, openly-licensed bank + practice app to an existing OER platform — e.g., a public
library consortium or an adult-literacy commons — as a reference deed) or (b) **mothballs** to
maintenance-only, with the decision recorded in governance. The vetted citizenship bank remains a
valuable public artifact in either case.

---

## Problem & beneficiaries

**Who is helped (directly):**
- **Prospective U.S. citizens** preparing for the naturalization civics test — disproportionately
  low-income, often with limited English proficiency, frequently studying without paid courses.
- **Adults without a high-school credential** pursuing an HSE diploma to unlock jobs, training, and
  college — a population that skews lower-income and is poorly served by paid test-prep.

**Who is helped (ultimately):** their families and communities, who benefit when a member gains
citizenship, a diploma, and the economic mobility that follows; and the broader public good of an
informed, civically literate populace.

**The need.** Both exams are high-stakes and *free to take*, yet quality preparation is not freely
or reliably available. Official study materials exist (USCIS publishes the civics questions, answers,
and reading/writing vocabulary, **including multilingual resources**; HSE exams publish skill
descriptors and some free practice) but are **fragmented, PDF/list-bound, and not structured for
active recall or spaced practice**. The gap is therefore **not** "no translations exist" — USCIS
publishes multilingual resources and free nonprofits (e.g., USAHello) already offer the Q&A in many
languages — but that **no open, structured, original-rationale, version-aware, spaced-practice item
bank exists** that learners can study from and that others can reuse. The free web fills the
remaining gap with **unsourced, often version-confused, and sometimes inaccurate** "practice tests,"
frequently ad-supported and inaccessible to screen-reader and low-literacy users. A wrong or outdated
answer here has real cost: a failed naturalization interview, a re-take fee, delay, and
discouragement.

**Verified need / partner:** **TO BE SECURED.** No specific adult-education program, library,
literacy council, community college, or immigrant-/refugee-serving nonprofit has yet agreed to adopt
or co-develop the bank. Target partner profiles: a public library system's adult-learning program; a
community-college adult-education / ESL department; a literacy coalition; an immigrant- or
refugee-resettlement nonprofit running naturalization workshops; a state adult-education office.
Until one is secured, the project builds the agent-neutral platform, the item schema, and the
**citizenship** bank (clean public-domain license) for review, marking all delivery/adoption work
`TO BE SECURED`. Outreach is **dated** (above); a **build-vs-pivot decision rule** governs slippage.

---

## Goals and non-goals

**Goals**

- Produce an open, free, accuracy-reviewed bank of **original** practice items for the U.S.
  naturalization civics test, each item **cited to an official USCIS source**.
- Guarantee, by construction and CI, that **no item ships without a citation and recorded accuracy
  review**, and that civic content is **non-partisan and factual**.
- Handle **dynamic answers** (officeholders that change, and answers that depend on the learner's
  state) correctly, with a "verify the current answer" affordance and a runtime staleness fail-safe.
- Be **version-correct and version-aware**: track the live **2008** and **2025** USCIS test versions
  (plus the **65/20** senior special-consideration bank), parametrize question count and pass
  threshold per version, treat **2020 as archived**, and present version selection as **neutral,
  USCIS-sourced information (not a determination of which test applies to a person)**.
- Deliver the bank through a **free, no-account, offline-capable, accessible** practice app plus
  **portable exports** (printable PDF, spaced-repetition deck, open dataset).
- Extend to **HSE-aligned** subject practice **only behind an explicit IP/legal review**, as
  original items aligned to publicly available standards, with a non-affiliation disclaimer.
- Reach real learners through a partner and **record genuine outcomes** (study completion,
  self-rated readiness, and pass results where ethically collectable).

**Non-goals**

- **Not** a reproduction of any proprietary or trademarked test (esp. **not** GED® items); **not**
  affiliated with, endorsed by, or representing USCIS, GED Testing Service, or any testing body.
- **Not** an official test, a score predictor presented as authoritative, or a guarantee of passing.
- **Not** legal or immigration advice; not a substitute for USCIS guidance, an accredited
  representative, or an attorney. (We point learners to official sources for binding answers.) In
  particular, **not** a determiner of **which test version applies to a specific person** or of
  65/20 / disability-exception eligibility — these are eligibility-adjacent and routed to USCIS.
- **Not** a partisan civics product: no opinion, advocacy, candidate/party framing, or
  "interpretation" beyond what official sources state.
- **Not** a data-harvesting study app: no accounts required, no learner PII collected to use the
  core product, no ads, no selling data.
- **Not** breadth-first: depth and verified accuracy for citizenship first; HSE and more languages
  later, and never breadth without review.

---

## Success metrics (outcomes)

Outcome-centric and beneficiary-first. Engagement vanity metrics (DAU, pageviews) are explicitly
**not** success.

| Metric | Baseline | Target (pilot) | How measured |
|---|---|---|---|
| Citation coverage of shipped items | none | **100%** of items carry an official-source citation (no source → cannot publish) | CI citation-coverage check on the item bank |
| Accuracy-review coverage | none | **100%** of shipped items have recorded reviewer sign-off (version-scoped) | Governance/reviewer ledger + CI status gate |
| Independent accuracy spot-check error rate | n/a | **0** factual errors found in a random ≥ 10% audit per release; any found → release blocked + root-caused | Independent reviewer audit; defect log |
| Non-partisanship | n/a | **0** items flagged as opinion/advocacy/partisan framing in review | Non-partisan rubric review + reviewer audit |
| Dynamic-answer correctness | n/a | **0** state/officeholder-dependent items served as a single static "correct" answer without the "verify current" affordance | Schema constraint + staleness test + audit |
| Stale-content containment | n/a | **0** items served past their `validUntil` without auto-flag/withhold + re-verification | Staleness test against `lastVerified`/`validUntil` |
| Version-correctness | n/a | **0** items mis-tagged by `testVersion`; **0** mock tests using the wrong format/threshold for the selected version (2008 = 10-of-100/6-to-pass; 2025 = 20-of-128/12-to-pass; 65/20 reduced bank) | Schema `testVersion` constraint + mock-test format test + reviewer audit |
| Readability of items + rationales | n/a | citizenship items at a **plain-language target (≈ grade 6–8)** unless the official term requires otherwise | Automated readability check + reviewer judgment |
| Accessibility | n/a | practice surface meets **WCAG 2.2 AA**; works **offline**; usable with screen reader + keyboard | Automated + manual a11y audit |
| Learners reached through a partner | 0 | ≥ **50** learners use the bank in a pilot cohort | Partner-reported (privacy-preserving counts) |
| Self-rated readiness improvement | 0 | ≥ **60%** of surveyed pilot learners report increased readiness after use | Anonymous opt-in pre/post survey |
| Documented pass outcomes (where ethically collectable) | 0 | ≥ **10** learners report passing after using the bank (voluntary, anonymous) | Voluntary partner-mediated self-report |

The **defining success outcome** (Definition of Shipped): a real partner adopts the bank and real
learners use it to prepare, with accuracy/non-partisanship independently verified and at least the
readiness-improvement target met — not merely a merged dataset.

---

## Scope

**In scope**

- An **item-bank schema** (machine-readable) with stem, options, correct answer, rationale,
  per-item **official-source citation + provenance**, exam, topic, difficulty, language,
  `testVersion` (`2008 | 2025 | senior-65-20`), `dynamicAnswer` flag, and `lastVerified`/`validUntil`.
  Question count and pass threshold are **parametrized per `testVersion`** (2008 = 10-of-100/6;
  2025 = 20-of-128/12; 65/20 = reduced starred bank).
- **Validation tooling** in CI: schema validity, exactly-one-correct-answer, citation presence,
  distractor sanity, readability, and dynamic-answer/staleness checks.
- The **citizenship** practice bank: original multiple-choice + flashcard items covering all
  official civics topics for **both live versions (2008 and 2025)**, cited to USCIS answers, with the
  **65/20 senior special-consideration subset** offered as a first-class filtered view, plus
  **reading & writing (English vocabulary) practice** as a deliverable (not just incidental support).
- An **oral/interview practice mode** (TTS/audio prompts + self-check) reflecting that the real test
  is an **oral interview**, clearly labeled "practice only, not an official score" and making **no
  AI-scoring claim**.
- **Dynamic-answer handling**: officeholder/state-dependent items rendered with a "verify the
  current answer for your state/date" affordance and a maintained lookup, never a stale static
  answer presented as authoritative.
- A **free, no-account, offline-capable, accessible** practice surface (PWA): practice mode, mock-
  test mode, flashcard/recall mode.
- **Exports**: printable PDF study sheets, a spaced-repetition deck (CSV/Anki-compatible), and the
  open JSON dataset itself.
- **Multilingual study scaffolding**: UI, instructions, rationales, and glossary in multiple
  languages (test items themselves kept in the official test language; see §7).
- An **HSE-aligned** subject bank (RLA/Math/Science/Social Studies) **only after** the IP/legal
  review, as original items aligned to public standards with a non-affiliation disclaimer.
- An **item-quality eval** (clarity, single-correct, distractor plausibility, readability, bias
  scan) and an outcomes/feedback loop.

**Out of scope (explicitly will NOT do)**

- Reproducing, paraphrasing-to-evade, or distributing any **proprietary/trademarked test content**
  (esp. actual GED®, HiSET®, or TASC items), or implying official affiliation/endorsement.
- Presenting itself as the **official test** or guaranteeing a pass / predicting an official score
  as authoritative.
- Any **individualized legal or immigration advice** (eligibility determinations, "should you
  apply," interview coaching beyond public study facts) — routed to official sources/accredited reps.
- **Partisan** content: opinions, advocacy, party/candidate framing, or interpretation beyond
  official-source statements.
- Collecting **learner PII**, requiring accounts, running ads, or monetizing/selling learner data.
- Serving **state/date-dependent answers** (current senators, governor, president, U.S.
  representative) as a single static "correct" answer.
- 50-state / all-exam breadth before the citizenship bank is accuracy-verified and shipped.

When a request or item touches the refused set (e.g., an HSE item that would copy proprietary
content, or a civics item drifting into opinion), it is **blocked from publication** by review/CI and
the issue is surfaced, not quietly shipped.

---

## Solution approach & architecture

This is primarily a **content + light delivery** project: the durable public good is the **vetted,
provenance-bearing item bank**, with a thin open app and exporters around it. Agent-neutral core; any
LLM-assisted drafting sits behind tooling and is always followed by human accuracy review.

**Stack.** TypeScript, ESM, pnpm workspaces (Elyos convention). Content stored as **structured
files** (JSON/YAML items) under version control — the dataset *is* the repo, so every change is
diffable, reviewable, and attributable. Validation via a schema (Ajv/Zod) run in CI. Delivery: a
static **PWA** (e.g., Astro/SvelteKit or plain TS — small, offline-first, no backend, no accounts),
served from static hosting. Exporters are small TS scripts. Any AI drafting uses Anthropic Claude
behind a thin provider-neutral client (model/pricing per the Claude API skill); **all drafted items
are human-reviewed before publish** — the LLM never has final say on a correct answer. Code license
**MIT**; content/data **CC-BY-4.0** (attribution to official sources preserved).

**Components**

1. **Item schema + content store (`/content`, `/schema`) — built first.** Each item is a record:
   `id`, `exam`, `testVersion` (`2008 | 2025 | senior-65-20`), `topic`, `stem`, `options[]`,
   `correctAnswer`, `rationale`, `sources[]` (official citation + URL + retrieval date +
   license/legal-status note), `difficulty`, `language`, `dynamicAnswer` (bool + kind: `officeholder`
   | `state-dependent` | `static`), `lastVerified`, `validUntil`, `reviewedBy`/`signoffVersion`. The
   bank parametrizes **question count + pass threshold per `testVersion`** (2008 = 10-of-100/6; 2025 =
   20-of-128/12; 65/20 = reduced starred bank) rather than assuming one static format. Items live as
   files so provenance and review are visible in version history.

2. **Validation + provenance enforcement (`/tools/validate`) — CI gate.** Enforces: schema
   validity; exactly one correct answer (or, for dynamic items, an explicit dynamic-answer record
   instead of a static key); **at least one official-source citation per item ("no source, no
   item")**; distractor sanity (no duplicate/contradictory options, no "all of the above" traps
   unless intended); readability within target; and the **staleness rule** (an item past
   `validUntil` is flagged/withheld). A PR that adds an item failing any check **fails the build**.

3. **Dynamic-answer subsystem (`/content/dynamic`).** For officeholder/state-dependent civics items
   (e.g., *"Who is one of your state's U.S. Senators now?"*, *"Who is the Governor of your state
   now?"*, *"What is the name of the President now?"*), the bank stores the **question and the method
   to find the current answer**, plus a maintained lookup table keyed by state/date, and the app
   renders a **"verify the current answer for your state/today"** affordance with a pointer to the
   official source. These items are **never** shipped as a single static correct answer.

4. **Practice surface (`/app`) — PWA.** No account, no PII, offline-capable. A **neutral version
   selector** lets the learner pick **2008 / 2025 / 65/20** with USCIS-sourced "if your N-400 was
   filed before/after Oct 20 2025…" guidance and a USCIS link — **information, never a determination**
   of which test applies to them (eligibility-adjacent → routed to USCIS). Modes: **practice**
   (immediate feedback + cited rationale), **mock test** (timed/sampled to the **selected version's
   format** — 10-of-100/6 vs 20-of-128/12 — score clearly "practice-only, not an official score"),
   **flashcard/recall**, and an **oral/interview practice mode** (TTS prompts + self-check, since the
   real test is oral; no AI-scoring claim). Persistent "Study material — not an official test; not
   legal/immigration advice; verify current answers and which test applies with USCIS" labeling.

5. **Exporters (`/tools/export`).** Printable **PDF** study sheets (for learners without reliable
   devices), a **spaced-repetition deck** (CSV/Anki-compatible), and the **open JSON dataset** for
   downstream OER reuse — all carrying source attribution and the non-official/non-advice labels.

6. **Item-quality eval (`/tools/eval`).** Automated checks (single-correct, distractor plausibility,
   reading level, simple bias/sensitivity scan) plus an LLM-judge pass that **flags for human
   review** (never auto-publishes). Reports defects per release.

7. **Official-update watch (`/tools/watch`) — CI.** Monitors the USCIS *Check for Test Updates* and
   2025-test pages and flags affected content for **re-verification** when USCIS publishes a change.
   This turns "the document went stale on its own currency axis" (the v0.1 → 2025 miss) into a
   **detected event** next time, feeding the staleness fail-safe and the review cadence.

**Claude API leverage (assistive only; human-gated).** Any AI drafting uses Anthropic Claude behind
the thin provider-neutral client (model/pricing per the Claude API skill). High-value, human-gated
uses: **drafting original items** (stems, plausible distractors, plain-language rationales) *from*
the official answers — never copying third-party question sets; **plain-language rewriting** to the
grade 6–8 target; **translation drafting** of UI/rationales/glossary (with human QA per language);
**spaced-repetition + difficulty calibration** proposals; and the **LLM-judge item-quality eval**
(flags single-correct violations, weak distractors, readability misses, possible bias → flags for a
human). **Where Claude must NOT have final say:** **accuracy to the official test** (a human verifies
every "correct answer" against current USCIS material — Claude drafts, it never certifies); **which
test version applies to a person** (eligibility-adjacent → route to USCIS, never decide); the
**non-partisan judgment** (the reviewer rubric is the authority); **translation QA** (a qualified
human verifies each language); and it **never fabricates** questions, answers, citations, or sources
("no source, no item" is CI-enforced, not model-trusted) and **never gives individualized
legal/immigration advice** (escalate, don't generate).

**Key decisions**

- **Provenance + accuracy are release gates, not documentation** — enforced in CI and review.
- **Citizenship first** (clean public-domain license); **HSE gated behind IP/legal review**.
- **Original items only** — we author distractors and rationales; we cite official *answers*, we do
  not copy proprietary test items.
- **Dynamic answers are first-class**, never silently static.
- **Version-awareness is first-class** — 2008 + 2025 (+ 65/20) tracked with format/threshold
  parametrized; 2020 archived; version selection is neutral USCIS-sourced info, not a determination.
- **Privacy by construction** — no accounts, no learner PII, no ads (see §14).
- Agent-neutral core; LLM drafting is assistive and always human-reviewed.

---

## Data, licensing & compliance

THIS IS THE CRITICAL SECTION. Be specific and conservative.

**Source material — citizenship (clean footing).** The U.S. naturalization civics test materials —
the official civics questions and answers, the **reading and writing vocabulary lists**, and related
USCIS study materials — are **works of the U.S. federal government and are in the public domain**
(17 U.S.C. § 105). We may freely reuse the **facts and official answers**; we still **cite and link**
each source and record provenance (source name, document, citation/URL, retrieval date, version,
license/legal-status note). We author **original** stems, distractors, and rationales rather than
copying any third party's question set.

**Test versions (currency — read carefully).** The civics test is **not static** and the version a
learner faces **depends on their N-400 filing date**:

- **2008 version** — applies to N-400s filed **before October 20, 2025**. Format: **100-question
  bank, 10 asked orally, 6 correct to pass**.
- **2025 version** — the **new USCIS civics test**, applies to N-400s filed **on or after October 20,
  2025**. Format: **128-question bank, 20 asked orally, 12 correct to pass**.
- **65/20 special consideration** — applicants aged **65+ with 20+ years as an LPR** study a
  **reduced (starred) subset**; carried as a first-class filtered view.
- **2020 version — historical only.** It was administered only **Dec 1 2020 – Apr 30 2021**, then
  reverted to 2008; it is **archived, not a live study target**.

The bank encodes this with a **`testVersion`** field and **parametrizes question count + pass
threshold per version** (no single static threshold). Source vetting captures both **live** versions
plus the 65/20 subset. Confirm current USCIS guidance at content time and re-verify via the
official-update watch (§6.7).

**Source material — HSE (encumbered; gated).** **"GED®" is a registered trademark of GED Testing
Service LLC**, a commercial joint venture (American Council on Education + Pearson); the actual GED
test content is **proprietary and copyright-protected**. We will **not** reproduce GED items,
paraphrase them to evade, or imply affiliation/endorsement. The HSE lane is therefore built as
**original practice aligned to publicly available skill standards** — e.g., the **College & Career
Readiness Standards for Adult Education** (a U.S. Dept. of Education publication, public domain) and
any **freely published, openly-licensed** official skill descriptors / free-practice domains — with a
prominent **"not affiliated with or endorsed by GED Testing Service / not GED® test content"**
disclaimer and **nominative trademark use only**. This lane does **not** begin until an explicit
**IP/legal review (M3, task `hse-legal-013`) clears the framing and source set**. The same caution
applies to HiSET® (ETS) and any other trademarked HSE brand.

**Provenance model.** Every item is backed by ≥ 1 `Source` record (official citation + URL +
retrieval date + version + legal-status note). The validator enforces **"no source, no item."**

**Staleness is fail-safe, not best-effort.** Each item carries **`lastVerified`** and a
**`validUntil`** derived from a per-type review interval (e.g., static civics facts re-verified on a
longer cadence; **dynamic/officeholder items on a short cadence**, and immediately on a known change
such as an election or a change to the official question set). At runtime/build, an item past
`validUntil` is **auto-flagged or withheld** (not served as current) until re-verified and
re-signed-off, which writes fresh dates. The "law/official-answer changed and content went silently
stale" failure mode becomes a **visible, gated event**.

**Output licensing.** Code: **MIT**. Content/data/docs: **CC-BY-4.0** (attribution to official
sources preserved on redistribution). Each export carries the license + the non-official/non-advice
labels.

**Privacy / PII stance (conservative).** The core product requires **no account and collects no
learner PII**. The practice app stores progress **locally on-device only** (no server, no profile).
Any optional outcome survey is **anonymous, opt-in, partner-mediated, and aggregate** — no
individual learner record, no immigration status, no contact info. No secrets, tokens, or PII in
logs, receipts, or committed files (Elyos rule).

**Non-partisanship & sensitivity (including a meta-layer).** Civic items state only what official
sources state; **no opinion, advocacy, party/candidate framing, or interpretation**. A non-partisan
rubric and reviewer sign-off are required (§8). Content avoids demeaning, exclusionary, or culturally
insensitive framing of immigrants or any group (sensitivity review in the rubric). **Meta-layer:**
the **2025 redesign is itself politically charged** (longer/harder, widely covered through a partisan
lens), so any learner-facing "the test changed / which version you take" copy must use a
**reviewer-vetted, strictly factual, non-causal** framing — **what changed, when, and who it applies
to, sourced to USCIS**, with **no political-causal narrative**. This explainer is an explicit rubric
item, and version selection is presented as neutral information routed to USCIS (not advice; see §8).

**Attribution.** Items cite official sources; redistribution preserves CC-BY attribution. Reviewers
are credited (with consent) in a reviewers ledger, version-scoped.

---

## Quality, review & risk gates

**Risk tier: MEDIUM** (per `docs/good-deed-definition.md`: domain-accuracy-critical content needing a
reviewer with relevant skill). It is **not HIGH** because it provides no individualized legal/medical/
financial advice — but accuracy, licensing, and non-partisanship are treated as safety-critical, and
any drift toward individualized immigration/legal advice **escalates the item to HIGH** and out of
scope unless a credentialed reviewer is engaged.

**Required reviews before a deed is "done":**

- **Maintainer** review on all PRs (engineering quality, agent-neutral core, schema/CI green, no
  PII/secrets in logs, license labels present).
- **Accuracy reviewer sign-off** — a qualified civics/government educator or experienced
  naturalization-prep instructor (and, for HSE, a relevant subject-matter educator) — recorded
  before any item bank ships. **No reviewer, no ship.** Sign-off is **version-scoped** (attaches to a
  specific item version + citation set; edits require re-sign-off, dovetailing with staleness dates).
- **Non-partisan + sensitivity review** against the published rubric for all civic content —
  **including the "the test changed" explainer and the version selector**, which must be strictly
  factual, USCIS-sourced, non-causal, and framed as **information, not a determination** of which
  test applies to a given person (eligibility-adjacent → routed to USCIS).
- **IP/legal clearance** for the HSE lane (trademark + source-reuse) before HSE content begins.
- **Accessibility review** (WCAG 2.2 AA) for the practice surface and exports.

**Persistent labeling:** every surface shows **"Study material — not an official test; not legal/
immigration advice; verify current answers and which test version applies to you with the official
source (USCIS)."**

**Definition of Shipped (project):** a real partner adopts the bank; real learners use it to prepare;
accuracy + non-partisanship are independently verified; citation/staleness gates are in force; and at
least the readiness-improvement outcome target is met and recorded.

---

## Roadmap & milestones

Phased: schema + accuracy/IP gates first; citizenship content next; delivery; HSE only behind legal
review; eval + hardening; partner adoption last (gated on a secured partner).

- **M0 — Foundation, schema & accuracy/IP gates (cold-start).**
  *Goal:* the item schema, validation/provenance CI gate, accuracy + non-partisan rubric, and the
  licensing posture exist before any content. *Exit:* repo + CI green; item schema + validator
  merged enforcing "no source, no item," single-correct, readability, staleness, **and `testVersion`
  validity with per-version question-count/pass-threshold parametrization (2008 + 2025 + 65/20; 2020
  archived)**; accuracy-review + non-partisan + sensitivity rubric published **including the
  reviewer-vetted "the test changed" explainer + neutral version-selector (not-advice) framing**;
  **pilot exam + licensing decision locked (citizenship first; HSE framing decided)**;
  non-official/non-advice framing wired into templates.

- **M1 — Citizenship content (accuracy-reviewed).**
  *Goal:* the citizenship practice bank, cited and expert-reviewed, with dynamic answers handled.
  *Exit:* USCIS sources vetted + provenance recorded **for both live versions (2008 + 2025) and the
  65/20 subset**; original items covering all official civics topics **per version** drafted and
  **accuracy-reviewed (sign-off recorded)**; **reading & writing (English vocabulary) practice** as a
  deliverable; **dynamic-answer subsystem live** (officeholder/state items never static); 100%
  citation coverage; plain-language + initial a11y pass. **Kill-gate:** if no accuracy reviewer is
  secured, content does not ship — platform/schema hold.

- **M2 — Delivery (app + exports + i18n scaffolding).**
  *Goal:* learners can actually study, online or offline, in their language. *Exit:* no-account
  offline PWA (practice/mock/flashcard **+ oral/interview practice** modes, with a **neutral
  version selector** and **per-version mock-test format**) with persistent non-official labels; PDF +
  spaced-repetition + JSON exports; multilingual UI/rationale/glossary scaffolding (test items in
  official language); **read-aloud/TTS audio** (offline) for low-literacy/ESL learners; WCAG 2.2 AA
  initial pass.

- **M3 — HSE-aligned content (gated on IP/legal review).**
  *Goal:* extend to HSE subjects **safely**. *Exit:* **IP/legal review cleared** (trademark posture
  + public-standard source set + non-affiliation disclaimer); original HSE-aligned items across
  RLA/Math/Science/Social Studies drafted, cited to public standards, and **subject-matter
  reviewed**. *(Does not start until the legal review clears.)*

- **M4 — Eval, hardening & pilot readiness.**
  *Goal:* prove item quality and harden for real learners. *Exit:* item-quality eval (single-correct,
  distractor plausibility, readability, bias scan) green with defects resolved; full WCAG 2.2 AA +
  offline verified; independent ≥ 10% accuracy spot-check passes; **official-update watch wired into
  CI (monitors the USCIS update/2025 pages → flags content for re-verification)**; **partner/org
  toolkit (printable class sets + facilitator guide)** drafted for CBO/library adult-ed; learner-pilot
  runbook ready.

- **M5 — Partner adoption & handoff (the deed).**
  *Goal:* real learners benefit. *Exit (Definition of Shipped):* a secured partner + steward; a pilot
  cohort uses the bank; accuracy/non-partisanship independently verified; readiness-improvement
  (and, where ethically collectable, pass) outcomes recorded. *(Gated on a secured partner — TO BE
  SECURED.)*

- **M6 — Sustain & scale (post-delivery).**
  *Goal:* durable maintenance and careful expansion (more languages/exams). *Exit:* maintenance
  rotation + ops runbook + outcomes dashboard; **content review cadence** (dynamic-answer refresh on
  schedule + on known changes; official-answer/standard/**test-version**-change re-verification driven
  by the official-update watch); gated expansion process (more languages/exams, and the reusable
  engine for other countries' citizenship tests).

Dependencies flow M0 → M1 → M2 → M4 → M5; **M3 (HSE) branches off M0 but is gated on its own IP/legal
review** and does not block citizenship delivery. The **pilot-exam + licensing decision is made in M0
and gates content**; M1 content blocks on the secured accuracy reviewer; M5 blocks on a secured
partner.

---

## Competitive landscape & differentiation

The naturalization-prep space is crowded but **structurally under-served on exactly the axes this
project gates on** (provenance, version-correctness, openness, accessibility). Mapping the field:

- **Official — USCIS Citizenship Resource Center** (uscis.gov/citizenship). The authoritative, free,
  public-domain source — now with multilingual resources and the 2025 materials. PDF/list-bound, not
  interactive, no spaced repetition, not built for low-literacy active recall. **This is the
  source-of-truth to cite, not a competitor to beat.**
- **USAHello** (free nonprofit). The closest mission-aligned peer: free, **Q&A in 17 languages with
  audio**, learner-friendly. *Weakness:* largely **reproduces official Q&A** rather than an original,
  provenance-bearing, openly-licensed, machine-readable bank; limited spaced-repetition/assessment;
  not an open dataset others can reuse.
- **Citizenry (app)** — most feature-rich: ad-free, supports **both 2008 and 2025**, AI mock
  interviews, Spanish virtual agent, flashcards/audio. *Weakness:* **closed-source, app-store walled,
  not open data, not publicly accessibility-audited**, single-vendor trust.
- **Citizen Now / "US Citizenship Test 2026 Plus" and SEO practice sites** — broad reach, AI/spoken
  feedback or large free question sets. *Weakness:* ads or paid tiers, closed, **unsourced**,
  inconsistent on version, generally not accessibility-audited — the exact "ad-laden, unsourced
  practice test" failure this project targets.
- **Quizlet / Anki community decks** — free, spaced-repetition-native, huge install base. *Weakness:*
  **no provenance, error-prone, version-confused** (decks mixing 100/128/"2024-2025"/state variants);
  a learner cannot tell which deck matches their test. **This is the clearest opening.**
- **iCivics / Khan Academy** — excellent free **K-12/general civics**, *not* naturalization prep:
  adjacent allies and style references, not competitors.
- **CBOs & libraries — CASA, CUNY Citizenship Now!, YMCA New Americans, public library adult-ed** —
  run in-person classes + application help. **Not competitors — they are the M5 delivery partners**
  (distribution, not rivalry).

**Differentiation (how this wins).** The durable edge is **not another study app** but an **open,
CC-BY, provenance-bearing, version-aware item bank** that becomes **reusable infrastructure** —
**distribution by reuse**:

1. **Provenance-as-a-gate + independent accuracy review** — a public trust artifact ("every answer
   cited to USCIS; reviewer signed off; spot-checked") no competitor offers.
2. **Open, reusable, version-aware dataset (CC-BY)** — libraries, CBOs, Quizlet/Anki authors, *and
   even rival apps* can ingest it; the bank becomes shared infrastructure, not a walled product.
3. **Correctness on the exact axis everyone else fails** — 2008/2025 version-awareness + 65/20 subset
   + staleness fail-safe + dynamic-answer subsystem, versus a version-confused field.
4. **Partner-delivered, not direct-to-consumer** — shipped through trusted CBOs/libraries (CASA, CUNY
   Citizenship Now, library systems) — a distribution + trust moat the app stores can't match.
5. **Accessibility / offline / print + privacy-by-construction** — for the device-poor, low-literacy,
   ESL learners the commercial apps and ad-laden sites under-serve.

---

## Adjacent opportunities

The reusable assets here (the provenance-gated rubric, the version/staleness/dynamic-answer
machinery, the human-verified translation pipeline, the exporters) make several **parallel and
perpendicular** spin-offs cheap — to be pursued only after citizenship is stable and each on its own
review/licensing footing:

- **know-your-rights** (parallel) — the same provenance-gated, multilingual, plain-language,
  **not-advice** pattern applied to immigrant/tenant/worker rights; high reuse of the rubric +
  labeling + translation-QA pipeline.
- **open-flashcards** (perpendicular) — extract the **item-bank + spaced-repetition engine** as a
  standalone open library + open deck format (Anki/CSV-compatible) usable by any subject.
- **vital-info-translations** (parallel) — reuse the **human-verified translation pipeline** for
  benefits/health/legal public information.
- **Reusable exam-prep engine** — parametrize the engine (schema, validator, dynamic answers,
  staleness, version-awareness, exporters) for **other countries' citizenship tests** (Life in the
  UK, Canada, Australia, the German Einbürgerungstest) and other public-standard exams — most are
  equally open-content-friendly and equally under-served.
- **MCP server (`civics-bank`)** — expose the vetted bank over MCP: version-aware question sampling,
  per-item provenance, and a current-officeholder lookup, so any agent or third-party app can query
  **verified, cited** questions; a second authoring-assist MCP could draft items against the rubric
  **for human review** (never auto-publish).

---

## Work breakdown

The itemized, schema-mapped backlog lives in **`TASKS.md`**: ~21 tasks across M0–M6 plus a future
backlog, each mapped to the Elyos Task JSON schema, with per-task acceptance criteria for the most
important items, milestone Definitions of Done, and a complete example Task JSON for the first M0
task (the pilot-exam + licensing decision). The first build items are the **item schema**, the
**validation/provenance CI gate**, and the **accuracy + non-partisan rubric**, reflecting their
status as hard product requirements; the **pilot-exam + licensing decision** and an early
**accuracy-reviewer secure** are sequenced so content investment is gated on a clean license and a
real reviewer.

---

## Governance, roles & stakeholders

- **Maintainer (Owner): TBD.** Owns the schema, agent-neutral core, validation/CI gates, and merge
  quality.
- **Reviewers / rotation:** at least one engineering reviewer plus a designated **content reviewer**
  who checks citation coverage and non-partisanship independently of item authors.
- **Accuracy reviewer (MEDIUM-tier sign-off): TO BE SECURED** — a qualified civics/government
  educator or experienced naturalization-prep instructor (and a relevant subject educator for HSE).
  Signs off all shipped items before release; tracked in a **version-scoped reviewers ledger** with
  credentials + consent. **Independence/COI:** a reviewer discloses material conflicts and recuses
  from content where conflicted; sign-off is **version-scoped** (does not carry forward to edits).
  **Name-use limits:** a reviewer's name/credentials may be published only for versions they
  approved, with consent, and may not imply endorsement of the whole product. **Disagreement
  fallback:** the reviewer holds a **veto on whether content is accurate enough to ship**; a
  maintainer cannot override a "do not ship" on substance — it escalates to a second reviewer / Elyos
  governance.
- **IP/legal reviewer (HSE gate): TO BE SECURED** — confirms trademark posture and source-reuse for
  the HSE lane before it begins.
- **Accessibility reviewer:** verifies WCAG 2.2 AA (may be the maintainer + automated tooling +
  community).
- **Steward (last-mile owner): TO BE SECURED** — owns the partner relationship and the
  adoption/hand-off that constitutes shipping.
- **Partner / requestor: TO BE SECURED** — the adult-education program, library system, literacy
  council, community college, or immigrant-/refugee-serving organization adopting the bank.
- **Community / board:** licensing edge-cases (esp. HSE trademark/source) and the dynamic-answer
  policy go through Elyos governance.

---

## Dependencies & integrations

- **External services:** static hosting/CDN for the PWA; Anthropic Claude API (assistive item
  drafting only, behind the neutral LLM client; never the final authority on a correct answer). No
  database or auth service is required for the core (no accounts).
- **Datasets / sources:** USCIS naturalization civics materials — **2008** (100 Q) and **2025** (128
  Q) questions/answers, the **65/20** reduced subset, and reading/writing vocabulary — public domain,
  provenance recorded (2020 archived); the USCIS *Check for Test Updates* page (official-update
  watch); for HSE, **only** public-domain / openly-licensed skill standards (e.g., CCR Standards for
  Adult Education) — pending IP/legal clearance.
- **Upstream/reference:** OER reuse channels (library consortia, adult-literacy commons) as potential
  pivot homes; spaced-repetition ecosystem (Anki-compatible export).
- **Elyos pieces:** `packages/schema` (Task JSON), `CLAUDE.md` work rules + refusal guardrails,
  `docs/good-deed-definition.md` (risk tiers), Elyos governance for license/edge-case decisions.
- **Human/decision dependencies (critical path):** the **pilot-exam + licensing decision (M0, gates
  content)**; a secured **accuracy reviewer** (blocks M1 ship); a cleared **IP/legal review** (blocks
  M3); a secured **partner + steward** (blocks M5).

---

## Risks & mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
|---|---|---|---|---|
| A practice item has a wrong "correct" answer → learner studies wrong thing, fails a life-changing exam | Medium | Critical | "No source, no item" CI gate; mandatory accuracy-reviewer sign-off before ship; independent ≥ 10% spot-check per release blocks on any error; item-quality eval | Accuracy reviewer / Maintainer |
| GED®/HiSET® trademark or proprietary-content infringement | Medium | Critical | Original items only; no proprietary content; nominative trademark use + non-affiliation disclaimer; HSE lane gated behind an explicit IP/legal review before any content | IP/legal reviewer |
| Dynamic answers (current officeholders / state-dependent) served as stale static "correct" answers | High | High | First-class dynamic-answer subsystem (never static); "verify current answer" affordance + official-source pointer; short re-verification cadence + on-change refresh; staleness fail-safe | Maintainer / Content reviewer |
| Civic content drifts into partisan/opinion framing | Medium | High | Non-partisan + sensitivity rubric; reviewer sign-off; items state only what official sources state; review flags = block | Content reviewer |
| Misread as official / as legal-immigration advice | Medium | High | Persistent "not official / not advice / verify with USCIS" labeling on every surface and export; route to official sources | Maintainer |
| No accuracy reviewer secured → M1 content blocked | Medium | High | Recruit via adult-ed programs, civics educators, naturalization clinics; do not ship content without sign-off (hard gate) | Maintainer / Steward |
| No delivery partner secured → cannot reach Definition of Shipped | High | High | Honest `TO BE SECURED`/`verifiedNeed:false`; dated partner-acquisition plan + build-vs-pivot rule (donate bank to an OER home or mothball, not ship to no one) | Steward / Maintainer |
| Official question set / answers change (USCIS revision) | Medium | High | Track both **live** versions (2008 + 2025) + 65/20 subset (2020 archived); **`testVersion`-scoped** content; **official-update watch in CI** flags changes; staleness fail-safe; review cadence + on-change re-verification + re-sign-off | Content reviewer |
| Content goes stale on its own currency axis (the v0.1 → 2025 miss) / learner studies the wrong version | High | High | `testVersion` field + per-version format/threshold parametrization; official-update watch turns a version change into a detected event; staleness fail-safe withholds stale items; reviewer audit of version tags | Maintainer / Content reviewer |
| "Which test do I take?" drifts from neutral info into immigration advice | Medium | High | Version selector is **USCIS-sourced information + link, never a determination**; 65/20 / exceptions routed to USCIS; reviewer-vetted non-causal "the test changed" explainer; HIGH-escalation rule on advice-drift | Content reviewer / Maintainer |
| 2025 redesign's political charge bleeds into copy (perceived partisanship) | Medium | High | Strictly factual, non-causal, USCIS-sourced framing of the version change as an explicit rubric item; non-partisan reviewer sign-off; no political-causal narrative | Content reviewer |
| Inaccessible to target learners (low literacy, screen-reader, no device) | Medium | High | Plain-language target; WCAG 2.2 AA; offline PWA; printable PDF export for device-poor learners | Maintainer / a11y reviewer |
| LLM-drafted item hallucinates a fact or distractor | Medium | High | LLM is assistive only; human accuracy review is mandatory before publish; citation required; eval bias/quality scan | Maintainer / Accuracy reviewer |

---

## Security & privacy

**Threat surface.** Inaccurate/misleading study content (primary harm vector); trademark/IP
infringement (HSE); misrepresentation as an official test or as legal advice; tampering with the
content bank or exports; minimal-but-nonzero supply-chain/static-hosting risk. Because the core has
**no accounts, no server, and no learner PII**, classic data-breach surface is intentionally tiny.

**Controls.**
- **Provenance + accuracy as the top control:** "no source, no item," mandatory review, independent
  spot-check, staleness fail-safe — content correctness is treated as the safety-critical property.
- **No-PII-by-construction:** core product requires no account and collects no learner data; app
  progress is local-device only; any outcome survey is anonymous, opt-in, partner-mediated, and
  aggregate (no immigration status, no contact info, no individual record).
- **Integrity:** the bank is version-controlled and reviewed; exports carry license + non-official/
  non-advice labels; published artifacts are checksummed.
- **No secrets/PII in logs, receipts, or committed files** (Elyos rule); any LLM-drafting API key is
  kept out of the repo.
- **Dependency + secret scanning in CI; minimal dependencies** for the static app.

**Abuse/misuse prevention.** The refused set — proprietary-content reproduction, official-affiliation
claims, partisan/opinion injection, individualized legal/immigration advice, learner-data harvesting
— is enforced at review/CI and through persistent labeling, not merely documented. The tool never
presents itself as authoritative on a pass/fail outcome.

---

## Sustainability & maintenance

After delivery, a named **maintenance rotation** owns the schema, validator, and app; the **steward**
owns the partner relationship and outcome tracking. Content carries a **review cadence enforced at
runtime, not just on a calendar**: each item's `lastVerified`/`validUntil` drives the staleness
fail-safe, with **dynamic/officeholder items on a short cadence and refreshed on known changes**
(elections, official-question-set revisions) and static civics facts on a longer cadence — stale
items are auto-flagged/withheld until re-verified and re-signed-off. Outcomes are tracked via
partner-mediated, anonymous, aggregate measures (learners reached, readiness improvement, voluntary
pass reports) — **not** engagement metrics. Expansion (more languages, HSE subjects, additional
exams) follows a documented, reviewer-gated process and only after citizenship is stable. The
item-quality eval and validator are maintained as living checks and expanded as new failure modes
appear.

---

## Open questions

- **HSE framing & trademark:** exactly how to scope the HSE lane (align to CCR Standards generically?
  brand-neutral "high-school-equivalency practice"? cover HiSET/TASC too?) — pending the M3 IP/legal
  review. The **decision rule is fixed** (no proprietary content, nominative use only, non-affiliation
  disclaimer, gated on legal clearance); the specific framing is open.
- **Dynamic-answer maintenance model:** maintain the officeholder lookup ourselves vs. always defer
  to an official live source? Proposal: store the *method + pointer*, keep a short-cadence lookup,
  never present a stale static answer — confirm with the accuracy reviewer.
- **Which languages first** for multilingual study scaffolding (Spanish almost certainly first; then
  per partner demand) — and the policy on keeping **test items** in the official language while
  translating **rationale/glossary**.
- **2008 vs 2025 civics version (resolved direction; confirm specifics):** build **2008 + 2025**
  (plus the **65/20** subset) and treat **2020 as archived** — confirmed as the working model. Open:
  whether the version selector defaults to one with the other available, and how to present
  filing-date guidance as **neutral information** (USCIS-sourced + link) without crossing into
  immigration advice (governance + reviewer call).
- **Oral/interview mode scope:** how far the TTS/audio interview-practice mode should go while keeping
  the firm **"no official-score / no AI-scoring claim"** boundary.
- **Audio/TTS:** quality, licensing, and offline packaging of read-aloud across many languages.
- **Official-update watch:** whether to auto-monitor the USCIS *Check for Test Updates* feed, and the
  exact re-verification cadence per item type.
- **Engine spin-off:** which country/exam (Life in the UK, Canada, Australia, German
  Einbürgerungstest) is the first reusable-engine spin-off, and that content's licensing/provenance.
- **Pass-outcome collection ethics:** how to record pass outcomes without ever touching immigration
  status or PII — keep strictly anonymous/voluntary/aggregate; confirm with partner + governance.
- **Lane:** donated by default; is there a future funded lane (with a hard budget cap) for expert
  accuracy-review hours or professional translation, without compromising independence?
- **Pivot home:** which OER platform/consortium is the preferred recipient if the build-vs-pivot rule
  triggers?

---

## References

- Proposal: `governance/proposals/civics-exam-prep.md` (**TO BE CREATED**; this PLAN precedes a
  formal proposal)
- Portfolio entry: `planning/ROADMAP.md` (Track 3 — Literacy & core education: `civics-exam-prep`)
- Elyos work rules & refusal guardrails: `CLAUDE.md`
- Good-deed definition & risk tiers: `docs/good-deed-definition.md`
- Task JSON schema: `packages/schema/src/schemas.ts`
- House-style sibling plans: `planning/projects/public-official-guide/{PLAN,TASKS}.md`,
  `planning/projects/oer-math/*` (educational-content sibling)
- Competitive + improvement analysis (source of truth for v0.2): `COMPETITIVE-ANALYSIS.md`
- Citizenship source (public domain): USCIS naturalization civics test materials — **2008** (100 Q,
  10 asked, 6 to pass) + **2025** (128 Q, 20 asked, 12 to pass) questions/answers, the **65/20**
  reduced subset, + reading/writing vocabulary; U.S. Government works per 17 U.S.C. § 105 (2020
  version archived)
  - USCIS 2025 Civics Test: https://www.uscis.gov/citizenship-resource-center/naturalization-test-and-study-resources/2025-civics-test
  - USCIS 128 Questions & Answers (2025): https://www.uscis.gov/sites/default/files/document/questions-and-answers/2025-Civics-Test-128-Questions-and-Answers.pdf
  - USCIS Check for Test Updates: https://www.uscis.gov/citizenship/find-study-materials-and-resources/check-for-test-updates
  - USCIS Multilingual Resources: https://www.uscis.gov/citizenship/find-study-materials-and-resources/citizenship-multilingual-resources
- Landscape references: USAHello (free, 17-language Q&A); Citizenry (closed app, 2008+2025);
  Quizlet/Anki (unsourced, version-confused); iCivics / Khan Academy (general civics, adjacent);
  CASA / CUNY Citizenship Now! / libraries (delivery partners) — full URLs in `COMPETITIVE-ANALYSIS.md`
- HSE standards (public domain): College & Career Readiness Standards for Adult Education (U.S. Dept.
  of Education) — *pending IP/legal review*
- Trademark caution: "GED®" is a registered trademark of GED Testing Service LLC (ACE + Pearson);
  HiSET® (ETS); TASC — proprietary; **not reproduced, not affiliated**

---

## Appendix A — Improvements applied

Twenty-five specific improvements made to this draft, each **applied** in the sections above (not
merely proposed):

1. **Trademark split made structural.** Reframed "GED" as the trademarked, proprietary product it is
   and moved the whole HSE lane behind an explicit IP/legal gate (M3, `hse-legal-013`) — applied in
   Exec summary, §5, §7, §9, Risks.
2. **Citizenship-first sequencing** justified by the clean public-domain (17 U.S.C. § 105) USCIS
   footing, so the project ships value before touching encumbered sources — applied in Exec summary,
   §9.
3. **Dynamic-answer subsystem promoted to a first-class component** (officeholder/state items never
   served static) with a dedicated task and metric — applied in §6.3, §4, §7, Risks, `dynamic-007`.
4. **"No source, no item" turned into a CI gate**, not a guideline — applied in §6.2, §8, §4
   (citation-coverage metric).
5. **Version-scoped accuracy sign-off** added (edits require re-sign-off; dovetails with staleness
   dates) — applied in §8, §11.
6. **Independent ≥ 10% accuracy spot-check per release**, with any found error blocking release —
   applied in §4, §8, Risks.
7. **Staleness fail-safe** (`lastVerified`/`validUntil` → auto-flag/withhold) carried over from the
   house style and tuned to short cadence for dynamic items — applied in §7, §15, M6.
8. **Non-partisan + sensitivity rubric** elevated to a required review gate with a zero-flag metric —
   applied in §7, §8, §4, `rubric-003`.
9. **Privacy-by-construction hardened:** no accounts, no PII, local-device-only progress, anonymous/
   aggregate outcome surveys — applied in §7, §14.
10. **Live civics versions** explicitly tracked, learner faces version by filing date — **corrected
    in v0.2 to 2008 + 2025 (+ 65/20 subset; 2020 archived)** with `testVersion` + per-version
    format/threshold — applied in §7, Open questions, Risks (see Changelog v0.2).
11. **Plain-language readability target** added as a CI check + metric (grade ≈ 6–8) for a low-
    literacy, ESL audience — applied in §4, §6.2, §8.
12. **Accessibility (WCAG 2.2 AA) + offline PWA + printable PDF** for device-poor learners made
    explicit deliverables and metrics — applied in §4, §5, §6.4–5, M2/M4.
13. **Multilingual scaffolding policy clarified:** translate UI/rationale/glossary, keep **test
    items in the official test language** — applied in §5, §6, Open questions, `i18n-012`.
14. **Dated partner-acquisition plan + build-vs-pivot decision rule** (donate to OER home or mothball
    rather than ship to no one) — applied in Exec summary, §2, Risks.
15. **Outcome metrics made beneficiary-centric** (readiness improvement, pass outcomes) with vanity
    metrics explicitly excluded — applied in §4.
16. **Pass-outcome collection ethics** constrained (anonymous, voluntary, aggregate, never touching
    immigration status/PII) — applied in §4, §14, Open questions.
17. **Risk-tier rationale stated** (MEDIUM, not HIGH) with an **escalation rule** to HIGH if content
    drifts into individualized legal/immigration advice — applied in §8.
18. **LLM-is-assistive-only** rule (human review is final authority on correctness) — applied in §6,
    §14, Risks.
19. **"Not official / not advice / verify with USCIS" labeling** mandated persistently on every
    surface and export — applied in §6.4, §7, §8.
20. **Exporters as a first-class deliverable** (PDF, spaced-repetition deck, open JSON) for reuse and
    device-poor learners — applied in §5, §6.5, `export-011`.
21. **Item-quality eval** (single-correct, distractor plausibility, bias scan) added with a defect
    metric — applied in §6.6, §4, `eval-016`.
22. **Reviewer veto + disagreement fallback** (maintainer cannot override "do not ship" on accuracy)
    — applied in §11.
23. **Content-as-version-controlled-files** decision (every change diffable/attributable/reviewable)
    — applied in §6.1, §6.
24. **MIT (code) / CC-BY-4.0 (content)** licensing fixed up front with attribution preserved on
    export — applied in §6, §7, TASKS mapping.
25. **Pivot-home open question + reference** named (library consortium / adult-literacy commons) so
    the build-vs-pivot rule is actionable, not abstract — applied in §12, Open questions, §16.

---

## Review sign-off

**Reviewer:** senior staff engineer + TPM (drafting author self-review pass).
**Date:** 2026-06-28. **Scope:** completeness against PLAN_SPEC's 17 sections, correctness against
`CLAUDE.md`, `docs/good-deed-definition.md`, and the Task schema; internal consistency between PLAN
and TASKS.

**Completeness check.** All 17 required H2 sections present and in order (Executive summary →
References), plus Appendix A and this sign-off. Each milestone (M0–M6) has a goal + measurable exit
criteria. Success metrics carry baseline + target + measurement. Risks table has the required five
columns.

**Correctness check (against Elyos rules).**
- *Good-deed criteria:* tangible public benefit (free exam prep for under-served learners) ✓; freely
  available (MIT/CC-BY, open dataset) ✓; not primarily for-profit (no ads, no data sale; explicitly
  non-affiliated with commercial test brands) ✓; no harm/discrimination/misinformation (accuracy +
  non-partisan + sensitivity gates) ✓; specific enough for AI sessions with required review ✓.
- *Risk tier:* MEDIUM correctly assigned with reviewer sign-off required and a HIGH-escalation rule
  for advice-drift ✓.
- *Refusal guardrails:* license/provenance rigor (PD/CC only; HSE gated) ✓; privacy/PII (no accounts,
  no learner PII) ✓; non-partisan civic stance ✓; no individualized legal/immigration advice ✓.
- *CLAUDE.md engineering:* TS/ESM/pnpm, MIT code / CC-BY content, agent-neutral core, no secrets in
  logs ✓.

**Issues found and fixed during review.**
- *Fix 1:* Initial draft implied reusing GED practice questions; corrected to **original items
  aligned to public standards** with the HSE lane gated behind IP/legal review (§7, M3).
- *Fix 2:* Early metrics included pass-rate without ethics constraints; added the **anonymous/
  voluntary/aggregate, no-immigration-status** rule (§4, §14).
- *Fix 3:* Dynamic-answer items were under-specified; promoted to a first-class subsystem + task +
  metric + staleness cadence (§6.3, §4, `dynamic-007`).
- *Fix 4:* Clarified that multilingual support translates rationale/glossary but **keeps test items
  in the official test language** to avoid teaching the wrong answer surface (§5, §6).

**Outstanding (human decisions required):** secure an accuracy reviewer (blocks M1 ship); secure an
IP/legal reviewer (blocks M3 / HSE); secure a delivery partner + steward (blocks M5 / Definition of
Shipped); Elyos governance to confirm the HSE framing and the dynamic-answer maintenance model.

**Verdict:** Plan is internally consistent and ready to drive the TASKS backlog. No item ships
without citation + accuracy sign-off; no HSE content begins without IP clearance; no "shipped"
without a real partner and recorded learner outcomes.

---

## Changelog — v0.2 (analysis merged)

Merged the findings of `COMPETITIVE-ANALYSIS.md` (2026-06-29) into the plan. Surgical/additive; no
guardrails weakened; no facts/questions invented.

**Correctness & currency fixes applied**
- **CRITICAL — test-version model de-staled:** replaced the obsolete **2008 + 2020** model with the
  live **2008 + 2025** split (2020 is historical only, administered Dec 1 2020 – Apr 30 2021 then
  reverted; the **new 2025 USCIS test took effect for N-400s filed on/after Oct 20 2025**). Encoded
  the **structural differences** — **2008 = 100 Q / 10 asked / 6 to pass**; **2025 = 128 Q / 20 asked
  / 12 to pass** — plus the **65/20 senior special-consideration** reduced bank. Added a `testVersion`
  (`2008 | 2025 | senior-65-20`) field and **parametrized question count + pass threshold per
  version** across schema, Exec summary, Goals, Scope, §6, §7, Roadmap, Dependencies, Risks, Open
  questions, References, and Appendix A.
- **Multilingual claim corrected (Finding 2):** dropped the inaccurate "official materials are
  English-only" framing; USCIS publishes multilingual resources and USAHello offers the Q&A in 17
  languages — the real gap is an **open, structured, original-rationale, version-aware, spaced-practice
  bank**, so the multilingual value is re-aimed at **plain-language rationales + glossary**.
- **Non-partisan meta-layer (Finding 3):** added a **reviewer-vetted, strictly factual, non-causal**
  framing requirement for the politically charged 2025 redesign / "the test changed" explainer (§7,
  §8, rubric, Risks).
- **Not-advice boundary at "which test do I take?" (Finding 4):** version selection is presented as
  **neutral USCIS-sourced information + link, never a determination**; 65/20 and exceptions routed to
  USCIS (Exec summary, Non-goals, §6.4, §8, Risks).
- **Assessment format (Finding 5):** mock-test mode parametrized to the selected version's format;
  added an **oral/interview practice mode** (real test is oral) with **no AI-scoring claim**.

**Strategy integrated**
- New **"Competitive landscape & differentiation"** section (USAHello, Citizenry, Citizen Now, SEO
  sites, Quizlet/Anki, iCivics/Khan as adjacent, USCIS as source-of-truth-to-cite, CASA/CUNY
  Citizenship Now/libraries as delivery partners); differentiator = **open, CC-BY, provenance-bearing,
  version-aware item bank as reusable infrastructure — distribution by reuse**.
- **Claude API leverage** folded into §6 (draft items from official answers, plain-language rewrite to
  grade 6–8, translation drafting, LLM-judge eval) with the hard limits preserved: **Claude never
  certifies correctness, never decides which version applies, never gives immigration advice**.
- **Optimizations folded into the Roadmap:** `testVersion` + version explainer (M0), 2008+2025+65/20
  sources + reading/writing deliverable (M1), oral mode + version selector + audio/TTS (M2),
  **official-update watch in CI** + partner/org toolkit (M4), version-change re-verification (M6).
- New **"Adjacent opportunities"** section (know-your-rights, open-flashcards,
  vital-info-translations, reusable exam-prep engine for other countries' tests, `civics-bank` MCP
  server).
- **Open questions merged** (oral-mode scope, version-selector presentation, audio/TTS, official-update
  watch cadence, first engine spin-off; version question resolved toward 2008 + 2025 + 65/20).

**Preserved unchanged:** all civic guardrails (non-partisan; official-source citation; not
legal/immigration advice; multilingual review), provenance-as-a-gate, HSE IP/legal gating, the
build-vs-pivot rule, privacy-by-construction, risk-tier (MEDIUM) and the HIGH-escalation rule, and the
17-section structure. `COMPETITIVE-ANALYSIS.md` left unchanged.
