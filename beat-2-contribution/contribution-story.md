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
**Pull Request:** [GitHub PR link, once opened]

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

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

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
```bash
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

- Tool:
- What it produced:
- Difficulties:
- What changed:

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

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

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

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
