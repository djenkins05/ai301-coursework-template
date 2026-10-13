# Evidence guide: where evidence lives in a plan package

## Evidence boundaries

In eval mode, use only the information provided in the package bundle, including the issue context, repo-facts block, repro-evidence block, candidate plan, and candidate plan comment. Do not retrieve outside evidence.

In live mode, use the student's draft plan and plan comment, the issue thread, the student's posted reproduction evidence, and relevant repository documentation. For the house issue, use the reproduction evidence quoted in the drafts. Do not assume missing evidence exists elsewhere.

## Diagnosis and grounding

**Where it lives:**

In eval mode, look at the candidate plan's explanation of the issue, suspected cause, and proposed fix. Compare these claims with the issue context and repro-evidence block, including the reproduction steps, observed behavior, expected behavior, and recorded outputs.

In live mode, compare the diagnosis in the student's draft plan with the issue description, issue thread, and evidence from the student's posted reproduction comment.

**What good looks like:**

The plan identifies a cause or working hypothesis that explains the behavior shown in the reproduction evidence. The diagnosis should not contradict the recorded results or treat an unverified assumption as a confirmed cause. If the cause is uncertain, the plan should explain how it will be investigated.

## Scope

**Where it lives:**

In eval mode, look at the candidate plan's in-scope and out-of-scope statements, proposed changes, and named files or components. Compare these against the issue's requested behavior, acceptance criteria, and any restrictions mentioned in the issue context or repo-facts block.

In live mode, compare the student's draft plan with the issue description, maintainer comments, and relevant repository structure to determine whether the proposed changes stay within the issue's boundaries.

**What good looks like:**

The plan defines a focused set of changes that directly addresses the reported issue without introducing unrelated features or unnecessary rewrites. It identifies what will and will not be changed clearly enough for a reader to recognize work that falls outside the plan.

## Executability

**Where it lives:**

In eval mode, look at the candidate plan's implementation steps, named files or areas, proposed approach, and order of work. Compare these details with the issue context and repo-facts block to check whether the proposed steps fit the repository.

In live mode, look at the student's draft plan, relevant source files, repository structure, and contribution documentation to determine whether another developer could follow the proposed approach.

**What good looks like:**

The plan identifies the files or components to investigate or modify and explains the implementation steps in an order another developer could follow. A stranger familiar with the project should be able to begin implementing the change without guessing a major step, required dependency, or design decision.

## Test plan

**Where it lives:**

In eval mode, look at the candidate plan's test steps, expected results, and proposed verification commands or checks. Compare these with the repro-evidence block's reproduction steps, observed outputs, and the issue's expected behavior.

In live mode, compare the student's draft test plan with their posted reproduction evidence, the repository's existing tests, and any testing instructions in the project documentation.

**What good looks like:**

The plan identifies a specific test or verification step that demonstrates whether the original issue has been resolved. It explains what result should change after the fix and includes enough detail to repeat the check. When applicable, it also identifies relevant regression tests to confirm the change does not break existing behavior.

## Honesty

**Where it lives:**

In eval mode, compare the candidate plan's claims about the cause, implementation, and expected outcome with the issue context, repro-evidence block, and any stated risks or unknowns. Look for assumptions presented as facts or claims that go beyond the available evidence.

In live mode, compare the student's draft plan and plan comment with their posted reproduction evidence, issue discussion, and stated implementation limitations. If the plan has been updated after implementation began, review the deviation notes in `plan.md` to determine whether changes from the original approach are explained. Do not rely on unquoted working-directory files or implementation changes outside the plan package.

**What good looks like:**

The plan distinguishes confirmed findings from assumptions and acknowledges uncertainties that could affect the implementation. It does not claim a fix has been tested or proven before evidence exists. If the implementation changes direction, the deviation notes explain what changed and why rather than presenting the original plan as if it was followed exactly.

## Comms

**Where it lives:**

In eval mode, read the candidate plan and plan comment against the issue description, thread highlights, and maintainer feedback. Compare the comment with the repo-facts block, especially contribution requirements, communication expectations, templates, and AI-use disclosure policies.

In live mode, read the issue thread, the student's draft plan comment, `CONTRIBUTING.md`, repository contribution documentation, issue or pull-request templates, and any dedicated AI-use policies such as `AI_POLICY.md` or `AI_USAGE_POLICY.md`.

**What good looks like:**

The plan comment identifies the specific issue, summarizes the proposed approach, and addresses relevant maintainer feedback instead of using generic boilerplate. It follows applicable repository communication and contribution requirements, including AI-use disclosure when required. The comment should not promise an unsupported outcome or deadline, and the proposed work should not contradict restrictions stated by maintainers. If the repository does not specify a particular requirement, its absence should not be treated as a failure.
