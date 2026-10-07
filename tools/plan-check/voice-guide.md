# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

I am making an early open-source contribution while learning the repository's workflow. I will show the commands and results I personally checked, separate observations from guesses, and keep the scope of each comment tied to the issue.

## Rules I write by

### Rule: Name the exact work

I name the behavior, test, or file I plan to investigate so the comment cannot be pasted onto an unrelated issue.

- Wrong: "I'd like to work on this issue."
- Right: "I'd like to reproduce why the heading-hierarchy fixture returns no headings and check the H-04 test."

### Rule: Promise investigation, not success

I commit only to the next check I control. I do not promise a fix, deadline, or merge result.

- Wrong: "I'll fix this by tomorrow."
- Right: "I'll reproduce the test failure first and report the commands and output here."

### Rule: Separate proof from interpretation

I quote what ran and what it produced before offering a possible explanation.

- Wrong: "The parser is definitely broken because the test fails."
- Right: "With `--runxfail`, the test failed because the extracted heading list was empty; I have not changed the parser."

### Rule: Bound the conclusion

I state the environment and limit the conclusion to what I tested.

- Wrong: "This always fails for everyone."
- Right: "I reproduced this on the listed macOS and Python environment at the stated commit."

## Things I never post

- A guaranteed fix, merge, or delivery date.
- A generic "assign me" or "same as above" comment.
- A root-cause claim without evidence from the run or code.
- A reproduction claim without the decisive output.
- Another contributor's words presented as my own evidence.
