# Procedure: how this tool grades a PR package

## Read order

1. In live mode read `scope.md` and `voice-guide.md` first, applying the frame's scope/refusal rules. In eval mode read only the package. Identify the issue, repository policy, PR template asks, and any explicit maintainer direction.
2. Read Plan context before the PR description: record the diagnosed failure, reproduction trigger and output, planned files, in/out boundary, steps, test plan, and each Deviations note. This gives an independent expectation.
3. Read the full committed Diff and commit list next, every hunk. Record the changed-file list, actual behavior changes, added/removed tests, and any debris. In live mode use `git diff main...HEAD`, not uncommitted draft files.
4. Read Test evidence and then the candidate title/description. Record commands with their printed output, compare them with the failing path and planned checks, then list each factual claim in the description. Reading claims last prevents persuasive prose from substituting for a diff or result.

## Evidence gathering

1. Use `references/evidence-guide.md` to map the four families. Pair each changed file and behavior with the exact plan line or deviation that authorized it. Pair each planned outcome with the diff that implements it; flag both extra and missing work.
2. Pair the issue-specific before/after claim with an observable result in Test evidence. For ancillary repository checks, record a named command/check and its reported outcome; do not require full stdout for each unless the repo explicitly does. Check that the after run exercises the failing path, not only a previously passing control.
3. Compare each description claim, including "nothing else changed" and any disclosed shortfall, with the complete diff and output. A negative claim is disproved by one counterexample hunk. Read the commit list as context, but base the decision on the diff.
4. Record the repo's required template fields, issue-link convention, contribution rules, and exact AI policy from Repo facts or live docs; compare with the candidate title and description. In eval mode treat every package as AI-assisted, but ask for a tool name or extent only if the policy itself asks for it. Record any explicit thread request.

## Check execution

1. Execute rubric checks in table order using the paired facts. Give `pass` only when the row's condition is shown, `fail` when a concrete counterexample appears, and `unclear` when required evidence is missing or cannot decide the condition. Do not invent output for the issue-specific repro; do not infer that an existing test is absent merely because a unified diff omits unchanged lines.
2. For Plan fidelity, a deviation repairs drift only if it appears in the plan and the description and tells what changed. For Decisive test evidence, distinguish the issue's failing trigger from a passing control; a check's honestly reported failure is evidence, not a fabricated pass. For Reviewable diff, inspect hunks outside the named fix, not just the summary.
3. Do not require extra prose, extra tests, a particular number of commits, or a perfect fix beyond the declared bounded scope. State every grade with one exact fact from the package. In live mode separately report any voice-guide breach or frame/procedure gap.

## Verdict assembly

1. Count `unclear` as failed for required checks. Accept only when every required row passes; otherwise reject. If several rows fail, cite the first failing required check in rubric order as the decisive reason, and list the others as additional reasons.
2. Emit a one-line evidence statement for every check in rubric order. End with the fixed JSON block from `SKILL.md`: item URL or bundle id, every check's name/grade/evidence, and binary verdict. Nothing follows the block.
