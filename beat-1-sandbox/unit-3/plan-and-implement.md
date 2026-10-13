# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

---

## Posted upstream

**GitHub username**

djenkins05

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64#issuecomment-6137574304

Hi, I'd like to share my implementation plan for issue #64.

In my reproduction, `test_query_with_partial_overlap` returned a score of `1.0` because the text chunk contains all four query terms from `"Python Django web framework"`. When I ran the test with `--runxfail`, it failed the assertion `0.3 < score < 0.9`.

I plan to update the test fixture so the chunk contains only some of the query terms. I'll keep the existing assertion and rerun the partial-overlap test to verify that the score falls within the expected range.

If the test passes, I'll remove the issue-specific `xfail` marker and run the full relevance scorer test file to check for regressions.

I'll keep the change focused on the test fixture rather than modifying the scoring algorithm unless the new test results show that a broader change is necessary.

---

## Your branch

**Branch**

`fix/64-partial-overlap-fixture`


**Evidence**

### Before implementation

**Environment:** macOS 14.0, Python 3.12.1, pytest 9.1.1, `.venv`.

**Base commit:** `99673c7`

**Implementation branch:** `fix/64-partial-overlap-fixture`

The original fixture contained all four query terms, causing the relevance scorer to return `1.0`.

Command:

```bash
.venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
```

Output:

```text
..x................                                                      [100%]
XFAIL tests/unit/test_relevance_scorer.py::TestRelevanceScorer::test_query_with_partial_overlap - issue #64: relevance scorer 'partial overlap' fixture actually has full overlap
18 passed, 1 xfailed in 1.09s
```

Command:

```bash
.venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
```

Output:

```text
>       assert 0.3 < score < 0.9
E       assert 1.0 < 0.9
tests/unit/test_relevance_scorer.py:58: AssertionError
relevance_scored avg_score=1.0 chunks_count=1 query_len=4
1 failed, 18 deselected in 0.24s
```

### After implementation

I changed the text chunk in `test_query_with_partial_overlap` from:

`Django is a Python web framework for rapid development`

to:

`Django is a Python tool for rapid development`

The updated chunk contains two of the four query terms, producing a score of `0.5`, which satisfies `0.3 < score < 0.9`.

I also removed the issue-specific `xfail` marker. No changes were needed to the relevance scoring algorithm or `pyproject.toml`.

Command:

```bash
.venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
```

Output:

```text
.                                                                        [100%]
1 passed, 18 deselected in 0.23s
```

An additional run with `-s` showed `avg_score=0.5`.

Command:

```bash
.venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
```

Output:

```text
...................                                                      [100%]
19 passed in 0.19s
```

### Repository checks

```bash
make lint
```

Output: `All checks passed!`

```bash
make typecheck
```

Output: `Success: no issues found in 76 source files`

```bash
make test-unit
```

Output:

```text
376 passed, 52 xfailed, 5 warnings in 20.05s
```

The warnings were related to deprecations and unawaited coroutines in other tests, not the modified fixture.

**Result:** The corrected test passes with a relevance score of `0.5`, the other relevance scorer tests pass, and the repository-wide lint, type-checking, and unit-test results show no reported failures.

## Eval iterations

**Run history**

1. **Initial partial run:** I ran the evaluation using `--limit 3` to check whether my rubric, evidence guide, and procedure worked together. The evaluation agreed on all three scored packages (3/3). My rubric correctly rejected `pkg-01` and accepted `pkg-02` and `pkg-03`.

2. **Full evaluation:** I then ran all 20 scored packages using `--save-run eval-run.txt`. The result was 19/20 agreement, exceeding the target of 18/20. The only disagreement was `pkg-14`, where my rubric returned `reject` while the gold label was `accept`. The failed check was `Claims match evidence`.

Final category results:

```text
clear-accept       6/7
scope-creep        4/4
thread-convention  2/2
unbuildable        3/3
wrong-cause        4/4
```

Final agreement:

```text
agreement: 19/20 scored items  (bar: 18/20: PASS)
```

I kept the original rubric after the full run because it met the evaluation target and correctly classified all packages in the other four categories.

**Package analysis**

Package: `pkg-14`

My rubric decided: `reject`

Gold label: `accept`

Package `pkg-14` was in the clear-accept category. During my full evaluation, my rubric rejected the package because the required `Claims match evidence` check failed.

This check evaluates whether a plan distinguishes confirmed findings from assumptions and avoids making unsupported claims. Since the check is required, its failure caused the entire package to receive a `reject` verdict even though the other checks did not prevent acceptance.

The gold label was `accept`, suggesting my rubric was more conservative than necessary when evaluating the plan's claims. I kept the check unchanged because my full evaluation achieved 19/20 agreement, and relaxing it without understanding the disagreement could cause other packages to be accepted incorrectly.

**Check rationale**

One required check I included was `Claims match evidence`.

The check currently reads:

| Claims match evidence | The candidate plan's statements about confirmed causes, completed work, test results, risks, and unknowns read against the repro-evidence block and issue context. | Pass if the plan distinguishes observed facts from assumptions and does not claim successful implementation or verification without supporting evidence. Fail if an important unknown is presented as confirmed or a claim about the issue contradicts the available evidence. | required |

I made this a required check because an implementation plan should be based on what the reproduction evidence actually proves. A plan can sound convincing while treating assumptions as confirmed facts or claiming that a fix works before testing it.

I chose this wording to make the check evaluate whether the plan's claims are supported by evidence rather than how confident or detailed the writing sounds.

I did not revise this check after the full evaluation because the rubric correctly classified 19 of the 20 packages and met the target agreement.

**Trade-offs**

The main trade-off I accepted was keeping `Claims match evidence` as a required check even though it contributed to rejecting `pkg-14`, whose gold label was `accept`.

Making this check less strict might allow `pkg-14` to pass, but it could also allow plans with unsupported claims to be accepted.

I chose not to change the rubric because the full evaluation already reached 19/20 agreement. All four other categories had perfect agreement, including both thread-and-convention packages. Without evidence that loosening the check would improve overall reliability, I kept the original wording.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; the skill files in `tools/plan-check/`.