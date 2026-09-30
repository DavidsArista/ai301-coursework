# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

## Your identity upstream

**GitHub username**

DavidsArista

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71#issuecomment-5920608134

I'd like to reproduce why `test_extract_heading_hierarchy` returns no headings and check the H-04 test. I'll run it on the current `main` branch with the `xfail` disabled for the run, then compare the indented fixture with `_extract_heading_hierarchy`'s expected input. I'll post the environment, exact command, failure output, and a control showing whether removing only the fixture indentation changes the result. I won't change the parser during this reproduction.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71#issuecomment-5920684987

## Reproduction report

I reproduced the H-04 test failure on the current `main` branch.

### Environment

- macOS 26.6.2 (Apple silicon)
- Python 3.14.1
- pytest 9.1.1
- Code: `f89c06fc3ff292df2a04a39ac51319d32a76b779`
- Development dependencies installed in a fresh `.venv` with `pip install -e ".[dev]"`

### Steps and observed output

From a fresh clone:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install --upgrade pip setuptools wheel
.venv/bin/python -m pip install -e ".[dev]"
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```

`--runxfail` makes pytest run the test normally instead of treating the current H-04 marker as the result. The test failed at its first content assertion:

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED [100%]

>       assert len(headings) > 0
E       assert 0 > 0
E        +  where 0 = len([])

tests/unit/test_readme_parser.py:156: AssertionError
============================== 1 failed in 0.57s ===============================
```

I then checked the fixture directly, once unchanged and once with only its common leading indentation removed:

```python
import textwrap
from ingestion.parsers.readme_parser import ReadmeParser

markdown = """
        # Main Title
        Some content

        ## Subsection
        More content

        ### Sub-subsection
        Even more content

        ## Another Section
        Final content
        """

parser = ReadmeParser()
for label, content in (
    ("indented fixture", markdown),
    ("dedented control", textwrap.dedent(markdown)),
):
    headings = parser._extract_heading_hierarchy(content)
    print(f"{label}: count={len(headings)} levels={[h['level'] for h in headings]}")
```

Output:

```text
indented fixture: count=0 levels=[]
dedented control: count=4 levels=[1, 2, 3, 2]
```

### Result

This reproduces the behavior described in #71. On this environment and commit, the fixture as written produces an empty heading list and the test fails with `assert 0 > 0`. Removing only the fixture's common indentation produces four headings with the expected levels 1, 2, and 3. I did not modify `_extract_heading_hierarchy` or the test during this reproduction.

## Eval iterations

**Run history**

1. Initial full run: `agreement: 19/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in disclosure)`. The rubric accepted `pkg-20`, missing the only disclosure-wall package.
2. Revised the Repository conventions check and evidence guide to state that eval packages are AI-assisted course work when applying a policy that requires disclosure of any AI use. Targeted `--only pkg-20,pkg-07` rerun: `agreement: 2/2 scored items`. `pkg-20` became reject while `pkg-07`, a previously accepted case, remained accept. This partial run did not decide the bar.
3. Final confirming full run: `agreement: 20/20 scored items  (bar: 18/20: PASS)`. The harness generated `eval-run.txt` and recorded the file fingerprints; I did not edit that transcript.

**Package analysis**

`pkg-20` initially received `accept` from my rubric, while the instructor gold label is `reject`. The package's repo-facts block says, "All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance" and the candidate comments did not disclose assistance. My first rule read the policy as conditional on the candidate explicitly saying AI was used, even though the course eval packages are treated as AI-assisted work. That made the tool pass a package that could not meet the repo's stated policy. The revised check rejects `pkg-20` for missing disclosure; its strong environment, steps, and artifacts cannot make up for that separate requirement.

**Check rationale**

The current `rubric.md` check reads exactly:

| Repository conventions | Repo-facts bug-report asks and contribution policy, including any AI-use or disclosure rule, read against both candidate comments. | The comments satisfy every stated convention that applies to comments or reports. In eval mode, treat every candidate package as AI-assisted course work: if the policy requires disclosure of any AI use, the required disclosure must be present and specific even when the candidate does not independently claim AI use. In live mode, apply the policy to the actual workflow described by the student. If the policy is silent or expressly permits use without disclosure, silence passes. | required |

I changed this check after the first full run because a policy requiring disclosure of *any* AI use has to be evaluated against the known context of the package, not just against what the candidate happens to admit. The rule distinguishes eval mode from live mode: eval packages have a known course provenance, while live checks must apply the actual repository policy to the student's actual workflow. It also leaves policy silence alone rather than inventing an obligation.

**Trade-offs**

The tighter rule makes the one-package disclosure category visible, but it depends on knowing that the eval packages are AI-assisted. It would be too broad to assume that every unrelated live contribution used AI. I ran `pkg-07` as a canary because its policy permits assistive use and its candidate claim explicitly says, "I used an AI assistant to help me organize this report; I ran and verified every step myself." The targeted rerun kept `pkg-07` accepted while changing `pkg-20` to reject, and the final full run matched all 20 gold labels.
