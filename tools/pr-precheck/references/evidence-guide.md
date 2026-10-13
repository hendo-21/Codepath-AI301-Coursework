# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift; checks: clear-title, description-matches-diff, no-drift)

<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->

**Where it lives**
- Live mode: the plan's scope pair and deviation notes are in `plan.md` (or the house plan). The diff is on the branch. The title and description are in `pr_draft.md`.
- Eval mode: the scope pair and any deviation notes are in the plan-context block. The title, description, and diff are in the candidate PR block.

**What good looks like**
- clear-title: a maintainer reading only the title would correctly identify what the diff changes. Nothing the title names is missing from the diff, and nothing significant in the diff is missing from the title. A disclosed partial fix is named as partial.
- description-matches-diff: every claim about what changed, why, and how it behaves now can be pointed to in the diff. If the description says the work follows the plan, every planned item is in the diff or its omission is disclosed. A disclosed shortfall is fine; an undisclosed one is drift.
- no-drift: every planned item appears in the diff or has a disclosed omission, and every changed file or hunk is covered by the plan, required by repo policy (for example a test file or changelog entry), or a disclosed and justified deviation. Drift runs both ways: more than the plan, or less with no note.

## Test evidence (harness category: not-tested; check: tested)

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

**Where it lives**
- Live mode: the evidence is in `test_evidence.md`. The plan's verification plan is in `plan.md`. The repro steps and before-state are in the issue and the repro report. The repo's required commands are in the PR template and `CONTRIBUTING.md`.
- Eval mode: the evidence is in the candidate PR block's test-evidence section. The verification plan is in the plan-context block. The repro steps are in the issue and thread highlights. The required commands are in the repo-facts block.

**What good looks like**
- Every failure mode the issue's repro names is shown fixed: the command run after the fix on the changed path and what it printed, as a transcript or screenshot, for example the failing repro from the report now passing.
- The plan's other steps and the repo's required checks are each reported with what was run and what it showed, for example "`cargo test -p nu-protocol` passes (312 tests)". Output is not required for these.
- Any step not run is disclosed with a reason. A bare "tests pass" with no command named does not count.

## Diff quality (harness category: unreviewable; check: reviewable)

<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

**Where it lives**
- Live mode: the diff and commits are on the branch.
- Eval mode: the diff and commits are in the candidate PR block.

**What good looks like**
- Every hunk contributes to the fix. There is no formatting churn, dead code, leftover debug code, commented-out blocks, or unrelated edits, including inside files the plan named.

## Standards and comms (harness category: standards-wall; checks: follows-repo-asks, internal-consistency)

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->

**Where it lives**
- Live mode: the repo's PR template (usually under `.github/`), `docs/CONTRIBUTING.md`, and any disclosure policy. The draft title and description are in `pr_draft.md`, and the commit messages are on the branch.
- Eval mode: the template and disclosure asks are in the repo-facts block. The title, description, and commits are in the candidate PR block.

**What good looks like**
- follows-repo-asks: every ask the template, contributing guide, and disclosure policy make is satisfied on substance, for example the issue link, the required sections filled with real content, the AI-use disclosure, and the commit format. Matching the template's layout is not the test.
- internal-consistency: every heading names what follows it, every summary sentence is supported by the content under it, and no leftover or copy-pasted text describes a different case.
