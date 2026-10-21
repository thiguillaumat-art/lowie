---
name: ship-post
description: Turn what you shipped (your recent git commits) into one honest build-in-public post for X and one for a subreddit. Use when the user says "/ship-post", "write a post about what I shipped", "turn my commits into a tweet", or wants to share progress on a side project.
---

# ship-post — your commits, turned into a post people can read

Free skill by Lowie {••} — https://getlowie.vercel.app

## What it does

1. Reads what you shipped: `git log` since the last 7 days (or since a ref the user gives), commit messages and the files that changed. Commits co-authored by Claude Code count.
2. Asks **one question**, and waits for the answer: *"In one sentence, what was annoying or impossible for the people who use this before, and what's different now?"* This sentence is the source of truth. Never skip it.
3. Picks **one** change worth talking about (the one a user would notice), not a changelog.
4. **Leads with the pain, not the technique.** People stop for a problem they recognise, not for the stack or the refactor that solved it. Open with what used to hurt, then what's different now; keep the implementation for the Reddit body or a reply. The pain must come from the user's answer or from something real users said, never invented. If the answer names no pain, describe the change plainly.
5. Writes:
   - **one X post** (≤ 280 characters, a link counts as 23), plain dev language, no hype;
   - **one Reddit post** for a single subreddit the user names (default: r/SideProject), written as a builder sharing progress and asking a real question, never as an ad.
6. If the post links to the user's product, add a tracking tag so they can count what each post brings: `?ref=x-MMDD` on X, `?ref=reddit-<subreddit>` on Reddit (today's date, lowercase). Tell them in one line that their analytics or signup form can read it.
7. Gives the user a ready link to post on X: `https://x.com/intent/post?text=<url-encoded post>` (it opens X with the text filled in; the user clicks Post).

## Hard rules

- **Never invent a number, a user count, a revenue figure or a result.** Only use numbers that appear in the commits, the diff, or the user's own sentence. If there is no number, write without one.
- **Never describe what users did, felt or said** (drop-off, complaints, feedback, "people kept asking") unless the user told you so in this conversation. If the post needs it, ask, or leave it out. Do not write it and add a disclaimer afterwards.
- A number from an old commit may have been changed by a later commit. Date it ("in September…") or check that it is still true in the current code.
- **Never post anything yourself.** Draft only; the user publishes.
- No "excited to announce", no emojis as bullet points, no "game-changer", no "🚀".
- Reddit: no product link in the body unless the subreddit's rules allow it; the user must check the rules first. Say so in one line.
- Write each post in the language of the people it is for: the product's own language on X, the subreddit's language on Reddit.
- If something in the user's sentence is not true in the code (a feature that doesn't exist, a name the site never uses), say so and write what the code actually does.
- If the last 7 days contain nothing a user would notice (only refactors, chores, deps), say it plainly and suggest posting about the problem being worked on instead, using the user's sentence.

## Where to post when nobody follows you yet

Learned on a real 14-day launch from zero (October 2026). Add the one or two tips that fit the user's situation, in one line each, after the drafts. Don't lecture.

- **A new account's own posts reach almost no one.** A short, useful reply under a fresh post from a bigger account is read by more people. One sentence, no link.
- **Reddit filters new and low-karma accounts** (automod, and anti-bot apps shared across many subreddits). Build a history of genuine comments before posting about your project. Never use a second account to get around a removal or a ban.
- **Hacker News may refuse submissions from new accounts** for some sites, free subdomains included. Don't repost through another domain; write to the moderators.
- **Count signups per `?ref=` tag, not likes or followers.** Followers can grow while nobody signs up.
- **Don't drop a type of post after one flop.** It could be the hour, the length or the first line. Retry at another time and change one thing at a time.
- **"Agreed!" under a post is not interest.** Interest is someone writing that they have the problem.

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
