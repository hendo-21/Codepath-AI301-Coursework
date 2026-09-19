# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/45

**Verdict output**

```
Grading

#45 — No property-based tests for the PII scrubber

Check	Grade	Evidence
active_release	pass	Same repo-wide fact: last push 2026-09-16
unclaimed	pass	assignees: [], 0 comments
stale_issue	pass	No comments
clear_scope	pass	One bounded ask: add hypothesis-based property tests to tests/unit/test_pii_scrubber.py; names the file and an effort estimate (4–6h)
has_labels	pass	Labeled enhancement, tests, tier-2
maintainer_responsive	unclear	Same repo-wide absence of any maintainer comment sample
has_contributing_docs	fail	Same repo-wide fact
Verdict: accept

Ranking by fit (your profile: Python-first, backend priority, want feature work over bug fixes, avoid gnarly concurrency):

All three accept, all three tie on the preferred checks (unclear / fail across the board — the repo-wide facts don't differentiate them). Ranking on fit alone:

1. #45 — PII scrubber property-based tests. Purely backend Python, genuinely new feature-building (not just patching a bug), and hypothesis is a good skill to pick up. Self-contained enough not to require deep system knowledge, but still a step up from a one-line fix.

{
   "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/45",
   "checks": [
   {"name": "active_release", "grade": "pass", "evidence": "No Release published; last push to main 2026-09-16, within 12 months of 2026-09-19"},
   {"name": "unclaimed", "grade": "pass", "evidence": "assignees: [], 0 comments, no linked PRs"},
   {"name": "stale_issue", "grade": "pass", "evidence": "No comments exist on the thread"},
   {"name": "clear_scope", "grade": "pass", "evidence": "Body specifies adding hypothesis property-based tests to tests/unit/test_pii_scrubber.py with a 4-6h estimate"},
   {"name": "has_labels", "grade": "pass", "evidence": "Labels: enhancement, tests, tier-2"},
   {"name": "maintainer_responsive", "grade": "unclear", "evidence": "No maintainer (Owner/Member/Collaborator) comments found anywhere in the repo to sample"},
   {"name": "has_contributing_docs", "grade": "fail", "evidence": "No CONTRIBUTING.md, AGENTS.md, or AI policy file at repo root"}
   ],
   "verdict": "accept"
}
```

---

## Eval iterations

**Run history**

1. 7/20
2. 12/20
3. 16/20
4. 17/20
5. 17/20
6. 19/20
7. 18/20

**Issue analysis**

- Issue: `issue-01`
- Gold: accept
- Vertict: reject
- Agree: NO
- Note: failed: clear_scope

**Check rationale**

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| clear_scope | issue body | The issue must clearly define a single concrete defect or focused feature request, even if it suggests multiple potential fixes or itemizes missing elements. Only reject issues that serve as open-ended discussions asking for design direction, broad umbrella epics, or posts lacking a specific problem statement. | required |

I added this check because I wanted to avoid issues that are underspecified or too ambiguous. As a newer contributor to open source projects, issues that are too broad in scope, or where the deliverable is unclear can add a layer of complexity to the experience I want to avoid. Ideally this check ensures that the accepted issues are atomic in scope with an end-goal I can easily understand.

**Trade-offs**

This check produced mixed verticts on subsequent reruns for `issue-01`. About half the time it would agree with the gold standard, and half the time it would differ. I suspect the model gets confused by language like "should", "could", or "consider" and determines the issue wording is too ambiguous. This issue also names multiple files that should be updated, which the model may iterpret as the issue being too broad in scope. The risk is that this check misses well-scoped and documented issues that would otherwise be an ideal fit for a new contributor given the issue's detailed description. 

---

## Selection rationale

**Selection rationale**

1. I've been doing a lot of CI/CD and frontend work lately, so wanted to pivot back to backend work. As a Tier 2 issue, the same tier I completed for AI201, I know it's something I can complete over the course of a week with the 4-6 hour time estimate.
2. Correctly identified the enhancement lable, bounded scope, and my desire for feature (enhancement) related work rather than just bug fixes. I considered my testing experience, which is more limited than my other experience, but the rubric and my scope doc didn't include any reference to my testing experience. That said I saw this as an opportunity to gain more experience with testing, and an opportunity to get hands on with a new testing methodology.
3. I have never used the `hypothesis` before so that will be a learning experience. 

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
