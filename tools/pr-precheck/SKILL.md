
---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

This tool answers one question about one pull request package: **Is this pull request ready to submit?**

A PR package includes the candidate pull request's title, description, commits, diff, and test evidence. These are evaluated against the issue being addressed, the implementation plan, any recorded deviations, and the repository's stated requirements.

The tool checks whether the implementation matches the plan, whether the test evidence supports the claimed results, whether the diff is reviewable, and whether the PR follows applicable repository standards.

Grade exactly one PR package per run. Do not grade multiple packages together or evaluate unrelated work. Apply the checks defined in `rubric.md` rather than relying on personal judgment.

## Inputs and modes

Identify the operating mode before evaluating the package.

**Live mode:**

Use live mode when reviewing the student's own pull request before submission.

Read the following inputs:

1. The student's posted `plan.md`, including the implementation steps, test plan, scope boundaries, and recorded deviations.
2. The student's branch diff containing every change relative to the repository's default branch. When the default branch is `main`, run `git diff main...HEAD` from the working copy to examine the complete diff.
3. The candidate PR title and draft description.
4. The student's test evidence, including original reproduction results, before-and-after behavior, executed test commands, and recorded outcomes.
5. The issue description, acceptance criteria, relevant issue-thread comments, and maintainer instructions.
6. The repository's stated requirements, including its PR template, contribution instructions, testing requirements, and AI-use disclosure policy.

For a house-chain student, read the supplied house plan and house reproduction package instead of the student's own plan and reproduction evidence. Apply the same rubric checks and verdict rule.

Gather issue-side and repository evidence from the actual scoped repository. Do not invent missing evidence or assume a requirement that the repository does not state.

**Eval mode:**

Use eval mode when the input is a supplied evaluation package bundle.

The bundle is the complete source of evidence. Read only the issue context, plan-context block, repo-facts block, candidate PR title, description, commits, diff, and test-evidence section contained in that bundle.

Do not search GitHub, fetch external information, inspect unrelated local files, or use personal knowledge to fill gaps in the package.

Evaluate every rubric check using the complete verdict rule. Do not skip checks because an earlier check failed. Use the bundle identifier as the output item.

## The scope seam (live mode only)

In live mode, read `scope.md` before examining or grading any other input.

Identify the repository specified by the `Repo:` line and confirm that the candidate PR targets that repository.

If the `Repo:` line still contains an unfilled placeholder, stop without grading and tell the student to replace it with their section's Path Review repository.

If the PR targets a repository outside the stated scope, refuse to grade it. Do not guess or substitute another repository.

Apply the Path Review house rules stated in `scope.md`, including opening the PR from the student's own fork and fix branch, implementing the posted plan for the assigned issue, and following the repository's PR template and contribution requirements.

In eval mode, ignore `scope.md` entirely. The evaluation bundle defines the available evidence.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` after confirming the repository is in scope.

Compare the candidate PR title and description with the communication rules in the voice guide.

Record specific violations, including unsupported claims, vague descriptions, unrealistic promises, missing explanations of limitations, or language that does not follow the student's stated writing rules.

Report any violated rule in the readable summary and identify the relevant text.

A voice-guide violation does not independently change the final verdict unless the same issue also fails a check in `rubric.md`.

In eval mode, ignore `voice-guide.md` entirely. Apply only the universal communication requirements defined in the rubric and supported by the bundle.

## Component reads

Read the tool components before grading the candidate PR.

1. Read `rubric.md` to identify the exact check names, evidence sources, pass conditions, weights, and final verdict rule.
2. Read `references/evidence-guide.md` to determine where each required fact can be found. Use its four evidence categories: plan fidelity, test evidence, diff quality, and standards and comms.
3. Read `procedure.md` and execute its read order, evidence-gathering steps, check execution, and verdict assembly instructions as written.

Use the rubric to decide what passes or fails, the evidence guide to locate relevant facts, and the procedure to determine how and when those facts are examined.

Do not invent additional checks, evidence sources, pass conditions, or grading steps during execution.

If the procedure does not explain how to handle a necessary step, report the gap rather than silently improvising a new process.

If `rubric.md` contains no student-authored checks or `procedure.md` contains no student-authored operating steps, refuse to grade. Explain which component is incomplete and instruct the student to complete it before running the tool.

Do not treat template comments as completed rubric or procedure content.

## Verdict and output

The tool returns one of two final verdicts:

- `accept`: The PR is ready to submit because every required rubric check passes.
- `reject`: The PR should be held because at least one required check fails or remains unclear.

There is no third verdict, numerical score, or "accept with reservations" outcome.

Before the final JSON block, provide a readable summary identifying the check results and the specific evidence supporting the verdict.

For a rejected package, identify the first failing or unclear required check in rubric order as the deciding check. Mention any additional failing checks separately.

For an accepted package, summarize the passing required checks and report preferred improvements separately.

End every completed grading response with the following fenced JSON block. Preserve the exact field names, order, and structure. Replace the placeholders with the evaluated PR URL or bundle identifier, actual check names, grades, evidence, and verdict.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

Include every rubric check in the `checks` array in the same order as `rubric.md`.

Use the PR URL in live mode and the bundle identifier in eval mode.

The JSON must be valid, enclosed in a fenced `json` block, and appear last in the response. Do not write anything after the closing fence.

## Grading discipline

**Evidence first:** Every check must identify the fact, result, missing artifact, or short quote that determined its grade. Do not assign grades using statements such as "looks good" or "seems correct."

**Grade the thing, not the polish:** Evaluate the actual implementation, diff, test results, plan fidelity, and stated repository requirements. Do not reject a complete PR because its description is short or its writing style differs from personal preferences.

**The rubric decides:** Apply the exact pass conditions in `rubric.md`. If a check passes according to its written condition, grade it as passing even when a different judgment feels more reasonable. Improvements belong in the rubric, not in an improvised decision.

**The procedure decides how:** Follow `procedure.md` in its stated order. Do not silently invent missing steps or substitute a different grading process.

**Unclear defaults to fail:** Assign `unclear` when the available evidence is insufficient to verify a check. Treat an unclear required check as a failure when assembling the verdict. If the rubric is silent about unclear grades, apply this same default.

**Honest reporting matters:** A disclosed limitation, deferred change, or recorded deviation is not an automatic failure. Compare the actual work with the plan and evaluate whether the available evidence satisfies each check. Disclosure does not replace required tests or excuse violations of repository policy.

**Complete every check:** Evaluate every rubric check before assembling the verdict, even if an earlier required check fails. Preferred checks are reported but never determine the final verdict.

**No unsupported assumptions:** In eval mode, use only the supplied bundle. In live mode, use only evidence from the allowed repository and the student's supplied materials. Do not invent test results, implementation details, maintainer instructions, or repository requirements.

