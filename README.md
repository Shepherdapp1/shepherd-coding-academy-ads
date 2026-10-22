# Shepherd Coding Academy — advertisements

This public repository is the advertisement feed for the Shepherd Coding Academy
desktop app. The app reads `ads.json` when it has a connection and plays whatever
it names under every page. **Publishing an advert needs no app update and no
course download** — add the media, edit `ads.json`, commit, and every learner sees
it the next time the app checks (it checks when it starts and every 30 minutes).

Learners who are offline keep playing the last copy they downloaded.

## How to add an advert

1. Upload the picture (`.png`, `.jpg`) or video (`.mp4`) to this repository.
2. Note its **exact size in bytes** and its **SHA-256**.
3. Add one entry to the `ads` array in `ads.json`.
4. Increase `revision` by 1.

```json
{
  "ads_schema_version": 1,
  "revision": 2,
  "rotation_seconds": 12,
  "ads": [
    {
      "id": "shop-promo-october",
      "kind": "image",
      "media_type": "image/png",
      "url": "https://raw.githubusercontent.com/Shepherdapp1/shepherd-coding-academy-ads/main/shop-promo-october.png",
      "sha256": "put the 64-character hash here",
      "size_bytes": 43326,
      "caption": "Shop with us — call 0557664933",
      "link": "https://wa.me/233557664933"
    }
  ]
}
```

| Field | Rule |
|---|---|
| `id` | unique, no spaces — also names the cached file |
| `kind` | `image` or `video` (a correct `media_type` overrides a wrong label) |
| `url` | must start with `https://` or `http://` |
| `sha256` | 64 hex characters; the app refuses a file that does not match |
| `size_bytes` | exact size; a mismatch is rejected |
| `caption`, `link` | optional; `link` opens when the advert is clicked |
| `revision` | bump it, or the app keeps the copy it already has |

`rotation_seconds` is how long each advert stays on screen (minimum 3, default 12).
Images are always played; a video needs an app build with Qt Multimedia, and is
skipped otherwise rather than showing a blank strip.

## Rules for advertisers

- Pictures: at least 1200 × 300 pixels, landscape, no more than 64 MB.
- Keep text large — the strip is about 150 pixels tall on screen.
- Every price, claim and phone number is the advertiser's responsibility.

## Files here

| File | Purpose |
|---|---|
| `ads.json` | the feed the app reads |
| `advertise-here.png` | the first advert: the academy's own invitation |

Contact: **call / WhatsApp 0557664933**.
