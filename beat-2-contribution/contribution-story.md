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

**Unit 6: Set up my voice-guard hook and create a local Claude memory file for the issue where my repo lives**

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
Using the Codepath issue search website, I selected my desired languages (Python, C,
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
by my scout to patch an issue where `stale_issue` measured gap between comments
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

- Tool: issue-scout (your scout: your search strategy, your rubric),
  and how you used it
  issue-scout - used to conduct a full scan, and to grade the two issues selected
  from the Codepath issue selection site. Full scan focused on finding populated repos,
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

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]
2. [Step 2]
3. [Observed result]

**Reproduction Evidence**

- **Commit showing reproduction:** [link to commit in your fork]
- **Screenshots/logs:** [if applicable]
- **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

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
