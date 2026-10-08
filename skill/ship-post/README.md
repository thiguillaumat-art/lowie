# ship-post {••}

A free Claude Code skill: it reads what you shipped (your recent git commits), asks you one question, and drafts **one X post** and **one Reddit post** about it. It never invents a number and never posts for you.

Made by [Lowie](https://getlowie.vercel.app), the AI marketing agent that reads your commits. Built in public on [@getlowie](https://x.com/getlowie).

## Install (10 seconds)

```bash
mkdir -p ~/.claude/skills/ship-post && curl -fsSL https://raw.githubusercontent.com/thiguillaumat-art/lowie/main/skill/ship-post/SKILL.md -o ~/.claude/skills/ship-post/SKILL.md
```

Then, inside a git repo, open Claude Code and type:

```
/ship-post
```

## What you get

```
Picked: <the one change a user would notice>

X (<n> chars)
<post>
Post it: <link that opens X with the text filled in>

r/SideProject
Title: <title>
<body>
Check the subreddit rules before posting.
```

## Rules it follows

- Only numbers that are in your commits, your diff or your own sentence.
- Drafts only: you read, you post.
- No "excited to announce", no rocket emojis.
- If you only shipped chores this week, it says so instead of making something up.

Want the full loop (finding the threads where you're the answer, and a Friday count of what actually brought signups)? [Join the Lowie waitlist](https://getlowie.vercel.app/?ref=gh-skill).

MIT license.
