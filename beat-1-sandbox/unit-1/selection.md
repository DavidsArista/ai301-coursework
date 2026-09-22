# Unit 1 — Issue Selection

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71


**Verdict output**

The following is the complete, unedited live comparison output using the completed fit profile. The selected issue is #71.

## Evidence summary

**Scope check (all three):** All three issues live in `codepath/pathreview-ai301-fa26-s1`, the scoped repo — in scope. Path Review's house rule (other students' claim comments don't block a claim) applies where relevant.

**Repo-level facts (shared by all three):**
- Not archived; `pushed_at: 2026-09-16` (5-6 days before today, 2026-09-21/22) — active.
- 0 releases, but the push-within-90-days branch of the check suffices.
- Last 5 default-branch commits (2026-08-24 to 2026-09-16) all authored by `Aburke225` (Andrew Burke), `author_association: COLLABORATOR` — human, non-bot.
- `docs/CONTRIBUTING.md` and `.github/PULL_REQUEST_TEMPLATE.md` never mention AI/LLM tooling — no ban, no disclosure checkbox; silence passes per rubric.

### Issue #71 — Heading hierarchy test fixture is indented
- Human maintenance: PASS — opened by COLLABORATOR `Aburke225` on 2026-09-10 (within 90 days), plus the commit evidence above.
- Active project: PASS — repo-level evidence above.
- Bounded contribution: PASS — single outcome: de-indent the fixture in `test_readme_parser.py` and drop the `xfail` marker for manifest H-04. No competing designs, no umbrella.
- Available work: PASS — `assignees: []`, `comments: []`, `closedByPullRequestsReferences: []`.
- Compatible contribution policy: PASS — repo-level evidence above.
- Verification guidance (preferred): PASS — named test `test_extract_heading_hierarchy`, and success is observable as an XPASS(strict)→pass CI flip.

### Issue #73 — README and `.env.example` disagree on the LLM API key
- Human maintenance: PASS — same as above, opened by `Aburke225` (COLLABORATOR) 2026-09-16.
- Active project: PASS.
- Bounded contribution: PASS — one outcome: make `README.md` and `.env.example` agree on `OPENROUTER_API_KEY`. Pure docs/config sync, no design ambiguity.
- Available work: PASS — `assignees: []`, `comments: []`, no linked PR.
- Compatible contribution policy: PASS.
- Verification guidance (preferred): PASS — exact documentation/config correction named (`OPENROUTER_API_KEY` missing from `.env.example`).

### Issue #68 — Keyword search raises `ZeroDivisionError` on empty index
- Human maintenance: PASS.
- Active project: PASS.
- Bounded contribution: PASS — one outcome: guard `KeywordSearcher.index()` against an empty corpus and drop the H-01 `xfail` marker.
- Available work: PASS — `assignees: []` and no linked/open PR anywhere in the repo (checked open-PR search too). Student `yulijasso` (association `NONE`) posted a detailed claim + repro 2026-09-20, but by the Path Review house rule other students' claims don't block; claim anyway.
- Compatible contribution policy: PASS.
- Verification guidance (preferred): PASS — full repro traceback, named test `test_empty_index`, explicit expected-vs-actual behavior.

**Verdict rule applied:** every required check passes for all three → all three **accept**.

## Ranking (fit profile: prefer focused test-fixture/documentation corrections over multi-component or architectural changes; small change with a named test and an observable result; no assumed Python expertise)

1. **#71** — a pure test-fixture correction (de-indent a markdown block) with a named test whose pass/fail state is the observable result (XPASS-strict flip on CI), and it touches no production logic — lowest risk for someone without assumed Python depth, while still practicing the full issue→fix→PR loop.
2. **#73** — a documentation/config consistency fix, equally in the profile's preferred bucket and equally low-risk, but verification is a manual file-diff rather than a named automated test, so it ranks just behind #71.
3. **#68** — accepted, but it requires editing real application logic (`KeywordSearcher.index()`), carries the longest stated estimate (2-4h vs 1-2h), and is already being actively worked by a classmate with a concrete plan — still fair game under the house rule, but the least "focused fixture/doc" fit of the three.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71",
    "checks": [
      {"name": "Human maintenance", "grade": "pass", "evidence": "Issue opened by COLLABORATOR Aburke225 on 2026-09-10; same author has default-branch commits through 2026-09-16."},
      {"name": "Active project", "grade": "pass", "evidence": "Repo not archived; pushed_at 2026-09-16T21:48:27Z, within 90 days."},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Body: 'Remove the indentation' in the test fixture and drop the xfail marker for H-04 — one concrete outcome."},
      {"name": "Available work", "grade": "pass", "evidence": "assignees: [], comments: [], closedByPullRequestsReferences: []."},
      {"name": "Compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template are silent on AI/tooling use."},
      {"name": "Verification guidance", "grade": "pass", "evidence": "Named test test_extract_heading_hierarchy; fix is observable as XPASS(strict)->pass."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73",
    "checks": [
      {"name": "Human maintenance", "grade": "pass", "evidence": "Issue opened by COLLABORATOR Aburke225 on 2026-09-16; commit history same as above."},
      {"name": "Active project", "grade": "pass", "evidence": "Repo not archived; pushed_at 2026-09-16T21:48:27Z, within 90 days."},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Body: 'Make the two files agree' (README.md and .env.example) — one concrete doc/config outcome."},
      {"name": "Available work", "grade": "pass", "evidence": "assignees: [], comments: [], closedByPullRequestsReferences: []."},
      {"name": "Compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template are silent on AI/tooling use."},
      {"name": "Verification guidance", "grade": "pass", "evidence": "Exact documentation correction named: add OPENROUTER_API_KEY to .env.example to match README.md."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68",
    "checks": [
      {"name": "Human maintenance", "grade": "pass", "evidence": "Issue opened by COLLABORATOR Aburke225 on 2026-09-10; commit history same as above."},
      {"name": "Active project", "grade": "pass", "evidence": "Repo not archived; pushed_at 2026-09-16T21:48:27Z, within 90 days."},
      {"name": "Bounded contribution", "grade": "pass", "evidence": "Body: single fix — add empty-corpus guard in KeywordSearcher.index() and drop the H-01 xfail marker."},
      {"name": "Available work", "grade": "pass", "evidence": "assignees: []; no linked/open PR; student comment claiming the issue (association NONE, 2026-09-20) is exempted by Path Review's house rule."},
      {"name": "Compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template are silent on AI/tooling use."},
      {"name": "Verification guidance", "grade": "pass", "evidence": "Full repro traceback, named test test_empty_index, explicit expected-vs-actual behavior in the thread."}
    ],
    "verdict": "accept"
  }
]
```

## Eval iterations

**Run history**

1. Initial full run: "agreement: 17/20 scored items  (bar: 18/20: below the bar)". Mismatches: issue-04, issue-09, and issue-19. The first rubric treated related missing cases too much like an umbrella and treated old claims as indefinite blockers.
2. Revised the Bounded contribution rule to distinguish related cases within one feature from independent workstreams. Revised Available work to expire unsupported claims after 90 days while keeping current assignees and open PRs blocking regardless of age. Targeted rerun with `--only issue-04,issue-09,issue-07`: "agreement: 3/3 scored items". This was a partial check, not the submitted full run.
3. Final full run with the current rubric: "agreement: 19/20 scored items  (bar: 18/20: PASS)". The harness wrote `eval-run.txt`; it was not hand-edited.

**Issue analysis**

For `issue-09`, the initial rubric returned `reject`; the instructor gold label is `accept`. The revised rubric's final verdict is `accept`. The snapshot records "this issue: assignees: none; linked PRs: conda/conda#11627 (closed)". The claim "I'd like to take a swing at this as my first open-source contribution" is dated 2022-01-20, while the snapshot is captured 2026-08-05. The first rule treated that old claim as still blocking. The revised rule recognizes that an old claim without recent progress, a current assignment, or an open PR is not evidence of ongoing work. The requested `conda config --clear channels` behavior is a concrete outcome; one closed PR and issue age alone do not establish repeated implementation failure.

**Check rationale**

Exact current Available work row from `tools/issue-select/rubric.md`:

| Available work | Repo-facts assignees and linked PR states; entire comment thread for claims, assignments, PR references, and release of claims. In live mode also inspect the Development sidebar and referenced PR states. | Issue is open, has no current assignee, no open implementation PR, and no unresolved claim or progress update within the past 90 days. A later explicit withdrawal or maintainer reopening to contributors clears a claim. A claim older than 90 days with no newer progress, no assignee, and no open implementation PR is stale and does not block work; an open PR or current assignment blocks regardless of age. A PR reference in the thread must be considered even if absent from the sidebar. A closed unmerged PR is not an active claim; a merged fix requires explicit evidence of remaining work. Apply Path Review's exception for other students' claim comments in live mode only. | required |

This separates a recent claim from an abandoned attempt. The 90-day boundary is a conservative screening choice, not proof that a contributor has stopped working. An open PR or current assignee still blocks regardless of age, and references in comments count even when the Development sidebar omits them. In live Path Review grading, the supplied classroom rule exempts other students' claim comments.

**Trade-offs**

The revised rule changes `issue-09` from reject to accept, while the targeted rerun still rejects `issue-07`. The "90 days" threshold can miss someone who is still working privately but has not posted progress, has no assignment, and has no open PR. Conversely, it can reject a recent claim from someone who has already stopped. It is a repeatable evidence threshold, not a guarantee of availability. The full-run score above reports the observed outcome rather than assuming that every other verdict stayed the same.

## Selection rationale

**Selection rationale**

1. I chose issue #71 because I want a focused first contribution with a clear way to check the result while I learn the GitHub contribution workflow. I am using AI-assisted tools to help me understand the work, and a test-fixture correction gives me a concrete change to inspect and verify. The issue estimates 1–2 hours; I am treating that as a starting estimate rather than a promise, because environment setup and learning the test code may take additional time. The small stated scope makes it easier to plan than a change across several components.

2. The verdict correctly identified a specific correction: remove the Markdown fixture's indentation and remove the associated H-04 `xfail` marker. It also identified the named test, `test_extract_heading_hierarchy`, as a way to verify the result. I weighed the opportunity to practice reading and validating a test, rather than only changing documentation. The rubric cannot measure how quickly I will understand this code or get the environment running, so I still need to inspect the fixture and run the test myself in Unit 2. An accepted verdict is a reason to investigate, not proof that the fix has already been reproduced.

3. I expect writing a specific, evidence-based claim to require more preparation than simply asking to take the issue. In Unit 2, I will recheck its current status and describe what I understand about the fixture and how I plan to verify the change. The supplied Path Review rule permits shared student work, so another student's claim comment alone would not rule it out. I still need to check for changes such as a completed fix or an active PR under the current rules. I have not posted a claim as part of Unit 1.
