# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

DavidsArista

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71#issuecomment-6043309427

I reproduced #71 on macOS 26.6.2 with Python 3.14.1 at `f89c06f`. With `--runxfail`, `test_extract_heading_hierarchy` fails at `assert 0 > 0`. Passing its current eight-space-indented fixture directly to the parser returns `count=0 levels=[]`; removing only that indentation returns `count=4 levels=[1, 2, 3, 2]`. That points to the fixture rather than the parser.

I plan to change only `tests/unit/test_readme_parser.py`: put the Markdown heading markers at column one, remove the H-04 `xfail` marker, and assert the expected heading levels in order. I won't change `_extract_heading_hierarchy` or other parsing behavior. I'll rerun the issue-specific test with and without `--runxfail` and the readme-parser test file; the issue-specific test should change from FAIL/XFAIL to PASS with four headings.

## Your branch

**Branch**

`fix/71-heading-hierarchy-fixture`

**Evidence**

Before, from the fork at `f89c06fc3ff292df2a04a39ac51319d32a76b779`:

```bash
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy FAILED [100%]

=================================== FAILURES ===================================
_______________ TestReadmeParser.test_extract_heading_hierarchy ________________

self = <tests.unit.test_readme_parser.TestReadmeParser object at 0x10a634320>
parser = <ingestion.parsers.readme_parser.ReadmeParser object at 0x10a52aa50>

    @pytest.mark.xfail(
        strict=True,
        reason="issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings",
    )
    def test_extract_heading_hierarchy(self, parser):
        """Test heading hierarchy extraction."""
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
        headings = parser._extract_heading_hierarchy(markdown)

        assert isinstance(headings, list)
>       assert len(headings) > 0
E       assert 0 > 0
E        +  where 0 = len([])

tests/unit/test_readme_parser.py:156: AssertionError
=========================== short test summary info ============================
FAILED tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy
============================== 1 failed in 0.09s ===============================
```

Direct control from my Unit 2 reproduction, before the change:

```bash
.venv/bin/python repro_issue_71.py
```

```text
indented fixture: count=0 levels=[]
dedented control: count=4 levels=[1, 2, 3, 2]
```

After the change, from branch `fix/71-heading-hierarchy-fixture`:

```bash
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail
```

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]

============================== 1 passed in 0.06s ===============================
```

Without `--runxfail`, confirming the strict xfail marker is gone:

```bash
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v
```

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]

============================== 1 passed in 0.05s ===============================
```

## Eval iterations

**Run history**

1. First full 20-package run: 17/20 agreement, below the 18/20 bar. It disagreed on `pkg-09`, `pkg-14`, and `pkg-20`.
2. Targeted `--only pkg-01,pkg-03,pkg-04,pkg-07,pkg-09,pkg-14,pkg-20` run after revising the rubric, evidence guide, and procedure: 6/7 agreement. This was a partial diagnostic run, not the submitted run; `pkg-09` changed to accept and `pkg-20` changed to reject, while the canaries kept their expected labels.
3. Confirming full 20-package run: 19/20 agreement, passing the 18/20 bar and matching at least one item in every category. This is the run in `eval-run.txt`.

**Package analysis**

`pkg-20` (Ghostty): my final rubric decided **reject**, matching the gold **reject** label. The plan's capacity-change diagnosis, bounded implementation, and two regression tests passed their checks. My first run incorrectly accepted it because the comment did not explicitly admit AI use and the grader treated that silence as evidence of no AI assistance. The frozen repo facts say Ghostty requires disclosure of **all** AI use in comments, with the tool and extent. The final rubric treats every eval candidate as AI-assisted, so its `Thread and repository fit` check fails this comment for omitting that disclosure. This is why a technically strong plan was held.

**Check rationale**

The current check in my uploaded `rubric.md` reads exactly:

> | Thread and repository fit | Candidate plan comment and plan compared with explicit maintainer direction in Thread highlights and Repo facts, including contribution and AI-use policies. | The comment addresses applicable maintainer direction and follows stated repository constraints. For eval bundles, treat every candidate as AI-assisted: when the stated policy requires disclosure of any AI use in comments, the comment names the tool and extent. Do not invent a disclosure requirement where none is stated. | required |

I revised this after the first full run accepted `pkg-20`. The prior wording asked for disclosure only if the policy required it but did not tell the grader that every eval candidate is AI-assisted. It now connects Ghostty's explicit all-use policy to the candidate comment while leaving repositories with no such policy alone.

**Trade-offs**

This check can reject a technically sound plan solely because its public comment omits a required disclosure; that is intentional when the repository makes disclosure a condition of contributing. In the targeted rerun, `pkg-20` changed from accept to reject. The `pkg-03` clear-accept canary stayed accept because its repo asks for comments in the contributor's own voice but does not impose the same issue-comment disclosure, and `pkg-04` stayed reject for ignoring maintainer direction.
