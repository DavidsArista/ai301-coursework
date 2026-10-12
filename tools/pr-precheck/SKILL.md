---
name: pr-precheck
description: Grade a proposed pull request against its plan, issue, diff, evidence, and repository standards before submission. Use for a live draft PR or a frozen eval package.
---

# pr-precheck: rubric-driven PR grading

## The question

Decide exactly one question for one PR package: is this ready to submit? A package contains a candidate PR title, description, commits, diff, and test evidence, judged against the issue and the plan it claims to implement. Grade the delivered change, not how polished its prose sounds. Do not expand the task into making a new fix.

## Inputs and modes

In live mode, read the student's `plan.md` including `## Deviations`, `test_evidence.md`, and `pr_draft.md` in the working copy, the issue body and thread, and the repository's PR template and contribution policy. Get the committed branch's whole diff against the default branch with `git diff main...HEAD` (three dots), and its commit list; ignore uncommitted draft files as part of the diff. The draft's first line is the PR title and the rest is its description. On a house chain, use its supplied house issue, reproduction pack, and plan in the same roles. If any input is absent, record that absence; never silently replace it with an imagined fact.

In eval mode, the supplied frozen package bundle is the entire world. Read only its Issue, Repo facts, Thread highlights, Plan context, Candidate PR (title, description, commits, unified diff), and Test evidence. Never fetch a live issue or repository, and run every check with the full verdict rule.

## The scope seam (live mode only)

Read `scope.md` before gathering any live evidence. If its Repo line still has a placeholder, stop and tell the student to fill it with the section's Path Review repo. Refuse to grade a PR targeting any other repo or issue than the scoped source and the issue tied to the student's plan. Apply the scope's house rules, including one PR per issue per student and a PR from the student's fork. Ignore `scope.md` in eval mode.

## The voice seam (live mode only)

Read `voice-guide.md` before grading the outgoing PR title and description. Report any specific rule they break, quoting the rule and the offending text. Voice feedback does not change the rubric verdict unless a rubric check explicitly uses it. Ignore the voice guide in eval mode.

## Component reads

Read `rubric.md` for every check and the verdict rule. Use `references/evidence-guide.md` to locate each evidence family. Execute `procedure.md` exactly for read order, evidence pairing, check execution, and verdict assembly. If the procedure omits a needed step, report the gap rather than inventing one. If the rubric has no filled checks or the procedure has no authored steps, refuse to grade: an empty tool cannot issue a verdict.

## Verdict and output

Return only `accept` (ready to submit) or `reject` (hold). You may give a short evidence-based summary first, including voice and procedure-gap notes in live mode. End with the following fenced JSON block, valid and last, with nothing after it:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Name the actual fact or quote behind every check grade. A terse PR with a faithful diff and decisive output can pass; a polished description cannot rescue drift or an untested path. Apply the rubric's stated pass conditions even if the result feels surprising, and follow the procedure without improvising around gaps. Treat an `unclear` required check as failed when the rubric is silent: unverifiable work is not ready to submit.
