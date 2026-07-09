# Health Camper content

This repo feeds the "Around the campfire" section of the Health Camper iOS
app. Each region gets its own feed file; the app picks the right one from the
user's iPhone region (with a manual override in the app's Settings) and falls
back to `global.json`.

## How to publish new content (daily routine)

1. Open the feed file for the region (`feeds/global.json`, `feeds/ca.json`,
   `feeds/np.json`, `feeds/us.json`, `feeds/in.json`).
2. Add a new item at the TOP of the `items` list:

```json
{
  "id": "ca-2026-07-10-1",
  "date": "2026-07-10",
  "title": "Short headline",
  "message": "The motivational message people will read.",
  "videoURL": null,
  "author": "Rujal"
}
```

3. Update the `"updated"` date at the top of the file.
4. Commit + push (or edit directly on github.com — the pencil icon — and
   commit from the browser; works from a phone too).

Apps pick up changes on next open or pull-to-refresh. No app update needed.

## Adding a video

1. Drop the video file into `videos/` (keep it short and compressed —
   under ~50 MB; GitHub blocks files over 100 MB).
2. Set the item's `videoURL` to:
   `https://raw.githubusercontent.com/GITHUB-USERNAME/health-camper-content/main/videos/FILENAME.mp4`
3. Commit + push.

## Rules

- `id` must be unique — use the `region-date-number` pattern.
- Valid JSON only: double quotes, commas between items, no trailing comma.
  If a feed breaks, the app silently falls back to the last cached content,
  so a typo won't crash anyone — but the new content won't show either.
- Keep this repo PUBLIC — the app reads it without authentication.
  Don't put anything private in here.
