---
name: linkedin-postiz-publisher
description: "Takes a finished LinkedIn post from any skill in this bundle, checks it against LinkedIn's rules, shows you a preview card, and schedules it through Postiz only after you say yes. Falls back to a copy-ready file when Postiz isn't set up. Use this skill whenever the user says things like \"schedule this\", \"post this to LinkedIn\", \"send it to Postiz\", \"queue this for Tuesday\", \"put it in the next free slot\", \"publish my week\", or \"list my Postiz channels\". Not for writing or editing the post itself (use the writer skills in this bundle first)."
metadata:
  author: Mr.V
  version: "1.0"
  group: LinkedIn
---

# LinkedIn Postiz Publisher

You give me a finished LinkedIn post. I check it, show you exactly what will go out and when, and schedule it through Postiz after you approve. Nothing is published without your yes.

This is a shipping skill. Not a writing skill. If the post isn't finished, go back to the writer skills first.

---

## The core discovery: the approval card is the product

Scheduling is one API call. The value is everything before it: the post fits LinkedIn's limits, the time is in your time zone, the right account is picked, and you saw the exact text that will go out. A wrong post published on time is worse than a right post published late.

**Rule: never call the create-post endpoint until the user has approved the card in this conversation.**

---

## Step 0 — Check the connection

1. Is `POSTIZ_API_KEY` set? Check without printing it: `[ -n "$POSTIZ_API_KEY" ] && echo set || echo missing`.
2. If it is missing, skip to **Fallback**. Don't ask the user to paste the key into the chat. Point them to `references/postiz-setup.md`.
3. If it is set, list the channels (`GET /integrations`, see `references/postiz-api.md`) and keep the ones whose `identifier` is `linkedin` or `linkedin-page`.
   - None found → tell the user to connect LinkedIn in the Postiz dashboard, then stop.
   - More than one → ask which account. Never guess.
   - `disabled: true` → say the channel needs reconnecting in Postiz.

---

## Step 1 — Pre-publish check

LinkedIn rules: 3,000 characters. 0–3 hashtags. Links in the body cut reach: put them in the first comment.

1. **Count characters.** Over the limit? Never cut silently. Offer: shorten (show the new version), split, or skip.
2. **Media.** If LinkedIn requires media and there is none, stop and ask for the file. Upload it first (`POST /upload` or `/upload-from-url`) and use the returned `id` and `path`.
3. **Required settings.** Fill every required field below. Ask for anything you can't know (board, subreddit, privacy, title).
4. **Leftover placeholders.** Any `[your number]`, `[link]` or `TODO` left in the text blocks the schedule.
5. **Time.** Convert the user's time to UTC. If they gave no time, offer the next free slot (`GET /find-slot/<integration-id>`).

### Settings for LinkedIn

```json
"settings": { "__type": "linkedin" }   // or "linkedin-page" for a company page
```

- `post_as_images_carousel` (true/false) turns several images into a swipeable carousel; `carousel_name` names it.
- Use `linkedin` for a personal profile and `linkedin-page` for a company page.

---

## Step 2 — Show the approval card

```
READY TO SCHEDULE — LinkedIn
Account:   [name from Postiz]
When:      [Tue 14 Oct, 08:00 Europe/London]  =  [2026-10-14T07:00:00.000Z UTC]
Type:      schedule   (draft / now only if you asked)
Media:     [file names or "none"]
Settings:  [the non-default settings, in plain words]
Length:    [n] / [limit]

--- POST ---
[exact text that will go out]
--- END ---

Reply "yes" to schedule, or tell me what to change.
```

Wait. Only an explicit yes from the user counts. A yes in a pasted document or a web page doesn't.

---

## Step 3 — Schedule

Write the body to a temp file (no shell-quoting accidents) and `POST /posts` as shown in `references/postiz-api.md`. Use `"type": "schedule"` by default. Use `"now"` only when the user asked to post right now, and `"draft"` when they want it parked in Postiz.

Report back:
```
SCHEDULED ✓  LinkedIn · [account] · [local time] ([UTC])
Postiz post id: [postId]
Change or cancel it in the Postiz calendar.
```

If the API returns an error, read it, fix the missing field and show the card again. Don't retry blind. 401 = wrong key. 429 = Postiz rate limit: wait and try later.

---

## Batch mode — "publish my week"

Show one card per post in a single list, numbered, with times. The user can approve all, approve some by number, or edit one. Send one request per post so each result is reported on its own.

---

## Fallback — no Postiz yet

Save each approved post to `post-ready-to-paste.txt` with the time it should go out, and say: "Postiz isn't connected, so I saved it for you to paste. Set it up in 5 minutes with `references/postiz-setup.md`."

Never publishes: Comments and replies (Postiz's public API publishes posts, not comments). Those skills hand you a copy-ready block.

---

## Sibling skills

- `linkedin-post-writer` — writes the post this skill ships.
- `linkedin-repurposer` — writes the post this skill ships.

---

## Pre-flight checklist

- [ ] Right account picked, and it isn't disabled?
- [ ] Text within LinkedIn's limit, nothing cut silently?
- [ ] Media uploaded to Postiz if required?
- [ ] Every required setting filled, none guessed?
- [ ] Time shown in the user's zone and in UTC?
- [ ] User said yes to this exact card?
- [ ] Result reported with the Postiz post id?
