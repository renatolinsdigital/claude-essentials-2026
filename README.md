# Claude Basics - Using It in 2026

A practical cheat sheet for choosing the right model, prompting better, and avoiding the common mistakes. Written for people who use Claude every day and want more out of it without reading extensive documentation.

**Contents:** [Models](#1-the-four-claude-models) ·
[The Fable method](#2-the-fable-method) ·
[The prompt to copy](#3-the-prompt-you-should-copy) ·
[Long chats](#4-claude-gets-dumber-in-long-chats) ·
[Sounding human](#5-stop-sounding-like-ai) ·
[Skills](#6-skills-worth-having-permanently) ·
[Features](#7-features-to-turn-on) ·
[Projects vs. chats](#8-projects-vs-plain-chats) ·
[Verifying output](#9-verify-before-you-trust-it) ·
[Mistakes to avoid](#10-what-not-to-do) ·
[Quick reference](#quick-reference-card)

---

## 1. The four Claude models

There is no single "Claude." There are four models that determine how Claude
responds, and picking the wrong one is the most common and most expensive
mistake people make.

| Model | Model ID | What it is | Use it for |
|---|---|---|---|
| **Haiku 4.5** | `claude-haiku-4-5-20251001` | Fastest, least smart | Speed, small jobs, high volume, classification |
| **Sonnet 5** | `claude-sonnet-5` | The middle one | Everyday work, most coding |
| **Opus 5** | `claude-opus-5` | Very smart, included in your plan | Most of your day-to-day work |
| **Fable 5** | `claude-fable-5` | The smartest, pay per use | The first prompt on a hard problem. Nothing else |

### How to actually choose

- **Default to Opus 5.** It is included in a paid plan and strong enough for
  nearly everything you will throw at it.
- **Drop to Haiku** when the job is mechanical and you want it now: extracting
  fields, renaming things, quick lookups, running the same small task 200
  times.
- **Reach for Fable** only when the problem is genuinely hard and the framing
  matters more than the typing: architecture decisions, a plan you will
  follow for weeks, something you cannot easily reverse.

Fable is metered per use, so treat it as a consultant you call in, not a
colleague you chat with all day.

### Effort level

Separate from the model is how much thinking it does per answer.

- **High** is the sensible default.
- **Max** for genuinely hard problems where a wrong answer costs you real
  time.
- **Low** for small, obvious work where you just want the output.

Effort is a dial you can turn per task. A high-effort Sonnet often beats a
low-effort Opus on a well-scoped problem.

---

## 2. The Fable method

The highest-leverage workflow in this whole document. Three steps.

**Step 1. Open with Fable 5 at high effort.**
Your first prompt frames the entire problem. Every later message inherits
that framing. Spend your best model on the moment that matters most.

**Step 2. Answer its questions.**
Ask it to interview you before it starts work. It will surface the
constraints you forgot to mention, which is exactly where most bad output
comes from.

**Step 3. Switch to Opus 5 at high effort and finish the job.**
Stay in the same chat. Click the model name and change it mid-conversation.
The expensive framing is already in the context; the execution does not need
to be expensive.

### Why this works

Claude re-reads the entire conversation on every single message. That means:

- Cost grows with conversation length, not just with what you typed.
- The quality of message 1 keeps paying you back, or keeps costing you.

Rough shape of how a long chat compounds (illustrative, not a price list):

| Conversation length | Relative cost |
|---|---|
| 2 prompts | pennies |
| 19 prompts | tens of times more |
| 40 prompts | approaching a hundred times more |

The takeaway is not the exact numbers. It is that a 40-message chat is not
twice as expensive as a 20-message chat. It is far worse than that.

---

## 3. The prompt you should copy

```
I need [task] for [goal].
I will know it worked when [target].
Ask me questions first, using the AskUserQuestion tool.
```

Four things are doing the work here:

1. **[task]** tells it what to produce.
2. **[goal]** tells it why, so it can make judgment calls the way you would.
3. **[target]** gives it a definition of done it can check itself against.
4. **Ask me questions first** stops it from guessing at everything you left
   out.

### Before and after

Old prompt, weak:

> "Write a follow-up email to this client."

Better prompt:

> "This client owes me 2 invoices and went quiet 3 weeks ago. Here is the
> thread. Get me paid without burning the relationship. Plan it, draft what
> is needed, ask me what you don't know."

The second one is not longer for the sake of it. It carries the stakes, the
history, the constraint, and the permission to ask. That is the whole
difference.

---

## 4. Claude gets dumber in long chats

Not because the model degrades, but because the context fills with noise, old
dead ends, and abandoned decisions it still has to reconcile.

- **Around 40 prompts:** answers get measurably worse and bills get bigger.
- **Around 100 prompts:** leave. Open a new chat. Paste in only what matters.
- **When Claude is wrong, do not argue.** Scroll up, edit the prompt that
  produced the bad answer, and resend. Arguing leaves the wrong answer
  sitting in the context forever. Editing deletes it.
- **Turn off connectors you are not using.** Every active integration loads
  its tool definitions into every single message.
- **New task, new chat. Every time.** The cheapest habit on this list to
  build.

These thresholds are rules of thumb, not hard limits. A dense technical chat
can wear out its welcome well before 40 messages; a chat of short back-and-forth
confirmations can run longer. Watch for the symptom, not the counter: Claude
re-explaining things you already settled, or contradicting a decision from
earlier in the same conversation.

---

## 5. Stop sounding like AI

Claude has recognizable verbal tics. If you are writing anything a human will
read, strip these out.

### Giveaway sentence shapes

- "It's not X, it's Y."
- "Forget X. This is Y."
- "Less X, more Y."
- "The question isn't X. The question is Y."
- "X is dead. Y is the future."

All five are the same move: a fake contrast that sounds insightful and says
nothing.

### Banned words

delve, leverage, unlock, tapestry, seamless, robust, pivotal, harness,
empower, streamline, game-changer

### Also remove

- Em dashes
- Title-Case Headings
- Bold-first bullets ("**Thing:** explanation")
- "Let's dive in"
- Lists of exactly three things

That last one is real. Claude reaches for three items by reflex. Use two, or
five, or seven, when that is the honest number.

### How to enforce it

Keep an anti-ai-writing-style skill containing the banned words and banned
sentence shapes, and have Claude audit its own drafts against it before
showing you anything. This rule applies to prose meant for a human reader:
emails, posts, decks. It does not apply to reference material like this one,
where bold labels and short bullets exist to make the page scannable, not to
sound persuasive.

---

## 6. Skills worth having permanently

Skills are reusable instruction sets that load when relevant. Three are worth
setting up on day one:

- **about-me:** who you are, what you do, what you love, what you hate. Kills
  an entire category of wrong-tone output.
- **my-company:** your role, your goals, where the business actually is. Lets
  Claude make business judgment calls instead of generic ones.
- **anti-ai-writing-style:** the banned list from section 5, applied as a
  self-audit.

Important caveat: do not load every skill you own. Each active skill narrows
what Claude explores. Skills are guardrails, and guardrails on every side
leave nowhere to go.

---

## 7. Features to turn on

- **Research mode.** Makes a plan, reads sources, hands back something closer
  to an analyst report than a chat reply. Use it when you need the sources,
  not just the summary.
- **Incognito mode.** Zero context carried in. Use it when you want a
  genuinely new idea and not a remix of everything you have discussed before.
- **Artifacts.** Claude writes a working mini-app that runs live on the right
  of your screen. Real code, not a description of code.
- **HTML infographics.** Claude cannot draw. It can code. If you want a
  visual, ask for an HTML design rather than an image.
- **Interactive charts.** Paste a CSV and ask for an interactive chart. Far
  more useful than asking it to describe your data back to you.
- **Memory.** Lets Claude carry facts about you and your projects across
  separate conversations, without you re-explaining them every time. Review
  what it has stored occasionally; delete anything stale or wrong.
- **Custom instructions / style.** A standing preference (tone, format,
  units, language) applied to every chat by default, so you are not repeating
  it in every prompt.

---

## 8. Projects vs. plain chats

A Project bundles fixed reference material, documents, a style guide, a
codebase, so that every conversation inside it starts with that context
already loaded.

- **Use a Project** for recurring work against material that does not change
  often: a client's brand guidelines, a codebase you work in daily, a body of
  research you keep referencing.
- **Use a plain chat** for anything one-off, and for anything creative where
  you want a fresh angle rather than a remix of the Project's files (see
  mistake #2 in the next section).
- **Do not treat a Project like a junk drawer.** Forty loosely related files
  dilute the context as much as they inform it. Keep only what every chat in
  that Project will actually need.

---

## 9. Verify before you trust it

Claude can state something incorrect with the same confident tone as
something correct. Fluency is not evidence.

- **Treat unfamiliar facts, numbers, and citations as unverified** until you
  check them yourself. This applies doubly to anything you did not already
  know before asking.
- **For code, run it.** Passing a review or looking plausible is not the same
  as working.
- **For research, open the source.** A summary can misquote or overstate what
  the underlying document actually says.
- **For numbers, recompute the ones that matter.** Arithmetic errors are rare
  but they happen, and they are expensive when they land in a budget or a
  contract.
- **Ask it to flag its own uncertainty** rather than assuming a confident
  answer means a correct one. It will tell you when asked directly far more
  often than it will volunteer it.

The higher the stakes of being wrong, the more this matters. A blog post
draft can tolerate an unchecked claim. A number that goes into a filing
cannot.

---

## 10. What not to do

**1. Using Fable for small jobs.**
Rewriting an email with Fable is shooting a bird with a bazooka. Opus does
it, and Opus is already included.

**2. Piling forty files into a Project and then asking for a new idea.**
Projects are for repeated work against fixed material. For anything
creative, start from an empty chat.

**3. Loading every skill you own.**
Each one narrows the search space. More skills means less exploration, not
more capability.

**4. Asking it to "make it punchier."**
Adjectives do almost nothing. Instead, paste writing you think is bad and say
"never write like this." Negative examples carry far more signal than vague
positive direction.

**5. Chasing whatever technique launched this month.**
A technique matters once it has become invisible, when you use it without
thinking about it. Until then, just do your job better.

**6. Trusting a confident answer because it was confident.**
See section 9. The tone of a Claude answer carries no information about its
accuracy.

---

## Quick reference card

| Situation | Do this |
|---|---|
| Starting something hard | Fable 5, high effort, ask it to interview you |
| Ordinary work | Opus 5, high effort |
| Bulk or mechanical work | Haiku 4.5 |
| Claude gave a bad answer | Edit the original prompt, do not argue |
| Chat is past 40 messages | Wrap up or restart |
| Chat is past 100 messages | Leave. New chat. |
| New task | New chat, always |
| Writing for humans | Run it against the banned words and shapes |
| Want a visual | Ask for HTML, not an image |
| Recurring work on fixed material | Use a Project |
| One-off or creative work | Use a plain chat |
| An unfamiliar fact, number, or citation | Verify it before you rely on it |
