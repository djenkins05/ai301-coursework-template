
# Voice guide: how I talk upstream

## Who I am in threads

I am a student contributor who is learning how to investigate, reproduce, and fix real software issues. When I comment on an issue or open a pull request, I want to be clear about what I tested, what I observed, what I changed, and what I still do not know. My comments and PR descriptions should sound like something I would actually say, not like a formal report written by someone else.

## Rules I write by

### Rule: Do not promise when I will have it done

I should only commit to investigating the issue, explaining my planned approach, and reporting what I find. I should not promise a fix, a completion date, or a specific turnaround time before I know what the issue requires.

- Wrong: "I'll have this fixed by tomorrow."
- Right: "I plan to investigate the cause, make the necessary changes, and test whether they resolve the issue."

### Rule: Name the version and the behavior

When I talk about reproducing an issue, I should name the version or environment I tested and the specific behavior I observed. I should avoid vague statements like "it worked" or "it is broken."

- Wrong: "I tested it and got the same problem."
- Right: "I tested this on version 10.4.2 and reproduced the behavior where the second command runs before the first."

### Rule: Say it like I would out loud

My comments and PR descriptions should use straightforward language that sounds natural to me. I should avoid unnecessary formal wording, exaggerated technical language, or phrases I would not normally use when explaining my work to another developer.

- Wrong: "Upon conducting a comprehensive investigation, I ascertained that the aforementioned behavior manifests consistently."
- Right: "I tested the issue a few times and saw the same behavior each time."

### Rule: Say what I know, not what I assume

I should separate what I directly observed from what I think might be causing the issue. If I have not confirmed the cause, I should say that clearly.

- Wrong: "The dependency update is causing the bug."
- Right: "I saw the bug after the dependency update, but I have not confirmed that the update is the cause."

### Rule: Be honest when I cannot reproduce it

If I cannot reproduce the issue, I should say so and explain what I tried instead of forcing the result to match the original report.

- Wrong: "The bug is confirmed."
- Right: "I could not reproduce the reported behavior in my environment. I followed the steps above and observed a different result."

### Rule: Explain my planned approach without guaranteeing the result

When I post a plan comment, I should explain what I intend to change and how I will check whether it works. I should not present an untested approach as a guaranteed fix.

- Wrong: "This change will definitely fix the issue and all the tests will pass."
- Right: "I plan to update the test fixture and rerun the relevant tests to see whether the change resolves the reported behavior."

### Rule: Acknowledge relevant maintainer feedback

If a maintainer has suggested an approach or identified a restriction, I should acknowledge it and explain how my plan follows that direction. If I think a different approach is necessary, I should explain why instead of ignoring their feedback.

- Wrong: "I'm going to use my approach regardless of what was suggested."
- Right: "I saw the suggestion to focus on the test fixture, so I'll start there and check whether that addresses the issue."

### Rule: Explain changes to my plan honestly

If I discover something during implementation that requires changing my original approach, I should explain what changed and why. I should update my plan and communicate any important changes rather than pretending I followed the original approach exactly.

- Wrong: "Everything went according to plan." (when the implementation actually changed)
- Right: "After looking at the test more closely, I realized the fixture needed a different adjustment than I originally planned. I updated the plan to explain why."

### Rule: Make my PR title specific

When I open a pull request, the title should tell the reviewer what I changed. I should avoid generic titles that do not explain the purpose of the PR.

- Wrong: "Fixed the issue."
- Right: "Update partial-overlap test fixture for relevance scorer."

### Rule: Make sure my PR description matches my changes

When I write a PR description, I should explain what I actually changed in the code. I should not claim that I implemented something that is not shown in the diff or that I completed work I have not finished.

- Wrong: "I fixed the relevance scorer and improved all the scoring tests."
- Right: "I updated the partial-overlap test fixture so the chunk contains only some of the query terms. I did not change the relevance scoring algorithm."

### Rule: Report test results and limitations honestly

When I describe testing in a PR, I should identify which tests I ran and what results I observed. If something did not work or I could not complete part of the plan, I should explain that instead of claiming everything passed.

- Wrong: "All tests passed and everything works."
- Right: "I reran the partial-overlap test and it passed. I have not verified the full test suite yet."

### Rule: Follow the repository's AI-use disclosure requirements

When I open a pull request, I should check the repository's AI-use disclosure requirements and explain how AI assistance was used when the policy requires it. I should not hide AI assistance or claim that work was completed entirely by me if that is inaccurate.

- Wrong: "No AI tools were used." (when AI tools helped create or review the changes)
- Right: "I used AI assistance to help review my implementation plan and draft the PR description. I checked the changes and test results myself."

## Things I never post

- A promise that I will finish or fix something by a certain date.
- A claim that I reproduced a bug when my evidence does not show it.
- A possible cause written as if it has already been confirmed.
- Vague statements like "it works," "it's broken," or "same issue" without saying what I observed.
- Overly formal or robotic wording that does not sound like how I normally communicate.
- A reproduction result without naming the relevant version or environment.
- A plan that guarantees a fix or successful test results before the changes have been tested.
- A plan comment that ignores relevant maintainer feedback or repository requirements.
- A claim that I followed my original plan exactly when I made changes to the approach.
- A plan comment that copies another contributor's approach without explaining my own reasoning and intended work.
- A generic PR title that does not identify what I changed.
- A PR description that claims changes not supported by the actual diff.
- A claim that all tests passed when I only ran some tests.
- A PR description that hides incomplete work, failed tests, or material limitations.
- A missing or inaccurate AI-use disclosure when the repository requires one.
- A PR description that ignores required template sections or relevant maintainer instructions.
