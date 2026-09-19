# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| active_release | repo-facts/latest release (date) | The latest release date is within 12 months of captured date in eval item header section. If none is published refer to repo-facts/last push to any branch. | required |
| unclaimed | repo-facts/this issue/assignees and the issue comment thread | The issue is clearly unassigned according to the issue comment thread (eg. issue is intentionally unassignable, has been unassigned due to contributor inactivity, does not contain comments about work completed by another contributor within the last 30 days). Check issue/assignees as a fallback | required |
| stale_issue | issue comment thread | If there are comments, the time between comments is fewer than 90 days | required |
| clear_scope | issue body | The issue must clearly define a single concrete defect or focused feature request, even if it suggests multiple potential fixes or itemizes missing elements. Only reject issues that serve as open-ended discussions asking for design direction, broad umbrella epics, or posts lacking a specific problem statement. | required |
| has_labels | issue/labels ex. "bug", "good first issue", "easy to fix" | The issue contains a label indicating the type of work, priority, or if it's beginner friendly | required |
| maintainer_responsive | repo-facts/maintainer first-response sample | maintainer comments within 45 days of PR being opened for any of the 5 samples | preferred |
| has_contributing_docs | repo-facts: contribution policy | CONTRIBUTING.md is in the repo AND/OR there is a statement on AI usage | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept an issue if all required checks pass. If any required check fails, reject the issue. Use preferred weight to rank accepted issues. If unsure on any required check, reject the issue but use the uncertainty to rank rejected issues.
