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

[Confirm this is the exact branch name you created on your fork before submitting.]

**Evidence**

### Before implementation

I reproduced Issue #64 on macOS 14.0 using Python 3.12.1, pytest 9.1.1, and commit `99673c7`. The repository had no local code changes.

Running the original test file:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
```

Output:

```text
18 passed, 1 xfailed
XFAIL ...::test_query_with_partial_overlap - issue #64: relevance scorer 'partial overlap' fixture actually has full overlap
```

Running the partial-overlap test while ignoring the `xfail` marker:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
```

Output:

```text
>       assert 0.3 < score < 0.9  # Partial overlap should be in middle range
E       assert 1.0 < 0.9
tests/unit/test_relevance_scorer.py:58: AssertionError
relevance_scored  avg_score=1.0 chunks_count=1 query_len=4
1 failed, 18 deselected
```

Calling the scorer directly:

```bash
venv/bin/python -c "from rag.evaluator.relevance_scorer import RelevanceScorer; print(RelevanceScorer().score('Python Django web framework',[{'text':'Django is a Python web framework for rapid development'}]))"
```

Output:

```text
1.0
```

This confirmed that the fixture contained all four query terms, producing a full-overlap score instead of a partial-overlap score.

### After implementation

[PASTE YOUR ACTUAL AFTER-IMPLEMENTATION COMMANDS AND TERMINAL OUTPUT HERE.]

Rerun the partial-overlap test:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
```

Then rerun the full relevance scorer test file:

```bash
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
```

[Record the observed score, test results, and whether the `xfail` marker was removed. Do not claim these tests passed until you have run them.]

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

Package `pkg-14` was in the clear-accept category. My rubric rejected it because the required check `Claims match evidence` failed, even though the gold label accepted the plan.

This check requires plans to distinguish observed facts from assumptions and avoid making unsupported claims about causes, completed work, or verification results.

[ADD THE SPECIFIC CLAIM OR EVIDENCE FROM pkg-14 THAT CAUSED THIS CHECK TO FAIL. This must come from the actual package or individual evaluation output.]

The disagreement suggests that my rubric may have interpreted a claim more strictly than the gold label intended. However, the summary alone does not establish exactly why the check failed.

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