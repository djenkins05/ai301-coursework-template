# Implementation Plan — Issue #64

**Issue:** https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64

## Problem Description

The `test_query_with_partial_overlap` test is supposed to verify that the relevance scorer returns a middle-range score when a query only partially matches a text chunk. However, the current test fixture contains all four query terms from `"Python Django web framework"`.

The chunk `"Django is a Python web framework for rapid development"` contains every query term, which produces a relevance score of `1.0` instead of satisfying the expected range `0.3 < score < 0.9`.

## Reproduction Evidence

I reproduced Issue #64 using the following environment:

- macOS 14.0
- Python 3.12.1
- pytest 9.1.1
- `structlog` installed
- Repository commit `99673c7`
- Branch `issue-64`
- No local code changes

Running the original test file produced:

```text
18 passed, 1 xfailed
```

The partial-overlap test was marked as an expected failure.

When I ignored the `xfail` marker using `--runxfail`, the test failed with:

```text
assert 0.3 < score < 0.9
E assert 1.0 < 0.9
```

Calling the relevance scorer directly with the original query and chunk also returned `1.0`.

These results confirm that the fixture contains full keyword overlap even though the test is intended to check partial overlap.

## Diagnosis

The evidence points to the test fixture as the cause of the failing assertion rather than a confirmed problem with the relevance scoring algorithm.

All four query terms appear in the text chunk, so the scorer returns `1.0`. The fixture needs to contain only some of the query terms to test partial overlap correctly.

## Proposed Fix

I plan to modify the text chunk used in `test_query_with_partial_overlap` so that it contains only some of the query terms.

I will keep the test focused on verifying partial overlap and preserve the expected score range of `0.3 < score < 0.9`.

I will also review the existing `xfail` marker. If the updated fixture makes the test pass consistently, I will remove the marker so the test runs normally.

## Scope

**In scope:**

- Update the text fixture in `test_query_with_partial_overlap`.
- Keep the existing partial-overlap assertion.
- Review and remove the issue-specific `xfail` marker if the corrected test passes.
- Run the relevant tests to verify the change.

**Out of scope:**

- Modifying the relevance scoring algorithm unless new evidence demonstrates that it is necessary.
- Rewriting unrelated tests.
- Adding new scoring features or changing the relevance calculation.

## Implementation Steps

1. Open `tests/unit/test_relevance_scorer.py` and locate `test_query_with_partial_overlap`.
2. Review the existing query, chunk, assertion, and `xfail` marker.
3. Modify the chunk so that at least one query term is missing while enough terms remain to produce a partial-overlap score.
4. Run the partial-overlap test with `--runxfail` to check whether the corrected fixture satisfies `0.3 < score < 0.9`.
5. If the test passes, remove the issue-specific `xfail` marker.
6. Run the complete relevance scorer test file to check for regressions.
7. Review the final changes to confirm that they stay within the planned scope.

## Test Plan

### Before implementation

The original reproduction was performed using:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
```

Observed result:

```text
18 passed, 1 xfailed
```

Running the partial-overlap test while ignoring its expected-failure marker:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
```

Observed result:

```text
1 failed, 18 deselected
E assert 1.0 < 0.9
```

The direct scorer call also returned `1.0`.

### After implementation

Run the partial-overlap test again:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
```

Expected result:

The test passes because the updated fixture represents partial keyword overlap and produces a score strictly between `0.3` and `0.9`.

After removing the issue-specific `xfail` marker, run:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
```

Expected result:

The corrected partial-overlap test passes normally, and the other relevance scorer tests continue to pass.

Record the actual output after implementation rather than assuming these results.

## Risks and Unknowns

The exact relevance score depends on how the scorer calculates keyword overlap. I will verify the result before selecting the final fixture text.

Removing too many query terms could cause the score to fall below the required range. I will choose a fixture that produces a valid partial-overlap score while keeping the test's purpose clear.

The current `xfail` marker also needs to be reviewed. I will only remove it after confirming that the corrected test passes.

If changing the fixture does not resolve the test failure, I will investigate the result before modifying any scoring logic.

## Deviations

Implementation has not started yet. I will update this section after making and testing the change to explain whether I followed the original plan or needed to adjust it.