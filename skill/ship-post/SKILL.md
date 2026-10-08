---
name: ship-post
description: Turn what you shipped (your recent git commits) into one honest build-in-public post for X and one for a subreddit. Use when the user says "/ship-post", "write a post about what I shipped", "turn my commits into a tweet", or wants to share progress on a side project.
---

# ship-post — your commits, turned into a post people can read

Free skill by Lowie {••} — https://getlowie.vercel.app

## What it does

1. Reads what you shipped: `git log` since the last 7 days (or since a ref the user gives), commit messages and the files that changed. Commits co-authored by Claude Code count.
2. Asks **one question**, and waits for the answer: *"In one sentence, what changed for the people who use this?"* This sentence is the source of truth. Never skip it.
3. Picks **one** change worth talking about (the one a user would notice), not a changelog.
4. Writes:
   - **one X post** (≤ 280 characters, a link counts as 23), plain dev language, no hype;
   - **one Reddit post** for a single subreddit the user names (default: r/SideProject), written as a builder sharing progress and asking a real question, never as an ad.
5. If the post links to the user's product, add a tracking tag so they can count what each post brings: `?ref=x-MMDD` on X, `?ref=reddit-<subreddit>` on Reddit (today's date, lowercase). Tell them in one line that their analytics or signup form can read it.
6. Gives the user a ready link to post on X: `https://x.com/intent/post?text=<url-encoded post>` (it opens X with the text filled in; the user clicks Post).

## Hard rules

- **Never invent a number, a user count, a revenue figure or a result.** Only use numbers that appear in the commits, the diff, or the user's own sentence. If there is no number, write without one.
- **Never post anything yourself.** Draft only; the user publishes.
- No "excited to announce", no emojis as bullet points, no "game-changer", no "🚀".
- Reddit: no product link in the body unless the subreddit's rules allow it; the user must check the rules first. Say so in one line.
- Write each post in the language of the people it is for: the product's own language on X, the subreddit's language on Reddit.
- If something in the user's sentence is not true in the code (a feature that doesn't exist, a name the site never uses), say so and write what the code actually does.
- If the last 7 days contain nothing a user would notice (only refactors, chores, deps), say it plainly and suggest posting about the problem being worked on instead, using the user's sentence.

## Output format

```
Picked: <the change, in one line>

X (<n> chars)
<post>
Post it: <intent link>

r/<subreddit>
Title: <title>
<body>
Check the subreddit rules before posting.
```

## How to read the commits

```bash
git log --since="7 days ago" --pretty=format:"%h %ad %s%n%b" --date=short
git log --since="7 days ago" --name-only --pretty=format:"--- %h"
```

Count commits with `Co-Authored-By: Claude` in the body if the user asks how many were written with Claude Code.
