---
name: linkedin-repurposer
description: "Rebuilds something you already made — a tweet, thread, video script, blog post, newsletter or caption — into a native LinkedIn post with a new hook above the fold, LinkedIn length and spacing, real stakes and the link moved out of the body. Use this skill whenever the user says things like \"turn this tweet into a LinkedIn post\", \"repurpose my newsletter for LinkedIn\", \"adapt this video for LinkedIn\", \"this did well on X, make it work on LinkedIn\", \"cross-post this to LinkedIn\", or \"make this LinkedIn-native\". Not for writing from a blank page (use linkedin-post-writer)."
metadata:
  author: Mr V
  version: "1.0"
  group: LinkedIn
---

# LinkedIn Repurposer

You paste something you've already made. I hand back a LinkedIn post that reads like it was written for LinkedIn first — plus a short map of what came from where.

This transforms. It doesn't generate. The idea, the claims and the numbers stay yours.

---

## The core discovery: keep the spine, rebuild the body

Pasted content flops because every platform has a different shape. A tweet is too short and has no whitespace. A newsletter is too long and has three ideas. A video script talks to an ear, not an eye.

What travels between platforms is the **spine**: the one claim, story or number worth keeping. Everything around it gets rebuilt.

**Rule: never paste and trim. Extract the spine, then write the LinkedIn post around it.**

---

## Step 0 — Intake

1. **The source.** Text, transcript or script. If it's a link, ask for the text (or read it with web search if available and say so).
2. **Goal reaction:** comments, reposts, likes or saves. Default: comments.
3. **Length:** default 900–1,300 characters.
4. **Where the source link should go**, if any. Default: first comment.

---

## Step 1 — Extract the spine

Write it in one sentence before drafting anything:
`SPINE: [the claim] — proved by [the story or number].`

If the source has three ideas, pick one. Offer the other two as separate posts.

- Bad → "SPINE: lots of tips on email marketing."
- Good → "SPINE: welcome emails that ask one question get more replies than ones that deliver a freebie — proved by 31% vs 9% reply rate in my own list test."

---

## Step 2 — Rebuild by source type

| Source | What to do |
|---|---|
| **Single tweet** | It's a hook, not a post. Keep the line, grow the argument under it with stakes and proof. |
| **X thread** | Unroll into one flowing post, not a numbered list. The best tweet becomes the hook — usually not tweet 1. |
| **Video / script** | Lead with the payoff, then how you got there. Cut spoken filler ("so basically", "alright guys"). Link the video in the first comment. |
| **Blog / newsletter** | Take the most quotable claim plus the one story that proves it. Don't summarise the whole piece. |
| **Instagram / TikTok caption** | Strip emoji density and hashtag blocks. Add the professional stakes LinkedIn readers care about. |

---

## Step 3 — Re-hook for the fold

The source's hook rarely survives. Write a new first line for LinkedIn using a hook family from `linkedin-post-writer`, picked by the goal. Line 1 is a statement or number, never a question, and the hook lands within the first ~200 characters.

---

## Step 4 — Strip platform leftovers

Remove:
1. "Link in bio", "smash subscribe", "RT if you agree".
2. @-handles from X or Instagram (use real names, or tag on LinkedIn properly).
3. Hashtag walls. Keep 0–2 at the end.
4. "As I tweeted last week…" throat-clearing.
5. Links in the body — move them to the first comment.

Add:
1. One moment of real stakes if the source had none.
2. Blank lines between every 1–2 sentences.
3. A specific closing question.

---

## Step 5 — Scrub

Run the quick `linkedin-humanizer` check. Keep the source's real numbers and names exactly.

---

## Worked example

**Source (tweet):** "Unpopular opinion: your welcome email shouldn't deliver the freebie. It should ask a question. Mine went from 9% to 31% replies."

**Output:**
```
My welcome email used to deliver a free PDF. Reply rate: 9%.

I changed one thing. Instead of the PDF, the first email asks a single question: "What made you subscribe today?"

Reply rate: 31%.

The PDF still arrives, in email two.

What I didn't expect was what the replies did for everything else. 214 people told me, in their own words, what they wanted. Six of my next ten posts came straight from those answers.

A freebie gets downloaded. A question gets you a conversation, and a list of topics you didn't have to guess.

What's the first thing your welcome email asks people to do?
```
MAP: tweet line → hook rebuilt as a number-first statement · "214 people" and "6 of 10 posts" → asked the user and confirmed · link → none.

---

## Output format

```
SPINE: [one sentence]
SOURCE → LINKEDIN MAP: [what was kept, cut, added]

--- POST (copy-ready) ---
[post]
--- END ---

Characters: [n]
First comment: [link text, or "none"]
Spin-offs: [other ideas from the source worth their own post]
Placeholders to fill: [ ]
```

---

## Sibling skills

- `linkedin-postiz-publisher` — schedule the finished post through Postiz after you approve it.
- `linkedin-post-writer` — no source yet; start from scratch.
- `linkedin-humanizer` — full scrub or audit of the result.
- `ig-repurposer`, `threads-repurposer`, `x-thread-builder` — take the same spine to other platforms.

---

## Pre-flight checklist

- [ ] Spine written in one sentence first?
- [ ] Rebuilt, not pasted and trimmed?
- [ ] New hook inside the first ~200 characters, not a question?
- [ ] All platform leftovers stripped, link moved to first comment?
- [ ] Source numbers and claims unchanged, nothing added that the user didn't confirm?
- [ ] Ends with a specific question?
