# Procedure: how this skill grades a plan package

## Read order

1. Identify whether the package is being graded in eval mode or live mode. In eval mode, use only the supplied package bundle. Do not search GitHub or retrieve outside information. In live mode, read `scope.md` first and confirm the issue belongs to the allowed repository. If the scope is missing or contains an unfilled repository placeholder, stop without grading. Then read `voice-guide.md` and record its communication rules.

2. Read `rubric.md` and `references/evidence-guide.md` before evaluating the package. Record the exact check names, evidence sources, pass conditions, weights, and verdict rule. Use the evidence guide to determine where each required fact should be found.

3. Read the issue context first. Record the reported problem, expected behavior, acceptance criteria, affected components, and relevant maintainer instructions. This establishes what the plan is supposed to resolve before considering the proposed solution.

4. Read the reproduction evidence next. Record the environment when relevant, reproduction steps, observed behavior, expected behavior, and any outputs or artifacts supporting the result. Note whether the issue was successfully reproduced or whether the evidence shows a documented unsuccessful attempt. In live mode, use the student's posted repro comment. For the house issue, use only the reproduction evidence quoted in the drafts.

5. Read the repo-facts block in eval mode or the relevant repository documentation in live mode. Record applicable contribution policies, templates, testing conventions, communication requirements, and AI-use disclosure rules. Do not treat an unstated requirement as mandatory.

6. Read the candidate plan after the issue and reproduction evidence. Record its diagnosis, proposed implementation, affected files or components, scope boundaries, implementation steps, tests, expected results, assumptions, and risks. Reading the evidence first helps prevent the proposed explanation from influencing the interpretation of the original failure.

7. Read the candidate plan comment last. Compare its proposed approach with the plan, issue thread, maintainer feedback, and applicable repository conventions. In live mode, also compare the comment with the rules in `voice-guide.md`. Do not begin grading until these sources have been reviewed.

## Evidence gathering

1. **Diagnosis and grounding:** Locate the candidate plan's stated cause or working hypothesis. Compare it with the repro-evidence block's observed behavior and outputs. Record whether the diagnosis explains the reported behavior and whether the proposed fix addresses that diagnosis rather than only hiding the symptom. If the cause is uncertain, record whether the plan includes a step to investigate it.

2. **Scope:** Locate the plan's proposed changes, named files or components, and any in-scope or out-of-scope statements. Compare these with the issue's acceptance criteria and maintainer restrictions. Record whether each major change is necessary to resolve the issue or introduces unrelated work. Do not require a separate scope heading when the boundaries are clear from the content.

3. **Executability:** Locate the plan's implementation steps, affected code areas, and order of work. Compare these with the issue context and available repository facts. Record the starting point, major actions, and any material dependency or design decision another developer would otherwise need to guess.

4. **Test plan:** Locate the plan's proposed test commands, test cases, verification steps, and expected outcomes. Compare them with the original reproduction steps and observed outputs. Record which check exercises the reported failure, what result is expected after the fix, and whether any relevant regression coverage is included. A test must distinguish the original failure from the corrected behavior.

5. **Honesty:** Compare the plan's claims with the reproduction evidence and issue context. Record statements presented as confirmed findings, unresolved assumptions, risks, and limitations. Check whether the evidence supports those statements. In live mode, if the plan has been updated after implementation began, examine its deviation notes and record what changed and why.

6. **Comms:** Compare the candidate plan comment with the issue description and thread highlights in eval mode, or the live issue thread in live mode. Record any relevant maintainer instructions and whether the comment follows them. Then compare the comment and proposed approach with the repo-facts block or live contribution documentation. Record any applicable template, communication, or AI-use disclosure requirements and whether they are satisfied. If no applicable requirement is stated, record that no restriction was found rather than assuming one exists.

7. Keep the gathered evidence organized under the corresponding rubric check names. For each check, record the specific fact, result, or short quote that will support its grade. Do not fill gaps with assumptions. In eval mode, do not use information outside the package bundle.

## Check execution

1. Execute every check in the order it appears in `rubric.md`. Use the evidence already gathered for that check. Revisit the relevant source only when a necessary detail was missed or conflicting evidence needs to be resolved.

2. Grade **Diagnosis matches reproduction** by comparing the stated cause or hypothesis with the recorded reproduction behavior. Grade **Fix addresses the cause** by determining whether the proposed implementation addresses the supported cause or includes an investigation step before choosing the fix.

3. Grade **Scope is bounded** by comparing the proposed changes with the issue's requirements. Grade **Implementation is executable** by determining whether another developer could identify where to start and follow the major steps without guessing a material action or decision.

4. Grade **Test verifies the fix** by checking whether the proposed verification exercises the relevant code path and identifies an observable corrected result. Grade **Claims match evidence** by comparing the plan's statements with what the available evidence actually establishes.

5. Grade **Comment addresses the thread** by checking whether the plan comment identifies the issue, communicates the intended work, and follows relevant maintainer instructions. Grade **Repository conventions followed** by checking compliance with applicable contribution, template, communication, and AI-use requirements.

6. Grade **Risks and limitations identified** by examining whether material uncertainties have been acknowledged or addressed. Grade **Regression coverage** by examining whether the plan includes a relevant regression check or identifies existing coverage for the corrected behavior.

7. Assign `pass` when the evidence satisfies the check's stated pass condition. Assign `fail` when the evidence shows the condition is not satisfied. Assign `unclear` when the necessary evidence is missing or insufficient to decide. Do not invent missing information or automatically interpret silence as a violation when the rubric explicitly allows an unstated requirement.

8. For every grade, record a one-line evidence statement identifying the fact or quote that determined the result. Apply the rubric's pass condition as written, even when a different judgment feels more reasonable. Do not add new requirements during grading.

9. Complete all checks before determining the final verdict. A failed required check does not end the evaluation early. Preferred checks must also receive grades, even though they do not determine acceptance.

## Verdict assembly

1. Review the completed check results and their weights in `rubric.md`. Confirm that every check has a grade of `pass`, `fail`, or `unclear` and a supporting evidence statement.

2. Return `accept` only if every `required` check receives `pass`. Return `reject` if any required check receives `fail` or `unclear`. Preferred check results do not change the verdict.

3. For a rejected package, identify the failed or unclear required checks in the readable summary and explain the deciding evidence. For an accepted package, summarize the required checks that passed and mention any preferred improvements separately.

4. In live mode, report any violations of `voice-guide.md` in the readable summary and quote the specific voice rule involved. Do not change the verdict based only on a voice-guide violation unless a rubric check independently fails.

5. Produce the output using the exact check names and order from `rubric.md`. Each check must include its grade and a one-line evidence statement. Use the issue URL in live mode or the bundle identifier in eval mode for the `item` field.

6. End with a valid fenced JSON block using this structure:

```json
{
  "item": "<issue URL or bundle id>",
  "checks": [
    {
      "name": "<exact rubric check name>",
      "grade": "pass",
      "evidence": "<specific supporting fact or quote>"
    }
  ],
  "verdict": "accept"
}
```

7. Include every rubric check in the `checks` array, not just the example entry. Use only `accept` or `reject` for the final verdict. The JSON block must be the last content in the output, with nothing written after it.