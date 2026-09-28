# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

Where it lives:
- Eval bundle: the candidate repro report's Environment section,
  compared against the version the issue targets, as stated in the
  issue context (or the repo-facts block, when it's the one that names
  the version).
- Live mode: the draft repro report's environment section, compared
  against the version named in the issue thread (title, body, or
  labels) — check the thread itself; don't assume a fixed location.

What good looks like: `yq version 4.53.3 (Homebrew), macOS 15.5 (arm64),
zsh 5.9. The issue was filed against 4.53.2; I tested the current
release.`

Reproduction reports that use later build versions but still reproduce
the issue described in the issue description pass, as long as the
tested version and the issue's target version are both named.

Reconciliation only applies when the issue names a target version in
the first place. If the issue never states one, there's nothing to
reconcile against, and the report's stated version passes on its own.
But if the issue does name a target version and the report states its
own version while never engaging with the issue's at all, that's a
fail.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

Where it lives:
- Eval bundle: the repro report's steps section, which follows the
  Environment section, compared against the preconditions stated in
  the issue context.
- Live mode: the draft's steps section, compared against the
  preconditions described in the issue thread, wherever the thread
  states them (the issue body, a linked comment, a template field).

What good looks like: The steps begin with a description of the
starting state, and this state is consistent with the preconditions
named in the issue. The steps may be written, or represented as code
blocks or screenshots. Artifacts show a clear path from setup to
output that is consistent with the issue.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

Where it lives:
- Eval bundle: the repro report's output artifacts (the section that
  states expected vs. actual behavior), compared against the
  expected/actual behavior stated in the issue context or, when the
  issue body alone doesn't state it, the thread highlights.
- Live mode: the draft's output artifacts, compared against the issue
  thread's description of the bug and any error text or screenshots it
  includes.

What good looks like: A clear description of expected versus actual
behavior, where actual behavior is backed by real program output (a
code block, snippet, or screenshot). A match means the specific
symptom named in the issue, such as the same error message, the same wrong
value, the same wrong exit code, the same visual defect, appears in
the artifact. A different symptom in the same feature area (a
different error from the same command, a crash instead of the wrong
output the issue names) is adjacent, not a match, even when the
artifact was clearly produced by trying to reproduce the same issue. A
correctly-targeted attempt that honestly reports it did not trigger the
behavior, naming what differed, also passes.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

Where it lives: The claim comment's stated conclusion, compared
against the repro report's own evidence (see Behavior shown, above,
for where that evidence lives).

What good looks like: A conclusion, relevant to the issue, made based
on the evidence the report actually shows. A comment that states the
issue could not be reproduced, and describes the steps taken in the
attempt, is still an honest claim. What fails: a confident
claim of reproduction when the report's artifacts show a different
symptom than the issue names, show no output at all, or address a
different part of the issue than the one claimed.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

Where it lives:
- Eval bundle: the repo-facts block, when it states a contribution
  policy or AI-disclosure requirement, compared against the candidate
  claim comment and repro report.
- Live mode: wherever the repo states its own rules, such as a contributing
  guide, an issue or PR template, or a pinned comment, compared against
  the draft comments. Which of these exists, or whether any does,
  varies by repo; check the repo itself rather than assuming a
  standard location.

What good looks like: whatever content or disclosure the repo's stated
policy requires (for example, an AI-use disclosure) is actually present
in the comment. Judge this on substance present or absent, never solely on
whether the comment's structure or headings mirror a template's. A
comment that covers the required substance in its own words may pass
even if it doesn't look like the template, and one that mimics the
template's shape without the required content fails.
