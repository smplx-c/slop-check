---
name: slop-check
description: Check a draft before it reaches a person, and find where it shifts work onto the reader instead of doing it. Use when asked to slop-check, de-slop, tighten, or sanity-check something before sending.
---

# Slop check

Run this on a draft before a person has to read it — a message, document, summary, answer, or commit message.

> **Unvalidated.** This check has not been run against a test set. The nine signatures below come from observed failures, not from measurement, and the severity order is a judgment. A quiet result from it is weak evidence, not clearance.

## The test

One question decides everything here:

> Does this move work to the reader that the writer should have done?

Slop is not bad writing. Bad writing announces itself. Slop reads well and still costs the recipient time, because the thinking it appears to contain was never done. BetterUp Labs and Stanford's Social Media Lab, who named it, define it as content that "appears polished but lacks real substance, offloading cognitive labor onto coworkers."

The cost is invisible to whoever produced it. That is why this runs as a separate step: the author cannot feel the problem.

## What to look for

Go through these in order. The first three cost people real time; the rest are padding.

**1. Unverified specifics.** A number, name, version, path, link, command, or quote stated with confidence. This is the worst kind, because it looks most like substance and the reader only finds out when it fails.

You are flagging candidates, not certifying facts. You cannot see what the author checked, so do not try to judge it — list every factual specific whose source is not visible in the draft itself, and for each say: verify, attribute, or mark as an assumption. Where you have tools, verify the pivotal ones and name which you verified. Where you do not, say so. Never let silence imply the specifics are sound.

**2. Untested instructions.** Commands, code, or steps presented as working. Shipping a command you have not executed is a claim you did not earn. You cannot tell from the text whether it was run, so treat every one as unrun unless the draft says otherwise: run it, or have the draft say plainly that it is untested.

**3. Answer not given.** The question was yes or no and the reply is a discussion. Or the recommendation is "it depends" without naming what it depends on. Put the direct answer in the first sentence. If there genuinely isn't one, say what is missing and what would settle it.

**4. Unasked scope.** The reply answers more than was asked — extra sections, adjacent observations, a second topic nobody raised. Cut to the question. A related point earns its place only if the reader would act differently without it.

**5. The trailing offer.** Ending with "shall I also…?" when nothing was asked for. It turns a finished turn into a decision the reader now has to make. At most one, and only when the next step is genuinely unclear and genuinely theirs.

**6. Repetition across turns.** A recommendation made a third time after the reader did not act on it twice. They heard it. Repeating it is noise, and it reads as not listening.

**7. Structure exceeding content.** Headers, tables, bullets and bold lead-ins wrapped around two sentences of substance. Formatting should follow from having several things to separate. If the content is a paragraph, make it a paragraph.

**8. Restated input.** Opening by summarizing what the reader just said before answering it. They know what they wrote. Start at the answer.

**9. Placeholder substance.** "Several factors", "best practices", "various considerations", a list of category names with nothing inside them. Each is a sentence that survived without saying anything. Replace with the specific, or delete.

## Severity

* **Blocking** — items 1 and 2. An unverified fact or an untested command sends the reader down a wrong path. Fix before sending.
* **Serious** — item 3. If the answer is absent, nothing else about the draft matters.
* **Worth fixing** — items 4 to 9. These cost reading time and credibility, not correctness.

## Output

Report only what you found, hit by hit:

```
<severity> · <item> · <quote or location>
→ <the specific fix>
```

Then one line on what to do before sending.

Do not open with an assessment of the draft's overall quality. Do not list the checks that passed. Do not praise the parts that were fine.

A clean draft gets one sentence saying so — followed by one naming what this pass could not check: which specifics you had no way to verify, and which commands you could not run. A report that stays silent about its own limits commits item 1 itself, and a reader who takes that silence for clearance is worse off than with no check at all.

If the draft is long, name the single cut that removes the most reader-time for the least loss, and be specific about it — "the three paragraphs under X repeat the table above."

## Applying it to this check's own output

The report fails if it is longer than the fix would be. Three real hits beat nine marginal ones. Where a draft has one blocking problem and six cosmetic ones, lead with the blocking problem and compress the rest into a single line.

And when nothing is wrong, say nothing is wrong. Manufacturing findings to look thorough is the same failure pointed the other way.
