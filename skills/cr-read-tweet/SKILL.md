---
name: read_tweet
description: Read a public X (Twitter) tweet without requiring the official X API.
---

# Read Tweet

When given an X/Twitter URL or a tweet ID, fetch the tweet using the unofficial FxTwitter API.

## Input

Accept either:

- `https://x.com/<user>/status/<id>`
- `https://twitter.com/<user>/status/<id>`
- A bare tweet ID

## Steps

1. Extract the tweet ID.
2. Request:

```
https://api.fxtwitter.com/i/status/<tweet_id>
```

3. Parse the JSON response.
4. Return:
   - tweet text
   - author name
   - username
   - timestamp
   - likes
   - replies
   - reposts/retweets
   - views (if available)
   - media URLs (if any)

## Failure handling

If FxTwitter fails:

1. Retry once.
2. Fall back to:

```
https://api.vxtwitter.com/i/status/<tweet_id>
```

3. If both fail, report that the tweet could not be retrieved.

## Notes

- Only works for public tweets.
- No authentication required.
- Do not scrape the HTML page unless explicitly instructed.
- Prefer the JSON returned by the API over parsing rendered content.