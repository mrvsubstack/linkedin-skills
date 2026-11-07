---
name: linkedin-humanizer
description: "Strips the patterns that make a LinkedIn post or comment read machine-written — stacked AI vocabulary, reveal bridges, staccato fragments, triple lists, performed honesty — without flattening the writer's real voice. Three modes: Rewrite (default), Audit (pass/fail review before posting, no rewrite) and Profile (learn your voice from 3–6 past posts). Use this skill whenever the user says things like \"humanize this LinkedIn post\", \"this sounds like ChatGPT\", \"de-AI my draft\", \"audit this before I post\", \"check my post\", \"why does this feel off\", or \"learn how I write on LinkedIn\". Not for writing from scratch (use linkedin-post-writer) and not a tool for beating AI detectors."
metadata:
  author: Mr V
  version: "1.0"
  group: LinkedIn
---

# LinkedIn Humanizer

You paste a draft. I hand back the cleaned version, a short list of what I changed and why, and a verdict: **reads human / mixed / reads AI**.

What this is not: a detector-beater. No edit reliably fools AI detectors, and on a 200-word post their scores are noise. This skill fixes what **human readers** notice — the patterns that make someone think "AI wrote this" and scroll past.

---

## The core discovery: one marker is English, three is a signature

"Crucial" is a normal word. "Crucial" next to "landscape" next to "leverage" in one paragraph is a fingerprint. Readers don't react to single words. They react to density and to a handful of structural habits.

The second half of the discovery: **over-correcting is its own tell.** A draft chopped into "Short. Punchy. Done." fragments, with every dash removed and a fake confession bolted on, reads more machine-made than the original.

**Rule: judge by the paragraph, not the word. Edit in proportion to real problems. A clean draft gets two touches, not twenty.**

---

## The three modes

### Mode 1 — Rewrite (default)
**When:** you have a draft and want it ready to post.
**How:** run the four passes below, return the clean version and a change list.

### Mode 2 — Audit
**When:** "check this before I post". You want a verdict, not a rewrite.
**How:** run the audit checklist. Return **Blockers** (fix before posting), **Warnings** (worth fixing) and one suggested fix per item. Change nothing.

### Mode 3 — Profile
**When:** "learn how I write". You paste 3–6 posts you wrote yourself and liked.
**How:** pull out checkable habits — average sentence length, how you open, how you close, words you use and never use, punctuation quirks (lowercase starts, "..", one em dash), how you handle numbers. Output them as rules with a real example each. Hand them to `voice-profile-bank` to store. Never invent a rule you can't point to in their posts.

---

## The four passes (Rewrite mode)

### Pass 1 — Scrub
Count markers per paragraph. **3 or more → rewrite the paragraph. 2 → replace the weakest. 1 → leave it.**

**Vocabulary markers:** significant, crucial, notably, comprehensive, insights, robust, leverage, foster, landscape, nuanced, holistic, streamline, elevate, empower, navigate, unlock, seamless, fundamentally, ultimately, delve, tapestry, journey (as metaphor).

**LinkedIn-flavoured markers:** "quietly", "X matters.", "load-bearing", "doing the heavy lifting", "let that sink in", "that's the real story", "built different".

**Grammar markers:** a sentence opening with an -ing clause ("Leveraging our data, we…") → put the actor first. Nominalisations ("the implementation of") → use the verb.

**Single-hit phrases — always fix:**
1. "It's not X, it's Y" and its cousins ("This isn't about X. It's about Y.")
   - Bad → "It's not about posting more. It's about posting better."
   - Good → "I posted half as often in March. Views went up 40%."
2. Reveal bridges: "The result?", "The catch?", "Here's the thing", "Here's what happened", "Plot twist:".
3. "Stop X, start Y" openers.
4. "In today's fast-paced world", "game-changer", "deep dive", "at the end of the day".
5. Closers: "What do you think?", "Tag someone who needs this", "Agree?".

**Punctuation:** em dashes capped at about one per 100 words. Replace the excess with a comma, colon or brackets — **never a full stop** (that creates fragments). Don't remove every dash; zero is its own tell. Straight quotes, not curly.

### Pass 2 — Rhythm
Fix only what's broken. Never manufacture variety.
1. **Kill fragment runs.**
   - Bad → "Simple. Effective. Free."
   - Good → "It's simple, it works, and it costs nothing."
2. **Max two standalone fragments in the whole post.**
3. **No one-word paragraphs** ("Still." "Exactly.").
4. **No "Why? Because…" fake dialogue.**
5. **Triple lists:** one natural triple per post is fine. Two stacked, perfectly parallel triples → break one.
6. **Machine-flat paragraph** (every sentence the same length, nothing doing work): change one sentence, not the whole paragraph.
7. **Keep the layout.** 1–2 sentences per paragraph with blank lines is normal LinkedIn formatting, not a tell.

### Pass 3 — Add (only what the writer gives you)
A human post usually has:
- One number with a referent: who, what, when or what it cost. "$4,730 in overage fees on the March invoice", not "significant costs".
- One named thing: a person, company, tool, place or date.
- One moment you saw, heard or did.
- One flat, dated, uncomfortable fact — with no framing sentence.
  - Bad → "I'll be honest, this one hurt. We lost a client."
  - Good → "We lost our largest client on 14 February."

If the draft lacks these, **ask**. Never insert a number, name, confession or hedge the writer didn't give you. Banned insertions: "let me be honest", "real talk", "I'll say the quiet part", "honestly?", "I might be wrong but".

### Pass 4 — Self-check
Re-read once and ask:
1. Did I create fragment runs, reveal bridges or a long/short/long/short seesaw? → merge back.
2. Did I add a framed confession or a hedge? → strip it.
3. Did I flatten the writer — every dash gone, every triple gone, every quirk sanded off? → restore it.

If any answer is yes, dial back.

---

## Audit checklist (Mode 2)

**Blockers:**
- Question as line 1.
- Hook doesn't land in the first ~200 characters.
- Link in the body.
- Any paragraph with 3+ markers.
- Any "It's not X, it's Y", reveal bridge or "Stop X, start Y".
- An invented-sounding stat with no source.
- Over 3,000 characters (verify current limit).

**Warnings:**
- More than 2 hashtags.
- Generic close ("Thoughts?").
- No number with a referent, no named entity.
- More than 2 standalone fragments.
- Em dashes above the cap.

---

## Worked example (Rewrite)

**Input:**
"In today's fast-paced landscape, leveraging AI is crucial. The result? Teams that unlock seamless workflows. It's not about working harder. It's about working smarter. Agree?"

**Output:**
```
We put an AI note-taker in every sales call in June.

By August, reps were spending 3 hours less a week on CRM updates. Two of them used the time for more calls. One used it to leave at 5.

I'm fine with both.

Which admin task would you hand over first?
```
Changes: removed 6 markers in one paragraph (fast-paced, landscape, leveraging, crucial, unlock, seamless) · cut reveal bridge "The result?" · cut "not X, it's Y" · replaced "Agree?" with a specific question · **asked the user** for the June date and the 3-hour figure before using them.
Verdict: reads human.

---

## Output format

```
MODE: [rewrite / audit / profile]
VERDICT: [reads human / mixed / reads AI] (a reader estimate — not a detector score)

--- CLEAN VERSION (copy-ready) ---
[text]
--- END ---

CHANGES
- [pattern found] → [what I did]
PARAGRAPH DENSITY: P1 [n] · P2 [n] · …
ASKED / NEEDS FROM YOU: [numbers, names, dates]
LEFT ALONE ON PURPOSE: [quirks kept]
```

---

## Sibling skills

- `linkedin-post-writer` — write the post in the first place.
- `voice-profile-bank` — store the rules Profile mode finds.
- `final-edit-modes` — line-edit in Mr V's own published voice.
- `ig-humanizer`, `threads-humanizer`, `x-humanizer` — same method, other platforms.

---

## Pre-flight checklist

- [ ] Markers counted per paragraph, not per word?
- [ ] Every single-hit phrase fixed?
- [ ] No fragments created, no dash swapped for a full stop?
- [ ] Nothing inserted the writer didn't supply?
- [ ] Self-check run, over-corrections reversed?
- [ ] Verdict labelled as a reader estimate, never a detector promise?
