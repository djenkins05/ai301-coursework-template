
# Procedure: how this tool grades a PR package

## Read order

1. Identify whether the tool is running in live mode or eval mode. In eval mode, use only the supplied PR package bundle. Do not search GitHub, read local files outside the bundle, or retrieve external information. In live mode, read `scope.md` first and confirm that the pull request targets the repository named in its `Repo:` line. If the repository placeholder is unfilled, or the PR targets another repository, stop without grading. Then read `voice-guide.md` and record its communication rules.

2. Read `rubric.md` and `references/evidence-guide.md` before evaluating the package. Record the exact check names, evidence sources, pass conditions, weights, and verdict rule. Use the evidence guide to determine where each required fact should be found.

3. Read the issue context and repository requirements. Record the reported problem, expected behavior, acceptance criteria, relevant maintainer instructions, required PR template sections, contribution policies, and AI-use disclosure requirements. In eval mode, use the issue-context and repo-facts blocks. In live mode, use the actual issue thread and repository documentation. Do not invent requirements that are not stated.

4. Read the implementation plan before examining the diff or PR description. Record the plan's scope pair, intended implementation, affected files or components, scope boundaries, test plan, expected results, and any recorded deviations. Reading the plan first establishes what the implementation is supposed to deliver before examining what was actually changed.

5. Read the candidate PR's unified diff and commit list. In live mode, inspect the branch's complete changes relative to the repository's default branch using `git diff main...HEAD` when the default branch is `main`. Record every changed file, the functional changes, supporting edits, and any unrelated modifications or debugging leftovers. Compare the changes against the plan and its recorded deviations.

6. Read the candidate PR's test evidence. Record the original reproduction steps, observed behavior before the fix, expected behavior after the fix, test commands, actual results, and the outcomes of the repository's required checks. Compare the evidence with the plan's test plan and the issue's expected behavior.

7. Read the candidate PR's title and description last. Compare its claims with the actual diff, recorded test results, plan, and repository requirements. Record whether the description accurately identifies the implemented work, documented deviations, remaining limitations, testing results, template requirements, and AI-use disclosure. In live mode, also compare the title and description with `voice-guide.md`.

8. Do not begin assigning grades until the relevant evidence has been gathered. Keep the evidence organized under the exact check names from `rubric.md`.

## Evidence gathering

1. **Changes match the plan:** Locate the plan's intended changes, affected files, scope boundaries, and recorded deviations. Compare them with the candidate PR's unified diff and changed-file list. Record whether every functional change is planned or covered by a documented deviation. Identify any unplanned behavior or unrelated change.

2. **Planned work is accounted for:** Compare each major implementation step and expected outcome in the plan with the actual diff. Record which portions were completed and whether any omitted or incomplete work is explicitly identified as a limitation, deferral, or recorded deviation. Do not treat an honestly disclosed limitation as an automatic failure.

3. **Description matches the actual changes:** Compare the PR title and description with the diff and commit contents. Record every substantive claim about the fix or implementation and whether the changed code supports that claim. Identify contradictions, overstated completion, or material changes not acknowledged in the description.

4. **Reproduction evidence demonstrates the change:** Locate the plan's test steps and original reproduction evidence. Compare them with the candidate PR's before-and-after results. Record the behavior before the change, the expected corrected behavior, the actual observed result, and whether the tested code path addresses the reported issue. Do not accept unsupported statements such as "fixed" or "tests pass" as observable evidence.

5. **Repository checks have visible results:** Locate the repository's stated testing requirements in the repo-facts block or live repository documentation. Compare them with the PR's test-evidence section. Record the applicable check commands, which checks were executed, their outcomes, and any disclosed failures or omissions. For failed checks, record whether the evidence establishes that the failure is unrelated to the submitted change.

6. **Diff is focused and reviewable:** Examine the unified diff and commit list. Compare changed files and hunks with the plan's scope and recorded deviations. Record unrelated formatting changes, debugging statements, generated artifacts, dead code, commented-out code, or unrelated modifications. Determine whether these changes materially interfere with reviewing the intended fix.

7. **Pull request follows the repository template:** Locate the required PR template sections in the repo-facts block or live repository template. Compare each applicable section with the candidate PR's description. Record missing sections, unfilled placeholders, unrelated boilerplate, and justified not-applicable responses where permitted.

8. **AI-use disclosure follows repository policy:** Locate the repository's stated AI-use disclosure requirements in the repo-facts block or live contribution documentation. Compare those requirements with the PR's disclosure section. Record whether the required disclosure is present and whether it addresses the stated policy. Do not assume AI assistance was used without evidence.

9. **Contribution instructions are followed:** Locate the repository's stated contribution requirements and any explicit maintainer instructions. Compare them with the PR's commits, diff, branch information, and description. Record whether each applicable mandatory requirement is satisfied or whether an allowed exception is documented. Do not introduce requirements not found in the supplied evidence.

10. **PR explains the change for reviewers:** Examine the title, description, plan context, and test evidence. Record whether a reviewer can identify the issue addressed, actual implementation, verification performed, and any material remaining limitation. Judge whether this information is available, not the length or formatting of the description.

11. Keep the evidence organized by rubric check. For every check, record the specific fact, result, missing artifact, or short quote supporting its grade. If two sources conflict, record the contradiction rather than assuming one is correct. In eval mode, do not use information outside the bundle.

## Check execution

1. Execute every check in the exact order it appears in `rubric.md`. Use the evidence gathered for each check. Revisit the relevant source only when necessary to resolve a missed detail or conflict.

2. Grade **Changes match the plan** by comparing all functional changes in the diff with the planned scope and recorded deviations. Grade **Planned work is accounted for** by verifying that planned work is implemented or that omitted work is explicitly disclosed.

3. Grade **Description matches the actual changes** by comparing the PR's claims with the changed code and commits. Fail claims about implemented functionality that the diff contradicts.

4. Grade **Reproduction evidence demonstrates the change** by checking that the evidence identifies the original behavior and shows an observable result for the intended change. Grade **Repository checks have visible results** by comparing the executed checks and recorded outcomes with the repository's stated requirements.

5. Grade **Diff is focused and reviewable** by inspecting changed files and hunks for unrelated work or leftover artifacts that materially obscure the implementation.

6. Grade **Pull request follows the repository template** by checking each applicable required section. Grade **AI-use disclosure follows repository policy** by applying the repository's stated disclosure requirements. Grade **Contribution instructions are followed** by checking applicable mandatory contribution rules and maintainer instructions.

7. Grade **PR explains the change for reviewers** by determining whether the provided title, description, and evidence identify the issue, implementation, verification, and material limitations without requiring unsupported assumptions.

8. Assign `pass` when the available evidence satisfies the check's pass condition. Assign `fail` when the evidence contradicts the condition or demonstrates a missing mandatory element. Assign `unclear` when the evidence is insufficient to determine the result. Do not invent evidence, additional checks, or requirements.

9. For every check, record a one-line evidence statement identifying the specific fact, quote, result, or missing evidence that determined the grade. Apply the rubric's exact pass condition even when a different outcome seems preferable.

10. Evaluate every check before assembling the verdict. A failed required check does not end the evaluation early. Preferred checks must also be graded even though they do not determine acceptance.

11. Treat documented deviations, disclosed limitations, and deferred work according to the rubric's stated conditions. An honest disclosure is not automatically a failure, but disclosure alone does not replace required verification or excuse a separate mandatory requirement.

## Verdict assembly

1. Review every completed check and its weight in `rubric.md`. Confirm that each check has exactly one grade of `pass`, `fail`, or `unclear` and a one-line evidence statement.

2. Return `accept` only when every required check receives `pass`. Return `reject` when at least one required check receives `fail` or `unclear`. Preferred checks do not affect the final verdict.

3. If multiple required checks fail or are unclear, select the first failing or unclear required check in rubric order as the deciding check. Quote its specific evidence in the readable summary. Report the remaining failing checks separately.

4. For an accepted package, summarize why the required checks passed and mention preferred improvements separately. Do not change an accepted verdict based only on a preferred check.

5. In live mode, report any violations of `voice-guide.md` in the readable summary and identify the specific rule involved. A voice-guide violation does not change the verdict unless a rubric check independently fails.

6. Produce the output using the exact check names and order from `rubric.md`. Every check must include its grade and a one-line evidence statement. Use the pull request URL in live mode or the bundle identifier in eval mode for the `item` field.

7. End the response with a valid fenced JSON block using this structure:

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

8. Include every rubric check in the `checks` array, not just the example entry. Use only `accept` or `reject` as the final verdict. The JSON block must be the last content in the response, with nothing written after it.
