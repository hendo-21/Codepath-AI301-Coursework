# Procedure: how this skill grades a plan package

## Read order

1. In live mode, read `scope.md` and confirm the issue is inside the scoped source; note any house rules.
2. In both modes, read the issue description and note the expected vs. actual behavior. This will be used later to judge the plan package against.
3. In live mode, read the issue comment thread's claim comment and reproduction report; the thread may contain multiple claim comments and reports from other students, so read and judge only those authored by `hendo-21`. In eval mode, read the repro section of the eval package. In both modes, note whether the author was able to reproduce the issue and why or why not, and note the author's diagnosis of the root cause; this is the baseline the plan package's stated diagnosis gets checked against.
4. In both modes, read `rubric.md` and `references/evidence-guide.md`. List the rubric's checks and verdict rule.
5. Read the whole plan package before grading anything. The deciding evidence is usually whether the plan's artifacts describe a fix based in the evidence of the repro report.

Why the order matters: beginning with `scope.md` confirms you're looking in the right place. Reading the issue description, claim comment, and repro report provides critical context about the issue the plan package claims to fix; without it, there's nothing to evaluate the plan package against. `rubric.md` and `references/evidence-guide.md` provide instructions on how to evaluate the package and where to look; without it package evaluation is not grounded in anything meaningful. The plan package is read last once all the relevant context is gained because the package is judged against these artifacts and not just the content present.

## Evidence gathering

**Diagnosis & grounding (diagnosis-based)**
- Live mode: Pull the repro report from the thread at the issue URL and the stated cause or diagnosis from the draft plan package.
- Eval mode: Pull from the repro section and candidate plan section of the eval package.
- Record: The stated cause or author's diagnosis of the bug described in the issue and reproduced with evidence in the repro report.

**Scope (scope-bounded)**
- Live mode: Pull from the draft plan package. Look for words like "scope" or "in: ..." and "out: ..."
- Eval mode: Pull from the eval package candidate plan section. Look for words like "scope" or "in: ..." and "out: ...".
- Record: The stated specific files and / or modules in scope. If out-of-scope files are named, record those too.

**Executability (stranger-executable)**
- Live mode: Pull from the draft plan package section that describes the implementation plan. 
- Eval mode: Pull from the eval package's candidate plan section, and the section of the package that describes the implementation plan. 
- Record: the implementation procedure stated in the plan.

**Test plan (tests-observable)**
- Live mode: Pull from the draft plan's named testing / verificaton section, or where the draft plan describes the approach for testing the planned fix and the test's expected outcome.
- Eval mode: Pull from the eval package's candidate plan where the plan describes the approach for testing the planned fix and the test's expected outcome.
- Record: the testing procedure and expected outcome the author will use to validate their proposed plan fixes the issue.

**Honesty (comment-faithful, honesty-calibrated)**
- Live mode: Pull from the draft plan's comment and discrepancy evidence from draft's implementation plan section, and from the thread's stated asks. Also pull the plan's own risk / assumption / caveat language, and compare it against the strength of the diagnosis evidence gathered above.
- Eval mode: Pull from the candidate plan comment and discrepancy evidence from the candidate plan's implementation plan section, and from the thread's stated asks. Also pull the candidate plan's own risk / assumption / caveat language, and compare it against the strength of the diagnosis evidence gathered above.
- Record (comment-faithful): the claim comment, compared against both the plan and the thread. If the comment promises something the plan doesn't describe, record that as a discrepancy. Separately, check the thread for anything explicitly asked for (by reviewers or house rules); if the plan addresses it but the comment fails to mention it, record that omission too. Both kinds of discrepancy should be presented to the author as feedback.
- Record (honesty-calibrated): any point where the plan states something as settled fact (e.g. "this will fix it," "the cause is X") that the diagnosis evidence only partially supports or leaves untested; and any point where the plan does correctly flag a genuine unknown as a risk or assumption. Note both, since the second is what a pass looks like.

**Comms (convention-friendly)**
- Live mode: Pull from the entire draft plan package.
- Eval mode: Pull from the eval package's candidate plan and candidate plan comment.
- Record: Discrepancies between the content and structure of the plan package, and the repo's stated templates / developer guidelines / contribution policies.

**Consistency (internal-consistency)**
- Live mode: Pull from the entire draft plan package.
- Eval mode: Pull from the eval package's entire candidate plan and candidate plan comment.
- Record: specific examples of leftover copy-pasted text and instances where a claim doesn't match the evidence that follows it, found within the candidate plan and plan comment. (The claim comment and repro report are graded separately, under `repro-check`; note anything odd there only as incidental feedback, not as part of this check's verdict.)

## Check execution

Run the checks in the following order:
1. diagnosis-based
2. scope-bounded
3. stranger-executable
4. tests-observable
5. internal-consistency
6. comment-faithful
7. honesty-calibrated
8. convention-friendly

If the evidence a check needs is genuinely absent from the package (e.g., no testing section at all), grade that check `F` and say what's missing; don't mark it `?`. Reserve `?` for evidence that exists but is ambiguous to interpret.

A check may be graded from the notes taken during evidence gathering without re-reading the full package, unless grading it raises a question evidence gathering didn't answer, in which case re-read the relevant part.

## Verdict assembly

Each check gets a `P` for pass, `F` for fail, or `?` for unclear. Once all checks are graded, apply the verdict rule from `rubric.md` to establish a final grade. Apply the following guide for what evidence gets quoted in the output for the deciding check. 

| Check | Evidence to quote |
|---|---|
| diagnosis-based | Pass: the diagnosis or cause identified in the repro report restated in the plan package artifacts. Fail: a diagnosis or cause stated in the repro report but omitted from the plan package artifacts |
| scope-bounded | Pass: the specific files or modules in, and if given out, of scope. Fail: a package lacking a description of scope has nothing to quote |
| stranger-executable | Pass: a one-sentence summary of the stated implementation plan. Fail: a package lacking executable steps has nothing to quote; one that contains steps but the steps are so vague as to not be executable by someone with no issue context the steps should be quoted |
| tests-observable | Pass: a one-sentence summary of the stated verification plan. Fail: quote the verification steps and say what observable outcome is missing from them. If a verification approach is missing entirely, state that. |
| comment-faithful | Pass: a one sentence summary stating the consistency of the comment and plan. Fail: specific text from the comment that promises things not supported by the plan, or specific text from the thread the comment omits despite the plan addressing it. |
| honesty-calibrated | Pass: the specific risk, assumption, or caveat language the plan uses for its genuine unknowns. Fail: the specific claim the plan states as settled fact, next to what the diagnosis evidence actually supports. |
| convention-friendly | Pass: a one sentence summary stating the adherence to repo policies and standards. Fail: specific text from the plan compared to the stated repo policy that highlights where they differ. |
| internal-consistency | Pass: a one sentence summary stating the claim consistency throughout. Fail: specific examples from the plan and comment evidence of copy-paste relics or mismatching claims. |