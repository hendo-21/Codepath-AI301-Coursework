# I built a Claude skill to vet PRs before they're opened, and tested it on a PR that was later merged in Python's `typeshed`

## Overview

`pr-precheck` is a Claude skill that answers the question: is this PR ready to submit? It reads the diff, commits, test evidence, title and description against my stated plan and the issue it seeks to resolve, and if any one of its seven required checks fails or is unclear, it issues a HOLD verdict. `pr-precheck` helps me catch scope creep, unsupported or mis-supported claims, and internal inconsistencies, and helps me show up repo-ready with a PR that is grounded in repo rules and with language that is professional and respects a maintainer's time. I wrote the rubric by which it grades, the procedure that tells it how to read the package and gather evidence, and the refusal and grading rules. I also described where evidence lives for each check and what good looks like, and I wrote a voice guide to grade the language I use in my draft to ensure I show up to these spaces with professionalism. I leveraged this new skill to audit my PR for an issue in Python's `typeshed` project, which provides type annotations for Python's official and third-party libraries. I resolved incomplete stubs for the network analysis library, `networkx`, in 10 `networkx` functions by reviewing upstream source code to confirm the node type for the return graph of those functions, and changing them from `Graph[Incomplete]` to `Graph[_Node]` in the stub files. The skill caught an accidental code change in the diff that was unplanned, which I reverted before opening my PR. The PR was merged the next day with no feedback. [PR #16729](https://github.com/python/typeshed/pull/16729)

## What happened

I built a procedure that provides the model with instructions on how to read the PR package, what evidence to gather for each rubric check, the order the checks should run in, and what to quote when a check passes or fails. I created refusal and grading rules like "unclear defaults to fail", and provided examples of where to find the evidence needed for a rubric check, and what good evidence looks like for each check. To ensure I show up to the open-source community with a high standard of professionalism, I provided the tool with a voice guide. Similarly, the voice guide provides the skill with a check on the language of my draft PR to keep language that could erode trust with the community out of my PRs. For example, in my voice guide I have a rule of not committing to timelines, to ensure that I don't overcommit to a task and be seen as unreliable. 

It was critical to me that the skill enforced consistency throughout the PR package. Consistency with the issue, the test evidence, the stated plan, the actual code changes, and with the claims made in the title and PR body themselves. I achieved this in how I ordered actions in the procedure, e.g. "The diff is read before the description so the description's claims are tested against what the diff actually changes, not the reverse. An author's framing can make a diff look more aligned than it is.", and in the pass condition for each rubric check.

My `typeshed` issue was an umbrella issue searching for help resolving incomplete modules. `typeshed` uses `Incomplete` in their stubs when, say, a third-party library function's types are unknown, usually because they have not been verified via the source code. I reviewed the libraries supported by `typeshed`, and found `networkx`, a network analysis library that I used last term in my grad-level Graph Theory class. This was my first PR in this project, and I am still new to the experience overall, so I opted for work that could be verified easily in the `networkx` source code. I found 10 functions that were marked `Incomplete` for the node type in the graph returned by the function. After reviewing the source code for each function, I verified that the return graph was constructed from the nodes of the input graph, so the node type of the returned graph should match that of the input graph. Since the input graph was already defined in the stub, this was a simple change from `Graph[Incomplete]` to `Graph[_Node]` (matching the input type) for each function. 

Despite the straightforward fix, `pr-precheck` did not pass my initial draft. Below is the log output from a separate skill, `ship-gate`, which blocks any PR opened via the GitHub CLI that fails checks (in this case, `pr-precheck` and some others).

```text
- verdict: BLOCK (block)
- pr-precheck checks:
  - clear-title [fail]: Title says "graph-returning algorithm stubs" but diff also retypes minimum_spanning_edges, an Iterator[_Node]-returning (non-graph) function
  - description-matches-diff [fail]: Description's claim and function list never mention minimum_spanning_edges, which the diff changes
  - no-drift [fail]: minimum_spanning_edges change in mst.pyi is absent from plan.md's 10-function scope table and has no deviation note
  - tested [pass]: Both runtests.py commands (3.10, 3.12 + --run-stubtest) pasted with full green output; repro_14031.py mypy output matches plan's stated expectation
  - reviewable [fail]: minimum_spanning_edges hunk in mst.pyi is an unrelated, unplanned edit not contributing to the stated fix
  - follows-repo-asks [pass]: Agent disclosure present per AGENTS.md; description describes the problem without linking an issue, per AGENTS.md's PR guidance; no testing plan included
  - internal-consistency [pass]: Headings and summary sentence are each supported by the content beneath them
```

`ship-gate` blocked my PR from being opened because `pr-precheck` had failing checks. The issue was in the `no-drift` check failure: `minimum_spanning_edges change in mst.pyi is absent from plan.md's 10-function scope table and has no deviation note`. I had mistakenly changed the return type for `minimum_spanning_edges` and the skill caught it. I knew exactly what the issue was thanks to the evidence in the failing `clear-title` check: `Title says "graph-returning algorithm stubs" but diff also retypes minimum_spanning_edges, an Iterator[_Node]-returning (non-graph) function`.

I reverted the mistake, and amended the commit:
```diff
--- a/stubs/networkx/networkx/algorithms/tree/mst.pyi
+++ b/stubs/networkx/networkx/algorithms/tree/mst.pyi
@@ -56,7 +56,7 @@ def minimum_spanning_edges(
     keys: bool = True,
     data: bool | None = True,
     ignore_nan: bool = False,
-) -> Iterator[_Node]: ...
+) -> Iterator[Incomplete]: ...
```

After running `ship-gate` again, all of `pr-precheck`'s rubric checks passed:

```text
- verdict: PASS
- pr-precheck checks:
  - clear-title [pass]: Title names the exact 10-function Graph[Incomplete]→Graph[_Node] swap across the 3 files the diff touches, nothing more.
  - description-matches-diff [pass]: The 3 upstream-link groups (mst.pyi, core.pyi, unary.pyi) match the diff's 3 changed files and 10 functions one-for-one.
  - no-drift [pass]: All 10 planned functions present in diff; unary.pyi import removal pre-disclosed in plan.md step 2; dict-returning functions correctly excluded.
  - reviewable [pass]: Every hunk is a return-type change or the disclosed import removal; no debris or unrelated edits.
```

This is what my contribution looked like for 1 of 10 changed functions:

```diff
# stubs/networkx/networkx/algorithms/tree/mst.pyi (1 of 10 functions shown)
 @_dispatchable
 def minimum_spanning_tree(
     G: Graph[_Node], weight: str = "weight", algorithm: str = "kruskal", ignore_nan: bool = False
-) -> Graph[Incomplete]: ...
+) -> Graph[_Node]: ...
 # ...same change in 9 more functions across mst.pyi, core.pyi, and unary.pyi
```

And here is a summary of my contribution across the three affected files:

```text
 stubs/networkx/networkx/algorithms/core.pyi            | 12 +++++-------
 stubs/networkx/networkx/algorithms/operators/unary.pyi |  3 +--
 stubs/networkx/networkx/algorithms/tree/mst.pyi        |  8 ++++----
 3 files changed, 10 insertions(+), 13 deletions(-)
```

My PR was merged 10 hours after I opened it, with no feedback:
```text
title:    [networkx] Replace Incomplete in graph-returning algorithm stubs
state:    MERGED
created:  2026-11-07T03:01:41Z   (Nov 6, 7:01 pm PST)
merged:   2026-11-07T13:01:36Z   (Nov 7, 5:01 am PST)
mergedBy: srittau
```

## Limitations and what's next

`pr-precheck` is only as good as the plan, since it compares the PR package against the plan. If there's a mistake in the plan, then `pr-precheck` will not hold the PR. Fortunately, I have a `plan-check` skill to grade a plan against an issue and its reproduction report, but if I were to use `pr-precheck` without verifying the plan, I could open a flawed PR. `pr-precheck` is also a language-model grader, so the evidence it cites for a rubric check varies run to run. For example, for the `no-drift` check on my PR package for this contribution, run 3 said `All 10 planned functions present in diff; … dict-returning functions correctly excluded.` while run 5 said `the unary.pyi Incomplete import removal (but not core.pyi/mst.pyi) matches the plan's stated per-file rule.`. Run 5 highlighted a detail of my plan that run 3 never did. The risk here is when a check is borderline; some runs may give it a pass, and others a fail. A good next step would be to add a step that runs the skill a few times, and if a check disagrees across runs, hold the PR.

As for the contribution to `typeshed`, there are still more incomplete stubs in `networkx`, and I look forward to resolving those too.