# Procedure: how this skill grades a plan package

## Read order

1. In live mode read scope.md and voice-guide.md as SKILL.md requires, then gather only the scoped issue and its posted reproduction. In eval mode use only the supplied bundle; never fetch a live issue.
2. Read the Issue, Thread highlights and Repo facts first. Record the reported failure, explicit maintainer requests, repository constraints and any AI-disclosure rule. Record when a rule is absent.
3. Read Repro evidence before the candidate diagnosis. Record the failing trigger, expected and actual output, controls that isolate the cause, and untested gaps. This prevents a confident plan or thread claim from becoming the assumed truth.
4. Read the Candidate plan, then Candidate plan comment. Record cause, chosen code area, included and excluded work, first actionable step, tests with expected outputs, uncertainty, and what the comment tells maintainers.

## Evidence gathering

1. Use references/evidence-guide.md to locate each family. In a bundle, labeled sections are the whole evidence. In live mode use the issue body and thread, repository docs, the student's posted repro comment and the two drafts; do not silently substitute private files for missing statements in drafts.
2. Put each causal claim beside the repro trigger and each control. Ask whether the alleged cause remains when the outcome disappears, or the outcome persists when the cause is removed. Record the decisive pair with exact observations.
3. List areas to change, exclusions and the first actionable edit; compare with the issue and maintainer direction. Separate necessary regression tests from unrelated work.
4. Map each proposed test to the repro's failed behavior and record the output that would count as fixed. List material assumptions and how they will be checked. Record each explicit thread request, template or policy requirement and the matching words in the comment.

## Check execution

1. Apply rubric rows in table order to gathered facts. Grade pass only when the stated pass condition is met, fail when a concrete fact contradicts it, and unclear when relevant evidence is missing or insufficient. Never repair a plan by imagining unstated code, tests or disclosures.
2. For diagnosis prefer isolating repro controls over a thread assertion. A compatible internal mechanism may remain an inference if the plan can test it; a contradictory control fails it. For verification inspect the expected observation, not merely the test command. For thread fit enforce only explicit applicable requests and policies. In eval mode treat every candidate as AI-assisted when applying a stated AI-use policy; a policy covering comments requires disclosure in the candidate comment, including tool and extent.
3. A terse plan may pass when its cause, boundary, starting point and observable test meet the checks. Do not impose headings, length, line numbers or polish.
4. Record a one-line deciding fact for every grade and any procedure gap in the readable summary. In live mode separately note voice-guide violations as SKILL.md requires.

## Verdict assembly

1. Count every required unclear as a failed gate. If all required checks pass, accept; otherwise reject. Preferred checks do not affect the calculation.
2. Summarize decisive evidence before the final JSON, including any mismatch between a claimed cause and a repro control. End with the exact JSON shape in SKILL.md, every named check, one evidence line per check and the binary verdict. Put nothing after that JSON block.
