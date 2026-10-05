# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis-based | The plan's fix, compared to the reproduction report's evidence | The plan's fix addresses the cause the reproduction evidence points to, not only a symptom the evidence also shows | required |
| scope-bounded | The plan's described approach | The plan names the specific files or modules it will change, with no open-ended language ("and related areas", "etc.") suggesting the boundary isn't fixed. A list of out-of-scope files or areas may be named, but omission of such out-of-scope areas does not cause this check to fail so long as specific files or modules are named as in-scope | required |
| stranger-executable | The plan's fix implementation procedure | Procedure names specific files and steps such that a developer unfamiliar with the investigation could know which file to open first and which change to make, without having to ask any clarifying questions | required |
| tests-observable | The plan's verification / testing section, compared to the thread's reproduction report | The testing plan describes an observable, checkable outcome (something a stranger could run and see pass or fail) that would confirm the behavior identified in the reproduction report is fixed | required |
| comment-faithful | The plan's comment, compared to the plan itself | The comment promises only what the plan actually describes; it does not omit something the thread asked for that the plan does address | required |
| honesty-calibrated | The plan's stated confidence (claims, risks, caveats), compared to what the diagnosis evidence actually supports | The plan flags genuine unknowns as unknowns rather than asserting them as settled; it does not state a risk, assumption, or untested step as fact | required |
| convention-friendly | The entire plan package compared to the repo's issue templates / developer guidelines / contribution policy | Any content the policies require is present, judged on substance present or absent, not on whether it mirrors a template | required |
| internal-consistency | Every label, heading, and summary sentence in the candidate plan and plan comment, compared to the content it introduces | Each label/heading names what actually follows it, and each summary sentence's claim matches the evidence right after it; no leftover or copy-pasted text describing a different case | required |

## Verdict rule

A plan package that passes all required checks is ready to post. If any 
check fails, hold the post. Unclear counts as a fail.