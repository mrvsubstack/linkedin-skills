---
name: linkedin-content-planner
description: "Builds a 7-day LinkedIn plan from your theme, audience and pillars: which day gets which pillar, hook family, format, goal reaction and close, plus a daily list of people to comment on and a weekly balance check. Use this skill whenever the user says things like \"plan my LinkedIn week\", \"what should I post on LinkedIn this week\", \"give me a LinkedIn content calendar\", \"I keep posting randomly on LinkedIn\", \"plan my launch week on LinkedIn\", or \"build me LinkedIn content pillars\". Not for drafting the posts themselves (use linkedin-post-writer) or for a Substack plan (use substack-content-planner)."
metadata:
  author: Mr V
  version: "1.0"
  group: LinkedIn
---

# LinkedIn Content Planner

You give me what you want to be known for, who you want to reach and how many days you can post. I hand back a 7-day calendar where every post has a job, plus the commenting plan that makes the posts actually get seen.

This is a planning skill. It decides **what** and **why**. `linkedin-post-writer` does the **how**.

---

## The core discovery: plan the reactions, not the topics

Most calendars list topics. "Monday: leadership. Tuesday: AI." That's a list of nouns. It says nothing about what the post has to earn.

A week that only chases comments reads like bait. A week that only chases likes builds no pipeline. A good week spreads four reactions — **comments, reposts, likes, saves** — and each one does a different job for you.

**Rule: every slot in the plan names its goal reaction before it names its topic.**

---

## Step 0 — Intake

1. **Theme or focus** for the week. Default: "what I'm working on right now".
2. **Audience** in one line.
3. **Posting days.** Default: 3 posts (Tue, Wed, Thu). Range: 2–5. More than 5 rarely helps a personal profile.
4. **Pillars.** If none, use the default mix below.
5. **Raw material.** Stories, numbers, wins, mistakes, client questions from this week. The plan is only as good as this list. If it's empty, ask for 5 things that happened recently — not 5 opinions.
6. **Any launch or offer** this week. Default: none.

---

## Step 1 — Set the pillar mix

| Pillar | Share | What it proves |
|---|---|---|
| **Authority** | 40–50% | You know the work: frameworks, data, teardown |
| **Story** | 30–40% | You're a real person: mistakes, turning points, behind the scenes |
| **Community** | 15–25% | You lift others: thanks, spotlights, answering a question |
| **Offer** (optional) | max 1 post/week | What you sell, as the natural next step |

Rules:
1. **3–5 pillars, never more.** Six pillars is no pillars.
2. **No pillar above 60% of the week.**
3. **Offer max once a week.** A second sales post costs more trust than it earns.

---

## Step 2 — Assign goal and hook family per slot

| Goal | Hook families that fit (see `linkedin-post-writer`) |
|---|---|
| Comments | Contrarian with receipts · controlled comparison · dated admission |
| Reposts | Named thanks · end-of-an-era · free framework |
| Likes | Cold-open scene · good news in bad clothes · title stripped |
| Saves | Odd-precision ledger · plain-English glossary · free framework |

Rules:
1. **Each goal appears at least once in a 4-post week.** In a 3-post week, skip whichever goal matters least this week and say which.
2. **No hook family twice in 7 days.**
3. **Alternate formats inside a pillar.** Text, document/carousel, image, poll. Don't run three text posts for Authority.
4. **Every angle comes from the raw material.** Never put a number in an angle the user didn't give you.
   - Bad → "Tue: Authority — 5 tips for better meetings"
   - Good → "Tue: Authority — the 23-minute meeting rule that cut our weekly calls from 9 to 4 (from your note on 14 Oct)"

---

## Step 3 — Add the commenting plan

Comments on other people's posts put you in front of audiences that don't follow you yet. Plan them like posts.

For each posting day:
- **3–5 people or archetypes** to comment on ("peer founders with 5–20k followers", "two VCs who post about your category").
- **Mix:** about 70% peers, 20% people a level above, 10% potential buyers.
- **Volume:** 5–15 thoughtful comments a day, ideally in the hour before and after you post.
- **Pattern:** use `linkedin-comment-drafter` for each one.

---

## Step 4 — Run the weekly balance check

- [ ] At least one Story post with a real, dated detail.
- [ ] At least one Authority post with a number or receipt.
- [ ] At least one post that points (softly) at what you sell or offer.
- [ ] No pillar above 60%.
- [ ] No hook family repeated.
- [ ] Goals spread across the week.

If something fails, swap a slot. Say which and why.

---

## Worked example

**Input:** "B2B copywriter, audience is SaaS founders, 3 posts, raw material: rewrote a pricing page that lifted trials 18%; lost a retainer in August; a client asked 'how long should a homepage be?'"

**Output (calendar):**
| Day | Pillar | Goal | Hook family | Format | Angle |
|---|---|---|---|---|---|
| Tue | Authority | Saves | Odd-precision ledger | Document (6 slides) | The 7 lines we changed on a pricing page, and the 18% trial lift |
| Wed | Story | Comments | Dated admission | Text | "I lost my biggest retainer in August. The reason was in my own proposal." |
| Thu | Community | Reposts | Free framework | Text | Answering a client's "how long should a homepage be?" with the checklist I use |

Skipped goal: likes — this week is about pipeline. Commenting: 10/day, focus on 4 SaaS founders who post on pricing.

---

## Output format

```
WEEK OF [date] · Theme: [ ] · Audience: [ ]
Pillar mix: Authority [ ]% · Story [ ]% · Community [ ]% · Offer [ ]%

| Day | Time | Pillar | Goal | Hook family | Format | Angle (source) | Close |
|-----|------|--------|------|-------------|--------|----------------|-------|

COMMENTING PLAN
| Day | Who (names or archetypes) | Count | Note |

BALANCE CHECK: [each item ✓/✗, with the fix]
MISSING MATERIAL: [what to ask for before drafting]
Next step: draft each post with linkedin-post-writer.
```

Posting times: use the user's analytics if they have them. If not, write "weekday morning in your audience's time zone — confirm with your own analytics." Don't present general timing advice as fact.

---

## Sibling skills

- `linkedin-post-writer` — draft each slot.
- `linkedin-comment-drafter` — write the daily comments.
- `linkedin-engager-analytics` — after the week, see who actually engaged.
- `substack-content-planner` — if LinkedIn is feeding a newsletter, plan both together.

---

## Pre-flight checklist

- [ ] Every slot has a goal reaction before a topic?
- [ ] Every angle traces back to the user's raw material?
- [ ] No invented numbers?
- [ ] Pillar mix within limits, offer max once?
- [ ] No hook family repeated?
- [ ] Commenting plan included for each posting day?
- [ ] Balance check run and shown?
