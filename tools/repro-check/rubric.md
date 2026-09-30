# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Specific, honest claim | Claim comment read against the issue title, body, and thread highlights. | The claim names the issue's concrete behavior or affected surface, states a next investigation or reproduction step, and makes no promise to deliver a fix or meet a date. A generic assignment request, a me-too, or a guaranteed outcome fails. | required |
| Repository conventions | Repo-facts bug-report asks and contribution policy, including any AI-use or disclosure rule, read against both candidate comments. | The comments satisfy every stated convention that applies to comments or reports. In eval mode, treat every candidate package as AI-assisted course work: if the policy requires disclosure of any AI use, the required disclosure must be present and specific even when the candidate does not independently claim AI use. In live mode, apply the policy to the actual workflow described by the student. If the policy is silent or expressly permits use without disclosure, silence passes. | required |
| Relevant environment | Issue context and repo-facts read against the repro report's OS/platform, tool and runtime versions, configuration, and code state. | The report records the environment details needed to place the attempt and matches the issue's target. A material difference is allowed only when it is named and the report does not claim the difference away. Missing a detail that can change the behavior fails; irrelevant version inventory is not required. | required |
| Rerunnable steps | Repro report's starting state, inputs, commands or actions, and controls, read against the issue's trigger and the repo's setup/reporting instructions. | A stranger can repeat the attempt from the stated starting state through the trigger using only public inputs and the report. The steps preserve the issue's decisive syntax, option, configuration, or ordering. Private dependencies, skipped triggers, or an adjacent command fail. | required |
| Artifact proves the target | Repro report's verbatim output, log, traceback, screenshot description, or measured observation read directly against the issue's actual and expected behavior. | At least one artifact visibly distinguishes the reported behavior from normal or adjacent behavior and matches the issue's target. A control may supply the distinction. Assertions, version banners, successful startup, or unrelated errors alone fail. An evidenced cannot-reproduce passes when the artifact shows the attempted trigger and the report does not claim reproduction. | required |
| Honest conclusion | Repro report's expected, observed, and conclusion language read against its own artifacts and any environment deviation. | The conclusion says exactly what the artifacts establish: reproduced, not reproduced, or cannot determine. It does not upgrade correlation to a root cause, call a different symptom the same bug, generalize beyond tested environments, or conceal a material deviation. | required |

## Verdict rule

For a full package, accept only when every required check passes; a fail or unclear holds the package. For a claim-only draft, grade Specific, honest claim and Repository conventions, mark the four repro-dependent checks `unclear` with `not yet applicable: claim-only draft`, exclude those four from the verdict, and accept only if both applicable checks pass. No check may be rescued by polish, length, confidence, or another check's strength.
