# Contribution: Finish incomplete modules #14031

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Ian Henderson
**GitHub Username:** hendo-21
**Issue:** [\[GitHub issue link\]](https://github.com/python/typeshed/issues/14031)
**Pull Request:** [\[GitHub PR link\]](https://github.com/python/typeshed/pull/16729)

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

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

**Unit 5: Set up my issue-scout skill and establish a search strategy**

Given I am still quite new to the world of open source, I focused my
strategy on finding issues labeled "good first issue" and "easy". I
am interested in pushing myself, so I also included queries for
enhancement or feature work. Initial scans using my scout returned
lots of issues created same-day in small/personal projects. These issues
did not align with my goals of contributing to established projects,
so I added queries to grab repos with greater than 200 stars, and
then filter the issues by those repos. I also added a more comprehensive
list of technologies and practices I am familiar with to my fit profile
to help my scout find issues more suited to my experience.

**Unit 6: Set up my voice-guard hook and create a local Claude memory file for the repo where my issue lives**

For my voice-guard skill, I extended my voice guide with rules for how I talk to
maintainers. The rules I created focus on helping me stay honest about showing my
work, providing context when it's necessary, and respecting maintainers' time.
After install, the hook failed on the no-body test, and then passed for the
subsequent times I used it. I also created the repo-memory file, which includes
important context from my claim comment, a table detailing the subsystem my issue
touches, and critical norms and policies I need to follow for my work and
eventual PR submittal.

**Unit 7: Set up my ship-gate tool and defined a ship manifest, grounded in repo policies**

For my ship-gate skill, I created a ship manifest: a set of required checks that must
pass prior to opening a PR. These checks are specific to the repo I'm working in and
were built from the repo's CONTRIBUTING.md and AGENTS.md files. The manifest leaves
room for excluding failing checks that don't touch my fix, but for this repo there
were none. I made no changes to my ship manifest or the tool after my initial draft
as my PR passed CI and was merged quickly with no feedback.

**Unit 8: Set up pr-monitor and defined its playbook**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

I created the rules for my playbook using the repo's contributor docs and by reviewing
open and closed PRs to get a sense of maintainer behaviour. I ran pr-monitor on my PR
branch and it read the PR thread, providing me with information on the thread status,
like time of last activity, number of checks passed, state, etc., and a draft comment
grounded in the thread context. Since my PR was merged quite quickly, its drafted
comment included a thank you for the review and merge, and a statement reiterating
key details about the PR. I posted the thank you in the merged and closed PR and
rejected the rest.

---

## Why I Chose This Issue

Going into this course I was hoping to dedicate time to an issue that focused on
feature development or an enhancement, so this motivated my search initially.
Using the CodePath issue search website, I selected my desired languages (Python, C,
and JavaScript), and then feature, enhancement, and good first issue labels, as well
as a couple of the named orgs. I also wanted to contribute to an established project.
After a lengthy search through claimed or stale issues, I found two that looked
appealing. The first was adding a package to `open-telemetry`, and the second was finishing
incomplete modules for `typeshed`. My scout revealed a critical fit issue with the `open-telemetry`
issue, which was that issue required Kotlin/Gradle/Android, none of which I have experience
with. The second issue my scout initially rejected on the grounds that the issue was stale,
and the scope was infeasible. As evidence, it cited a lengthy gap between comments and
earlier comments: `'Finish incomplete modules' spans many stubs; maintainer says
remaining ones 'not particularly approachable'`.

However, the scout missed that the most recent comment from a collaborator provided
guidance on where to look for incomplete stubs and modules. I reviewed the stubs folder
for third-party packages that `typeshed` provides type hints for and found one I was
familiar with: `networkx`. There I noticed some incomplete stubs for algorithms I used
for a course I took last term. I had a hunch this would be a good fit despite the reject
verdict. Before asking for a re-grade, I updated my rubric based on friction noted
by my scout to patch an issue where `stale_issue` measured the gap between comments
instead of time since last activity, and to patch an issue with `scope_feasible` that
missed comments where a maintainer redirects an issue as they did with this issue. I then
re-graded the issue on the redirection provided by the maintainer, and my own intended scope per
their redirection, and the scout issued an accept verdict with it now passing on the
previously failing checks `stale_issue` and `scope_feasible`. I looked at the source
code for the `networkx` function stubs I intend to complete for the PR and they
motivate a simple one-line change for about 10 functions, which is an appropriate
scope for the amount of time I have remaining in the course. The work also fits because
Python is my strongest language and I have a small amount of bug fix open-source experience,
so reading through the source code to find the proper return type should feel familiar.
Typeshed is also a large project so it fits with my motivations on that front. From
a learning perspective, I've always wondered how functions get their type annotations
so this will be an entirely new domain.

[\[Claim comment link\]](https://github.com/python/typeshed/issues/14031#issuecomment-6586150705)

**Toolkit**

- Tool: issue-scout - used to conduct a full scan, and to grade the two issues selected
  from the CodePath issue selection site. Full scan focused on finding populated repos,
  issues with labels `good first issue`, `enhancement`, `feature`, split among my three
  familiar programming languages: Python, C, and JavaScript. `rubric.md` was patched with
  the `scope_feasible` check which replaced `clear_scope` from the sandbox era. Also changed
  `stale_issue` and `scope_feasible` as described above. Since a maintainer redirected the issue
  in a comment in the issue thread, I asked my scout to re-grade a scope I described based on
  that redirection.
- What it produced: Full scan produced lots of issues in small repos opened same day as scan until
  I added a query for repos with a certain star count. The initial scan on the two issues produced
  `accept` and `reject` verdicts on the `open-telemetry` and `typeshed` issues respectively. As
  noted, the issues were more due to shortcomings with the rubric. After patching the rubric
  as described above, the `typeshed` issue got an `accept` verdict and a `moderate` rating
  after describing my planned scope as invited to by the maintainer's comment redirecting
  the issue.
- Difficulties: None really. The issues were mostly related to the queries and rubric. Both
  patched and improved scout outcomes.
- What changed: As noted, I patched the queries for a full scan to include repos meeting a
  certain star threshold, and I patched the rubric to more accurately reflect how issues
  show up in the wild.

---

## Understanding the Issue

**Problem Description**

As noted above, the issue's body identified incomplete modules as those with a `__getattr__` function
with an "incomplete module" comment. Later, a maintainer commented that the remaining modules with
module-level `__getattr__` weren't particularly approachable, and provided direction on where to find
incomplete stubs and modules; this is where my work comes from. `typeshed` provides type annotations for the Python
standard library and many other popular third-party libraries, which are used by type checkers like `mypy`,
`pyright` etc. After reviewing the codebase, I found stubs in a network analysis package I used last term,
`networkx`. I identified three stub files with functions that use `Incomplete` for the function's return type.
For example, in `stubs/networkx/networkx/algorithms/tree/mst.pyi`, the function `minimum_spanning_tree()`
takes a graph `G` as input with the annotation `Graph[_Node]`, where `_Node` is the type of the nodes
themselves (`int`, `str`, etc.), and returns `Graph[Incomplete]`. In the `networkx` code for
`minimum_spanning_tree()`, the graph returned by the function is a tree `T` that is built from the same
nodes of `G`, so the node type for the return annotation should match the input node type. Type
checkers interpret `Graph[Incomplete]` as `Graph[Any]`, which provides incomplete information to the
programmer by failing to match the return type to the input type. It means that the type checker cannot
catch mistakes involving the returned graph's nodes, like trying to make nodes of type `int` uppercase.
This same pattern is consistent across the three files named in my claim comment.

**Expected Behavior**

Example:
```python
from typing import reveal_type
import networkx as nx

def main() -> None:
    g: nx.Graph[int] = nx.Graph()
    g.add_edge(1, 2, weight=1)

    tree = nx.minimum_spanning_tree(g)  # algorithms/tree/mst.pyi
    reveal_type(tree)
    for n in tree.nodes:
        n.upper()
```

This snippet creates a networkx graph `g` with nodes of type `int`, generates a minimum spanning tree, `tree`, from `g`,
then reveals the type of `tree` and attempts to make the nodes in `tree` uppercase. The type checker should flag
that a node of type `int` cannot be made uppercase, and the `reveal_type(tree)` should show 
`networkx.classes.graph.Graph[int,...]`.


**Current Behavior**

Using `mypy`:
```text
Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
Success: no issues found
```

The same pattern holds across all named file stubs for functions that define `Graph[_Node]` for the input and
`Graph[Incomplete]` for the output.

**Affected Components**

typeshed stub files
- stubs/networkx/networkx/algorithms/tree/mst.pyi (functions: minimum_spanning_tree, partition_spanning_tree,
  maximum_spanning_tree, random_spanning_tree)
- stubs/networkx/networkx/algorithms/core.pyi (functions: k_core, k_shell, k_crust, k_corona, k_truss)
- stubs/networkx/networkx/algorithms/operators/unary.pyi (function: complement)

source code context: networkx 3.6.1
- networkx/algorithms/tree/mst.py
- networkx/algorithms/core.py
- networkx/algorithms/operators/unary.py


**Toolkit**

- Tool: repro-check - used to grade and iterate on my reproduction report
- What it produced: As far as understanding the issue goes, repro-check helped me dig deeper into both the affected `typeshed` in
  order to provide satisfactory justification for my claims. It pushed me to find and name the specific lines from the upstream
  source code that justify my claims, as you will find in the next section, "Reproduction Process - Analysis".
- Difficulties: The tool repro-check tool rejected my report twice before accepting my third revision. The issues were not with
  components of the tool, but rather with insufficiently justifying my claims.
- What changed: Nothing with the rubric or any piece of the tool changed. The tool helped push me to cite specific parts of the
  codebase and upstream source code to justify my claims.

---

## Reproduction Process

**Environment Setup**

Env:
- OS: macOS 26.5.1, arm64
- Python: 3.12.4
- Package manager: pip 26.3, in a venv
- Project: typeshed 93fc9280a and networkx 3.6.1
- Type checker: mypy 2.4.0
- Test deps: pyright 1.1.414, Node v24.8.0 / npx 11.6.0

Setup steps:
- create a venv per AGENTS.md
- pip install -r requirements-tests.txt
- pip install "numpy>=1.21" "matplotlib>=3.8"

Challenges:
On unmodified main, the first test run failed pyright, ty and pyrefly, while mypy passed.
The cause was that `numpy` and `matplotlib` weren't installed. `numpy` is declared in networkx's
`METADATA.toml`. `matplotlib` is imported by `nx_pylab.pyi` but isn't declared, because CI
gets it from `seaborn`'s dependencies.

**Steps to Reproduce**

1. Clone typeshed and check out the tested commit:
   `git clone https://github.com/python/typeshed && cd typeshed && git checkout 93fc9280a`
2. Create and activate a venv (per AGENTS.md), then install:
   `pip install -r requirements-tests.txt "numpy>=1.21" "matplotlib>=3.8"`
3. Run `networkx` stubtests: `python tests/runtests.py stubs/networkx --run-stubtest`. The stubtests
pass at this commit
4. Save the test script below to `repro_14031.py` in the `typeshed` root
5. From the root, run: `MYPYPATH=stubs/networkx mypy repro_14031.py`

**Reproduction Evidence**

- **Commit showing reproduction:** [\[repro script committed to my fork\]](https://github.com/hendo-21/typeshed/commit/0f2a96d9a)
- **Screenshots/logs:**
  - Script output actual:
  ```text
  repro_14031.py:13: note: Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
  repro_14031.py:18: note: Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
  repro_14031.py:23: note: Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
  Success: no issues found in 1 source file
  ```
  - Expected result is that the reveal type is `networkx.classes.graph.Graph[int,...]` for each return graph, and
  the type checker finds three errors, one for each attempt at making each node of type `int` in each return graph uppercase.

- **My findings:** According to the `networkx` source code (`core.py:149`, `core.py:344`, the `complement` code in `unary.py`, `mst.py`'s `T = 
G.__class__()`), each graph returned by the functions mentioned as in-scope for my claim comment builds its return graph 
using the nodes from the input graph. Therefore, the type of the node in the function's return graph should match that of 
the input graph. The complete list of affected files and components with this pattern is listed in the "Understanding the
Issue" section.

**Toolkit**

- Tool: repro-check - used to grade my reproduction report draft.
- What it produced: It took three grading rounds before I got a pass verdict. Reject verdicts were all down to
  failures on my `internal_consistency` check as I left copy-pasted text, or did not ground claims in evidence. Failed
  check feedback: "Stale 'Setup steps' block duplicates Steps 1-2; complement's result still called a 'subgraph' 4x; Note claims matplotlib is needed for networkx stub tests but METADATA.toml lists only numpy and pandas". I did not provide
  enough evidence for why packages needed to be included in the reproduction steps. After fixes, the tool passed the failing
  check with the comment "pass. The duplicate setup block is gone, "subgraph" is now "return graph" everywhere, the matplotlib note is accurate, and the stubtest step states its result."
- Difficulties: I was not consistent throughout my repro report in justifying claims with evidence. I added the
  `internal_consistency` check to my rubric as an honesty check, and to make sure my claims are grounded and specific. With
  the examples above, I had a note that stated the additional packages were required, but not why. 
- What changed: Nothing with the rubric or any piece of the tool changed. My repro report was updated to provide more
  evidence for claims, and to cite sections of the codebase to make claims more specific.

---

## Solution Approach

**Analysis**

The function stubs named below are currently incomplete for the function's return type (they show 
`Graph[Incomplete]`). Type checkers interpret that the return type of the graph's nodes is `Any`. This is inconsistent with the `networkx` source code which shows that the graph returned by the function is built using the nodes from the input graph. This means that the type of the node in the return graph should be the same type as that of the node in the input graph. 

| Stub (typeshed line) | Upstream function (line) | How the return graph is built (line) |
|---|---|---|
| `stubs/networkx/networkx/algorithms/tree/mst.pyi` `minimum_spanning_tree` (L70) | `tree/mst.py#L557` | `T = G.__class__()` + `add_nodes_from(G.nodes.items())` (L609) |
| `stubs/networkx/networkx/algorithms/tree/mst.pyi` `partition_spanning_tree` (L74) | `tree/mst.py#L617` | same pattern (L673) |
| `stubs/networkx/networkx/algorithms/tree/mst.pyi` `maximum_spanning_tree` (L78) | `tree/mst.py#L681` | same pattern (L736) |
| `stubs/networkx/networkx/algorithms/tree/mst.pyi` `random_spanning_tree` (L82) | `tree/mst.py#L745` | `nx.empty_graph(G.nodes)` (L918) or `nx.Graph()` + `add_edges_from(U)`, where U is a subset of `G.edges()` (L966) |
| `stubs/networkx/networkx/algorithms/core.pyi` `k_core` (L12) | `core.py#L154` | `_core_subgraph` (L210), which returns `G.subgraph(nodes).copy()` (L125, L149) |
| `stubs/networkx/networkx/algorithms/core.pyi` `k_shell` (L16) | `core.py#L215` | `_core_subgraph` (L277) |
| `stubs/networkx/networkx/algorithms/core.pyi` `k_crust` (L20) | `core.py#L282` | inlined `G.subgraph(nodes).copy()` (L344) |
| `stubs/networkx/networkx/algorithms/core.pyi` `k_corona` (L24) | `core.py#L349` | `_core_subgraph` (L406) |
| `stubs/networkx/networkx/algorithms/core.pyi` `k_truss` (L26) | `core.py#L412` | `H = G.copy()` (L470), with edges/nodes removed, then `return H` (L488) |
| `stubs/networkx/networkx/algorithms/operators/unary.pyi` `complement` (L13) | `operators/unary.py#L9` | `R = G.__class__()` + `add_nodes_from(G)` (L36) |

**Proposed Solution**

My solution is to change `Graph[Incomplete]` to `Graph[_Node]` to match the stub's existing convention for the input graph: `Graph[_Node]`. My change is 
limited to the instances where the return graph is constructed using the nodes from the input graph, and it touches only the named functions in the files
above.

**Implementation Plan**

1. Change the return type in each `typeshed` function stub listed above from `Graph[Incomplete]` to `Graph[_Node]`.
2. Remove `from _typeshed import Incomplete` from `unary.pyi`. My fix resolves all incompletes for this stub.
3. Run required repo tests: `PATH="$PWD/.venv/bin:$PATH" .venv/bin/python tests/runtests.py stubs/networkx --python-version 3.10` and `PATH="$PWD/.venv/bin:$PATH" .venv/bin/python tests/runtests.py stubs/networkx --run-stubtest --python-version 3.12`
4. Save the test script below to `repro_14031.py` in the `typeshed` root
5. From the root, run: `MYPYPATH=stubs/networkx mypy repro_14031.py` to confirm the reveal type is 
`networkx.classes.graph.Graph[int,...]` and the `mypy` catches the three errors for trying to make an `int` 
upper case. Script pasted below for reference.

Test script:
```python

from typing import reveal_type

import networkx as nx


def main() -> None:
    g: nx.Graph[int] = nx.Graph()
    g.add_edge(1, 2, weight=1)
    g.add_edge(2, 3, weight=2)
    g.add_edge(1, 3, weight=3)

    tree = nx.minimum_spanning_tree(g)  # algorithms/tree/mst.pyi
    reveal_type(tree)
    for n in tree.nodes:
        n.upper()

    core = nx.k_core(g)  # algorithms/core.pyi
    reveal_type(core)
    for n in core.nodes:
        n.upper()

    comp = nx.complement(g)  # algorithms/operators/unary.pyi
    reveal_type(comp)
    for n in comp.nodes:
        n.upper()
```

**Toolkit**

- Tool: plan-check - used to grade my implementation plan and plan comment
- What it produced: reached an accept verdict on my third pass. Each reject verdict was a result of a failing `internal-consistency` check. This was the
  evidence cited by the tool for the failing check: `Comment: 'The function stubs my PR will target functions that are...' (merged-draft relic); plan says node type 'can be Graph[Any,...]'; 'three errors' vs ten functions."` and `Stub column lists 'operators/unary.py' instead of .pyi; step 3 is a leftover that duplicates steps 5-6 and comes before them.`
- Difficulties: no issues with the tool itself, the feedback on the failing check was warranted. I made changes to the plan and not the tool. This check
  did exactly what I wanted it to, which was catch bad copy-pastes and conflicting sentences.
- What changed: I deleted bad copy-pastes, fixed garbled sentences, and expanded my implementation steps to include specifics on how I'll test my solution
  so that it was consistent with my repro report and the repo's own standards.

---

## Testing Strategy

Post fix, my test script shows expected behavior: revealed type is `networkx.classes.graph.Graph[int,...]` and the type checker flags 3 issues
in the test script. See below for evidence. Per repo policy, I also ran the required test suite, which showed all tests passing before and
after my fix. Evidence is also shared below.

**Test Script (see Implementation Plan)** </br>
BEFORE:
```text
repro_14031.py:13: note: Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
repro_14031.py:18: note: Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
repro_14031.py:23: note: Revealed type is "networkx.classes.graph.Graph[Any, dict[str, Any], dict[str, Any]]"
Success: no issues found in 1 source file
```

AFTER:
```text
repro_14031.py:14: note: Revealed type is "networkx.classes.graph.Graph[int, dict[str, Any], dict[str, Any]]"
repro_14031.py:16: error: "int" has no attribute "upper"  [attr-defined]
repro_14031.py:19: note: Revealed type is "networkx.classes.graph.Graph[int, dict[str, Any], dict[str, Any]]"
repro_14031.py:21: error: "int" has no attribute "upper"  [attr-defined]
repro_14031.py:24: note: Revealed type is "networkx.classes.graph.Graph[int, dict[str, Any], dict[str, Any]]"
repro_14031.py:26: error: "int" has no attribute "upper"  [attr-defined]
Found 3 errors in 1 file (checked 1 source file)
```

**Repo Tests** </br>
Python 3.10 tests BEFORE:
```text
$ PATH="$PWD/.venv/bin:$PATH" .venv/bin/python tests/runtests.py stubs/networkx --python-version 3.10
--- TEST SUMMARY: All tests passed! ---

pre-commit Success
Check structure: Success
Pyright: Success
ty: Success
pyrefly: Success
mypy: Success
stubtest: Skipped
Pyright regression tests: Success
mypy regression test: Success

```

Python 3.12 tests BEFORE:
```text
$ PATH="$PWD/.venv/bin:$PATH" .venv/bin/python tests/runtests.py stubs/networkx --run-stubtest --python-version 3.12
...
--- TEST SUMMARY: All tests passed! ---

pre-commit Success
Check structure: Success
Pyright: Success
ty: Success
pyrefly: Success
mypy: Success
stubtest: Success
Pyright regression tests: Success
mypy regression test: Success

```

Python 3.10 tests AFTER:
```text
$ PATH="$PWD/.venv/bin:$PATH" .venv/bin/python tests/runtests.py stubs/networkx --python-version 3.10
...
--- TEST SUMMARY: All tests passed! ---

pre-commit Success
Check structure: Success
Pyright: Success
ty: Success
pyrefly: Success
mypy: Success
stubtest: Skipped
Pyright regression tests: Success
mypy regression test: Success
```

Python 3.12 tests AFTER:
```text
$ PATH="$PWD/.venv/bin:$PATH" .venv/bin/python tests/runtests.py stubs/networkx --run-stubtest --python-version 3.12
...
--- TEST SUMMARY: All tests passed! ---

pre-commit Success
Check structure: Success
Pyright: Success
ty: Success
pyrefly: Success
mypy: Success
stubtest: Success
Pyright regression tests: Success
mypy regression test: Success
```

**Toolkit**

- Tool: pr-precheck - checked my draft against my commit and changes therein.
- What it produced: A summary of my draft PR, the changes and my claims, checked against my rubric and voice guide.
- Difficulties: The tool functioned as intended, and correctly flagged accidental drift in my draft PR. As a part of ship-gate, I ran the tool
  three times to get an accept. Here's a summary from pr-precheck for when ship-gate returned a HOLD:
  ```text
  in your rubric's words:
    - clear-title [fail]: Title says "graph-returning algorithm stubs" but diff also retypes minimum_spanning_edges, an Iterator[_Node]-returning (non-graph) function
    - description-matches-diff [fail]: Description's claim and function list never mention minimum_spanning_edges, which the diff changes
    - no-drift [fail]: minimum_spanning_edges change in mst.pyi is absent from plan.md's 10-function scope table and has no deviation note
    - reviewable [fail]: minimum_spanning_edges hunk in mst.pyi is an unrelated, unplanned edit not contributing to the stated fix
  Fix your branch. If a check asks for something this repo doesn't ask for, fix that check in your rubric instead, and say so in your Unit 7 Toolkit entry.
  ```
- What changed: Reverted the accidental drift, amended my commit, and pushed the commit. Here's the summary from the instance ship-gate
  accepted my draft:
  ```text
  Scope check: repository is `python/typeshed`, a public repo — in scope per `scope.md`. No course house rules apply; repo conventions (`CONTRIBUTING.md`, `AGENTS.md`) govern. No linked PRs or issue thread were available to check for parallel work, so that courtesy can't be verified from this package.

  Voice-guide check: no violations found. The description is a single grounded summary sentence, cites upstream line links as evidence, discloses the agent factually, carries no timeline language, no obsequiousness, and stays concise.

  ## Per-check findings

  **clear-title** — "[networkx] replace incomplete in graph-returning algorithm stubs" names exactly the diff's scope: 10 functions across `mst.pyi`, `core.pyi`, `unary.pyi` all changing `Graph[Incomplete]` → `Graph[_Node]`. Doesn't overclaim (e.g., doesn't imply all `Incomplete` in networkx is fixed) or underclaim. **Pass.**

  **description-matches-diff** — The description's claim ("functions build their return graphs from the input G's nodes, so return type can be `Graph[_Node]`") is borne out in all three changed files. All three upstream links correspond to real sources. One minor simplification: the `mst.py#L609` link is used as a single representative citation for all four `mst.pyi` functions, though `plan.md`'s own table shows they build graphs at different lines (609/673/736/918/966). This doesn't misstate what changed, and the plan's own table backs the claim — not drift, just compressed citation. **Pass.**

  **no-drift** — Plan names exactly 10 functions in exactly these 3 files; diff touches exactly those 10 functions in exactly those 3 files, plus the one disclosed-by-plan import removal in `unary.pyi` (plan step 2). Nothing else changed. **Pass.**

  **tested** — No issue thread was found (confirmed absent by the gate), so there's no issue-named repro to re-run; the plan substitutes its own verification script (`repro_14031.py`), which was run and shows the post-fix result (`reveal_type` → `Graph[int, ...]`, 3 expected `.upper()` errors). Both required test commands from `AGENTS.md`/`plan.md` were run and their full pasted output is present, including the initial black autofix being resolved before the final clean run. **Pass.**

  **reviewable** — Every hunk is a return-type edit or the one import removal; the line-collapsing in `core.pyi` is Black's mechanical consequence of the shorter annotation, not unrelatedformatting churn. No debug code, no dead code, no unrelated edits. **Pass.**

  **follows-repo-asks** — AGENTS.md asks: follow CONTRIBUTING.md (generic, satisfied), no new test files for simple `.pyi` changes (none added), one-sentence summary (satisfied), no testing plan in description (satisfied), link to issue or describe problem — never both (description describes the problem only, consistent), agent name disclosed in the author's own words (satisfied). **Pass.**

  **internal-consistency** — Single-paragraph description, link list, and agent disclosure all describe the same change; no contradictory headings or leftover copy-paste text. **Pass.**
  ```

---

## Implementation Notes

**[11/06/26]**

Confirmed in `networkx` source code personally that the return graphs consist of the input graph's nodes. Where I was unsure about
the `networkx` code, I used Claude to flesh out my understanding so that I can stand behind the change. `Graph[Incomplete]` changed to
`Graph[_Node]` in all functions named in "Solution Approach".

Ran all tests per my implementation plan and confirmed they all passed. My fix is now complete and there were no deviations from the plan.

**[11/06/26]**

Accidentally changed the return type for a function `minimum_spanning_edges`, a function not named in my fix scope. The accident was caught by
my ship-gate and pr-precheck tools. Restored the return type to `Iterator[Incomplete]`, amended my commit, and pushed before opening my PR. Repo policies say not to amend commits, but that's only after a PR has been opened.

**Toolkit**

- Tool: ship-gate - built a ship manifest for the tool so that it runs repo-specific checks on the drafted changes. All checks must pass in
  order to open a PR. The manifest was built from the repo policy docs CONTRIBUTING.md and AGENTS.md, which emphasized running existing
  tests, and being responsible that CI passes. Since CI can only be checked when the PR is opened, there was no check to add. All tests passed
  prior to my fix so there were none to exclude; the repo explicitly asks contributors to omit tests for small changes like mine.
- What it produced: it ran each command in my ship manifest and then ran my pr-precheck tool. 
- Difficulties: I forgot to commit my changes on my first run of ship-gate, so the tool failed. My second use of the tool flagged the
  drift described above. The tools themselves worked perfectly and I made no changes to the manifest or pr-precheck rubric.
- What changed: As mentioned in the previous section, I reverted the accidental drift, amended the commit and pushed the change before
  re-running ship gate and getting a "ready to post" verdict.

---

## Pull Request

**PR Link:** [\[GitHub PR URL\]](https://github.com/python/typeshed/pull/16729)

**PR Description:** 

The networkx functions below build their return graphs from the input G's nodes, so their return types can be `Graph[_Node]` to match the input `Graph[_Node]`, instead of `Graph[Incomplete]`.

networkx 3.6.1 source:

- Upstream for mst.pyi (minimum_spanning_tree, partition_spanning_tree, maximum_spanning_tree, random_spanning_tree)
- Upstream for core.pyi (k_core, k_shell, k_crust, k_corona, k_truss)
- Upstream for unary.pyi (complement)

Agent: Claude Code (claude-opus-5-5), used to find other functions that build their return graph from G similarly to minimum_spanning_tree, and to explain parts of the networkx source. I checked each against source.

> Note: typeshed's AGENTS.md says PR descriptions should either link the issue or describe the problem, never both, and should not include a testing plan. Following the course's own rule that the repo's asks win, I left out Fixes #14031 (it would also close a broad tracking issue my PR only contributes to) and the before/after output (kept in test_evidence.md). I linked the PR to the issue with a comment on #14031 instead.

**Maintainer Feedback:**

- [11/07/26]: PR opened. Awaiting reply.
- [11/07/26]: PR merged with no comment or feedback.

**Status:** Merged

**Toolkit**

- Tool: pr-monitor and its playbook (`playbook.md`). The playbook was straightforward to produce because CONTRIBUTING.md already shared
  review timeline expectations, how to follow up etc. The work was providing samples of posts I would make in my own voice.
- What it produced: My PR was merged within 12 hours or so of opening it, with no feedback, so the pr-monitor only had the merge action to
  work with. It produced a merge thank-you note and reiterated some of the work I did in the PR. For example:
  ```text
  The issue noted in my claim comment (#14031) can't be closed by this PR alone — it covers many other incomplete-stub cases beyond the ten functions here, so this is a partial contribution toward it, not a full fix.

  Nothing was deliberately left out of scope within the three files touched (`mst.pyi`, `core.pyi`, `unary.pyi`); all ten candidate functions identified were addressed.
  ```
- Difficulties: I didn't think it was necessary to include comments reiterating the work, or the files that were changed that the maintainer
  just reviewed and approved. I did accept the thank you note though and posted it.
- What changed: I rejected the part of draft-move that re-stated the work I completed and the comment about the issue noted in my PR. I posted
  the thank you to the merged and closed PR.

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

- [CONTRIBUTING.md helped a lot for setting up my environment, creating my testing plan and draft PR](https://github.com/python/typeshed/blob/main/CONTRIBUTING.md)
- [`networkx` 3.6.1 source code](https://github.com/networkx/networkx/tree/networkx-3.6.1/networkx)
- [Closed typeshed PRs as reference for the shape of my PR draft](https://github.com/python/typeshed/pulls?q=is%3Apr+state%3Aclosed)
- [Python docs on static typing](https://typing.python.org/en/latest/)
