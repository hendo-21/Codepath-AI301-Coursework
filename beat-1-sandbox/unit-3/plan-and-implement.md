# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

hendo-21

**Plan comment**

Link: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-6004475695

I confirmed that the issue is with the `regex` pattern being used to match US phone numbers in the PII scrubber. Currently it lacks the space character as an optional separator (the main cause of the bug), which I'll add in my fix. I also found that the `regex` pattern matches on the pattern after the  leading `(`, when it's included, so it never gets scrubbed. Not a safety issue, but I propose new boundary logic for the pattern so that the entire phone number, `(` inclusive, is redacted. The addition of the space separator does widen the scope of what can be redacted; see my note below.

## Plan

### Diagnosis

As noted in my repro report, the `regex` PII patterns defined in `safety/pii_scrubber.py` for US phone numbers has two issues:
- The space character is missing from the list of optional separators
(lists only `[-.]`).
- The `regex` expression starts with a word boundary (`\b`). A `\b` fails between a space and a `(` (both are non-word characters), so when the optional area code parenthesis is used, the match starts one character later, at the first digit, and the leading parenthesis is not matched by the pattern. This doesn't leak any PII, but it also doesn't redact the entire phone number.

### Scope

This fix is strictly constrained to the `phone_us` `regex` pattern of  the `PIIScrubber` class in `safety/pii_scrubber.py`, and to the removal of `xfail` from the four failing tests as noted in the verification section below.

### Plan

1. Add the space character to the `phone_us` `regex` pattern as an optional separator, in all three places the pattern allows one (after the optional `+1`, after the area code, and between the middle groups): `[-.]` -> `[-. ]`.
2. Replace the leading `\b` in the `regex` pattern with `(?:(?<!\w)|(?=\())`. A match may now start in either of two cases:
   1. The character before the match is a non-word character (the general case, which includes a `(` after a space or dash).
   2. The next character is a `(`, so a `(` directly after a word character (e.g. if a resume presented a phone number as `call(555)...`) is still included in the match. This case was not included in my repro report but I have added it as a test case in my test script below.

The trailing `\b` is unchanged.

### Verification

1. Remove the `xfail` markers from the four failing unit tests `test_us_phone_number_redaction`, `test_us_phone_formats`, `test_detect_phone_pii`, and `test_phone_at_start_of_text` in `tests/unit/test_pii_scrubber.py` (they are `strict=True`, so they would otherwise report as failures once the fix works), and confirm they all pass after the fix.
2. I'll rerun my test script to confirm all phone numbers, including the leading parenthesis, are redacted and detected in each test.

Test script:
```python
from safety.pii_scrubber import PIIScrubber

s = PIIScrubber()
print('\nTest 1:Issue description test')
print(s.scrub('Call me at (555) 123-4567 or 555-123-4567'))
print(s.detect('Call me at (555) 123-4567'))

print('\nTest 2: optional area code parentheses and optional - or . separator')
print(s.scrub('Call me at (555)-123-4567 or 555-123-4567'))
print(s.detect('Call me at (555)-123-4567'))

print('\nTest 3: optional area code parentheses and mixed optional separator')
print(s.scrub('Call me at (555)123-4567 or 555-123-4567'))
print(s.detect('Call me at (555)123-4567'))

print('\nTest 4: optional area code parentheses and no optional separator')
print(s.scrub('Call me at (555)1234567 or 555-123-4567'))
print(s.detect('Call me at (555)1234567'))

print('\nTest 5: no area code parentheses and no optional separator')
print(s.scrub('Call me at 5551234567 or 555-123-4567'))
print(s.detect('Call me at 5551234567'))

print('\nTest 6: area code parenthesis directly after a word character')
print(s.scrub('call(555) 123-4567 or 555-123-4567'))
print(s.detect('call(555) 123-4567'))
```

### Note

Adding the space character as an optional separator widens the scope of what resume text matches and therefore what may be redacted. For example, a student describing an accomplishment in terms of numbers using the 3 3 4 digit format would see those numbers redacted. I expect these would be rare. 

---

## Your branch

**Branch**

`fix/53-us-phone-regex-separators`

**Evidence**

## Eval iterations

**Run history**

1. 19/20
2. 18/20

**Package analysis**

| package | gold | rubric | agree | note |
|---|---|---|---|---|
| `pgk-03` | accept | reject | NO | failed: honesty-calibrated |

I picked this issue and check because I re-ran the skill on this issue multiple times, and 4/5 times
the check passed, but in the final eval run it failed. I did not save the final eval run results, so
I couldn't check the model's reasoning, however this was a check I went back-and-forth on so there
must be some amiguity the model is having a hard time parsing. In this package, the first line of the
described approach notes a list of command builders and claims that they accept `--` as end-of-options.
In the following sentence the author notes that they have tested some of the builders locally, but not
all, and that they will confirm the others via manpages. The check specifically fails an untested
assumptions presented as fact. I suspect that when the check fails, it fails on the first sentence's
assertions, and when it passes, it accepts the second sentence as an honest flag of known unknowns.

**Check rationale**

| Check | evidence | Pass Condition | Weight |
|---|---|---|---|
| honesty-calibrated | The plan's stated confidence (claims, risks, caveats), compared to what the diagnosis evidence actually supports | The plan flags genuine unknowns as unknowns rather than asserting them as settled; it does not state a risk, assumption, or untested step as fact | required |

This check is a guard against overclaiming, which speaking from personal experience, is a tendency new
contributors can fall into. It keeps the plan grounded in the evidence of the repro report and filters out
speculation. As written, it still allows for speculation in the plan by not rejecting plans that use phrases
like "I suspect" or "my guess is that". I think it's fine for a contributor to share hypotheses about
various corollaries related to their issue as they can lead to productive dialogue with the maintainers.
However, it should be done without stating such hypotheses as fact.

**Trade-offs**

As noted above, this check might flip either accept or reject if there are instances in the plan's approach
where a suspected overclaim is made, but then walked back later in the plan. I would rather the check fail
in such instances so that I can either take some additional time to research my solution (as in `pkg-03`, look
at the manpages prior to submitting the plan), or make my known unknowns more explicit. 

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
