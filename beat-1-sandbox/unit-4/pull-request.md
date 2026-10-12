# Unit 4 — Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s1/pull/160

**Branch**

`fix/71-heading-hierarchy-fixture`

## Eval iterations

**Run history**

1. Full run: 17/20 scored packages agreed with the gold labels. `pkg-08`, `pkg-11`, and `pkg-16` were false rejects.
2. Targeted `--only` run after revising the skill: 7/7 agreed, including those three former disagreements and reject canaries `pkg-01`, `pkg-07`, `pkg-17`, and `pkg-20`.
3. Confirming full run: **20/20** agreed, with a match in every category. This is the run saved in `eval-run.txt`.

**Package analysis**

`pkg-20`: my rubric returned `reject`, matching the gold `reject`. The plan, diff, and reproduction evidence support the Ghostty color-scheme fix, but the repository facts state that its AI policy requires disclosure of both the tool used and the extent of assistance. The candidate PR contains neither. My required Repository standards check therefore fails even though its technical fix is plausible.

**Check rationale**

My current `rubric.md` check reads exactly:

> | Repository standards | Compare Candidate PR description, issue thread, Repo facts' PR template and contribution/AI policies. | Applicable required template sections and issue linkage contain real content; explicit maintainer requests and contribution rules are met or honestly explained. In eval mode all packages are AI-assisted. Require a tool name and extent only when the stated policy asks for them; a policy asking merely for human-authored comments is met by a comment that says it is in the contributor's own words unless contradicted. Do not invent a policy where none is stated. | required |

I revised this check after the first full run rejected `pkg-11`, a gold `accept`, by applying Ghostty's stricter disclosure standard to a different repository. The current wording ties each requirement to that repository's stated policy. It still rejects `pkg-20`, where the strict requirement is explicit.

**Trade-offs**

The narrower policy rule accepts `pkg-11` instead of treating absent tool-and-extent details as a universal failure. It gives up a blanket disclosure requirement, so it could miss an unstated expectation. I re-ran `pkg-20` as a reject canary in the targeted pass; it remained `reject`, and the final full run matched both packages' gold labels. Likewise, my test-evidence rule accepts a named ancillary check with its reported outcome without demanding a full transcript, while still requiring decisive before/after proof for the issue-specific regression. That revision let `pkg-08` and `pkg-16` pass without letting the `not-tested` canary `pkg-07` through.
