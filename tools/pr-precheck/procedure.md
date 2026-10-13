# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

1. Live mode: read `scope.md`, confirm the PR's repo is the scoped repo, and note the house rules. Read `voice-guide.md` and note its rules (they inform the summary only). Eval mode: skip both.
2. Both modes: read `rubric.md` and `references/evidence-guide.md`. List the checks, their pass conditions, and the verdict rule, so you know which facts to note while reading.
3. Both modes: read the issue description. Note the expected vs. actual behavior and the repro steps.
4. Read the repro report, which is context for the plan and for the `tested` check.
   - Live mode: read the author's repro report comment in the issue thread (or the house repro pack, if routed to one). Read only comments authored by the PR author, since the thread may hold other students' claims and reports. The author supplies their GitHub handle when invoking the skill; if no handle was given, ask for it before reading the thread, and do not look for it in the skill files.
   - Eval mode: read the repro report in the thread highlights or the plan-context block.
   - Note: the failing steps, the before-state output, and the diagnosis.
5. Read the plan, which is the baseline the PR is graded against.
   - Live mode: read `plan.md` (or the house plan, if routed to one), and the plan comment in the thread if one was posted, again only from the PR author.
   - Eval mode: read the plan-context block and the repo facts.
   - Note: the scope pair (in and out), the implementation steps, the verification plan, and every deviation note.
6. Read the repo's asks.
   - Live mode: read the PR template, `docs/CONTRIBUTING.md`, and any disclosure policy.
   - Eval mode: read the repo-facts block's template and disclosure asks.
   - Note: required sections, issue-link format, disclosures, commit format, and required test, lint, or CI commands.
7. Read the PR itself, in this order: the diff, then the commits, then the test evidence, then the draft title and description.
   - Live mode: `git diff main...HEAD` from the clone's top folder, then `pr_draft.md`, then `test_evidence.md`.
   - Eval mode: the candidate PR block's sections.
   - Note: the changed files and the purpose of each hunk, any debris, what each test-evidence entry shows, and every claim the title and description make.

Why the order matters:
- `scope.md` first confirms you are looking in the right place.
- The rubric comes before the evidence so you know which facts to record while reading.
- The issue, the repro report, and the plan come before the PR because every later check is a side-by-side against them: the title against the diff and the issue, `no-drift` against the plan's scope and deviation notes, `tested` against the plan's verification plan, issue repro steps, and the repo's required checks.
- Repo asks come before the PR so you know what the repo requires before you see what the PR does.
- The diff is read before the description so the description's claims are tested against what the diff actually changes, not the reverse. An author's framing can make a diff look more aligned than it is.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

Take every fact from the sources named below, and record "absent" for any source that is missing.

### Plan fidelity (checks: clear-title, description-matches-diff, no-drift)

**clear-title**
- Live mode: Pull the title from `pr_draft.md`, the diff from the branch, and the issue from the issue URL.
- Eval mode: Pull the title and diff from the candidate PR block and the issue from the issue section.
- Record: What the title claims to change, and what the diff actually changes. Note anything the title claims that the diff doesn't contain, and anything significant in the diff the title doesn't convey. Note whether a partial fix is named as partial.

**description-matches-diff**
- Live mode: Pull the description from `pr_draft.md`, the diff from the branch, and the plan and its deviation notes from `plan.md`.
- Eval mode: Pull the description and diff from the candidate PR block and the plan from the plan-context block.
- Record: Each claim the description makes about what changed, why (the root cause, compared with the repro report's diagnosis) and how it behaves now, each set beside the diff. Record any "follows the plan" claim and whether the diff's departures from the plan are disclosed.

**no-drift**
- Live mode: Pull the diff from the branch, and the scope pair and deviation notes from `plan.md`.
- Eval mode: Pull the diff from the candidate PR block, and the scope pair and any deviation notes from the plan-context block.
- Record: Every planned item, and every changed file and hunk. Mark each planned item as present in the diff, or omitted with where the omission is disclosed (deviation notes or description). Mark each changed file or hunk as covered by the plan, required by repo policy (for example a test file or changelog entry), or a deviation, with where it is disclosed and justified. Anything else is unplanned.

### Test evidence (check: tested)
- Live mode: Pull the test evidence from `test_evidence.md`, the verification plan from `plan.md`, the repro steps and before-state from the issue description and repro report (read order, steps 3 and 4), and the repo's required test, lint and CI commands from the PR template or `CONTRIBUTING.md`.
- Eval mode: Pull the test evidence from the candidate PR block, the verification plan from the plan-context block, the repro steps from the issue and thread highlights, and the required commands from the repo facts.
- Record: Two lists. List one is the plan's verification steps; list two is the repo's required commands. For each entry, record whether pasted output or a screenshot is present, whether it visibly matches the claimed command, whether it shows the post-fix result, and, if the step was not run, whether that is disclosed with a reason.

### Diff quality (check: reviewable)
- Live mode: Pull the diff and the commits from the branch.
- Eval mode: Pull the diff and commits from the candidate PR block.
- Record: Each hunk, marked as contributing to the fix or as debris (formatting churn, dead code, leftover debug code, commented-out blocks, or an unrelated edit), including inside files the plan named. Also record any commit that carries unrelated or noisy changes.

### Standards and comms (checks: follows-repo-asks, internal-consistency)

**follows-repo-asks**
- Live mode: Pull the repo's PR template (usually under `.github/`), `docs/CONTRIBUTING.md`, and any disclosure policy. Read them against the title and description in `pr_draft.md` and the commit messages.
- Eval mode: Pull the PR template and disclosure asks from the repo-facts block. Read them against the candidate PR's title, description and commits.
- Record: Each ask the sources make (issue link, required sections, disclosures including AI-use, commit format), and where in the title, description or commits it is satisfied on substance. Do not grade on layout.

**internal-consistency**
- Live mode: Pull the whole of `pr_draft.md`.
- Eval mode: Pull the whole candidate PR block (title and description).
- Record: Each heading or label whose following content does not match it, each summary sentence the content beneath it doesn't support, and any leftover or copy-pasted text describing a different case.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

Run the checks in the following order:
1. clear-title
2. description-matches-diff
3. no-drift
4. tested
5. reviewable
6. follows-repo-asks
7. internal-consistency

Run every check, even after one fails; the summary needs a line per check and the verdict rule needs all the grades.

If the evidence a check needs is genuinely absent from the package (e.g., no test evidence at all), grade that check fail and say what's missing; don't mark it unclear. Reserve unclear for evidence that exists but is ambiguous to interpret.

A check may be graded from the notes taken during evidence gathering without re-reading the full package, unless grading it raises a question evidence gathering didn't answer, in which case re-read the relevant part.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

Grade each check pass, fail, or unclear (the labels used in the JSON output). Apply the verdict rule from `rubric.md`: accept only if every required check passes. Unclear counts as a fail.

The deciding check is the first failing or unclear check in rubric order. Quote evidence for the deciding check using the table below. If the verdict is accept, quote the pass evidence for every check.

| Check | Evidence to quote |
|---|---|
| clear-title | Pass: a one-sentence summary of how the title claims neither more nor less than the diff shows. Fail: the part of the title that over- or under-claims, next to the diff content it misdescribes, or a partial fix presented as complete. |
| description-matches-diff | Pass: a one-sentence summary of how the description's claims about what changed and why are borne out by the diff. Fail: the description claim that the diff does not back up, next to what the diff shows, or the "implemented as planned" claim next to the plan departure. |
| no-drift | Pass: a one-sentence summary of how the changed files and hunks match the plan's scope and deviation notes. Fail: the planned item missing from the diff with no disclosure, or the changed file or hunk the plan and deviation notes do not cover. |
| tested | Pass: a one-sentence summary of how the test evidence covers the verification plan and the repo's required checks and shows the post-fix result. Fail: the verification step or required check that has no output, the output that does not match the claimed command, or the undisclosed gap. |
| reviewable | Pass: a one-sentence summary stating that every hunk contributes to the fix and no debris remains. Fail: the specific hunk that is debris, formatting churn, or unrelated, including inside plan-named files. |
| follows-repo-asks | Pass: a one-sentence summary of how the title, description, and commits satisfy the repo's stated asks. Fail: the specific ask that is not satisfied, quoted from the template, `CONTRIBUTING.md`, or disclosure policy, and where it should appear. |
| internal-consistency | Pass: a one-sentence summary stating that the draft's headings and summary sentences match their content. Fail: the specific heading or sentence next to the content that contradicts it, or the leftover copy-pasted text. |
