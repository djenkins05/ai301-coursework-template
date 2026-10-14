# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-howard/pull/80

**Branch**

fix/64-partial-overlap-fixture


## Eval iterations

**Run history**

I completed two full evaluation runs using my `pr-precheck` tool and the pinned Sonnet model.

- **Run 1:** 20/20 agreement with the gold labels. All five evaluation categories passed: clear-accept (7/7), not-tested (4/4), silent-drift (4/4), standards-wall (2/2), and unreviewable (3/3).
- **Run 2:** 20/20 agreement with the gold labels. I used `--save-run eval-run.txt` to generate the final evaluation artifact. The second run matched the first, so I did not make any changes to my tool files between the runs.

**Package analysis**

I selected `pkg-20` from the standards-wall category. My rubric returned `reject`, which matched the gold label of `reject`. My rubric checks whether a pull request follows the repository's required template, AI-use disclosure policy, and contribution instructions. This package was classified as a standards-wall rejection, and my rubric correctly identified it as not ready to submit.

Since my rubric achieved 20/20 agreement with the gold labels across all categories, I did not identify any improvements that needed to be made.
**Check rationale**

I included the following required check in my rubric:

> **Pull request follows the repository template**
>
> **Evidence:** The repo-facts block's PR-template requirements compared with the candidate PR's description. In live mode, the repository's PR template and draft description.
>
> **Pass condition:** Pass if every applicable required template section contains information addressing its stated purpose, or an explicit and justified "not applicable" response where permitted. Fail if a required section is missing, left as a placeholder, or filled with unrelated boilerplate. Do not require a particular description length or writing style.
>
> **Weight:** required

I chose this wording because a pull request can have correct code and tests but still fail to meet the repository's submission requirements. I wanted the check to focus on whether the required information was actually provided rather than how polished or lengthy the description was. It also allows justified "not applicable" responses when the repository permits them, so the tool does not reject an otherwise complete PR based on formatting alone.

**Trade-offs**

I prioritized evidence-based checks for plan fidelity, testing, diff quality, and repository standards rather than creating additional requirements based on writing style or PR length.

One trade-off is that a concise PR can pass as long as it provides the required information and observable evidence. This means my rubric may not distinguish between a detailed explanation and a shorter one that still meets the repository's requirements.

I accepted this trade-off because the tool is supposed to determine whether a PR is ready to submit, not whether it is the most polished submission possible.

I did not revise the rubric after my first full evaluation because it achieved 20/20 agreement across all five categories. My confirming run also achieved 20/20, giving me no observed evaluation disagreement that required a change.
