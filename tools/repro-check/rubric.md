# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env_recorded | Candidate repro report / Environment | The report states language/tool version, OS, shell etc.; when the issue names a target version, the report either matches it or explicitly reconciles the difference. Silence on the issue's version fails | required |
| followable_steps | Candidate repro report / steps | Steps start from a starting state matching the issue's stated preconditions and proceed through concrete actions (commands, code, or screenshots) sufficient for a stranger to reach the same output without a missing step | required |
| behavior_matches | Expected vs actual output in the candidate repro report | Output demonstrates the issue's specific behavior, not an adjacent one, or is a correctly-targeted attempt that honestly failed to trigger it and names what differed | required |
| claim_honesty | Candidate claim comment's stated conclusion, compared to the repro report's evidence | The conclusion matches what the report's evidence shows | required |
| comms_conventions | Claim comment and repro report content, compared to the repo's issue template / contribution policy | Any disclosure or content the repo's stated policy requires is present, judged on substance present or absent, never on whether it mirrors a template's headings | required |


## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept the reproduction package if all required checks pass. Unclear counts as a fail. Preferred checks are flags for the user's development and do not change the verdict. 
