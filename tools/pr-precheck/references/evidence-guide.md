# Evidence guide: where evidence lives in a PR package

In eval mode the bundle's labeled sections are the whole world. In live mode read `plan.md` (including Deviations), `git diff main...HEAD` and the committed log from the fork, `test_evidence.md`, `pr_draft.md`, the issue thread, PR template, and `docs/CONTRIBUTING.md`. Do not silently replace missing draft content with private facts.

## Plan fidelity (harness category: silent-drift)

Find the intended files, behavior, exclusions, test plan, and Deviations in Plan context; find what changed in every Candidate PR Diff hunk, and what is claimed in title/description. Live: compare `plan.md` with the entire three-dot branch diff and draft PR text. Good means no extra or missing material work; a smaller or changed slice is still faithful when the plan's Deviations and the description both disclose it. A claim of exact fidelity fails if any hunk or omitted planned outcome contradicts it.

## Test evidence (harness category: not-tested)

Find the failing repro and test plan in Plan context, then commands and results in Candidate PR Test evidence, plus regression tests in Diff. Repo facts and the PR template name applicable checks. Live: compare `test_evidence.md` with the plan and `make test-unit`, `make test-integration`, `make lint`, and `make typecheck` results where required. Good means observable before/after on the failing path, not just a previously passing control, and honest named outcomes for the repo checks. A plain "tests pass" without naming any check is inadequate; full stdout of every ancillary check is not required in eval mode.

## Diff quality (harness category: unreviewable)

Read the complete unified Diff and commit list, including hunks outside the advertised file or fix. Live: use `git diff main...HEAD` and `git log main..HEAD`. Good means the fix and relevant tests are visible without unrelated changes, debug prints, commented-out attempts, dead helpers, or bulk formatting churn. An adjacent hunk is judged for its actual content, not excused because it shares a file.

## Standards and comms (harness category: standards-wall)

Find required template fields, issue-closing syntax, contribution asks, thread direction, and stated AI policy in Repo facts, Issue, and Thread highlights; compare with Candidate PR title and description. Live: use the repo's PR template and contribution docs and the draft text. Good means every applicable required section is filled with real content, the issue is linked as asked, explicit requests are addressed, and stated AI-use disclosure is present. In eval mode every candidate is AI-assisted; name tool and extent only when the policy asks for them, while a human-voice rule is judged from the candidate comment. Do not invent a policy from silence. Whether the description accurately describes the diff belongs to Plan fidelity and Description truth.
