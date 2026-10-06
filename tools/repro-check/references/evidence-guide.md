# Evidence guide: where proof lives in a reproduction package

## Environment

**Where it lives:**
In eval mode, look in the repro report for the stated operating system, runtime or language version, dependency versions, project version or commit, configuration, and any setup details that affect the reproduction attempt. Read these against the issue context and the repo-facts block to determine which environment details matter for the reported behavior.

In live mode, look at the issue thread for the environment the reporter used, the repository documentation for supported versions or setup requirements, and the student's draft repro comment for the environment they actually tested.

**What good looks like:**
The report identifies enough of the relevant environment for another person to understand and repeat the attempt. If the tested environment differs from the one named in the issue, the difference is stated clearly enough that a reader can judge whether it may affect the result.

## Steps

**Where it lives:**
In eval mode, look in the repro report for the starting state, setup actions, commands, inputs, configuration changes, and sequence of actions used to trigger the reported behavior. Read these against prerequisites or setup requirements stated in the issue context and repo-facts block.

In live mode, compare the issue's reported reproduction steps and repository setup instructions with the steps written in the student's draft repro comment.

**What good looks like:**
A stranger with access to the project should be able to follow the attempt from the stated starting condition to the observed result without guessing a material command, input, prerequisite, or action. Missing details fail only when they could change or prevent the outcome.

## Behavior shown

**Where it lives:**
In eval mode, look at the repro report's recorded artifacts, including terminal output, error messages, logs, return values, screenshots described in the bundle, or other observed results. Compare those artifacts directly with the expected and actual behavior described in the issue context.

In live mode, compare the evidence included in the student's draft repro comment with the behavior described in the issue thread.

**What good looks like:**
The evidence shows the same behavior the issue reports, rather than a related error, different failure, or nearby problem. A cannot-reproduce result can also pass when the evidence clearly shows what happened instead under the documented attempt.

## Honesty

**Where it lives:**
In eval mode, compare the repro report's stated conclusion with its environment, steps, and observed artifacts. Pay attention to statements such as "reproduced," "confirmed," "could not reproduce," or claims about the cause.

In live mode, compare the wording in the student's draft repro comment with the results they actually recorded.

**What good looks like:**
The conclusion says only what the evidence supports. A successful reproduction is backed by evidence of the reported behavior. A cannot-reproduce result is backed by a meaningful documented attempt. Possible causes are not presented as confirmed unless the evidence establishes them.

## Comms

**Where it lives:**
In eval mode, read the claim comment against the issue title, description, and thread highlights. Read both the claim comment and repro report against the repo-facts block, especially the repository's bug-report requirements, contribution policy, communication rules, templates, and any AI-use or disclosure requirements.

In live mode, read the issue thread, `CONTRIBUTING.md`, contributor documentation, issue or pull-request templates, and any dedicated AI-use policy such as `AI_POLICY.md` or `AI_USAGE_POLICY.md`. Compare those rules with the student's draft claim and repro comments.

**What good looks like:**
The claim identifies the specific issue or behavior being investigated instead of using generic boilerplate. The comments do not promise an unsupported fix or deadline. They satisfy applicable repository requirements, including required AI-use disclosure or other contribution conditions. If the repository states no such requirement, silence is not treated as a failure. The repro comment should describe the student's own evidence rather than relying on another person's reproduction.

