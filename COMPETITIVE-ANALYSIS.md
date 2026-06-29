# Competitive + Improvement Analysis — `civics-exam-prep`

> Reviewer pass: 2026-06-29. Scope: PLAN.md v0.1.0 (+ TASKS.md skim). Web-grounded; URLs cited inline.
> Lane: donated. Risk tier (plan): MEDIUM. Civic guardrails: strictly non-partisan; accurate to the
> OFFICIAL current test; official-source citations; multilingual; not legal/immigration advice.

---

## 1. Correctness & completeness review of PLAN.md

The plan is unusually rigorous: provenance-as-a-CI-gate ("no source, no item"), version-scoped
accuracy sign-off, an independent ≥10% spot-check, a first-class dynamic-answer subsystem, a
staleness fail-safe, a non-partisan + sensitivity rubric, privacy-by-construction, and a clean
public-domain/trademark licensing split (citizenship first; GED® gated behind IP review). The
completeness against the 17-section spec is good and internally consistent. The findings below are
where it is **factually wrong, stale, or under-specified against the official current test**.

**FINDING 1 — CRITICAL: the test-version model is already stale (2008 + 2020 is wrong; it is now 2008 + 2025).**
The plan's central currency claim — "track both the **2008** and **2020** versions; the version a
learner faces depends on filing date" — is **out of date as of this plan's own date**. The 2020
redesign was administered only Dec 1 2020 – Apr 30 2021, then reverted to 2008 under the Biden
administration; a **new 2025 civics test took effect for N-400s filed on/after October 20, 2025**.
The live split is now **2008** (filed before Oct 20 2025) vs **2025** (filed on/after), and the 2020
test is **historical only**.
([USCIS 2025 Civics Test](https://www.uscis.gov/citizenship-resource-center/naturalization-test-and-study-resources/2025-civics-test),
[CLINIC](https://www.cliniclegal.org/resources/citizenship-and-naturalization/preparing-your-clients-2025-naturalization-civics-test),
[128 Q&A PDF](https://www.uscis.gov/sites/default/files/document/questions-and-answers/2025-Civics-Test-128-Questions-and-Answers.pdf)).
Structural differences the plan does not encode: 2008 = **100 questions, 10 asked, 6 to pass**; 2025
= **128 questions, 20 asked, 12 to pass**; plus a **65/20 special-consideration** reduced bank for
applicants 65+ with 20+ years LPR. Task `sources-005` literally instructs vetting "**2008 + 2020**"
and the schema/metrics assume one static pass threshold. **This is the single most important fix and
it ironically validates the plan's own staleness thesis: the document went stale on the exact axis it
warns about.** Remediation: replace 2020 with 2025 everywhere; add a `testVersion`
(`2008 | 2025 | senior-65-20`) field; parametrize question count and pass threshold per version;
treat 2020 as archived.

**FINDING 2 — "official materials are English-only" is inaccurate; it weakens (not kills) the multilingual gap.**
The plan repeatedly frames official study materials as "English-only" and "PDF-bound." USCIS in fact
publishes [multilingual citizenship resources](https://www.uscis.gov/citizenship/find-study-materials-and-resources/citizenship-multilingual-resources),
and USAHello already offers the Q&A in **17 languages with audio**
([USAHello](https://usahello.org/citizenship/prepare/citizenship-test-questions/)). The real gap is
not "no translations exist" but "no **open, structured, original-rationale, spaced-practice** bank
exists" — the plan should re-aim its multilingual claim accordingly (translate plain-language
**rationales + glossary**, not just Q&A, which is the plan's stated policy and is correct).

**FINDING 3 — non-partisan neutrality has an un-addressed meta-layer.** The rubric correctly bars
opinion/advocacy inside items. But the **2025 redesign itself is politically charged** (implemented
under the Trump administration, longer/harder, widely covered as such). Any learner-facing copy that
explains "the test changed" or "which version you take" risks partisan reading. The plan needs a
reviewer-vetted, strictly factual framing for the version change (what/when/who-it-applies-to, sourced
to USCIS, no causal-political narrative). Add this to the rubric explicitly.

**FINDING 4 — the not-advice boundary is thinnest exactly at "which test do I take?"** The plan's
general "not legal/immigration advice" labeling is strong, but the version-by-filing-date feature and
the 65/20 carve-out are **eligibility-adjacent**: telling a specific user which test applies edges
toward immigration advice. Resolution: present version selection as **neutral information + a link to
USCIS** ("if your N-400 was filed before/after Oct 20 2025…"), never as a determination, and route
edge cases (65/20, disability exceptions) to official sources. The HIGH-escalation rule covers drift,
but this specific surface should be called out.

**FINDING 5 — assessment/mock-test scoring is under-parametrized.** Mock-test mode must reflect the
correct format per version (6/10 vs 12/20; oral, not multiple-choice). The real test is an **oral
interview**; the plan's MC + flashcard modes are necessary but not sufficient — see Optimization 5.

**Solid as-is:** dynamic-answer subsystem (officeholder questions persist in 2025), provenance gate,
original-items/copyright posture, accessibility + offline + print, privacy stance, HSE gating, and
the build-vs-pivot rule. These are genuinely ahead of the field on rigor.

---

## 2. Competitive landscape

**Official — USCIS Citizenship Resource Center** ([uscis.gov/citizenship](https://www.uscis.gov/citizenship)).
Authoritative, free, public-domain, now with multilingual resources and the 2025 materials.
*Weakness:* PDF/list-bound, not interactive, no spaced repetition, no progress, not designed for
low-literacy active recall. This is the **source of truth**, not a study experience — and the thing
Elyos must cite, not compete with.

**USAHello** ([usahello.org/citizenship](https://usahello.org/citizenship/prepare/citizenship-test-questions/),
[classroom](https://classroom.usahello.org/citizenship/)). The closest mission-aligned competitor:
nonprofit, free, **17 languages**, audio, learner-friendly. *Weakness:* largely reproduces official
Q&A rather than an **original, provenance-bearing, openly-licensed, machine-readable item bank**;
limited spaced-repetition/assessment engine; not an open dataset others can reuse.

**Citizenry (app)** ([App Store](https://apps.apple.com/us/app/citizenry-uscis-civics-test/id6451455299)).
Most feature-rich: **ad-free**, supports **both 2008 and 2025**, unlimited AI **mock interviews**,
**Spanish-speaking virtual agent**, flashcards/quizzes/audio. *Weakness:* closed-source, app-store
walled, not open data, not accessibility-audited/public, single-vendor trust.

**Citizen Now** ([citizennow.com](https://citizennow.com/)) and **US Citizenship Test 2026 Plus**
([App Store](https://apps.apple.com/us/app/us-citizenship-test-2026-plus/id1103037173)). AI civics
simulator with spoken-answer feedback; 2008/2025 dynamic; per-state flashcards. *Weakness:* ads
(reduced) or paid tiers, closed, no provenance, AI-scoring claims unverified.

**SEO practice sites** — uscitizenshiptest.app, [citizenshiptests.org](https://citizenshiptests.org/us-citizenship-test/),
[uniontestprep](https://uniontestprep.com/u-s-citizenship-test/practice-test),
[test-guide](https://www.test-guide.com/free-citizenship-practice-tests.html),
civicsquestions.com. Free, broad reach. *Weakness:* ad-laden, **unsourced**, inconsistent on
version, generally not accessibility-audited — the exact "ad-laden, unsourced practice test" failure
the plan targets.

**Quizlet / Anki community decks**
([Quizlet 128 Q&A](https://quizlet.com/563497165/128-civics-questions-and-answers-test-flash-cards/),
[Quizlet 100 2024-2025](https://quizlet.com/932999959/100-citizenship-test-questions-2024-2025-flash-cards/)).
Free, spaced-repetition-native, huge install base. *Weakness:* **no provenance, error-prone,
version-confused** (decks mixing 100/128/"2024-2025"/state variants), no accuracy review — a learner
cannot tell which deck matches their test. This is Elyos's clearest opening.

**iCivics** ([icivics.org](https://www.icivics.org/teach)) and **Khan Academy U.S. Government & Civics**
([khanacademy.org](https://www.khanacademy.org/humanities/us-government-and-civics)). Free,
high-quality, standards-aligned **civic education** — but **K-12/general civics, not naturalization
prep**. Adjacent, not competitors; potential content-style references and spin-off allies.

**CBOs / libraries — CASA, CUNY Citizenship Now!, YMCA New Americans, NYPL/LA County libraries**
([We Are CASA](https://wearecasa.org/program/citizenship/),
[USCIS find-help](https://www.uscis.gov/citizenship/findcitizenshiphelp)). These run in-person
classes + application help. **They are not competitors — they are the delivery partners** the plan's
M5 needs; treat them as distribution, not rivalry.

---

## 3. Gaps we can fill

- **An open, CC-BY, machine-readable, provenance-bearing item bank.** Nobody offers this. USCIS is
  PDF; apps are walled; Quizlet/Anki are unsourced. A vetted open dataset is reusable by libraries,
  CBOs, *and* by the app/deck makers above.
- **Version-correct, staleness-guarded content.** The whole field is version-confused (Quizlet decks,
  SEO sites). A bank that is explicitly 2008-vs-2025 aware, with a fail-safe that withholds stale
  items, is a trust differentiator.
- **Multilingual study *scaffolding* with original plain-language rationales** (grade 6–8), not just
  translated Q&A — most rivals translate the answer, not the *explanation*.
- **Accessibility + offline + print.** WCAG 2.2 AA, offline PWA, and printable sheets for
  device-poor/low-literacy/ESL learners — unmet by ad-laden sites and unaudited apps.
- **No ads, no accounts, no data harvesting** — structurally cleaner than ad/data-monetized free
  sites and freemium apps.
- **A reusable engine for *other* citizenship tests** (Life in the UK, Canada, Australia, German
  Einbürgerungstest) and other public-standard exams — no open equivalent exists.

---

## 4. Differentiators to win

1. **Provenance-as-a-gate + independent accuracy review** — a public trust artifact ("every answer
   cited to USCIS; reviewer signed off; spot-checked") that no competitor offers.
2. **Open, reusable, version-aware dataset (CC-BY)** — distribution by *reuse*: libraries, CBOs,
   Quizlet/Anki authors, and even rival apps can ingest it; the bank becomes infrastructure.
3. **Correctness on the exact axis everyone else fails** — 2008/2025 version-awareness + staleness
   fail-safe + dynamic-answer subsystem.
4. **Partner-delivered, not direct-to-consumer** — shipped through trusted CBOs/libraries (CASA, CUNY
   Citizenship Now, library systems), a distribution + trust moat the app stores can't match.
5. **Accessibility/offline/print + privacy-by-construction** for the device-poor, low-literacy, ESL
   beneficiary the commercial apps under-serve.

---

## 5. Claude API leverage (and where Claude must NOT decide)

**High-value, human-gated uses:**
- **Draft original practice items** — generate stems, plausible distractors, and plain-language
  rationales *from* the official answers (never copying third-party question sets); every draft enters
  human accuracy review.
- **Plain-language rewriting** to the grade 6–8 target for low-literacy/ESL learners.
- **Translation drafting** of UI, rationales, and glossary across many languages (with human QA per
  language).
- **Spaced-repetition + difficulty design** — propose scheduling/calibration and item-difficulty
  tags.
- **LLM-judge / item-quality eval** — flag single-correct violations, weak/implausible distractors,
  readability misses, and possible bias/insensitivity → **flags for human, never auto-publishes**.
- **Distractor generation** and **readability scoring assist**.

**Where Claude must NOT have final say:**
- **Accuracy to the official test** — every "correct answer" must be verified against current USCIS
  material by a human reviewer; Claude can draft, not certify.
- **Which test version applies to a person** — version/eligibility is legal-adjacent; route to USCIS,
  never decide for the user.
- **Non-partisan judgment** — the reviewer rubric is the authority; Claude assists, the human signs.
- **Translation QA** — a qualified human verifies each language before publish.
- **No fabrication** — never invent questions, answers, citations, or sources; "no source, no item"
  is enforced in CI, not by the model.
- **No individualized legal/immigration advice** — out of scope; escalate, don't generate.

---

## 6. Ten concrete optimizations

1. **Fix the version model end-to-end:** replace 2008+2020 with **2008+2025** in PLAN, TASKS
   (`sources-005`), schema, and metrics; add a `testVersion` enum and parametrize question
   count/pass threshold (6/10 vs 12/20). *(Resolves Findings 1 & 5.)*
2. **Neutral version selector, not advice:** present "filed before/after Oct 20 2025 → version X" as
   sourced information with a USCIS link, never as a determination; route 65/20 and exceptions to
   official sources. *(Resolves Finding 4.)*
3. **Ship the 65/20 special-consideration subset** (the starred reduced bank) as a first-class
   filtered view — a population the apps mostly ignore.
4. **Cover the reading & writing components**, not just civics MC — the naturalization test includes
   an English reading/writing vocabulary test; the plan mentions vocab support but should make
   reading/writing practice a deliverable.
5. **Add an oral/interview practice mode** (TTS/audio prompts + self-check), since the real test is
   **oral** — Citizenry/Citizen Now lead here; close the gap *without* AI-scoring claims (label
   "practice only, not an official score").
6. **Reviewer-vetted "the test changed" explainer** — strictly factual, sourced, non-causal framing
   of the 2025 change, added to the rubric. *(Resolves Finding 3.)*
7. **Make the open dataset the headline deliverable** — stable schema + versioned releases so
   libraries, CBOs, Quizlet/Anki authors, and app devs can reuse it; distribution-by-reuse.
8. **Automated "official-update" watch in CI** — monitor the USCIS
   [Check for Test Updates](https://www.uscis.gov/citizenship/find-study-materials-and-resources/check-for-test-updates)
   page; flag content for re-verification when USCIS publishes a change (turns Finding 1 into a
   detected event next time).
9. **Audio/TTS for low-literacy + ESL, offline** — match USAHello's audio; essential for the target
   learner and for accessibility.
10. **Pre-package a partner/org toolkit** — printable class sets + facilitator guide aimed at CASA /
    CUNY Citizenship Now / library adult-ed, converting "competitors that are actually partners" into
    the M5 distribution channel.

---

## 7. Parallel & perpendicular spin-offs

- **know-your-rights** (parallel): the same provenance-gated, multilingual, plain-language,
  not-advice pattern applied to immigrant/tenant/worker rights — high reuse of the rubric + labeling +
  translation-QA pipeline.
- **open-flashcards** (perpendicular): extract the **item-bank + spaced-repetition engine** as a
  standalone open library + open deck format (Anki/CSV-compatible) usable by any subject.
- **vital-info-translations** (parallel): reuse the **human-verified translation pipeline** for
  benefits/health/legal public information.
- **media-literacy-curriculum** (perpendicular): reuse the **non-partisan civic-content rubric** and
  item engine for media/information literacy.
- **Reusable exam-prep engine**: parametrize the engine (schema, validator, dynamic-answers,
  staleness, exporters) for **other countries' citizenship tests** (Life in the UK, Canada,
  Australia, German Einbürgerungstest) and other public-standard exams — most are equally
  open-content-friendly and equally under-served.
- **MCP server** (`civics-bank`): expose the vetted bank over MCP — version-aware question sampling,
  per-item provenance, and a current-officeholder lookup — so any agent or third-party app can query
  *verified, cited* questions. A second authoring-assist MCP could draft items against the rubric for
  human review.

---

## 8. Open questions

1. Confirm the pivot: treat **2020 as archived** and build **2008 + 2025** (and 65/20)? (Strongly
   recommended; current plan text says 2008 + 2020.)
2. Scope of an **oral/interview mode** vs. the firm "no official-score" boundary — how far to go.
3. How to present **version selection** without crossing into immigration advice — governance +
   reviewer call (Finding 4).
4. **Audio/TTS** quality, licensing, and offline packaging across many languages.
5. Which **country/exam** is the first engine spin-off, and that content's licensing/provenance.
6. Whether to **auto-monitor the USCIS update feed** and the exact re-verification cadence per item
   type.
7. **Pivot home** for the build-vs-pivot rule (library consortium vs adult-literacy commons) — still
   unnamed in the plan.

---

### Sources
- USCIS 2025 Civics Test — https://www.uscis.gov/citizenship-resource-center/naturalization-test-and-study-resources/2025-civics-test
- USCIS 128 Questions & Answers (2025) — https://www.uscis.gov/sites/default/files/document/questions-and-answers/2025-Civics-Test-128-Questions-and-Answers.pdf
- USCIS Study for the Test — https://www.uscis.gov/citizenship/find-study-materials-and-resources/study-for-the-test
- USCIS Check for Test Updates — https://www.uscis.gov/citizenship/find-study-materials-and-resources/check-for-test-updates
- USCIS Multilingual Resources — https://www.uscis.gov/citizenship/find-study-materials-and-resources/citizenship-multilingual-resources
- USCIS Find Citizenship Help — https://www.uscis.gov/citizenship/findcitizenshiphelp
- CLINIC — Preparing Clients for the 2025 Test — https://www.cliniclegal.org/resources/citizenship-and-naturalization/preparing-your-clients-2025-naturalization-civics-test
- USAHello citizenship Q&A (17 languages) — https://usahello.org/citizenship/prepare/citizenship-test-questions/
- Citizenry app — https://apps.apple.com/us/app/citizenry-uscis-civics-test/id6451455299
- Citizen Now — https://citizennow.com/
- US Citizenship Test 2026 Plus — https://apps.apple.com/us/app/us-citizenship-test-2026-plus/id1103037173
- Quizlet 128 Q&A — https://quizlet.com/563497165/128-civics-questions-and-answers-test-flash-cards/
- Quizlet 100 (2024-2025) — https://quizlet.com/932999959/100-citizenship-test-questions-2024-2025-flash-cards/
- iCivics — https://www.icivics.org/teach
- Khan Academy U.S. Government & Civics — https://www.khanacademy.org/humanities/us-government-and-civics
- We Are CASA citizenship — https://wearecasa.org/program/citizenship/
- citizenshiptests.org — https://citizenshiptests.org/us-citizenship-test/
- UnionTestPrep — https://uniontestprep.com/u-s-citizenship-test/practice-test
- Test-Guide — https://www.test-guide.com/free-citizenship-practice-tests.html
