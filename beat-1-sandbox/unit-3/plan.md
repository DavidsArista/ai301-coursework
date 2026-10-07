# Plan for issue #71: heading hierarchy test fixture

## Diagnosis

On macOS 26.6.2 with Python 3.14.1 at commit `f89c06fc3ff292df2a04a39ac51319d32a76b779`, I reran the H-04 test with `--runxfail`. It failed at `assert len(headings) > 0` because the result was `[]`. My posted reproduction also passed the fixture text directly to `_extract_heading_hierarchy`: the eight-space-indented version gave `count=0 levels=[]`, while removing only that common indentation gave `count=4 levels=[1, 2, 3, 2]`. The parser matches heading markers at the start of a line. This evidence points to the fixture, not a parser defect.

## Scope

Change only `tests/unit/test_readme_parser.py`: make the H-04 fixture's heading markers start at column one and remove its strict `xfail` marker. Keep the expected hierarchy visible by asserting the observed levels in order. Do not change `ingestion/parsers/readme_parser.py`, other fixtures, or heading parsing semantics.

## Steps

1. In `TestReadmeParser.test_extract_heading_hierarchy`, remove the common indentation from the multiline Markdown fixture so the `#`, `##`, and `###` markers are actual headings.
2. Remove that test's `@pytest.mark.xfail` decorator; it should now run as a normal test.
3. Run the issue-specific test, `.venv/bin/python -m pytest tests/unit/test_readme_parser.py -q`, `.venv/bin/python -m pytest tests/unit -q`, `.venv/bin/black --check tests/unit/test_readme_parser.py`, and `.venv/bin/ruff check tests/unit/test_readme_parser.py`. Review the diff to confirm the change stayed within the planned test.

## Test plan

Before the change, run `.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v --runxfail`; expect failure with `assert 0 > 0`. The direct helper control on the unmodified fixture gives `count=0 levels=[]`; on the same text with only indentation removed it gives `count=4 levels=[1, 2, 3, 2]`.

After the change, rerun the same pytest command and run the test without `--runxfail`; expect PASS in both, not XFAIL or XPASS. The corrected fixture should yield four headings in the order `[1, 2, 3, 2]`. Run `.venv/bin/python -m pytest tests/unit/test_readme_parser.py -q` to check neighboring parser tests.

## Risks and unknowns

Before the build, I had not yet run the corrected test. I checked whether removing the indentation preserved the expected levels and whether neighboring parser tests depended on the old fixture. After the build, the corrected issue-specific test passed, the readme-parser file reported 14 passed with one unrelated xfail, and the full unit suite reported 376 passed with 52 existing xfails.

## Deviations

The built change followed the posted plan. I edited only the H-04 test fixture in `tests/unit/test_readme_parser.py`, removed its strict `xfail` marker, and asserted the four heading levels in order. I did not change the parser. The issue-specific test now passes with and without `--runxfail`:

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]
1 passed in 0.06s
```
