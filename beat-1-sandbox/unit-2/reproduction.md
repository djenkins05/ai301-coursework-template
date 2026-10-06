# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

djenkins05

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64#issuecomment-6008273060

Hi, I'd like to investigate this issue. I'll look into `test_query_with_partial_overlap` and check whether the fixture's full query overlap is causing the relevance scorer to return `1.0` and fail the `assert 1.0 < 0.9` check. I'll document the version, steps I used, and what I observe.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64#issuecomment-6008702655

## Reproduction: issue #64 reproduced

**Environment**
- macOS 14.0 (Darwin 23.0.0, build 23A344)
- Python 3.12.1 in a fresh virtual environment
- pytest 9.1.1
- structlog installed because the relevance scorer imports it
- Repo: `pathreview-ai301-fa26-howard`
- Branch: `issue-64`
- Commit: `99673c7`
- Code state: exactly as cloned, with no local edits (`git status` clean)

**Steps**

```bash
cd pathreview-ai301-fa26-howard
python3 -m venv venv
venv/bin/pip install pytest structlog

# 1. Run the test file as-is
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX

# 2. Run the partial-overlap test while ignoring its xfail marker
venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap

# 3. Call the scorer directly
venv/bin/python -c "from rag.evaluator.relevance_scorer import RelevanceScorer; print(RelevanceScorer().score('Python Django web framework',[{'text':'Django is a Python web framework for rapid development'}]))"
```

Without `structlog` installed, test collection fails with:

```text
ModuleNotFoundError: No module named 'structlog'
```

**Observed output**

The first command passes the rest of the test file and reports the partial-overlap test as expected to fail:

```text
18 passed, 1 xfailed
XFAIL ...::test_query_with_partial_overlap - issue #64: relevance scorer 'partial overlap' fixture actually has full overlap
```

Running the test with the `xfail` marker ignored shows the underlying assertion:

```text
>       assert 0.3 < score < 0.9  # Partial overlap should be in middle range
E       assert 1.0 < 0.9
tests/unit/test_relevance_scorer.py:58: AssertionError
relevance_scored  avg_score=1.0 chunks_count=1 query_len=4
1 failed, 18 deselected
```

Calling the scorer directly returns:

```text
1.0
```

**Expected behavior**

`test_query_with_partial_overlap` is intended to represent a partial keyword overlap, so the score should fall strictly between `0.3` and `0.9`.

**Actual behavior**

The query is `"Python Django web framework"`, which contains four terms. The chunk is `"Django is a Python web framework for rapid development"`, and it contains all four query terms. That produces full overlap, so the scorer returns `1.0` and the assertion `0.3 < score < 0.9` fails.

**Result**

Reproduced. In this environment and code state, the scorer returns `1.0` because the test fixture contains all of the query terms. This matches the behavior described in issue #64. I have not made any code changes.


## Eval iterations

**Run history**

1. **First full run:** `19/20` scored items agreed. The only disagreement was `pkg-09`, where my rubric returned `reject` while the gold label was `accept`. The failed check was `Reproduction steps are followable`.

2. **Partial `--only pkg-09` run:** `0/1` scored items agreed. After revising the reproduction-steps check, `pkg-09` still returned `reject` while the gold label was `accept`. Because this was a partial run, it did not determine the overall bar or category floor.

3. **Second full run:** `17/20` scored items agreed. This revision also missed the disclosure category, so I rejected the revision and restored the earlier rubric wording.

4. **Final confirming full run:** `19/20` scored items agreed. I restored the earlier rubric wording and saved this run with the harness to `eval-run.txt`.

`categories: clear-accept 7/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`

`agreement: 19/20 scored items  (bar: 18/20: PASS)`


**Package analysis**

Package: `pkg-09`

My rubric decided: `reject`

Gold label: `accept`

My rubric rejected `pkg-09` because it failed the `Reproduction steps are followable` check. The package documented a cannot-reproduce attempt for the `--exec-batch` ordering issue. It included the environment, commands, observed output, repeated attempts, and an explanation that the exact trigger condition might require a different argument-length distribution or a lower forced argument-size limit. My rubric interpreted that uncertainty as requiring the reader to guess a material condition needed to reach the reported bug, so it rejected the package even though the gold label accepted the documented cannot-reproduce attempt.

**Check rationale**

The check currently reads:

> `| Reproduction steps are followable | The repro report's stated setup, commands, inputs, and actions, read against prerequisites in the issue description and repo-facts block. | Pass if a stranger with the referenced project can follow the reported sequence from the stated starting condition to the observed result without having to guess a material step, command, input, or prerequisite. Fail if reproducing the attempt requires guessing information that could change the outcome. | required |`

I kept this wording because I wanted the check to judge whether a stranger could actually repeat the documented attempt rather than rewarding a report just for having a list of steps. I briefly loosened the check to make cannot-reproduce reports easier to accept, but that revision caused additional packages to flip and lowered the full-run agreement from 19/20 to 17/20 while also missing the disclosure category. I therefore restored the stricter wording that produced the stronger overall result.

**Trade-offs**

The main trade-off is that the `Reproduction steps are followable` check is conservative about missing or uncertain trigger conditions. That helped prevent incomplete reproduction reports from being accepted, but it also caused `pkg-09` to be rejected even though the gold label accepted its well-documented cannot-reproduce attempt. I tested a looser version of the check with `--only pkg-09`, but it still did not resolve that package, and a later full run caused other previously correct packages to flip. I therefore accepted the `pkg-09` miss rather than weakening the check in a way that reduced the rubric's overall reliability.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
