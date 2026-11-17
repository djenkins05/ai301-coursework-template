# Toolkit Portfolio

**Student:** Da'Karri Jenkins

## Featured Tools

I chose Issue Scout, Repro-Check, Plan-Check, and PR Precheck because they cover the different stages of my open-source contribution process: finding an issue, reproducing it, planning the fix, and checking a pull request before submitting it. Throughout the semester, I learned that AI tools need clear instructions, reliable evaluation criteria, and testing to make useful recommendations.

**Issue Scout**

**What it is, and the judgment hole I wrote:**

Issue Scout searches GitHub for open issues, ranks them cheaply against a search strategy, and grades the top five against a rubric. The judgment I wrote was the fit profile, the search strategy, and my original seven-check rubric (commit `493e695`, November 16, 2026), including a required "Newcomer-sized scope" check. I wanted the tool to decide what makes an issue realistic for me instead of relying only on GitHub labels.

**How it evolved, dated:**

On November 16, 2026, I ran two scans, and I want to keep them separate. Scan 1 (`scan-output.md`) was my first run with the original rubric. Scan 2 (`scan-output1.md`, commit `473fffb`) ran about 15 minutes later, and GitHub's top 100 results for the same queries had already changed. Scan 2 also included a retrospective grade of Rafter CLI issue #29, which I had claimed on November 12 and opened PR #362 for on November 13. The scout never found #29, because it wasn't in the top 100 of any query.

After Scan 2, I applied a staff-provided rubric patch to my installed skill. The patch replaced my "Newcomer-sized scope" row with a staff-written `scope-feasible` row, and I pasted it in unchanged. It also added a difficulty note (straightforward, moderate, or ambitious) that never changes a verdict. I didn't design or rewrite that criterion. Then I regraded three issues. The patch exists only in my installed skill: the rubric in my `ai301-unit5-starter` repository still has my original row, and the regrade appendix is only in the installed copy of `scan-output1.md`.

**Evidence:**

Scan 1 (`scan-output.md`, November 16, 2026): 500 issues retrieved, 425 ranked, top five graded, 4 ACCEPT and 1 REJECT. Gulliver #191 was accepted. The one REJECT was the pipOS event-listener audit (#120), which I had graded `unclear` on scope because a rubric about "one focused bug fix" had no case for open-ended audits.

Scan 2 (`scan-output1.md`, commit `473fffb`, November 16, 2026): 500 unique issues retrieved, 417 ranked, top five graded, 2 ACCEPT (memtomem-stm #1394, infinispan #18514) and 3 REJECT (openspective #11, Starry-Palace #325, globalstack #135).

The staff row says a candidate fails scope only when "there is no single piece of work in it: a codebase-wide checklist, an 'improve X everywhere', or a container issue tracking many sub-tasks." My original row passed only "one focused bug fix or feature."

Regrade under the staff patch (Scan 2 issues plus #29):

- Starry-Palace #325 changed from REJECT to ACCEPT, with the difficulty note "ambitious." The regrade described it as production deployment work, and it noted that the patched rubric now accepts an issue an outside contributor realistically can't do. A rubric ACCEPT didn't make it a good fit for me.
- Rafter CLI #29 was evaluated retrospectively and wasn't discovered by the scout. The original rubric rejected it for two reasons: umbrella scope, and my own PR #362 failing "not already being worked on." After the patch it was still REJECT, now only because of the existing PR.
- globalstack #135 stayed REJECT because "Issue has enough direction" was still `unclear`.

My notes in `scan-notes1.md` (lines 25-34) list nine improvements, such as a "premise still true" check, a cap per repository, and label-filtered queries. Those are proposed future improvements. I haven't implemented any of them.

This showed me that changing a rubric changes the tool's decisions, and that the tool's formal result isn't the same as my own judgment about what to work on.

**Repro-Check**

**What it is, and the judgment hole I wrote:**

Repro-Check grades a reproduction package, meaning a claim comment plus a repro report, against its issue and decides whether it is ready to post upstream. The judgment I wrote was the rubric (`rubric.md`) and the evidence guide (`references/evidence-guide.md`), which tells the skill where proof lives in a package and what good looks like. I also wrote the voice guide. I wanted the tool to check whether a report was actually useful to another developer, not only whether it had the right headings.

**How it evolved, dated:**

On September 30, 2026, commit `07cfb76` rewrote `rubric.md` and completed `evidence-guide.md`. On October 1, 2026, commit `edfbe1a` refined the rubric and added the evaluation run, which scored 19/20. On October 5, 2026, commit `63016cb` updated the voice guide. These were three separate changes on three dates. I don't have a score from before the September 30 rewrite, so I can't say how much it improved.

On November 16, 2026, I used Repro-Check on my Rafter CLI reproduction package for issue #29 and ran it four times. The first problems were about evidence access, not necessarily the quality of my reports. In Run 1 the skill couldn't read its own rubric files because the reads were denied, so I didn't get a verdict. In Run 2 it could not read issue #29 or `CONTRIBUTING.md`, so three criteria came back `unclear` and the verdict was REJECT, because the rubric counts `unclear` as a fail. Run 3 could read what it needed and returned ACCEPT, with a warning that my grep did not match my claim. Run 4 returned ACCEPT again, with a note about my install commands. After Run 3 I re-ran the grep with the right patterns and softened the wording, and I labeled the install commands as adapted.

**Evidence:**

Repro-Check evaluation: 19/20 (October 1, 2026, commit `edfbe1a`).

November 16, 2026 runs (`unit10/repro-check-run1.txt` to `run4.txt` in `ai301-unit6-starter`):

- Run 1: no verdict, because file reads were denied.
- Run 2: REJECT, with three criteria `unclear` because the issue and `CONTRIBUTING.md` were not readable.
- Run 3: ACCEPT, with a warning about the grep claim: the pattern `resolve_key|write_payload|EXIT_QUOTA_EXHAUSTED` "doesn't search for any of those three."
- Run 4: ACCEPT, with a note that my install commands differ from `CONTRIBUTING.md`. All six required checks passed.

My Python tests showed 4 passed and the Node reference test showed 11 passed.

Run 3's grep warning was a real catch. The checker found a claim in my report that its own evidence didn't support, and I hadn't noticed that myself.

**Plan-Check**

**What it is, and the judgment hole I wrote:**

Plan-Check grades a plan package, which is a plan plus a plan comment read against the issue and its reproduction evidence, and decides whether the plan is ready to build from. The judgment I wrote was the rubric, procedure, evidence guide, and voice guide. I wanted a way to check whether a plan made sense instead of accepting an AI-generated one on sight.

**How it evolved, dated:**

I authored Plan-Check on October 8, 2026, in `ai301-unit3-starter` commit `c95c555`: rubric, procedure, evidence guide, voice guide, and an evaluation run. The evaluation scored 19/20. On October 12, 2026, commit `c702132` uploaded and copied those files into my course repository. That was the copy date, not when I wrote the tool.

The `plan-check/scope.md` that was installed for my Rafter CLI work on November 16 was provided by staff, and I didn't write or update it. It says "Staff wrote this file. It ships filled; there is nothing to edit." Its rules include keeping the plan comment off the issue thread.

Unlike Issue Scout and Repro-Check, I don't have a before-and-after result showing that a specific revision of Plan-Check changed a grading decision. Its evolution is thinly recorded.

**Evidence:**

October 8, 2026: commit `c95c555` (authoring and evaluation run). October 12, 2026: commit `c702132` (copy into the course repository).

Evaluation score: 19/20.

November 16, 2026: Plan-Check returned ACCEPT with 10/10 checks passing on my Rafter CLI plan (`plan.md`) and plan comment (`plan-comment.md`). That grade was retrospective, because I wrote both files after I had already implemented the tests and opened PR #362. It didn't approve the plan before I wrote code. The result still told me something: it noted that the plan covers 4 of the Node file's 11 scenarios and that the package was retrospective, and its voice notes flagged that my draft comment asked two questions at once.

**PR Precheck**

**What it is, and the judgment hole I wrote:**

PR Precheck reviews a proposed pull request before submission. It checks things like whether the diff matches the plan, whether the description matches the changes, and whether test results and AI-use disclosure are visible. The judgment I wrote was the rubric, procedure, evidence guide, and voice guide for it.

**How it evolved, dated:**

On October 13, 2026, I updated the skill files and ran the evaluation in `ai301-unit4-starter` (commit `e6fd2c6`). It scored 20/20. The same day I copied the files into my course repository (commit `340eaca`).

On November 16, 2026, the ship-gate install put a staff-written live scope over the installed `scope.md` and kept the earlier sandbox scope as `scope.md.sandbox`. That was the staff installation, not something I wrote. After that I ran PR Precheck as part of the ship-gate checks on my PR #362 draft, and it accepted it.

PR Precheck changed very little. I have no before-and-after result showing that anything improved its decisions, and I don't want to overstate its development.

**Evidence:**

October 13, 2026: starter commit `e6fd2c6`; course-repository copy `340eaca`. Evaluation score: 20/20.

November 16, 2026: the installed scope was replaced by the staff version, with the earlier scope preserved as `scope.md.sandbox`.

The 20/20 shows the tool met its tested requirements, and the ship-gate runs show that I used it on real work.

## Inventory

- Issue Select (Unit 1): An early issue-evaluation tool that grades one candidate issue against a rubric. I edited its rubric and fit profile in commits dated September 28 and 29, 2026, and it scored 19/20 on its evaluation.

- Voice Guard (Unit 6): A hook that checks my outgoing GitHub comments against my voice guide before they post. The voice-guide rules are mine. The checker code (`check_voice.py`) and the Upstream section were not written by me: staff supplied the checker, and Claude Code drafted the Upstream section, which I haven't fully reviewed. My own run of the tests on November 16 showed 20 passed and 1 skipped (a live test that needs `VOICE_LIVE=1`).

- Ship Gate (Unit 11): A check that decides whether a PR is ready to go out. `check_gate.py` is staff-provided. I wrote `ship-manifest.md` in my `rafter-cli` clone with four must-pass checks. The gate log shows PASS at 18:34, 19:29, and 19:47 on November 16. It also logged one BLOCK at 18:36, which was the expected stop from a setup test of the hook.

- PR Monitor (Unit 12): A read-only tool that checks my pull request and drafts my next move. `monitor.py` is staff-provided. I ran it fully once on PR #362 at 20:32 on November 16, and it drafted "Wait, no nudge yet." The playbook was revised at 20:41 after that draft missed that GitHub was holding my workflow run at `action_required` for maintainer approval.

## The Arc

**Beat 1**

Date: September 30 to October 1, 2026

Friction: I needed Repro-Check to judge whether a report was actually useful to another developer, not only whether it had the right sections.

Change: On September 30 (commit `07cfb76`) I rewrote the rubric and completed the evidence guide. On October 1 (commit `edfbe1a`) I refined the rubric and added the evaluation run.

Result: Repro-Check scored 19/20 on the evaluation.

**Beat 2**

Date: October 5, 2026

Friction: I wanted the way Repro-Check communicated its feedback to be clearer.

Change: I updated the Repro-Check voice guide (commit `63016cb`).

Result: none. I have no separate before-and-after result for the voice guide update.

**Beat 3**

Date: October 8, 2026

Friction: I wanted a way to check an implementation plan before relying on it, instead of assuming a proposed solution was correct.

Change: I wrote Plan-Check's rubric, procedure, evidence guide, and voice guide (commit `c95c555`). I uploaded it to my course repository on October 12 (commit `c702132`), but October 8 is when I authored it.

Result: Plan-Check scored 19/20 on the evaluation.

**Beat 4**

Date: October 13, 2026

Friction: I needed a consistent way to check whether a pull request was ready, including whether it had enough testing and supporting evidence.

Change: I updated PR Precheck's skill files and ran its evaluation (commit `e6fd2c6`), then copied it into the course repository (commit `340eaca`).

Result: PR Precheck scored 20/20 on the evaluation.

**Beat 5**

Date: November 16, 2026

Friction: When I ran Repro-Check on my Rafter CLI reproduction package, the first two runs gave me no usable verdict. Run 1 couldn't read the skill's files, and Run 2 could not read the issue or `CONTRIBUTING.md`.

Change: I made the evidence available (including a saved snapshot of the issue), then ran it again. After Run 3's warning about my grep claim, I re-ran the grep with the right patterns, softened the wording, and labeled my install commands as adapted.

Result: Run 3 returned ACCEPT with the grep warning, and Run 4 returned ACCEPT with all six required checks passing and a note about my install commands. The early problems were about evidence access, not necessarily the quality of my reports.

**Beat 6**

Date: November 16, 2026

Friction: My Issue Scout rubric rejected issues because of how strictly it read scope. I saw this when I graded Rafter CLI #29 after the fact, and the original rubric rejected it as an umbrella issue even though I had claimed one clearly bounded test file. Scan 1 (425 ranked, 4 ACCEPT and 1 REJECT) and Scan 2 (417 ranked, 2 ACCEPT and 3 REJECT) were separate runs.

Change: I applied the staff-provided `scope-feasible` patch to my installed rubric, unchanged, and regraded three issues.

Result: Starry-Palace #325 changed from REJECT to ACCEPT, but the regrade still called it ambitious, so the ACCEPT didn't make it a good fit for me. #29 stayed REJECT because of my existing PR #362. My nine proposed improvements in `scan-notes1.md` are still proposals.

**Beat 7**

Date: November 16, 2026

Friction: I wanted a structured review of my Rafter CLI plan, but I had already written `plan.md` and `plan-comment.md` after finishing the implementation.

Change: I ran Plan-Check on them under the staff-provided wild scope, and treated the result as a retrospective grade.

Result: ACCEPT with 10/10 checks passing. Because the plan came after the code, this shows the package was internally consistent, not that Plan-Check guided my work.

## Limitations and What's Next

One of the biggest things I learned from building my toolkit is that AI tools are useful, but they still depend on the quality of the instructions and the judgment of the person using them. Even when a tool gets a high evaluation score, it can still make mistakes or miss important context. The evaluation scores (19/20, 19/20, 20/20) tell me a tool agreed with the answer key on those test packages. They don't tell me it will be right on my real work.

The Rafter CLI work taught me the most because it was real. Most of Repro-Check's early problems came from what the tool could read, not from how good my report was. Plan-Check's ACCEPT came after the code was written. Issue Scout never found the issue I actually chose, and its formal REJECT for #29 was partly a gap in the rubric and partly my own PR. I kept the tool's verdict and my own judgment separate.

If I continued developing these tools, I would first try the nine improvements I proposed for Issue Scout, especially a check that the issue's premise is still true. I would also use Plan-Check before I write code, so that its result could change a decision. And I would make the tools work together more closely: Issue Scout to find candidates, Repro-Check to verify the bug report, Plan-Check to evaluate the solution, and PR Precheck to review the finished work.

Overall, this toolkit helped me become more organized and intentional about open-source contributions. The most important part of using AI isn't accepting every answer it gives. It is checking the evidence and being honest about what a result does and doesn't show.

**Tool limits.**

issue-scout: It can accept issues that pass the rubric but are too ambitious for my experience or time (Starry-Palace #325 was a rubric ACCEPT), and it can't tell my own claim or PR from someone else's.

repro-check: Passing its rubric doesn't guarantee that a bug can be reproduced in every environment, and it can only grade the evidence it is allowed to read.

plan-check: It can evaluate whether a plan looks reasonable, but it can't guarantee that the implementation will work, and my only real use of it so far was retrospective.

pr-precheck: It checks submission readiness, but it can't guarantee maintainer approval or catch every problem that might appear during review.
