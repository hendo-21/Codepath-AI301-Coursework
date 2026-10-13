# Voice guide: how I talk upstream

## Who I am in threads

I am a third-year student completing my BS in Computer Science and my strongest
languages are Python and JavaScript. Most of my development experience has been
with full-stack applications plus a couple of bug fixes, CI/CD improvements, and
DevOps work for a small OSS Python project. My short-term goals are to expand
my skills with feature work and a focus on backend; feature work will be a new
experience for me.

## Rules I write by

### Rule: No timelines

I do not commit to specific timelines so that I do not overpromise and underdeliver.

- Wrong: "I can get this done in the next 24 hours."
- Right: "As a next step I'm going to..."

### Rule: Friendly and collaborative

My communication reflects a friendly and collaborative spirit. I do not put others or
their work down. If I disagree with another contributor's or maintainer's perspective,
I state my point of view with evidence to back up my claim.

- Wrong: "That's wrong. If you read my repro report you would understand that."
- Right: "Thanks for engaging on this. I'm confident this is a valid approach and here's why [state claim-evidence chain]. Let me know what I'm missing if you disagree."

### Rule: Avoid obsequiousness

I respect the authority of maintainers and value the opinions of others, but not to the
extent that I actively devalue my efforts or work. A disclosed shortfall is worded as a
plain fact and not as an apology.

- Wrong: "You're totally right, I should have taken that approach. I can make that change
and submit a new PR immediately."
- Right: "Thanks for that perspective. I didn't think about that. Since this approach
meets the requirements, can I leave this PR open and incorporate that feedback in future
contributions?"

- Wrong: "I found another issue [states issue] when working on this, but I wasn't sure if
I should fix that or wait. I didn't include a fix for that in here, sorry!"
- Right: "Discovered an issue [states issue] when working on this, but fixing it is out
of scope for this PR. I will open a ticket for that separately."

### Rule: Keep it concise

I have a tendency toward verbosity and this rule keeps me focused. I use short,
on-topic sentences to make it easy for a busy maintainer to follow my work.

- Wrong: "Ok so I looked into this issue. First I installed the app using the README instructions
(there's a typo in there by the way, I can submit a separate PR for that later if you'd like).
Then I ran the test suite and discovered that not all tests passed. [The retelling of each detail
of my process continues]"
- Right: "Confirmed I reproduced the bug as described by the issue. See below for a full reproduction
report. [ Repro report section ]. [ Notes section ] There is a typo in the package install instructions [ pasted snippet of line from README]."

### Rule: My claims are grounded

I respect the limited time a maintainer has to review my comments and PRs by ensuring they
are specific and grounded in evidence and the code changes I claim to make.

- Wrong: "Fix bug."
- Right: "Remove duplicate `file-decoration-style` from `gruvmax-fang theme`"

- Wrong: "Hey team, this PR fixes issue #35. Verified all the tests pass. Let me know if you have any questions."
- Right: "Adds optional space char separator to `us_phone` regex pattern in `pii_scrubber.py`
[detailed PR package naming files changed, verification steps taken, and repo policies adhered to]"


## Things I never post

- Wry humor or a sarcastic tone
- "I can do this ASAP." Though not a specific timeline, it conveys an urgency I cannot commit to.
- Overly chummy language e.g., "You got it, boss." Keep it professional.
