---
name: linkedin-profile-optimizer
description: "Audits a LinkedIn profile section by section and rewrites the headline, About, Featured and Experience so the profile turns post readers into inbound leads, job offers or followers. Use this skill whenever the user says things like \"review my LinkedIn profile\", \"rewrite my headline\", \"fix my About section\", \"what should go in Featured\", \"my profile reads like a CV\", \"LinkedIn profile audit\", or \"make my profile bring in clients\". Not for writing feed posts (use linkedin-post-writer) or planning content (use linkedin-content-planner)."
metadata:
  author: Mr V
  version: "1.0"
  group: LinkedIn
---

# LinkedIn Profile Optimizer

You paste your profile (or screenshots of it) and tell me what you want it to bring in. I hand back a scorecard of nine sections, the three fixes that matter most, and before → after rewrites ready to paste.

This skill reads only what you show it. A bare profile URL can't be read reliably, so paste the text.

---

## The core discovery: your profile is a landing page, not a CV

People reach your profile from one place: a post or comment of yours that made them curious. They have one question — "should I follow, hire or message this person?" — and about 5 seconds to answer it.

A CV answers "what have you done?" A landing page answers "what can you do for me?" Most profiles are CVs.

**Rule: every section must answer the visitor's question for the one goal you picked. If a line only serves your ego, cut it.**

---

## Step 0 — Intake

Ask for, one at a time if missing:
1. **Pasted text**: headline, About, the top 2–3 Experience entries, Skills, custom URL.
2. **The visual three**: photo, banner, Featured — screenshots or one sentence each.
3. **The goal** (pick one): **Clients**, **Job offers**, or **Authority/followers**. Default: Clients.
4. **Who you want to reach**, in one line ("ops leaders at 50–500 person SaaS companies").
5. **One proof point**: a result with a number. If none, mark proof as MISSING — don't invent one.

Never score a section you haven't been shown. Write "NOT SHOWN" instead.

---

## Step 1 — Score nine sections

Score each **Pass / Needs work / Fail**. Character limits and image sizes change — confirm current specs with web search before quoting them as fact, and label anything unverified.

| # | Section | Passes when |
|---|---|---|
| 1 | **Photo** | Face clearly visible, recent, plain background, looks like you on a video call |
| 2 | **Banner** | Says what you do or for whom; key text not hidden behind the photo on mobile |
| 3 | **Headline** | Names who you help and the result — not just a job title (limit ~220 chars) |
| 4 | **About** | Opens with the reader's problem, first ~3 lines work alone, first person, ends with one action |
| 5 | **Featured** | 2–3 items, each matched to the goal |
| 6 | **Experience** | Bullets are verb + result with a number, not duties |
| 7 | **Skills** | Top 3 pinned and match the words your target buyer or recruiter searches for |
| 8 | **Custom URL** | Clean name, no random digits |
| 9 | **Recommendations** | At least 2–3 specific ones from people your target trusts |

---

## Step 2 — Rewrite what failed

### Headline
**Formula:** `[What you do] for [who] | [result or proof] | [one hook of personality or point of view]`

1. **Lead with the buyer, not the title.**
   - Bad → "Senior Marketing Manager at Acme | Passionate about growth"
   - Good → "I help B2B SaaS teams turn webinars into pipeline | 41 webinars, $2.3M sourced | Ex-Acme"
2. **Use the words your audience searches.** "Fractional CFO" beats "financial strategist" if that's the phrase buyers type.
3. **Ban CV filler.** Passionate, driven, results-oriented, thought leader, visionary.

### About — the 7-beat structure
1. **Hook (first ~3 lines, before "see more")** — the reader's problem in their words.
2. **Why it's hard** — the thing everyone tries that doesn't work.
3. **What you do differently** — your method in one or two sentences.
4. **Proof** — numbers, names you're allowed to use, results.
5. **Who it's for (and not for)** — one line each.
6. **A human line** — one specific, true personal detail.
7. **One action** — DM a word, book a call, read the newsletter.

Bad opening → "I am a results-driven marketing professional with 12 years of experience."
Good opening → "Your webinar got 400 signups. Then sales asked where the pipeline was."

Keep it 200–350 words, first person, short paragraphs.

### Featured — pick by goal
| Goal | Item 1 | Item 2 | Item 3 |
|---|---|---|---|
| Clients | Lead magnet or free resource | Case study with a number | Booking link or offer page |
| Job offers | Portfolio or work sample | Your best-performing post | Talk, article or project |
| Authority | Newsletter signup | Best post or series | Podcast/press feature |

### Experience
Rewrite each bullet as **verb + what changed + number**.
- Bad → "Responsible for managing social media."
- Good → "Grew LinkedIn page from 1,100 to 9,400 followers in 10 months; 31% of demo requests cited it."

If the user has no number, write `[your number]` and ask.

### Recommendations
Draft a specific ask, not LinkedIn's default:
"Hi [name] — would you write 2–3 lines about the [project] we did? Especially [the specific result]. Happy to return the favour."

---

## Worked example

**Input:** Headline "Founder at Brightline Studio". About opens "Brightline Studio is a creative agency founded in 2019." Goal: clients. Audience: DTC brands doing $1–10M.

**Output (headline + About hook):**
```
BEFORE: Founder at Brightline Studio
AFTER:  Ad creative for DTC brands doing $1–10M | 212 ads shipped in 2025 | We test 10 hooks before we film 1

BEFORE: Brightline Studio is a creative agency founded in 2019.
AFTER:  Your ads stopped working in week three. Again.
        Not because the product changed. Because the hook wore out and nobody had the next ten ready.
```
(The "212 ads" number came from the user. Never fill it in yourself.)

---

## Output format

```
GOAL: [clients / job offers / authority]

SCORECARD
| # | Section | Score | One-line reason |

TOP 3 FIXES (ranked by impact)
1. [ ]
2. [ ]
3. [ ]

REWRITES (copy-ready)
### Headline — before / after
### About — before (first 3 lines) / after (full)
### Featured — the 3 items and what each thumbnail says
### Experience — before / after bullets
### Recommendation ask — message text

MISSING (you need to supply): [proof points, numbers, links]
```

---

## Sibling skills

- `linkedin-content-planner` — your post pillars should echo the headline and About.
- `linkedin-post-writer` — write the flagship post you'll pin in Featured.
- `linkedin-humanizer` — scrub the About for AI phrasing before you paste it.

---

## Pre-flight checklist

- [ ] One goal chosen, and every rewrite serves it?
- [ ] Only sections the user actually showed were scored?
- [ ] Headline names who + result, no CV filler?
- [ ] About's first 3 lines work on their own?
- [ ] Every Experience bullet has a number or a `[your number]` placeholder?
- [ ] No invented results, clients or testimonials?
- [ ] Limits and image specs either verified or labelled unverified?
