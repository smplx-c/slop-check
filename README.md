# Slop check

**A gate between a draft and a person: find the places where it shifts work onto the reader instead of doing it.**

A Claude skill. Nine signatures, ranked by what they actually cost, and a report that is allowed to be one sentence long.

→ [**Download `slop-check.skill`**](https://github.com/smplx-c/slop-check/releases/latest/download/slop-check.skill) for Cowork and the Claude app, or clone the folder for Claude Code — see [Installation](#installation).

---

## The problem it solves

Bad writing announces itself. Slop does not. It reads well, carries headers and confident specifics, and still costs the recipient time, because the thinking it appears to contain was never done.

BetterUp Labs and Stanford's Social Media Lab call it [workslop](https://hbr.org/2025/09/ai-generated-workslop-is-destroying-productivity) — "content that appears polished but lacks real substance, offloading cognitive labor onto coworkers." In their survey of 962 US desk workers, 38% reported receiving it and put the cleanup at 3.4 hours a month. Shopify's Tobi Lütke has [a blunter name](https://fortune.com/2026/09/17/shopify-tobias-lutke-ai-slop-grenades/): *"slop grenades that people toss at each other."*

The reason it keeps happening is the asymmetry: it is cheap to produce and expensive to read, so nothing stops the person generating it. The author cannot feel the cost, which is also why self-review does not catch it. That is the case for running an explicit pass with one question:

> Does this move work to the reader that the writer should have done?

## What it checks

Nine signatures, ordered by damage:

| | Signature | Cost |
|---|---|---|
| 1 | Unverified specifics — a number, path, link or quote stated with confidence, never checked | **Blocking** |
| 2 | Untested instructions — commands or code presented as working, never run | **Blocking** |
| 3 | Answer not given — a yes/no question met with a discussion | **Serious** |
| 4 | Unasked scope — answering more than was asked | Worth fixing |
| 5 | The trailing offer — "shall I also…?" when nothing was asked for | Worth fixing |
| 6 | Repetition across turns — the third mention of advice already ignored twice | Worth fixing |
| 7 | Structure exceeding content — headers and tables around two sentences | Worth fixing |
| 8 | Restated input — summarizing the reader's own message back at them | Worth fixing |
| 9 | Placeholder substance — "several factors", "best practices", empty categories | Worth fixing |

The first two are first for a reason. An unverified fact or an untested command does not waste time, it sends the reader somewhere wrong — and it is the hardest kind to spot, because confident specifics are what substance looks like.

They are also the two the check cannot settle on its own. It can see that a draft asserts a version number; it cannot see whether the author looked it up. So items 1 and 2 flag candidates rather than certify facts, and a quiet report has to say what it had no way to check. A gate that can silently certify what it cannot inspect is worse than no gate, because the reader stops looking.

**This check has not been run against a test set.** The nine signatures come from observed failures, not measurement, and the severity order is a judgment. Treat a clean result as weak evidence.

## What it doesn't do

It will not stop a model producing slop by default. Skills load when invoked, and whoever is producing slop is not invoking the slop check. This is a gate you run on a draft, not a personality. Default behaviour belongs in `CLAUDE.md` or your output settings.

It also has opinions you may not share — item 5 treats the trailing offer as a defect, which is wrong in a conversation that is genuinely collaborative. Change the line.

## Installation

A skill is a folder of instructions. On invocation, `SKILL.md` is loaded into Claude's context and changes how it approaches that one response. It is plain text, calls no tools, and has no environment dependency, so it runs anywhere Claude loads skills. Only the install route differs.

**Claude Code** — clone into your skills directory:

```bash
git clone https://github.com/smplx-c/slop-check.git ~/.claude/skills/slop-check
```

**Cowork / Claude Desktop** — download `slop-check.skill` from the [latest release](https://github.com/smplx-c/slop-check/releases/latest) and drop it into a chat. The file card shows **Save skill**, provided your organization permits skill creation.

## Using it

```
/slop-check
```

on the preceding output, or paste the draft after it. It also answers to "de-slop this" and "check this before I send it".

## Relationship to minto

[minto](https://github.com/smplx-c/minto-skill) and this skill overlap without duplicating. `/minto critique` asks whether the argument holds — is the answer up front, does each claim rest on what sits beneath it. Slop check asks whether the draft is fit to send — is anything in it unverified, untested, padded or unasked for.

A document can pass one and fail the other. Well-argued and three times too long, with a command nobody ran. Or tight and fully verified, with the conclusion buried on page two.

## Repository layout

```
slop-check/
├── SKILL.md      the check itself
└── README.md     this document
```

One file, deliberately. A long document against bloated output would be its own counterexample.
