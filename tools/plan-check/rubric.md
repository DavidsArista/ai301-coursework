# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Grounded diagnosis | Candidate plan's cause and proposed change compared with the Repro evidence's trigger, controls and observed output; Issue and Thread highlights give context. | The proposed cause is compatible with the failing case and every decisive control, and the change targets that cause rather than a symptom. An internal mechanism may be a reasoned inference at plan time if no control contradicts it and the plan's checks can test it. A thread claim never overrides a contradictory control. | required |
| Bounded scope | Candidate plan's included/excluded work and named areas compared with the Issue and Thread highlights. | One bounded fix for the reproduced failure, plus necessary tests; no unrelated redesign, migration, feature, or cleanup. A deliberately narrower fix passes if its limitation is explicit. | required |
| Executable change | Candidate plan's chosen code location and action compared with Repo facts and the Issue. | Another contributor can start the chosen approach without first selecting an architecture or hunting for an unspecified component. Exact line numbers and lengthy prose are unnecessary. | required |
| Decisive verification | Candidate plan's test steps and expected result compared with the Repro evidence's failing trigger and observable output. | The test repeats the failure path or an equivalent regression and specifies an observable result that distinguishes fixed from unchanged. A generic suite alone or subjective feeling is insufficient. | required |
| Honest uncertainty | Candidate plan's claims, risks and unknowns compared with the Repro evidence, Issue and Thread highlights. | A material uncertainty that could invalidate the chosen fix is acknowledged or covered by a discriminating plan step or test. Do not fail a plan merely because it has not proven an internal mechanism, misstated a nondecisive attribution, or lacks a ritual risks section. Reject confident claims that contradict a repro control or conceal a material untested assumption. | required |
| Thread and repository fit | Candidate plan comment and plan compared with explicit maintainer direction in Thread highlights and Repo facts, including contribution and AI-use policies. | The comment addresses applicable maintainer direction and follows stated repository constraints. For eval bundles, treat every candidate as AI-assisted: when the stated policy requires disclosure of any AI use in comments, the comment names the tool and extent. Do not invent a disclosure requirement where none is stated. | required |
| Clear communication | Candidate plan comment read beside the Issue and plan. | The comment names an issue-specific approach and verification clearly enough for a maintainer to understand the intended change. | preferred |

## Verdict rule

Grade each check pass, fail, or unclear. Missing or insufficient evidence is unclear. An unclear required check counts as failed. Accept only when every required check passes; preferred checks never affect the verdict. Otherwise reject and name the deciding failed or unclear checks.
