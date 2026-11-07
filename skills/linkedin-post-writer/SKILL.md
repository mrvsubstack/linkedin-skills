---
name: linkedin-post-writer
description: "Writes a LinkedIn post from a topic or rough notes, using a hook picked by the reaction you want (comments, reposts, likes or saves), a fold-proof opening and a clean pre-publish scrub, then hands it back as a copy-ready block. Use this skill whenever the user says things like \"write me a LinkedIn post\", \"turn this idea into a LinkedIn post\", \"I need a hook for LinkedIn\", \"draft my post for Tuesday\", \"make this land on LinkedIn\", \"give me 3 LinkedIn hooks for this\", or \"write a founder post about X\". Not for rebuilding something you already published elsewhere (use linkedin-repurposer) or checking a finished draft (use linkedin-humanizer in audit mode)."
metadata:
  author: Mr V
  version: "1.0"
  group: LinkedIn
---

# LinkedIn Post Writer

You give me a topic, a story or a pile of notes. I hand you back one finished LinkedIn post, ready to paste, with the hook chosen on purpose and the reasoning behind it.

This is a writing skill. Not a brainstorm. If you don't know what to post yet, plan the week first with `linkedin-content-planner`.

---

## The core discovery: the post is decided above the fold

LinkedIn shows roughly the first 2–3 lines (about 200 characters on most screens) before "…see more". Everything you wrote below that line only exists for people who clicked.

So the hook is not the first part of the post. It is the post's entire distribution strategy. A good body under a weak hook is a private journal entry.

**Rule: write the hook last, and pick it by the reaction you want — not by what sounds clever.**

---

## Step 0 — Intake (ask only for what's missing)

1. **Topic or raw material.** Notes, a story, a number, a lesson.
2. **Goal reaction.** Comments, reposts, likes or saves. Default: comments.
3. **Audience.** Who should stop scrolling. Default: peers in the user's field.
4. **Length.** Short (300–600 chars), standard (900–1,300), long (1,500–2,500). Default: standard. LinkedIn's hard cap is 3,000 characters — verify if unsure.
5. **One real detail.** A number, a date, a name, a moment. If none exists, ask for it. Never invent one.

If a voice profile from `voice-profile-bank` or past posts are available, load them first and match them.

---

## Step 1 — Pick the hook by goal

Each goal has a family of hooks that tends to earn it. Offer 2–3 that fit the topic and let the user choose.

| Goal | Hook family | Shape |
|---|---|---|
| **Comments** | Contrarian with receipts | "Everyone says [belief]. I tracked [thing] for [time]. [Opposite finding]." |
| | Controlled comparison | "Same [task], two ways. Only one variable changed. [Result]." |
| | Dated admission | "[Date]: I [specific mistake]. It cost [specific amount]." |
| **Reposts** | Named thanks | "[Number] people made [result] possible. None of them work for me." |
| | End-of-an-era | "[Old practice] died this year. Here's what replaced it." |
| | Free framework | "I charged [amount] for this framework. Here it is, free." |
| **Likes** | Cold-open scene | Drop the reader inside a moment with stakes. No setup line. |
| | Good news in bad clothes | Opens like a loss, resolves as an upgrade. |
| | Title stripped | "At work I'm [title]. At home [small humbling truth]." |
| **Saves** | Odd-precision ledger | "[Exact number] spent on [thing]. Line by line." |
| | Plain-English glossary | "[Jargon] explained like you're new to it." |

### Hook rules
1. **Statement or number in line 1. Never a question.** Questions belong at the close.
   - Bad → "Ever wondered why your posts flop?"
   - Good → "41 posts. 3 got past 2,000 views. All 3 broke the same rule."
2. **Odd precision beats round numbers.** "$4,730" reads like a receipt. "$5k" reads like a guess.
3. **No announced honesty.** The fact carries the vulnerability.
   - Bad → "I'll be honest, this one hurt: we lost a client."
   - Good → "We lost our biggest client on 14 February."
4. **No reveal bridges.** Cut "Here's the thing", "The result?", "Plot twist:", "Stop X, start Y".
5. **Pay off any curiosity gap within two lines.** An unpaid teaser reads as bait.

---

## Step 2 — Build the body

Use this spine for any hook:

```
HOOK         (1–2 lines, above the fold)
STAKES       (why this mattered — money, time, reputation, a person)
TURN         (what you noticed, tried or got wrong)
PROOF        (the number, the example, the before/after)
TAKEAWAY     (one sentence the reader can steal)
CLOSE        (a specific question — or a P.S. with a real follow-up)
```

### Body rules
1. **One or two sentences per paragraph, blank line between.** Mobile readers skim.
2. **One idea per post.** Three ideas means three posts.
3. **One contrast and one list of three, maximum.** More reads engineered.
4. **At least one moment of real stakes.** Pure insight posts don't travel. Something has to be at risk.
   - Bad → "Consistency is key to growth."
   - Good → "I posted 5 days a week for 11 weeks. Follower count moved 212. Then one honest post moved 1,900."
5. **No links in the body.** Put them in the first comment and say so in the delivery note. Verify current link treatment with web search if the user asks — it changes.
6. **0–2 hashtags, at the end.** Or none.
7. **Close with a question someone can answer from their own experience.**
   - Bad → "What do you think?"
   - Good → "What's one metric you stopped tracking and never missed?"

---

## Step 3 — Scrub before delivery

Run the quick version of `linkedin-humanizer` on the draft:
- No paragraph carries three or more stock AI words (leverage, crucial, landscape, robust, foster, elevate, navigate, comprehensive).
- No staccato runs ("Simple. Fast. Done.").
- No "It's not X, it's Y" more than once.
- Em dashes capped at about one per 100 words.
- Every number has a referent: who, what, when or what it cost.

---

## Worked example

**Input:** "Topic: I stopped using a content calendar. Goal: comments. Audience: solo consultants. Detail: I went from 3 posts a week planned to writing the morning of, and inbound calls went from 2 to 7 in a month."

**Output:**
```
I deleted my content calendar on 2 September.

Inbound calls that month: 7. The month before: 2.

For a year I planned 3 posts a week, 14 days ahead. Every post was on time. Every post was about something I'd stopped caring about by the day it went out.

Now I write the morning of, from whatever a client asked me the day before.

The posts are rougher. Two had typos.

But they answer questions people are actually asking this week, not the ones I guessed they'd ask a fortnight ago.

A plan protects your consistency. It can also protect you from being relevant.

Solo consultants: are you writing from a calendar or from your inbox?
```
Hook family: Dated admission → comments. 742 characters. Link: none.

---

## Output format

```
GOAL: [comments / reposts / likes / saves]
HOOK OPTIONS:
  A) [line] — family: [ ] — why it fits: [ ]
  B) [line] — family: [ ]
  C) [line] — family: [ ]
CHOSEN: [A/B/C]

--- POST (copy-ready) ---
[full post]
--- END ---

Characters: [n] / 3,000
First comment (if a link is needed): [text]
Best window: [user's audience peak; if unknown, "weekday mornings in your audience's time zone — check your own analytics"]
Placeholders to fill: [any [your number] left in]
```

---

## Sibling skills

- `linkedin-postiz-publisher` — schedule the finished post through Postiz after you approve it.
- `linkedin-content-planner` — decide what to post this week before writing it.
- `linkedin-hook-extractor` — steal the structure of a post you admire, then come back here.
- `linkedin-repurposer` — the idea already exists as a tweet, video or newsletter.
- `linkedin-humanizer` — full scrub or audit of a finished draft.

---

## Pre-flight checklist

- [ ] Goal reaction chosen, and the hook family matches it?
- [ ] Line 1 is a statement or a number, not a question?
- [ ] Hook lands inside the first ~200 characters?
- [ ] At least one real number with a referent — none invented?
- [ ] One moment of real stakes?
- [ ] No link in the body, 0–2 hashtags?
- [ ] Closing question is specific and answerable?
- [ ] Scrub passed: no 3+ AI words per paragraph, no staccato runs, em dashes capped?
- [ ] Delivered as one copy-ready block with character count?
