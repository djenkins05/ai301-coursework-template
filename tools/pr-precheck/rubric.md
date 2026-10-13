
# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Changes match the plan | The plan-context block's scope pair, planned implementation steps, recorded deviations, and the candidate PR's changed files and diff. | Pass if every functional change in the diff is within the plan's stated scope or is explicitly covered by a recorded deviation. Fail if the diff includes an unplanned change that affects behavior, files, or functionality without a documented deviation. | required |
| Planned work is accounted for | The plan-context block's intended changes and deviations, compared against the candidate PR's diff and description. | Pass if each planned change is implemented or any omitted or incomplete portion is explicitly identified as a limitation, deferral, or recorded deviation. Fail if planned work is missing without explanation or the PR claims completion that the diff does not support. | required |
| Description matches the actual changes | The candidate PR's title and description compared with its unified diff and commit contents. | Pass if every substantive claim about implemented behavior is supported by the diff and the description does not conceal a material difference from the implementation. Fail if the description claims a fix, feature, or level of completion contradicted by the diff. | required |
| Reproduction evidence demonstrates the change | The plan-context block's test plan and reproduction steps, compared with the candidate PR's before-and-after test evidence. | Pass if the evidence identifies the behavior before the change, the expected behavior after the change, and an observable result showing whether the change addresses the issue. An openly disclosed remaining limitation does not automatically fail this check if the evidence accurately demonstrates the bounded change being submitted. Fail if the PR only claims success without observable results or does not test the behavior the plan intended to change. | required |
| Repository checks have visible results | The candidate PR's test-evidence section and the repo-facts block's required checks or testing instructions. | Pass if the evidence identifies the repository's applicable checks, shows which commands or checks were run, and records their outcomes. A failed check may pass this evidence check if its failure is explicitly identified, explained, and shown to be unrelated to the submitted change. Fail if required checks are omitted without a documented, verifiable reason, or results are asserted without supporting evidence. | required |
| Diff is focused and reviewable | The candidate PR's unified diff and commit list compared with the plan's allowed scope and deviations. | Pass if the diff contains the intended implementation and necessary supporting edits without unrelated formatting changes, debugging statements, generated files, dead code, or unrelated modifications that obscure review. Fail if avoidable unrelated changes or leftover debugging artifacts materially interfere with reviewing the intended fix. | required |
| Pull request follows the repository template | The repo-facts block's PR-template requirements compared with the candidate PR's description. In live mode, the repository's PR template and draft description. | Pass if every applicable required template section contains information addressing its stated purpose, or an explicit and justified "not applicable" response where permitted. Fail if a required section is missing, left as a placeholder, or filled with unrelated boilerplate. Do not require a particular description length or writing style. | required |
| AI-use disclosure follows repository policy | The repo-facts block's AI-use disclosure instructions or stated contribution policy compared with the candidate PR's disclosure section. In live mode, the repository's current stated policy and draft description. | Pass if the PR includes the disclosure required by the repository's stated policy, identifies AI assistance when used, or explicitly states no AI assistance when the policy requires that declaration. Fail if a required disclosure is missing, incomplete, contradicts available evidence, or ignores a stated disclosure requirement. Do not assume AI use without evidence. | required |
| Contribution instructions are followed | The repo-facts block's contribution instructions, required PR practices, and any explicit maintainer direction, compared with the candidate PR's commits, diff, and description. | Pass if the PR follows each applicable stated requirement and addresses explicit maintainer instructions, or documents an allowed exception. Fail if an applicable mandatory requirement is visibly violated or ignored. Do not invent requirements that are not present in the provided evidence. | required |
| PR explains the change for reviewers | The candidate PR's title and description, plan-context block, and test-evidence section. | Pass if a reviewer can identify the issue addressed, the actual change, how it was checked, and any material remaining limitation without having to infer those facts from unrelated content. Fail if one or more of these facts cannot be determined from the supplied package. Do not grade on word count, tone, or formatting preferences. | preferred |

## Verdict rule

Grade every check as `pass`, `fail`, or `unclear` based only on the evidence and pass condition in its row.

- **pass:** The available evidence satisfies the stated pass condition.
- **fail:** The available evidence contradicts the pass condition or demonstrates that a required element is missing.
- **unclear:** The available evidence is insufficient to determine whether the pass condition is satisfied.

Return `accept` only when every required check receives `pass`.

Return `reject` if any required check receives `fail` or `unclear`. Treat `unclear` as a failure for verdict assembly because an unverifiable claim does not establish submission readiness.

Preferred checks must still be evaluated and reported, but their grades never change the final verdict.

Evaluate every check even when an earlier required check fails. Do not stop at the first failure.

For each check, record one concise evidence line identifying the specific fact, quoted statement, missing artifact, or contradiction that determined its grade. Never use unsupported descriptions such as "looks good" or "seems incomplete."

When multiple required checks fail, identify the first failing required check in table order as the deciding check in the readable summary. Include every check and its individual evidence in the final JSON output.

An honestly disclosed limitation, deferred edge case, or recorded plan deviation is not an automatic reason to reject. Evaluate whether the actual work, evidence, and disclosure satisfy the specific checks above. However, disclosure alone does not replace missing evidence or excuse an independently violated repository requirement.

Apply the same checks and verdict rule in live mode and eval mode. In eval mode, use only the supplied package. Do not fetch external information, assume missing requirements, or invent evidence.

The only final verdicts are `accept` and `reject`. Do not return a numerical score or a third verdict.
