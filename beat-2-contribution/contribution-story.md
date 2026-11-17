# Contribution: Python API Utility Test Parity (Rafter CLI Issue #29)

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Dakarri Jenkins
**GitHub Username:** djenkins05
**Issue Title:** test: Python test parity — add missing test files
**Issue:** https://github.com/Raftersecurity/rafter-cli/issues/29
**Pull Request:** https://github.com/Raftersecurity/rafter-cli/pull/362

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

This story documents my work toward adding missing Python API utility test coverage to Rafter CLI. The upstream contribution belongs in my fork of `Raftersecurity/rafter-cli`; this story belongs in my course repository at `beat-2-contribution/contribution-story.md`.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

The entries below are a dated record of actual work with the course tools. The issue-scout run (Unit 5) and the voice-guard and repo-memory work (Unit 6) and the ship-gate run (Unit 7, which the course also numbers Unit 11) are recorded, all on November 16, 2026; my PR-monitor run is not yet supplied, so that outcome remains explicitly pending rather than claimed.

**Unit 5: Issue-scout and issue selection**

On November 16, 2026, I ran my Issue-Scout retrospectively (this is its second scan that day, the one that also grades Issue #29; [scan-output1.md](https://github.com/djenkins05/ai301-unit5-starter/blob/473fffbc94fd278f897793ce3745f500b1e53122/scan-output1.md), [scan-notes1.md](https://github.com/djenkins05/ai301-unit5-starter/blob/473fffbc94fd278f897793ce3745f500b1e53122/scan-notes1.md)), after I had already claimed Issue #29 on November 12 and opened PR #362: five GitHub search queries retrieved 500 unique issues, which it ranked down to 417 candidates and then graded the top five, giving two ACCEPT and three REJECT verdicts. Because Rafter CLI Issue #29 was not among those results, I evaluated it separately, and the original rubric returned REJECT because it excludes umbrella issues and because my own open PR #362 failed the "not already being worked on" check. Before my November 12 claim that availability check would have passed, but the umbrella-issue rule would still have produced REJECT (a hypothetical assessment, not an earlier scout run). The scan exposed outdated issue information and weaknesses in my rubric, so I recorded proposed improvements instead of changing the rubric to force an ACCEPT. (On the same day, after this scan, I applied the separate staff `scope-feasible` patch to my installed skill's rubric; see the Toolkit block under Why I Chose This Issue.)

**Unit 6: Voice-guard and repository memory**

On November 16, 2026, I installed Voice Guard globally under `~/.claude/voice-guard/`, combining my Unit 2 and Unit 3 voice guide with a new Upstream communication section and a Claude Code `PreToolUse` Bash hook in `~/.claude/settings.json`, and validated it with 19 passing offline tests (a 20th, live test is skipped by default), a hook dry-run, a fresh non-interactive `claude -p` run that blocked `gh issue comment --help` and logged the decision, and live drafts that accepted a repro report, a claim, and a specific question while stopping a deadline promise, an aggressive message, an unapproved claim, and a repeated ping. During testing, my professional writing sample was first flagged by the new claim rule, so I revised the sample and added a compliant-claim example without changing the rule, and the hook wrongly blocked shell commands that carried GitHub comment text inside heredocs, so I changed unparseable GitHub commands from fail-open to fail-closed, added suggested rewrites to the stop messages, and used the editor tool to work around the heredoc false positives, which remain unresolved. I also wrote a 39-line `CLAUDE.local.md` in my Rafter CLI clone with the issue details, PR status, repository instructions, test commands, known failures, and AI contribution requirements, excluded from Git through `.git/info/exclude`, though I have not verified that it loads in a fresh Claude Code session, and Claude Code drafted the Upstream guide section, which I have not personally reviewed. Voice Guard was installed after I posted my Issue #29 claim on November 12 and opened PR #362 on November 13, so it did not check either submission; a later manual check of a copy of my posted claim passed, but that was a retrospective test, not a guarded post, and the Voice Guard source lives in my separate [`ai301-unit6-starter` repository](https://github.com/djenkins05/ai301-unit6-starter/tree/75de918a632d014879e0eba080dc9e4d9ba57ae2) (commit `75de918`), with its guard log kept local.

**Unit 7: Ship-gate and gate manifest**

On November 16, 2026 (course Unit 11), I installed the ship-gate and wrote `ship-manifest.md` in my rafter-cli clone with four must-pass checks taken from CONTRIBUTING.md and my CLAUDE.local.md (Python setup, the new tests, the Python suite, the Node api-utils reference test) and three dated exclusions. I ran it by hand on `test/python-api-utils-parity-29` and it printed `ship-gate: PASS` (again after I reworded the drafts) after all four checks and my pr-precheck (accept), alongside a separate plan-check that also accepted (all ten checks passing, described under Solution Approach), but only after I checked my failing suites against a clean upstream/main: the Python and Node `gates` failures I recorded when I opened the PR were real then, but upstream has since fixed those tests (Node `0783f862` on November 14, Python #365 on November 15), so they now pass on main, and only the `install-manifest` failure and the frozen pnpm install still fail there. PR #362 already existed, so I did not run `gh pr create` or push anything; the two-stop hook test is a separate step. The manifest turned the "not verified against main" note in my PR description into checked evidence, and showed that two of the three failures I recorded have since been fixed upstream.

**Unit 8: PR-monitor and playbook**

[DATE OF ACTUAL TOOL WORK — PENDING. 2-4 sentences: what PR-monitor read, the draft or assessment it generated, what your playbook said to do, and whether you accepted, revised, or rejected its suggestions.]

---

## Why I Chose This Issue

I originally selected Rafter CLI Issue #29 on November 12 because it looked like a manageable Python testing contribution that matched my computer science background and my experience with Python. The issue lets contributors pick individual missing Python test files, so instead of taking on all of it I focused on `python/tests/test_api_utils.py`, using the existing Node.js tests in `node/tests/api-utils.test.ts` as the reference. While investigating I found that four of the five test files listed in the issue already existed, and that many API utility scenarios were already covered elsewhere in Python, so I aimed for meaningful new coverage rather than duplicated tests. I selected and claimed the issue before running any scout evaluation; my Issue-Scout never recommended Issue #29, and I only learned its verdict afterward.

On November 16 I evaluated Issue #29 retrospectively with my Issue-Scout (my scan reports, in my `ai301-unit5-starter` repository, are [scan-output1.md](https://github.com/djenkins05/ai301-unit5-starter/blob/473fffbc94fd278f897793ce3745f500b1e53122/scan-output1.md) and [scan-notes1.md](https://github.com/djenkins05/ai301-unit5-starter/blob/473fffbc94fd278f897793ce3745f500b1e53122/scan-notes1.md)), and the original rubric returned REJECT for two reasons. First, **umbrella-issue scope**: the rubric treated the issue as too broad because it contains several independent tasks, even though the maintainer explicitly allowed contributors to claim a single missing test file and my task was small and clearly defined. Second, **existing contribution**: the "not already being worked on" check failed because my own PR #362 was already open. That second check would have passed before I claimed the issue on November 12, but even then the umbrella-issue rule would still have produced REJECT under the original rubric; that pre-claim picture is a hypothetical assessment, not an earlier scout run. I proceeded anyway, and kept going after learning the verdict, because the `test_api_utils.py` task was clearly bounded, could be added without changing production code, matched my Python testing experience, and I implemented four focused tests. The rubric simply did not distinguish an entire umbrella issue from an independently claimable task inside it, so this showed me a limitation in how my scout evaluates scope, not that my contribution was unsuitable. If I rebuilt the scout, I would have it check whether an issue's premise is still accurate, recognize independently claimable tasks within umbrella issues, and distinguish my own claims from other contributors' work.

**Where I found it, and what the scout says (added November 16, 2026).**

- Where I found the issue: I discovered Rafter CLI Issue #29 while looking for open-source contributions that matched my Python programming and testing experience. I selected the issue because it offered a focused opportunity to improve test coverage while learning how an established open-source project organizes and validates contributions.
- Issues my scout graded: scan 1 (Gulliver #191, pipOS #117, #119, #122, #120) and scan 2 (memtomem-stm #1394, openspective #11, infinispan #18514, Starry-Palace #325, globalstack #135), plus a direct retrospective grade of #29; the original reports are `scan-output.md` and `scan-output1.md` in my `ai301-unit5-starter` repository (the links above are pinned to commit `473fffb`).
- What the scout concluded about #29: under the original rubric, REJECT (umbrella-issue scope, and my own open PR #362 failed "not already being worked on"). That REJECT is the scout's recorded verdict and I am not replacing it. I did not rescore #29 here with the patched rubric; a regrade appendix exists only in my installed skill's copy of `scan-output1.md` (not in the Unit 5 repository) and is not used for the verdict. The patch's difficulty note for this issue is informational only: **straightforward** (the issue names `tests/test_api_utils.py` and its Node reference; the real effort was finding that four of the five listed files already existed and most scenarios were already covered elsewhere).
- Fit with my skills: Python, pytest, test-only work, reading a Node spec against Python behavior, no production code.
- What I hope to learn: I wanted to improve my ability to read unfamiliar codebases, compare implementations across programming languages, and write meaningful automated tests. I also wanted firsthand experience with the GitHub contribution process, including communicating with maintainers, following contribution guidelines, and opening a pull request for review.
- How well issue-scout worked: it did not find #29 (it was not in the top 100 of any of five queries), and the original rubric rejected it for a reason that was really a gap in the rubric (how to treat an independently claimable slice of an umbrella issue) plus my own PR. In the local regrade appendix, the scope patch changed only one of three regraded verdicts, to Starry-Palace #325, a production deployment task an outsider cannot do, which suggests the rubric also lacks checks for access the claimant doesn't have and for the claimant's own work.

**Claim comment:** https://github.com/Raftersecurity/rafter-cli/issues/29#issuecomment-6827269721

**Toolkit**

- Tool: Issue-Scout, using my five-query GitHub search strategy and original seven-check rubric. I used it on November 16 to evaluate Issue #29 retrospectively after already claiming the issue and opening my PR.
- What it produced: A scan of 500 unique issues, 417 ranked candidates, five fully graded issues with two ACCEPT and three REJECT verdicts, and a separate retrospective REJECT verdict for Rafter CLI Issue #29. The evaluation also showed that the availability check would have passed before my claim, while the umbrella-issue scope check would still have failed.
- Difficulties: Four of five supposedly missing Python test files were already present; overlapping test coverage required manual inspection; the rubric could not distinguish a narrowly scoped contribution within an umbrella issue or my own PR from another contributor's work; GitHub search results shifted between scans.
- What changed: Completed, November 16, 2026: I applied the staff `scope-feasible` patch to my installed skill's `~/.claude/skills/issue-scout/rubric.md`, replacing only the "Newcomer-sized scope" check and adding the difficulty note section, with a dated entry in that folder's `scan-notes1.md` (backup in `~/.claude/backups/unit10-pre-install-20261116-141149/`). That change exists only in the installed skill copy: the rubric in my `ai301-unit5-starter` repository and its Git history (commits `493e695` and `473fffb`) still show the original seven-check rubric, and the pinned scan reports still show the original scores. Still proposals, not implemented: a premise-still-true check, an already-covered-elsewhere step, my own umbrella wording (the staff patch only overlaps with it, and its evidence-guide counterpart still states the old scope rule), ignoring my own claim and PR in "not already being worked on", saying which repo the activity checks use, label-filtered queries, a per-repository cap, a minimum issue age, and saving the raw scan JSON.

---

## Understanding the Issue

**Problem Description**

Issue #29 asks for missing Python test coverage in Rafter CLI relative to the Node.js implementation. My selected part concerns API utility tests. The absence of the specific Python test file does not by itself prove all API utility behavior is untested, so the coverage gap must be established scenario by scenario.

Comparing the two implementations also surfaced one confirmed difference that is still an open question, not an established defect. `node/tests/api-utils.test.ts` expects `writePayload` to fall back to JSON output when `fmt='md'` and the payload has no markdown field. The Python helper, `write_payload` in `python/rafter_cli/utils/api.py`, currently emits an empty string in that case. Whether Python should match Node here is an unresolved parity question.

**Expected Behavior**

Relevant Python API utility behaviors should be exercised by automated pytest cases comparable to the existing Node.js scenarios. Tests should check applicable constants, credential-resolution priorities and errors, and output behavior such as JSON, Markdown, and quiet mode. The project should continue passing its existing checks without changing production CLI behavior for a test-only contribution.

**Current Behavior**

My local commands confirmed that `python/tests/test_api_utils.py` does not exist and `node/tests/api-utils.test.ts` does exist. A search of the Python tests also found coverage of `resolve_key`, `write_payload`, and exit codes in `test_error_handling_gauntlet.py`, plus credential handling in `test_config_secret_handling.py`. Existing Python tests therefore already cover many `resolve_key` and `write_payload` cases.

One confirmed behavioral difference: for `fmt='md'` with no markdown field, Node's `writePayload` falls back to JSON (per `node/tests/api-utils.test.ts`), while Python's `write_payload` emits an empty string. The existing Python test in `python/tests/test_error_handling_gauntlet.py` explicitly expects that empty string, so the current Python behavior is deliberately asserted. `shared-docs/CLI_SPEC.md` does not conclusively specify this helper-level fallback, so the difference is confirmed but it is not established as a defect.

At the point of this initial investigation (November 12, before implementation) I had not yet completed the full scenario-by-scenario comparison needed to identify every uncovered case, and I had not yet added any tests; I added four tests afterward (see Solution Approach and Implementation Notes).

**Affected Components**

- `node/tests/api-utils.test.ts` — Node.js reference tests.
- `python/rafter_cli/utils/api.py` — Python API utility functions, including `resolve_key` (line 170 in my checkout) and `write_payload` (line 202), plus API constants and helpers.
- `python/tests/test_error_handling_gauntlet.py` — existing Python checks for API utility behavior, including the test that expects an empty string from `write_payload` for `fmt='md'` with no markdown field.
- `python/tests/test_config_secret_handling.py` — existing credential-resolution checks.
- `python/tests/test_api_utils.py` — the file I proposed and then created, with four tests, in PR #362.
- `shared-docs/CLI_SPEC.md` — canonical CLI behavior reference if expected behavior needs clarification.

**Toolkit**

- Tool: VS Code terminal, `ls`, and `grep` for repository inspection.
- What it produced: Proof that the proposed file is missing, identification of `resolve_key` and `write_payload`, and discovery of related existing pytest cases.
- Difficulties: The named test file is absent, but several target behaviors are already covered elsewhere, making the true scope less obvious.
- What changed: I revised the plan from adding a file by name alone to comparing scenarios and adding only meaningful missing tests.

---

## Reproduction Process

**Environment Setup**

On November 12, 2026, I worked in VS Code on macOS on branch `test/python-api-utils-parity-29`. I set up Poetry and confirmed that its Python virtual environment was located at `/Users/djenkins/Documents/GitHub/rafter-cli/python/.venv`. `poetry run python --version` returned **Python 3.12.1**. An earlier version check showed **Node.js v25.2.1**. Initially, `poetry` was installed but was not found by zsh; checking `python3 -m site --user-base` and the executable under `~/Library/Python/3.12/bin/poetry` identified a PATH issue, which I resolved before running tests.

The Python dependencies were installed sufficiently for the test suite to run through Poetry. The project's contributing guide specifies Python 3.10+, Poetry, Node.js 18+, and pnpm 9+. Versions checked November 16, 2026 on the same machine: macOS 14.0, Poetry 2.5.1, pnpm 9.15.9; the branch is based on release commit `1ebad941815d91d45d7befe3295d15f23a8b05ad` (v0.11.7). The pnpm lockfile mismatch (checked November 16, 2026): `pnpm install --frozen-lockfile` fails with `ERR_PNPM_LOCKFILE_CONFIG_MISMATCH` because the `overrides` configuration doesn't match the lockfile. It fails the same way on clean upstream/main (`fcd20d8`), so I installed with `pnpm install --no-lockfile`, which left no lockfile change in my diff. The Node.js dependencies were installed with pnpm and the Node.js tests were run (results under Testing Strategy).

**Steps to Reproduce**

1. From the repository's `python/` directory, run `poetry run pytest -q` to establish the baseline.
2. Observe the baseline: **2,046 passed, 1 failed, 11 skipped, 2 warnings in 120.00 s**. The failure was `tests/test_gates.py::test_unicode_and_file_names_read_like_node`, where macOS raised `OSError: [Errno 92] Illegal byte sequence` while attempting to create a filename containing `auth\xff.py`.
3. Run `poetry run pytest -q --deselect=tests/test_gates.py::test_unicode_and_file_names_read_like_node` to isolate that pre-existing, apparently filesystem-related failure. Observe **2,046 passed, 11 skipped, 1 deselected, 2 warnings in 111.50 s**.
4. Run `ls tests/test_api_utils.py`; observe `No such file or directory`.
5. Run `ls ../node/tests/api-utils.test.ts`; observe that the Node.js reference test file exists.
6. Run `grep -nE '^def |^async def |^[A-Z_]+ =' rafter_cli/utils/api.py`; locate `resolve_key` at line 170 and `write_payload` at line 202, along with API constants and helpers.
7. Run `grep -R -n -E 'resolve_key|write_payload|EXIT_QUOTA_EXHAUSTED' tests`; discover related tests in `test_error_handling_gauntlet.py`, `test_config_secret_handling.py`, and other files.
8. Compare the actual test cases in both languages and identify scenarios with no existing Python coverage. The absent-before evidence is the missing-file check in step 4 plus the existing-coverage `grep` in step 7; the covered-after evidence is the targeted run of the four new tests described under Testing Strategy.

**Reproduction Evidence**

- **Commit showing reproduction:** none. Commit `451f78d042bb16bacb9bd79c2d807b81eec7c62e` contains the new tests, not the reproduction evidence, so it is not linked as one. The evidence is the terminal output below and in my local `unit10/repro-draft.md`.
- **Screenshots/logs:** Terminal output recorded November 12, 2026: original pytest baseline, deselected rerun, missing-file check, Node reference-file check, and `grep` results. Where the evidence is stored: nothing here is linked or committed to this course repository, because this story's header says no evidence uploads are part of Assignment 5. The reproduction report is [`unit10/repro-draft.md`](https://github.com/djenkins05/ai301-unit6-starter/blob/75de918a632d014879e0eba080dc9e4d9ba57ae2/unit10/repro-draft.md) in my `ai301-unit6-starter` repository (commit `75de918`, pushed); the raw November 12 terminal output was not saved anywhere else, and the November 16 re-runs and base comparison are in `test_evidence.md` in the root of my local rafter-cli clone, `/Users/djenkins/Documents/GitHub/rafter-cli/`, which is kept out of commits by `.git/info/exclude`. The numbers quoted in this story are copied from those files.
- **My findings:** The specifically named Python test file is absent, while several API utility behaviors are already covered elsewhere. The baseline suite has one unrelated macOS filename error; its other tests passed when that case was deselected. The scenario-level comparison then narrowed the work to four focused tests (see Solution Approach).

**Reproduction check (added November 16, 2026).** Issue #29 asks for a missing test file, so reproducing it means showing the gap, not a bug. On November 16 I re-verified: the upstream tree listing for `python/tests/test_api_utils.py` on upstream/main (`fcd20d8`) returns nothing, the Node reference test passes (`pnpm exec vitest run tests/api-utils.test.ts`, 11 passed), and on my branch `poetry run pytest tests/test_api_utils.py -v` gives 4 passed. A re-run grep found that the API base URL value, pretty-printed `write_payload` JSON, and all-six-exit-codes-distinct were not asserted by any existing Python test I could find (grep-based, so not proof). The full suite numbers above were recorded on November 12 and not re-run. The report is `unit10/repro-draft.md` in my Unit 10 materials and was not posted to GitHub.

**Toolkit**

- Tool: Poetry, pytest, `ls`, and `grep` in the VS Code terminal for the November 12 baseline; on November 16, also git, the Node.js Vitest reference test, and repro-check, run as `claude "repro-check: grade my claim comment in claim-draft.md and my repro report in repro-draft.md for issue https://github.com/Raftersecurity/rafter-cli/issues/29"` with the wild scope installed and the voice guide it shares with the guard.
- What it produced: A reproducible baseline (2,046 passed, 1 failed, 11 skipped), a comparison run excluding the known failure (2,046 passed, 11 skipped, 1 deselected), and evidence of the missing file and existing overlapping tests. On November 16, the re-verification described above and a final repro-check result of accept, with all six required checks passing, after earlier runs returned reject.
- Difficulties: Poetry initially was not on the shell PATH, and a pre-existing test attempted to create a filename macOS rejected with `Errno 92`. With repro-check, the first two runs could not read the skill files or the issue (permissions and no network in the nested session), so required checks came back unclear and counted as fail; the third caught a real error, my claim that three scenarios were "not covered anywhere" rested on a grep that did not search for them; the fourth noted my install commands differed from CONTRIBUTING.md.
- What changed: I fixed the Poetry command setup, retained the full-suite failure as baseline evidence, and used a narrowly deselected rerun to establish the status of the remaining tests without altering unrelated upstream code. For repro-check, I saved an issue snapshot for the grader, re-ran the grep with the right patterns and softened the wording, and labeled the install commands as adapted. The posted claim is a copy of the public comment, not an original draft, and I did not edit it.

---

## Solution Approach

**Analysis**

The immediate symptom is the missing `python/tests/test_api_utils.py`, but the underlying contribution should be framed as a *coverage gap*, not an assumed product bug. In `python/rafter_cli/utils/api.py`, `resolve_key(cli_opt)` resolves credentials and `write_payload(data, fmt, quiet)` handles output. Existing Python tests already exercise these functions, so I must read `node/tests/api-utils.test.ts` alongside `tests/test_error_handling_gauntlet.py` and `tests/test_config_secret_handling.py` to find specific differences. The relevant code locations are `resolve_key` and `write_payload`; whether any additional API helper needs tests remains to be verified.

The `write_payload` markdown fallback is the one confirmed Node/Python difference so far. `node/tests/api-utils.test.ts` expects JSON output when `fmt='md'` and no markdown field exists; `write_payload` in `python/rafter_cli/utils/api.py` emits an empty string, and `python/tests/test_error_handling_gauntlet.py` asserts that empty string. `shared-docs/CLI_SPEC.md` does not conclusively specify a helper-level fallback, so I am treating this as an unresolved parity question, not a confirmed bug. Existing Python tests already cover many `resolve_key` and `write_payload` cases, so most of the issue's scope is likely already met.

**Proposed Solution**

Add focused, isolated pytest cases in `python/tests/test_api_utils.py` for confirmed gaps relative to the Node.js tests and the shared CLI specification. Use fixtures or monkeypatching for environment variables and dependencies, and capture stdout/stderr where appropriate. The contribution stays focused on missing, nonduplicative Python test coverage. I am deliberately NOT changing `write_payload` or the existing gauntlet test to resolve the markdown-fallback difference: that would be a production behavior change that the spec does not clearly support. If I raise it, I will ask the maintainer on the issue first and, until they decide, avoid adding a test that contradicts the existing assertion. I do not plan to change production API behavior, introduce dependencies, reformat unrelated files, or make real network requests. If the comparison shows equivalent coverage already exists, I will re-scope the contribution or ask the maintainer rather than submit duplicate tests.

**Implementation Plan**

All steps below are done. The result is committed and part of PR #362.

1. Inspected `node/tests/api-utils.test.ts` and compared its cases with the Python tests in `tests/test_error_handling_gauntlet.py`, `tests/test_config_secret_handling.py`, and other relevant files.
2. Inspected `python/rafter_cli/utils/api.py`, especially `resolve_key()` and `write_payload()`, to find missing assertions.
3. Created `python/tests/test_api_utils.py` with four tests (exact API base URL, six distinct integer exit codes, pretty-printed JSON with quiet mode disabled, valid single-line JSON in quiet mode). Only this file was added; no production files were changed.
4. Ran `poetry run pytest tests/test_api_utils.py -v`: 4 passed.
5. Ran the Python suite (with the macOS-specific test deselected) and the Node.js suites; results are under Testing Strategy.
6. Reviewed the staged changes with Git before committing. (`python/poetry.toml` was still accidentally committed once and then reverted; see Implementation Notes.)

Deviations: the planned tests were narrowed after I found substantial existing Python coverage of `resolve_key`, `write_payload`, JSON, Markdown, quiet mode, and exit codes, so I did not copy the Node.js scenarios wholesale. The exit-code uniqueness test was added after I confirmed the existing coverage of the exit codes was incomplete. I also deliberately left the Markdown fallback and the quiet JSON separator differences untested and unchanged, because the intended parity behavior has not been resolved.

**Plan-Check (November 16, 2026).** The plan is recorded in `plan.md` and a draft issue comment in `plan-comment.md`, both written after the implementation, so they are retrospective. Plan-Check returned **accept** with all ten checks passing. It noted that the package is retrospective, that the plan covers 4 of the Node file's 11 scenarios (justified by existing coverage), and, as voice-guide notes, that the draft comment asks two questions at once. After the accept I reworded the draft comment locally (one question, the existing test files named, a note that Node already has these tests) and re-ran plan-check, which accepted again; it then suggested two more comment-only lines, which I added without a third run, and `plan.md` was not changed. I did not post the comment.

**Toolkit**

- Tool: Claude Code, used to analyze the Node.js and Python tests, review duplicate coverage, and implement the four tests; the VS Code terminal and `grep` for inspection. On November 16, plan-check graded the retrospective plan (accept).
- What it produced: The scenario comparison and `python/tests/test_api_utils.py` (four tests, 59 added lines).
- Difficulties: The identified API utility functions had substantial existing coverage, so adding a new test file required avoiding redundant assertions, and two Node/Python behavior differences could not be settled from the spec.
- What changed: I narrowed the plan from mirroring the Node.js file to four focused tests, and left the unresolved differences out of the tests and the production code.

---

## Testing Strategy

The implementation is complete, committed, and included in PR #362. Two observable checks demonstrate it.

**Check 1 — Reproduction before the change versus targeted and full-suite verification after:**
- Before: `ls tests/test_api_utils.py` returned `No such file or directory`, while `node/tests/api-utils.test.ts` exists. The Python baseline was **2,046 passed, 11 skipped, 1 deselected, 2 warnings** (with `tests/test_gates.py::test_unicode_and_file_names_read_like_node` deselected).
- After, targeted: `poetry run pytest tests/test_api_utils.py -v` → **4 passed**.
- After, full Python suite with the same test deselected: **2,050 passed, 11 skipped, 1 deselected, 2 warnings**. That is the baseline plus exactly the four new tests, with no other count changing.

**Check 2 — The repository's own Python and Node.js suites, with documented failures:**
- Python (as recorded November 12, when I opened the PR): the unmodified full suite does not pass on my machine. `tests/test_gates.py::test_unicode_and_file_names_read_like_node` fails on macOS with `OSError: [Errno 92] Illegal byte sequence` (an invalid UTF-8 filename). I did not edit that test; I recorded the original failure and used `--deselect` for the comparison runs above.
- Node.js reference tests: `pnpm exec vitest run tests/api-utils.test.ts` → **11 passed**.
- Node.js full suite: `pnpm test` → **2,462 passed, 2 failed, 57 skipped**. The two observed failures are `tests/gates.test.ts` (a macOS filename encoding error) and `tests/install-manifest.test.ts` (an EEXIST error creating a symlink). The symlink failure was reproduced when run independently. When I recorded these results (November 12), neither Node.js failure had been verified against an unchanged upstream `main`, so I described them as observed failures outside the changed Python test file, not confirmed pre-existing upstream failures; the November 16 check below adds that verification without changing these recorded results.

**Re-run and base comparison (November 16, 2026, evidence in my local `test_evidence.md`).** In a fresh shell with no virtual environment: targeted tests **4 passed**; full Python suite **2,050 passed, 1 failed, 11 skipped** (the `test_gates.py` Unicode test); Node `pnpm test` **2,462 passed, 2 failed, 57 skipped**. I then ran the failures on a clean upstream/main (`fcd20d8`) worktree. **When I opened PR #362 (created 2026-11-13), the results I recorded on November 12 above were accurate and stay as recorded**, including the Python and Node `gates` failures: macOS (APFS) refuses the invalid-UTF-8 file name those tests create. **After the PR was opened, upstream changed those tests:** Node commit `0783f862` (November 14) and Python PR #365, commit `2f1b0617` (merged November 15), so that they tolerate that error. **As of November 16, the Python and Node `gates` tests pass on clean main**, and still fail on my unrebased branch. **Still failing on clean main:** `tests/install-manifest.test.ts` (EEXIST) and `pnpm install --frozen-lockfile`. **Not yet run:** my four tests on top of current main, because I have not rebased. The PR description's note that the Node failures were not verified against main was accurate when written; this check adds the verification.

The final PR diff is one added file, `python/tests/test_api_utils.py` (59 added lines, 0 removed), with no production code changes.

**Toolkit**

- Tool: pytest through Poetry for the Python runs; pnpm and Vitest for the Node.js runs; Git to verify the staged diff.
- What it produced: The before/after Python counts above (2,046 → 2,050 passed), the targeted result (4 passed), the Node.js API result (11 passed), and the Node.js full-suite result (2,462 passed, 2 failed, 57 skipped).
- Difficulties: Two platform-specific failures on macOS (Python `Errno 92` and the Node.js `gates.test.ts` filename error) plus a Node.js symlink EEXIST failure mean I cannot claim any unmodified full suite passes. I also hit a pnpm lockfile mismatch (`ERR_PNPM_LOCKFILE_CONFIG_MISMATCH`, an `overrides` mismatch that also fails on clean upstream/main), and installed with `pnpm install --no-lockfile`.
- What changed: I preserved each failure as evidence instead of editing unrelated tests, used a narrow `--deselect` for the Python comparison, and described the Node.js failures as unverified against upstream `main` at the time; on November 16 I checked them against clean upstream `main` (see the re-run paragraph above).

---

## Implementation Notes

**November 12, 2026 — Selection and claim**

I selected Issue #29 and proposed handling the missing `python/tests/test_api_utils.py` test coverage. I posted a claim comment describing the planned Node/Python comparison and how I would test the change: https://github.com/Raftersecurity/rafter-cli/issues/29#issuecomment-6827269721. I created or checked out branch `test/python-api-utils-parity-29` for the work.

**November 12, 2026 — Environment setup and baseline**

I installed/configured Poetry, confirmed it used `python/.venv` with Python 3.12.1, and ran pytest. The baseline had 2,046 passing tests, one macOS filename-related failure, and 11 skips. A rerun that explicitly deselected the failing case had 2,046 passes and 11 skips. I left the unrelated failing test unchanged and recorded it for the final PR test plan.

**November 12, 2026 — Reproduction and scope refinement**

I verified that `tests/test_api_utils.py` is missing, while the Node.js reference file exists. My `grep` results also identified API-related tests already present in `test_error_handling_gauntlet.py` and `test_config_secret_handling.py`. I decided to compare the scenarios before writing tests, rather than creating redundant tests simply to match a filename.

**November 12, 2026 — API utility test analysis**

I compared the existing Node.js API utility tests with the Python implementation and existing pytest coverage. I found that many scenarios were already covered by `test_error_handling_gauntlet.py`, including exit codes, API key resolution, JSON output, Markdown output, and quiet mode.

I also discovered a potential behavior difference in the `write_payload()` function. The Node.js reference test expects JSON output when Markdown is requested but no Markdown field exists, while Python currently produces an empty string. An existing Python test explicitly checks for that behavior.

This changed my implementation approach. Rather than duplicating all existing tests, I plan to identify missing scenarios and verify the intended behavior against the shared CLI specification before implementing any changes.

**November 12, 2026 — Accidental configuration commit and revert**

I accidentally committed `python/poetry.toml`, a local Poetry configuration file that is not part of the contribution (commit `272df0c`), and reverted it in a follow-up commit (`329acbe`). Both commits are dated November 12, 2026 in `git log` (19:31 and 19:33 local time). The branch `test/python-api-utils-parity-29` therefore has three commits (`451f78d`, the original test commit, then `272df0c` and `329acbe`), but the final PR diff contains only `python/tests/test_api_utils.py`, with no production code changes. Lesson: check `git status` and the staged file list before committing so local setup files are not included.

**November 12, 2026 — Implementation**

I created `python/tests/test_api_utils.py` with four tests, after verifying the existing coverage first so I would not duplicate it:

1. `TestApiConstants::test_api_base_is_rafter_so` — the exact API base URL.
2. `TestApiConstants::test_all_exit_codes_are_distinct_integers` — six distinct integer exit codes. I added this after confirming the existing coverage of the exit codes was incomplete.
3. `TestWritePayloadFormatting::test_pretty_prints_json_when_not_quiet` — pretty-printed JSON with quiet mode disabled.
4. `TestWritePayloadFormatting::test_quiet_json_is_single_line_and_valid` — valid single-line JSON in quiet mode. My scan notes found this one largely overlaps the existing `test_compact_json_when_quiet` in `test_error_handling_gauntlet.py`, which asserts only that there is no newline; the new test adds a `json.loads` validity check.

I deliberately left the Markdown fallback and quiet JSON separator differences unchanged and untested, because their intended parity behavior has not been resolved. The original test commit is `451f78d042bb16bacb9bd79c2d807b81eec7c62e`. All four new tests passed. No production files were changed.

**November 12, 2026 — Testing and PR** (PR #362 is timestamped 2026-11-13T02:00Z, which is the evening of November 12 in my time zone)

Targeted run: 4 passed. Python full suite with one macOS-specific test deselected: 2,050 passed, 11 skipped, 1 deselected, 2 warnings. Node.js API tests: 11 passed. Node.js full suite: 2,462 passed, 2 failed, 57 skipped (details under Testing Strategy). I reviewed the staged diff, then opened PR #362 (https://github.com/Raftersecurity/rafter-cli/pull/362). The final PR diff is only `python/tests/test_api_utils.py`, with 59 additions and 0 deletions. No maintainer feedback has been received yet.

**November 16, 2026 — Ship-gate, plan and evidence (no code change)**

I installed the ship-gate, wrote `ship-manifest.md`, `plan.md`, `test_evidence.md` and `pr_draft.md` (all excluded from Git), ran plan-check (accept) and ran the ship-gate by hand (PASS). I made no commits, did not push, and did not touch PR #362 or post any comment. The branch still has the three commits listed above.

**Toolkit**

- Tool: VS Code terminal, Poetry, pytest, pnpm, Vitest, `grep`, `ls`, and Git, with Claude Code for the analysis and implementation.
- What it produced: A reproducible environment, baseline test output, a clarified scope for the API utility tests, and the committed `python/tests/test_api_utils.py`.
- Difficulties: Poetry's executable was initially not in zsh's PATH; macOS rejected the invalid-byte filename used by one pre-existing test; the target functions already had substantial coverage elsewhere; `python/poetry.toml` was accidentally committed.
- What changed: I configured Poetry, kept the unrelated failures visible in documentation, switched from filename-based implementation to coverage-based analysis, and reverted the accidental configuration file.

---

## Pull Request

**PR Link:** https://github.com/Raftersecurity/rafter-cli/pull/362

**PR Description:** The PR adds `python/tests/test_api_utils.py`, a test-only change for Issue #29 that adds four new pytest cases for the Python API utilities. Based on my earlier analysis, the cases were chosen to avoid duplicating coverage already in `test_error_handling_gauntlet.py` and `test_config_secret_handling.py` (the quiet-mode JSON test still partly overlaps an existing test; see Implementation Notes). The PR deliberately does not change `write_payload`'s `fmt='md'` behavior, which remains an unresolved parity question. Branch: `test/python-api-utils-parity-29`. The PR description links the issue with the wording `Related issue: #29`, not `Closes #29`.

- **The four new tests:**
  1. `TestApiConstants::test_api_base_is_rafter_so` — verifies that `API_BASE` exactly equals `https://rafter.so/api/`.
  2. `TestApiConstants::test_all_exit_codes_are_distinct_integers` — verifies all six API exit codes are integers and unique, including `EXIT_CONFIRMATION_REQUIRED`.
  3. `TestWritePayloadFormatting::test_pretty_prints_json_when_not_quiet` — verifies that `write_payload()` produces indented JSON with a newline when quiet mode is disabled and that the output parses back to the original data.
  4. `TestWritePayloadFormatting::test_quiet_json_is_single_line_and_valid` — verifies that quiet-mode output contains no newline and parses into the original data.
- **Final PR diff:** one added file, `python/tests/test_api_utils.py`; 59 added lines, 0 removed lines. No production code changes.
- **Commits:** three. `451f78d` added the API utility tests (full SHA `451f78d042bb16bacb9bd79c2d807b81eec7c62e`); `272df0c` accidentally included `python/poetry.toml`; `329acbe` reverted that configuration-file commit. `python/poetry.toml` therefore does not appear in the final diff (see Implementation Notes).
- **Testing evidence:**
  - Python targeted tests: 4 passed.
  - Python full suite with one macOS-specific test deselected (`tests/test_gates.py::test_unicode_and_file_names_read_like_node`): 2,050 passed, 11 skipped, 1 deselected, 2 warnings. This is the baseline 2,046 plus the 4 new tests.
  - Node.js API tests: 11 passed.
  - Node.js full suite: 2,462 passed, 2 failed, 57 skipped. The two failures were observed outside the changed Python test file:
    - `tests/gates.test.ts` — macOS rejects a filename containing invalid UTF-8 bytes.
    - `tests/install-manifest.test.ts` — an EEXIST error while creating a symlink at a `.rafter-new` path. This failure was reproduced when run independently.

    This is what the live PR description says, as written when I opened the PR: neither failure had been verified against an unchanged upstream `main` checkout, so they are described as observed failures, not confirmed pre-existing upstream failures. That was accurate then. My November 16 check against clean `main` (`fcd20d8`) is recorded under Testing Strategy: both `gates` failures were fixed upstream after the PR was opened, and `install-manifest` still fails on `main`. The corrected description is only a local draft and has not been posted. The PR changes no Node code.
- **AI assistance disclosure:** The PR description states: "Tests were implemented with assistance from Claude Code (Claude Sonnet 5.5). I reviewed the implementation and test results. Co-authored by Claude Code". The original test commit (`451f78d`) also carries the trailer `Co-Authored-By: Claude Sonnet 5.5 <noreply@anthropic.com>`.

**Maintainer Feedback:**

- As of November 16, 2026: none (no reviews or comments on PR #362 or on my claim).

**Status:** Open and awaiting review, checked November 16, 2026: not merged, 0 reviews, 0 comments, mergeable, no CI checks reported. The live description still has the older wording about the Node failures; a corrected draft is in my local `pr_draft.md` and is not posted.

**Toolkit**

- Tool: On branch `test/python-api-utils-parity-29`, I used:
  - Claude Code to analyze Node.js/Python parity, propose a focused test plan, implement the four tests, review duplicate coverage, and review the staged changes.
  - The VS Code terminal to run development, inspection, and testing commands.
  - Poetry to manage the Python virtual environment and run Python tooling.
  - pytest to run the four targeted Python tests and the larger Python suite.
  - pnpm to install Node.js dependencies and run the project's test commands.
  - Vitest to run the Node.js API reference tests and the broader Node.js tests.
  - Git to check branch status, stage the intended test file, and verify the staged diff.
  - GitHub to host the issue, claim comment, commits, and pull request.

  - Ship-gate (November 16, 2026): `python3 ~/.claude/ship-gate/check_gate.py --branch --base main --issue <issue #29 URL> --title "test: add Python API utility parity coverage (#29)" --body-file pr_draft.md`. It ran my four manifest checks and then my pr-precheck, and printed `ship-gate: PASS`.

  I have not used a PR-monitor tool for this PR.
- What it produced: Pull request #362 (https://github.com/Raftersecurity/rafter-cli/pull/362) containing the new `python/tests/test_api_utils.py` with four tests, and the test results recorded above.
- Difficulties: `python/poetry.toml`, a local Poetry config file, was accidentally included in commit `272df0c` alongside the test work. The Node.js full suite also showed two failures outside my changes (see testing evidence), which I had not verified against upstream `main` when I opened the PR (checked November 16; see Testing Strategy).
- Ship-gate difficulties: the gate normally runs before `gh pr create`, but PR #362 was already open, so I ran it by hand and did not open or change a PR. My `pr_draft.md` keeps `Related issue: #29` and not `Fixes #29`, because one test file doesn't finish the issue, so I passed the issue with `--issue`. Checking on November 16 showed that two of the three failures I recorded when I opened the PR (November 12 and 13) have since been fixed upstream, so on current main only `install-manifest` and the frozen pnpm install still fail.
- What changed: I reverted the accidental file in commit `329acbe`, leaving a three-commit branch whose final diff is only the intended test file (59 additions, 0 deletions). In future I will review the staged file list before each commit.

---

## Learnings and Reflections

**Technical Skills Gained**

I learned how to configure and verify a Poetry-managed Python environment, run a baseline pytest suite, isolate a failing test with `--deselect`, and inspect source functions and test coverage using command-line searches. The most important code-reading insight is that a missing test filename does not mean the feature has no tests: I found `resolve_key` and `write_payload` already covered in `test_error_handling_gauntlet.py` and `test_config_secret_handling.py`, so some of what the issue listed as missing already existed. Comparing the Node.js and Python tests also showed me that the two implementations can differ in small behaviors, such as the Markdown fallback in `write_payload`, and that a difference is not automatically a bug. I used pytest fixtures and JSON assertions (parsing output back to the original data) to write the four new tests.

**Challenges Overcome**

Poetry was installed but initially unavailable through my terminal PATH; locating its executable under `~/Library/Python/3.12/bin/poetry` resolved the setup problem. The baseline suite then failed on a macOS filename operation with `OSError: [Errno 92]`, so I documented the unchanged result and reran the other tests with that one case deselected. On the Node.js side I hit a pnpm lockfile mismatch (an `overrides` mismatch that also fails on clean upstream/main; I installed with `pnpm install --no-lockfile`) and documented two more platform-specific failures (`tests/gates.test.ts` and the `tests/install-manifest.test.ts` symlink EEXIST error) without claiming they existed upstream, since I had not yet checked them against an unchanged `main`; on November 16 I did, and found that the `gates` failure had been fixed upstream after my PR was opened while `install-manifest` still fails there. Existing coverage forced me to narrow the plan to four focused tests (although the quiet-mode JSON test still largely overlaps an existing one), and I left the unresolved Markdown fallback and quiet JSON separator differences alone rather than guess at the intended behavior. Finally, I accidentally committed `python/poetry.toml`, and reverted it so the final PR diff contains only `python/tests/test_api_utils.py`.

The Issue-Scout run on November 16 added a different kind of lesson. Its REJECT verdict for Issue #29 exposed a limitation in my rubric more than a problem with the contribution: the rubric classified the issue as an umbrella issue even though the maintainer explicitly allowed independent contributions, and it counted my own PR #362 against the "not already being worked on" check, which should not disqualify an issue in a retrospective evaluation. The issue would have passed the availability check before I claimed it on November 12 but still failed the umbrella-issue criterion, so the two reasons have to be kept apart. The current repository was also a better guide than the issue text, since four of the five listed test files already existed, and comparing the Node.js and Python tests kept me from duplicating them. I also learned to label a tool evaluation as retrospective, because the scan ran four days after my decision and cannot be presented as the reason I chose the issue.

Building Voice Guard taught me how a communication guard can keep my upstream habits consistent: a hook that reads every outgoing `gh` comment against my own rules turned a style guide I had been trusting myself to follow into something that actually stops a deadline promise or a repeated ping, and quotes the rule it broke. Deciding what to do with commands the guard cannot parse was the real design question. Failing closed is the safer default because an unreadable command could be an unchecked post, but it also produced false positives, and the hook blocked my own shell commands that only contained GitHub comment text inside heredocs. I worked around that by writing the text with the editor tool, and the heredoc problem is still unresolved. Testing both compliant and noncompliant drafts mattered for the same reason: my first professional sample was flagged by the stricter claim rule, which showed that the sample was wrong, not the rule, and I fixed the sample. I also wrote a 39-line `CLAUDE.local.md` in my Rafter CLI clone so a future Claude Code session starts with the issue, PR status, test commands, known failures, and AI contribution requirements, kept out of Git through `.git/info/exclude`; I have not yet checked that it loads in a fresh session. Finally, the guard did not protect my real claim or PR #362, because it was installed afterward, and the later pass on a copy of my posted claim is a retrospective check, not evidence of a guarded post. Building and testing it showed me that safeguards in AI-assisted development are only as trustworthy as the cases I test and the limits I record.

**What I'd Do Differently Next Time**

I would check the repository's current files and existing test cases before claiming a specific test-file task, because issue descriptions can become outdated. I would capture environment versions, baseline output, and command logs immediately so that PR evidence is easier to assemble; I still lack some versions as a result. I would also review `git status` and the staged file list before every commit, since I committed `python/poetry.toml` by accident and needed a revert commit to fix it. I would also improve the Issue-Scout rubric before using it to select my next contribution: checking that an issue's premise is still true, recognizing independently claimable tasks inside umbrella issues, and separating my own claims from other contributors' work. Those fixes are still proposals; the only rubric change I have made is applying the staff `scope-feasible` scope patch to my installed skill copy, which does not implement them.

---

## Resources Used

- [Rafter CLI Issue #29](https://github.com/Raftersecurity/rafter-cli/issues/29) — issue scope and contribution discussion.
- [My issue claim comment](https://github.com/Raftersecurity/rafter-cli/issues/29#issuecomment-6827269721) — records the proposed test file and testing plan.
- [Rafter CLI CONTRIBUTING.md](https://github.com/Raftersecurity/rafter-cli/blob/main/CONTRIBUTING.md) — development setup, test commands, PR requirements, and AI disclosure rules.
- [Node.js reference tests](https://github.com/Raftersecurity/rafter-cli/blob/main/node/tests/api-utils.test.ts) — test scenarios to compare with Python coverage.
- [Python API utilities](https://github.com/Raftersecurity/rafter-cli/blob/main/python/rafter_cli/utils/api.py) — functions and constants under investigation.
- [Shared CLI specification](https://github.com/Raftersecurity/rafter-cli/blob/main/shared-docs/CLI_SPEC.md) — canonical behavior reference to consult during implementation.
