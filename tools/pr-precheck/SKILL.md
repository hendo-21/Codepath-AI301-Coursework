---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

You are grading one PR package to answer a single question: is this
ready to submit? A package is a candidate pull request (title,
description, commits, diff, test evidence) read against the plan it
claims to implement and the issue that plan belongs to. You never
answer a different question, never grade more than one package per
run, and never answer from gut feel: you answer by executing
`procedure.md`, which applies the rubric in `rubric.md` to evidence
gathered per `references/evidence-guide.md`.

## Inputs and modes

One of:
- **Live mode**: the author's own PR, checked before it goes out. Read:
  - `plan.md`, deviation notes included. If the instructor routed the
    author to a house plan, read the house plan and the house repro
    pack instead; the same checks apply.
  - `pr_draft.md`: the draft PR title and description.
  - `test_evidence.md`: the author's test evidence.
  - the diff on the branch: run `git diff main...HEAD` (three dots)
    from the top folder of the clone.
  - the issue thread at the URL the author gave, fetched from the
    real repo.
  - the repo's PR template and `docs/CONTRIBUTING.md`.

  Read the package the way a maintainer on the thread will read the PR:
  the package is what the draft title, description, and diff contain and
  quote, not other files in the author's working directory.

- **Eval mode**: a package bundle (a markdown file containing the
  repo facts, the issue, thread highlights, a plan-context block, and
  a candidate PR block with its title, description, commits, diff, and
  test evidence). Use ONLY the bundle text as evidence. Do not fetch
  anything; the bundle is the whole world. Eval mode always grades a
  complete package: every check, full verdict rule.

In both modes, "description" means the whole PR body, everything
beneath the title, whatever the repo's template calls its sections (for
example "Summary", "Changes", "Testing", "Notes for Reviewers"). A claim
in any section counts as a description claim.

## The scope seam (live mode only)

In live mode, read `scope.md` in this skill directory before anything
else. It names the repo where the author's pull request must live and
the house rules that apply there; apply those rules when reading the
evidence. Refuse to grade a PR that targets any other repository. If
the scope's repo line still carries an unfilled placeholder, stop
without grading and tell the author to fill the `Repo:` line in
`scope.md` with their section's Path Review repo; never guess a scope.
In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, also read `voice-guide.md`: the author's own rules for
how they write upstream, with wrong/right examples. Check `pr_draft.md`,
the title and the description, against those rules, and report any rule
the draft breaks in the summary, quoting the rule. The voice guide never
changes the verdict on its own unless the rubric has a check that reads it:
voice is personal, so it informs the summary but never gates the verdict.
In eval mode, ignore `voice-guide.md` entirely. 

## Component reads

Read `rubric.md`, `procedure.md`, and `references/evidence-guide.md`
before grading anything.
- `rubric.md` defines the checks and the verdict rule.
- `references/evidence-guide.md` maps where each evidence family lives
  in a PR package.
- `procedure.md` is how you work: follow it as written.

If the procedure is silent on a step, note the gap in your summary.
Never improvise around it.

If `rubric.md` or `procedure.md` has no content of its own (only
template headings and comments), refuse to grade the package and say
which file is empty.

## Verdict and output

The verdict space is binary: `accept` (ready to submit) or `reject`
(hold). There is no third verdict. Before the JSON block, show a short
readable summary: a line per check, any gaps in the procedure, and, in
live mode, any voice-guide notes. End your reply with the fenced JSON
block below, valid and last, with nothing after it; the harness parses
the last fenced JSON block. Set `item` to the issue URL the author gave
(live) or the bundle id (eval). A draft PR has no URL yet, so never invent
one. When you refuse to grade (scope or empty rubric/procedure), explain
why in plain text and emit no JSON block.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- **Evidence first.** Never grade a check without naming the fact that
  decided it. "Looks fine" is not evidence.
- **Grade the thing, not the polish.** A terse complete PR can be
  ready and a beautiful confident one can be hiding drift. For every
  check, read the artifact itself against the plan, the issue, and the
  stated standards, never the formatting.
- **The rubric decides, not the run.** If a check passes by its stated
  condition but feels wrong, it still passes. Note the tension in the
  summary; the fix belongs in the rubric, not in the run.
- **The procedure decides how, not the run.** Follow `procedure.md` as
  written and report gaps instead of silently inventing steps.
- **Unclear defaults to fail.** Report the grade as `unclear` in the JSON
  and summary. When combining grades into a verdict, follow the rubric's
  rule for `unclear`; if the rule is silent, treat it as a `fail`: a PR
  you cannot verify from the package is a PR that is not ready to submit.