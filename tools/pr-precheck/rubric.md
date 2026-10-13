# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| clear-title | The draft PR title, read against the diff and the issue | A maintainer reading only the title would correctly identify what the diff changes. The title claims neither more nor less than the diff does. A title that names a disclosed partial fix as partial passes. | required |
| description-matches-diff | The draft PR description, read against the diff and the plan (including its deviation notes) | Every claim the description makes about what changed, why (root cause, where the issue has one), and how it behaves now is borne out by the diff. If the description says the work follows the plan, the diff must actually follow it; a description that says "implemented as planned" while the diff departs from the plan fails. A disclosed shortfall passes. An undisclosed one fails. | required |
| no-drift | The diff's changed files and hunks, read against the plan's stated scope and deviation notes | Every planned item is in the diff, or its omission is disclosed in the plan's deviation notes or the PR description. Every changed file or hunk is covered by the plan, or is a deviation that is disclosed and justified. Files the repo's own policy requires (for example a test file or changelog entry) count as covered. Anything else unplanned fails. | required |
| tested | The test evidence (live: `test_evidence.md`; eval: the bundle's test-evidence block), read against the issue's repro steps, the plan's verification plan, and the repo's required checks (the PR template, `CONTRIBUTING.md`, or the repo-facts block) | Each failure mode the issue's repro names is shown fixed: the command run after the fix on the changed path and what it printed, as a transcript or screenshot. The plan's other steps and the repo's required checks are each reported with what was run and the result; output isn't required. Any step not run is disclosed with a reason. A repro not re-run or run only on the unchanged path, a bare "tests pass", or an undisclosed gap fails. | required |
| reviewable | The diff and the commits | Every hunk contributes to the fix. No formatting churn, dead code, leftover debug code, or unrelated hunks appear, including inside files the plan named. | required |
| follows-repo-asks | The PR template, `docs/CONTRIBUTING.md`, and any disclosure policy (live), or the repo-facts block's template and disclosure asks (eval), read against the title, description, and commits | Every ask those sources make of a PR is satisfied on substance (for example issue link, required sections, disclosures, commit format). The check is not whether the description mirrors the template's layout. | required |
| internal-consistency | Each heading, label, and summary sentence in the draft PR, read against the content directly beneath it | Each heading names what follows it. Each summary sentence is supported by the content under it. No leftover or copy-pasted text describes a different case. | required |

## Verdict rule

Accept if every required check passes, and hold if not. Preferred checks never change the verdict, and unclear counts as a fail.
