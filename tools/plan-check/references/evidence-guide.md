# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

- Where it lives, diagnosis-based: the plan body, read against the repro
report. In an eval bundle: the candidate plan body where a cause or
diagnosis is stated, and the repro evidence expected vs. actual. In live
mode: the draft plan body where a cause or diagnosis is stated, and the
author's repro report in the issue thread (ignore all posts except for
those authored by `hendo-21`).
- What good looks like: the stated cause explains why the behavior in the
repro evidence occurs, not just a restatement of what the evidence observed.
A diagnosis that only describes the symptom the repo report shows without
naming the mechanism that produces it fails, even if every word of it is
consistent with the repro evidence.

## Scope

- Where it lives, scope-bounded: the plan body, where it mentions files
or modules in and out of scope. In an eval bundle: the candidate plan's
scope section or plan body where "in" and "out" are mentioned. In live
mode: the draft plan's scope section.
- What good looks like: the scope names specific files, modules, and/or
functions that the author will touch as part of their implementation plan.
Out-of-scope files, modules, or functions may be omitted if the draft plan
specifically names in-scope files, modules, or functions. Fails if the
scope statement includes open-ended language ("and related areas," "etc.,"
"and similar files") alongside the named files; that phrasing signals the
boundary isn't actually fixed, regardless of how many specific files are
also named.

## Executability

- Where it lives: the plan body, where it describes the implementation
steps. In an eval bundle: the candidate plan body typically as numbered
implementation steps with a section header such as "changes", "steps",
or "approach". In live mode: the draft plan's implementation plan section,
with the same use of numbered steps and headers demarcating the approach.
- What good looks like: the implementation steps name specific files,
functions, and/or modules and the specific changes to be made therein.
The steps should not assume the reader has any prior knowledge of the
codebase or additional context beyond the issue description. Fails if
the steps are vague or ambiguous enough to require a follow up question
asking for clarification.

## Test plan

- Where it lives, tests-observable: the plan body's description of the
verification approach for the proposed fix, read against the repro
report and the issue description. In an eval bundle: the candidate plan's
test or verification section, repro evidence, and issue body. In live
mode: the draft plan's test or verification section, the author's repro
report in the issue thread (authored only by `hendo-21`), and the issue
description.
- What good looks like: the verification plan states a specific and
observable expected outcome that confirms the behavior described in the
issue and reproduced in the repro report has been fixed. A test plan may
reference the repro report's reproduction steps instead of restating them,
as long as it still states that specific, observable expected outcome. It
fails if someone without the issue thread context could not follow the
plan and tell whether the test passed or failed.

## Honesty

- Where it lives, comment-faithful: the plan comment, read against the
  plan's implementation section and against the thread's stated asks
  (reviewer requests, house rules). In an eval bundle: the candidate
  plan comment, the candidate plan's implementation section, and the
  issue context / thread highlights. In live mode: the draft comment,
  the draft plan, and the live issue thread.
- Where it lives, honesty-calibrated: the plan's own risk, assumption,
  and caveat language (often under a "risks," "assumptions," or
  "open questions" heading, but not always labeled), read against the
  diagnosis evidence gathered for the diagnosis-based check. In an
  eval bundle: the candidate plan's risk/assumption language next to
  the repro-evidence block. In live mode: the draft plan's
  risk/assumption language next to the repro report posted to the
  thread.
- What good looks like, comment-faithful: the comment states only
  what the plan's implementation section actually describes, and
  anything the thread explicitly asked for that the plan addresses is
  also mentioned in the comment.
- What good looks like, honesty-calibrated: a claim the diagnosis
  evidence doesn't fully pin down is stated as a risk or assumption,
  not as settled fact ("the cause is likely X, to be confirmed by Y"
  rather than "the cause is X"). A plan that is confident only where
  the evidence is conclusive, and says so plainly elsewhere, is what a
  pass looks like next to one that states every claim with the same
  certainty regardless of how well-supported it is.

## Consistency

- Where it lives, internal-consistency: the entire candidate plan and
comment. In an eval bundle: the entire candidate plan and candidate plan
comment. In live mode: the draft plan and comment.
- What good looks like: no leftover copy-paste artifacts, each header/title
names what follows it, and each summary claim matches the evidence
that follows it.

## Comms

- Where it lives, convention-friendly: the entire plan package, compared
  against the repo-facts block's stated issue templates, developer
  guidelines, and contribution policy (including any AI-use disclosure
  requirement). In an eval bundle: the repo-facts block, read against
  the candidate plan and candidate plan comment. In live mode: the
  repo's CONTRIBUTING docs, issue template, and any house rules, read
  against the draft plan and comment.
- What good looks like: any content the repo's policies substantively
  require (e.g. a required AI-disclosure statement, a specific piece
  of information the issue template asks for) is present somewhere in
  the package, even if it doesn't appear under the same heading or in
  the same order the template uses. Fails only when required substance
  is actually missing, not because the package's structure or section
  names differ from the template's.
