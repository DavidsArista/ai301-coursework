# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

In an eval package, compare the issue context and repo-facts block with the repro report's environment line and setup notes. In live mode, compare the issue body, relevant maintainer comments, repository setup docs, and the draft report. Look for the OS or platform, relevant application/runtime versions, configuration or backend, and code state when those can affect the reported behavior.

Good evidence lets another reader tell whether the attempt exercised the issue's target. A different version or platform can pass when it is stated and the conclusion is limited to that environment. An unstated difference that can change the result, or no environment record where build, OS, driver, shell, or version matters, is insufficient.

## Steps

In an eval package, use the repro report's setup, commands, inputs, and numbered actions; use the issue context to identify the decisive trigger. In live mode, also consult public repository setup and test instructions. The package must carry every non-obvious input it depends on.

Good steps begin from a stated code/configuration state and preserve the issue's decisive syntax, ordering, flags, data, or UI action through the observed result. A stranger must be able to repeat them without a private repository, hidden configuration, or a guess such as "set up normally." Exact headings or a minimum number of steps are not required.

## Behavior shown

In an eval package, read the report's quoted output, traceback, log, screenshot description, exit status, or measurements against the issue's stated actual and expected behavior. In live mode, the draft comment must contain or quote the deciding artifact; an unposted local file does not count. Controls are evidence when they isolate the changed condition.

Good evidence visibly contains the reported failure or a measurement that separates it from normal behavior. Confirm that the error type, output state, input shape, and trigger match the issue. A version banner, successful launch, or different validation error only proves that adjacent event. For cannot-reproduce reports, the artifact should show that the stated trigger was actually attempted and what happened instead.

## Honesty

Compare the claim comment's promises and the repro report's expected/actual/conclusion statements with the artifacts and environment record. Read causal statements especially closely: a suspected source location is not a verified root cause unless the package shows evidence for it.

Good language is bounded by the evidence: "reproduced on this setup," "did not reproduce under these conditions," or "the output is inconclusive." It names material deviations and does not turn a different error into confirmation, a correlation into a cause, or one environment into a universal result. An honest, evidenced cannot-reproduce is a successful report.

## Comms

In an eval package, compare the candidate claim and report with the issue context, repo-facts bug-report asks, contribution policy, and any AI-use disclosure rule. Treat all candidate eval packages as AI-assisted course work; a policy requiring disclosure of any AI use therefore applies even when the candidate text does not announce that fact. In live mode, inspect the issue and repository's current CONTRIBUTING file, report template, and linked policy before grading the drafts, then apply the policy to the student's actual workflow.

A good claim names the issue-specific behavior or file and a concrete next step without promising a fix or date. A good report provides what the repository explicitly asks for and obeys any comment-level disclosure requirement. Boilerplate assignment requests, me-too comments, pressure for a fix, and guarantees fail. Policy silence does not create a disclosure requirement.
