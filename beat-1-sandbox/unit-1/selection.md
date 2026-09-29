# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64

**Verdict output**

Accepted, ranked by fit (Python/API/backend/testing/debugging, clearly scoped, no major architecture):

1. #26 – Add a safety event count to the health check endpoint — best fit: it's a backend/API wiring task with named files (api/routes/health.py, safety/monitoring.py), a named method to call, and an explicit 2–4 hour estimate. Very concrete and squarely in the "APIs, backend development" preference.
2. #64 – Relevance scorer "partial overlap" test fixture has full overlap — a clean, bounded testing/debugging fix (wrong fixture value) with an exact repro command and failing assertion.
3. #59 – Faithfulness checker scores claims unsupported on reworded context — a valid bug fix with repro steps and a concrete example, but ranked last because the fix requires devising a semantic-matching approach rather than just wiring an existing piece, giving it slightly more open-ended design ambiguity than the other two.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/26",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "repo pushed_at 2026-09-16, 12 days before today (2026-09-28)"},
      {"name": "Repository in use", "grade": "pass", "evidence": "commits on 2026-09-16 (x4) and 2026-08-24, all within 180 days"},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "wire existing SafetyMonitor.get_event_count() into health.py; touches 2 named files, no architecture change"},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "body names exact field (safety_events_last_hour), the method to call, and relevant files"},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "assignees: [], 0 comments, no linked/mentioned PRs found via search"},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "no CONTRIBUTING.md or AI policy file present (404 on all checked paths)"},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "lists relevant files and gives a 2-4 hour effort estimate"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "repo pushed_at 2026-09-16, 12 days before today"},
      {"name": "Repository in use", "grade": "pass", "evidence": "commits on 2026-09-16 (x4) and 2026-08-24, within 180 days"},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "fix one test fixture's query string in one test file; no architecture change"},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "names failing test test_query_with_partial_overlap and gives exact repro command/assertion"},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "assignees: [], 0 comments, no linked/mentioned PRs found via search"},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "no CONTRIBUTING.md or AI policy file present (404 on all checked paths)"},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "includes exact pytest repro command and the failing assertion"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/59",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "repo pushed_at 2026-09-16, 12 days before today"},
      {"name": "Repository in use", "grade": "pass", "evidence": "commits on 2026-09-16 (x4) and 2026-08-24, within 180 days"},
      {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "fix one function _is_supported() in faithfulness_checker.py; bug fix, not a redesign"},
      {"name": "Issue has enough direction", "grade": "pass", "evidence": "gives concrete example (Knows Python vs python expert) and named failing test test_multiple_context_chunks"},
      {"name": "Not already being worked on", "grade": "pass", "evidence": "assignees: [], 0 comments, no linked/mentioned PRs found via search"},
      {"name": "Contribution policy allows this work", "grade": "pass", "evidence": "no CONTRIBUTING.md or AI policy file present (404 on all checked paths)"},
      {"name": "Helpful guidance", "grade": "pass", "evidence": "repro command plus concrete before/after scoring example"}
    ],
    "verdict": "accept"
  }
]

---
## Eval iterations

**Run history**

`agreement: 14/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)`

`agreement: 2/6 scored items`

`agreement: 2/4 scored items`

`agreement: 19/20 scored items  (bar: 18/20: PASS)`

**Issue analysis**

For `issue-12`, my rubric originally decided `accept`, while the gold label was `reject`. My rubric accepted it because the repository was active, the issue was clearly scoped, and there was no current assignee or open linked pull request. However, the repo-facts block included the statement, `"We do not accept AI-generated code or documentation."` My original rubric did not treat that contribution policy as a blocker, so I added a required contribution-policy check. After that change, `issue-12` was graded `reject`, which matched the gold label.

**Check rationale**

`| Contribution policy allows this work | Repo-facts block contribution policy and any contribution restrictions stated in the issue or comment thread. | Pass if the repository does not prohibit the contribution method required for this course work. Fail if the repository explicitly says it does not accept AI-generated code or documentation, reserves the work for maintainers, marks it internal-only, or otherwise states that normal outside contributors may not submit this work. | required |`

I added this check because my first full evaluation showed `policy 0/1`, which meant my rubric completely missed that category. The check makes contribution rules part of the decision instead of assuming that an active and clearly scoped issue is automatically acceptable for a first contribution.

**Trade-offs**

This check changed the result for `issue-12`. Before adding it, my rubric accepted the issue because it looked active, clear, and unclaimed. After adding the contribution-policy check, it was rejected because the repository explicitly stated that it does not accept AI-generated code or documentation. The trade-off is that an issue can look like a strong first contribution in every other way but still be rejected because of the repository's contribution rules.

---

## Selection rationale

**Selection rationale**

1. Issue #64 fits my interests because it focuses on testing and debugging, which are areas I already have experience with and want to improve. It also fits the time available because it is a small, clearly scoped issue that points to one failing test fixture instead of requiring a large architectural change.

2. The verdict correctly identified that the repository is active, the issue is small in scope, the problem has enough direction, and nobody is currently assigned to it. It also correctly recognized the exact failing test and reproduction command as useful guidance. One thing I weighed that the rubric could not was my personal preference for the testing and debugging work in #64, even though #26 was ranked higher by the skill.

3. I expect the claiming process to be fairly straightforward because the skill found no current assignee, no comments, and no linked or mentioned pull requests for #64. I will still need to follow the Unit 2 instructions for writing the correct claim comment before starting the work.