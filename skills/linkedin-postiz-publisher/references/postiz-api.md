# Postiz public API — what this bundle uses

Docs: https://docs.postiz.com/public-api/introduction

## Connection

- `POSTIZ_API_KEY`: from Postiz → Settings → Public API. Sent as the raw `Authorization` header (no `Bearer`).
- `POSTIZ_API_URL`: optional. Defaults to the hosted API. Self-hosted: `https://<your-domain>/api/public/v1`.

```bash
BASE="${POSTIZ_API_URL:-https://api.postiz.com/public/v1}"
```

Never print the key, echo it into the chat, or put it in a URL.

## List channels

```bash
curl -s "$BASE/integrations" -H "Authorization: $POSTIZ_API_KEY"
```
Returns `[{ id, name, identifier, picture, disabled, profile }]`. `identifier` is the platform (`x`, `linkedin`, `linkedin-page`, `instagram`, `instagram-standalone`, `facebook`, `threads`, `youtube`, `tiktok`, `pinterest`, `reddit`, …). `id` is what you post to.

## Next free slot

```bash
curl -s "$BASE/find-slot/<integration-id>" -H "Authorization: $POSTIZ_API_KEY"
```
Returns `{ "date": "2026-01-15T10:00:00.000Z" }`.

## Upload media (before any post with an image or video)

```bash
curl -s -X POST "$BASE/upload" -H "Authorization: $POSTIZ_API_KEY" -F "file=@/path/to/image.png"
curl -s -X POST "$BASE/upload-from-url" -H "Authorization: $POSTIZ_API_KEY" \
  -H "Content-Type: application/json" -d '{"url": "https://example.com/image.png"}'
```
Allowed: jpeg, png, gif, webp, avif, bmp, tiff, mp4. No PDFs. Use the returned `id` and `path`.

## Create a post

```bash
curl -s -X POST "$BASE/posts" -H "Authorization: $POSTIZ_API_KEY" \
  -H "Content-Type: application/json" -d @/tmp/postiz-body.json
```

```json
{
  "type": "schedule",
  "date": "2026-10-14T07:00:00.000Z",
  "shortLink": false,
  "tags": [],
  "posts": [
    {
      "integration": { "id": "<integration-id>" },
      "value": [
        { "content": "Post text", "image": [ { "id": "<upload-id>", "path": "<upload-path>" } ] }
      ],
      "settings": { "__type": "<identifier>" }
    }
  ]
}
```

- `type`: `schedule` (default), `draft` (parked in Postiz), `now` (only when the user asks to post now; ignores `date`).
- `date`: UTC, ISO 8601.
- Several objects in `value` = a thread / chained replies (X, Threads).
- Response: `[{ postId, integration }]`.

## See and delete scheduled posts

```bash
curl -s "$BASE/posts?startDate=<ISO>&endDate=<ISO>" -H "Authorization: $POSTIZ_API_KEY"
curl -s -X DELETE "$BASE/posts/<post-id>" -H "Authorization: $POSTIZ_API_KEY"   # confirm with the user first
```

## Limits

- The create-post endpoint is rate-limited (the docs say 30–100 requests per hour depending on the page and plan). A 429 means wait.
- Request body max 50 MB. Upload media by URL instead of inlining it.
- Platform settings change. If Postiz returns a validation error, trust the error over this file.
