# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis matches reproduction | The candidate plan's stated cause or working hypothesis read against the repro-evidence block's observed behavior, expected behavior, and recorded outputs. | Pass if the diagnosis explains the reproduced behavior without contradicting the evidence. An uncertain cause can pass if identified as a hypothesis and the plan includes a way to investigate it. Fail if the plan ignores the reproduced behavior or claims a cause that the evidence contradicts. | required |
| Fix addresses the cause | The candidate plan's proposed implementation steps read against its diagnosis, the repro-evidence block, and the issue's expected behavior. | Pass if the proposed change directly addresses the supported cause or includes a step to determine the cause before selecting the fix. Fail if the approach only hides the observed symptom while leaving the identified underlying problem unresolved, or would not produce the expected behavior. | required |
| Scope is bounded | The candidate plan's proposed changes, in-scope and out-of-scope statements, and named files or components read against the issue context and acceptance criteria. | Pass if the proposed work stays focused on resolving the issue and any directly necessary supporting changes. Fail if it introduces unrelated features, unnecessary rewrites, or work beyond the issue's requirements without justification. An explicit out-of-scope section is not required when the boundaries are otherwise clear. | required |
| Implementation is executable | The candidate plan's implementation steps, files or components to change, and proposed approach read against the issue context and repo-facts block. | Pass if another developer familiar with the project could identify where to start and follow the major implementation steps without guessing a material action or design decision. Fail if essential steps, affected components, or technical decisions are missing or conflict with the available repository information. | required |
| Test verifies the fix | The candidate plan's test steps and expected results read against the repro-evidence block's original steps, observed outputs, and the issue's expected behavior. | Pass if the proposed verification exercises the reported failure through the relevant code path and identifies an observable result that distinguishes the original failure from the corrected behavior. Fail if the plan only says to run tests, provides unrelated tests, or gives no way to determine whether the issue was resolved. | required |
| Claims match evidence | The candidate plan's statements about confirmed causes, completed work, test results, risks, and unknowns read against the repro-evidence block and issue context. | Pass if the plan distinguishes observed facts from assumptions and does not claim successful implementation or verification without supporting evidence. Fail if an important unknown is presented as confirmed or a claim about the issue contradicts the available evidence. | required |
| Comment addresses the thread | The candidate plan comment read against the issue context, thread highlights, and relevant maintainer instructions or feedback. | Pass if the comment identifies the specific issue, communicates the intended approach, and follows any applicable maintainer direction. If no relevant maintainer direction exists, a specific and accurate summary of the proposed work passes. Fail if the comment is generic, ignores a relevant maintainer request, or proposes work that conflicts with an explicit thread restriction. | required |
| Repository conventions followed | The candidate plan comment and proposed approach read against the repo-facts block's contribution policy, templates, communication requirements, and AI-use disclosure rules. | Pass if the comment and approach comply with all applicable stated requirements, including required disclosures or restrictions on AI-assisted contributions. Fail if they violate an explicit requirement or omit a required disclosure. When the repository states no applicable requirement, do not fail for its absence. | required |
| Risks and limitations identified | The candidate plan's assumptions, risks, unknowns, and proposed implementation steps read against the issue context and repro-evidence block. | Pass if material uncertainties or implementation risks are acknowledged with a reasonable way to investigate or handle them, or if the available evidence establishes no material unresolved risk. Fail if a material risk is apparent but the plan provides no way to address it. | preferred |
| Regression coverage | The candidate plan's test steps read against the repro-evidence block, issue acceptance criteria, and any existing tests identified in the repo-facts block. | Pass if the test plan includes a relevant regression check or explains how the corrected behavior will remain covered by an existing test. Fail if it verifies only the immediate change without any regression coverage. | preferred |

## Verdict rule

Grade every check as `pass`, `fail`, or `unclear` using only the evidence available in the package.

- **Pass:** The evidence satisfies the check's stated pass condition.
- **Fail:** The evidence shows that the pass condition is not satisfied.
- **Unclear:** The available evidence is insufficient to determine whether the pass condition is satisfied. Do not assume missing facts or retrieve additional evidence in eval mode.

Return `accept` only when every `required` check receives `pass`.

Return `reject` if any `required` check receives `fail` or `unclear`.

`preferred` checks should be evaluated and reported, but their grades never change the final verdict.

Every check must include a one-line evidence statement identifying the fact, result, or quote that determined its grade. Use the exact check names from the table in the output JSON.

Do not reject a plan based only on formatting, length, missing headings, or writing style when its content satisfies the required conditions.