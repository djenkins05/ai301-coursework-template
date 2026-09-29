# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | Repo-facts block: recent default-branch commit dates and recent maintainer issue or pull request activity. | Pass if the repository has at least one default-branch commit or maintainer issue/pull request activity within the last 90 days. | required |
| Repository in use | Repo-facts block: the last 5 default-branch commit dates and recent issue or pull request activity. | Pass if at least 2 of the last 5 default-branch commits happened within the last 180 days, or there has been maintainer issue/pull request activity within the last 90 days. | required |
| Newcomer-sized scope | Issue body and comment thread: the required change, explicitly required behaviors, architecture changes, migrations, refactors, and major components involved. | Pass if the required work is one focused bug fix or feature and does not explicitly require a repository-wide refactor, major architectural redesign, data migration, or broad coordinated change across many unrelated components. Treat text labeled as suggestions, optional ideas, possible causes, "perhaps", "could", or "nice to have" as non-required unless the issue explicitly says those items must all be completed. | required |
| Issue has enough direction | Issue body and comment thread: title, problem statement, requested behavior, concrete examples, reproduction steps, expected behavior, acceptance criteria, or maintainer clarification. | Pass if the issue title or body identifies at least one concrete bug, missing feature, requested behavior, or specific example of work to perform. A list of concrete missing items or examples counts as enough direction even if the issue does not include reproduction steps, implementation instructions, or formal acceptance criteria. | required |
| Not already being worked on | Repo-facts block for assignees and linked pull requests, plus the chronological issue comment thread for claim, assignment, work-in-progress, release, abandonment, or unassign statements. | Pass only if there is no current assignee, no open linked pull request, and no contributor claim or statement that they are working on the issue that remains unresolved in the provided evidence. Treat each claim as active unless a later comment explicitly says that contributor was unassigned, released the issue, abandoned the work, or finished it. If the final claim/work-in-progress statement in the provided thread has no later release or unassign statement, fail this check even if the repo-facts block currently lists no assignee. In Path Review live mode, ignore student claim comments according to the house rule in `scope.md`. | required |
| Contribution policy allows this work | Repo-facts block contribution policy and any contribution restrictions stated in the issue or comment thread. | Pass if the repository does not prohibit the contribution method required for this course work. Fail if the repository explicitly says it does not accept AI-generated code or documentation, reserves the work for maintainers, marks it internal-only, or otherwise states that normal outside contributors may not submit this work. | required |
| Helpful guidance | Issue body and comment thread. | Pass if the issue includes at least one of the following: reproduction steps, file or component names, expected behavior, acceptance criteria, example output, concrete examples, or maintainer implementation guidance. | preferred |

## Verdict rule

Accept an issue only if every required check passes.

Preferred checks never change the accept or reject verdict. They are only used to help rank issues that already passed all required checks.

If a required check is graded `unclear`, treat it as a fail and reject the issue because there is not enough evidence to confirm that it is a good first contribution.
