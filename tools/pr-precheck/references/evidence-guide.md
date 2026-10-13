
# Evidence guide: where evidence lives in a PR package

## Evidence boundaries

In eval mode, use only the information provided in the package bundle, including the issue context, plan-context block, repo-facts block, candidate PR title, description, commits, diff, and test evidence. Do not retrieve outside evidence or assume missing information exists elsewhere.

In live mode, use the student's posted plan.md and recorded deviations, branch diff, draft PR title and description, test results, issue thread, and relevant repository documentation. Read scope.md first to confirm that the PR targets the allowed repository. For a house-chain student, use the house plan and reproduction evidence provided for that issue.

Use the evidence sources below to evaluate the checks in rubric.md. Do not treat an unstated repository requirement as mandatory or accept unsupported claims as proof.

## Plan fidelity (harness category: silent-drift)

**Where it lives:**

In eval mode, read the plan-context block's scope pair, implementation steps, expected behavior, and recorded deviations. Compare these with the candidate PR's unified diff, changed files, commits, title, and description. Use the issue context to confirm the intended behavior.

In live mode, read the student's posted plan.md, including any deviations, and compare it with the complete branch diff using `git diff main...HEAD` when the default branch is main. Review the issue description and relevant maintainer comments to identify the intended scope.

**What good looks like:**

Every functional change in the diff falls within the plan's stated scope or is covered by a recorded deviation. Each planned change is implemented, or any incomplete portion is explicitly identified as a limitation, deferral, or documented deviation.

The PR title and description accurately describe the changes shown in the diff. They do not claim that functionality was implemented or verified when the available evidence does not support that claim.

An honestly disclosed limitation or recorded deviation can be acceptable. A PR should not silently introduce unrelated work, omit planned changes without explanation, or claim completion that the diff contradicts.

**Related rubric checks:**

- Changes match the plan
- Planned work is accounted for
- Description matches the actual changes

## Test evidence (harness category: not-tested)

**Where it lives:**

In eval mode, read the plan-context block's test plan and reproduction steps. Compare these with the candidate PR's test-evidence section, including before-and-after results, executed commands, and recorded outputs. Read the repo-facts block to identify applicable repository testing requirements.

In live mode, compare the student's posted reproduction evidence and plan.md test plan with the captured before-and-after test results. Review the repository's testing instructions and applicable test suite to determine which checks should be executed.

**What good looks like:**

The PR identifies the original failure, explains the expected corrected behavior, and provides observable test results showing what happened before and after the implementation.

The test evidence must exercise the behavior described in the issue rather than an unrelated code path. Another developer should be able to identify what was tested and determine whether the observed result supports the claimed change.

Applicable repository checks are identified, and their execution outcomes are visible. An honestly reported failed check does not automatically invalidate the intended fix when the evidence establishes that the failure is unrelated to the change.

Statements such as "tests pass" or "the issue is fixed" are not sufficient without observable results or supporting evidence.

**Related rubric checks:**

- Reproduction evidence demonstrates the change
- Repository checks have visible results

## Diff quality (harness category: unreviewable)

**Where it lives:**

In eval mode, inspect the candidate PR's unified diff, changed-file list, and commit list. Compare the changes with the plan-context block's intended implementation, scope boundaries, and recorded deviations.

In live mode, inspect the complete branch diff using `git diff main...HEAD` when the default branch is main. Review the changed files and commit history to determine whether the implementation contains only the intended fix and necessary supporting changes.

**What good looks like:**

The diff contains the intended implementation and necessary supporting edits without unrelated changes that materially interfere with review.

A reviewer can identify the code responsible for the fix and determine how it addresses the issue. The changes remain focused on the plan and any recorded deviations.

Debugging statements, unrelated formatting changes, dead code, commented-out experiments, temporary files, and unnecessary generated artifacts should not remain when they obscure the intended change.

A change is not rejected simply because it modifies multiple files or requires supporting edits. The decision depends on whether those changes are related to the plan and remain reviewable.

**Related rubric checks:**

- Diff is focused and reviewable

## Standards and comms (harness category: standards-wall)

**Where it lives:**

In eval mode, read the repo-facts block's PR template requirements, contribution instructions, stated policies, AI-use disclosure requirements, and relevant maintainer directions. Compare these with the candidate PR's title, description, disclosure section, commits, and other supplied evidence.

In live mode, read the repository's PR template, CONTRIBUTING.md, any applicable AI-use policy such as AI_POLICY.md or AI_USAGE_POLICY.md, and relevant maintainer instructions in the issue thread.

Compare the draft PR title and description with the repository's stated requirements. Also read voice-guide.md and record any communication rules the outgoing PR text violates.

**What good looks like:**

The PR follows all applicable repository contribution requirements and explicit maintainer instructions. Every required PR template section contains information addressing its purpose, or a justified not-applicable response when the repository permits one.

When the repository requires AI-use disclosure, the PR provides the information requested by that policy. Do not assume AI assistance was used without supporting evidence, and do not invent disclosure requirements that the repository has not stated.

The PR title and description identify the issue being addressed, summarize the actual changes, report relevant test results, and disclose material limitations when applicable.

A concise PR can pass when its content satisfies the requirements. Do not reject a PR based only on its length, formatting, or writing style.

In live mode, report violations of voice-guide.md separately. A voice-guide violation does not change the verdict unless it also violates a rubric check.

**Related rubric checks:**

- Pull request follows the repository template
- AI-use disclosure follows repository policy
- Contribution instructions are followed
- PR explains the change for reviewers
