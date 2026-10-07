# Evidence guide: where evidence lives in a plan package

In eval mode use only the supplied package's named sections. In live mode use the scoped issue body and thread, its repository's stated docs and policies, the student's posted Unit 2 repro comment, and the draft plan and comment. The drafts must quote the evidence they rely on; private files are not part of what a maintainer sees.

## Diagnosis and grounding

Find the cause and mechanism in Candidate plan diagnosis/change text; find the trigger, output and isolating controls in Repro evidence. Issue and Thread highlights supply claims to investigate, not replacements for a control. Good means the mechanism is compatible with both bad and contrasting good runs. An unproven internal detail can be a reasonable inference when the plan can test it; a contradicted control holds the plan. Live: compare the draft with the posted repro comment and issue thread.

## Scope

Find included and excluded areas in Candidate plan scope/change text; compare with Issue and Thread highlights. Good means a bounded causal fix and necessary test without unrelated migration or redesign. A narrow slice is acceptable when its limits are explicit. Live: use the draft and current thread.

## Executability

Find the chosen file, component or callback and concrete action in Candidate plan change steps; compare names and constraints with Repo facts. Good means a contributor can begin without choosing the basic architecture or guessing where to edit. A concise one-file change may suffice. Live: use the draft and repository layout/docs.

## Test plan

Find commands or manual actions and expected observations in Candidate plan test text; compare with Repro evidence's decisive failing steps and controls. Good means a repeated trigger, or equivalent regression, visibly distinguishes fixed from unchanged behavior. A generic suite can supplement but not replace that observation. Live: compare the draft with the posted repro comment.

## Honesty

Find causal certainty, unknowns, risks and any deviation note in Candidate plan and comment. Check material claims against Repro evidence and Thread highlights. Good means a material unknown that could invalidate the fix has a planned check or test; do not require direct proof of every internal detail before a plan can be posted. A supported narrow change needs no artificial uncertainty. Live: use drafts, posted repro and thread.

## Comms

Read Candidate plan comment against Thread highlights and Repo facts: maintainer requests, prior work, contribution instructions and any stated AI-use disclosure. Good means it responds to applicable direction and contains any explicitly required disclosure. In eval mode every candidate is treated as AI-assisted, so a policy requiring disclosure of any AI use in comments requires the tool and extent in the candidate comment. Do not infer a disclosure rule from silence. Live: use the current thread and repository's own docs before grading the draft.
