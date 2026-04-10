# Version Control Rules — Jazz Party Site

## Single Source of Truth
- **One repo, one location:** `/Users/mac/Documents/neighborhood-jazz-party`
- **Workspace symlink:** `~/.openclaw/workspace/jazz-party-site` → points here
- **DO NOT clone this repo elsewhere.** If you need access, use the symlink or this path.

## Commit Rules
1. **Every change gets committed.** No local-only modifications left dangling.
2. **Commit before switching context.** If you touch a file, `git add && git commit` before moving on.
3. **Push after every commit.** Vercel auto-deploys from `main`. If it's committed, push it.
4. **Descriptive commit messages.** Say what changed and why.

## Image / Asset Changes
- When replacing an image (e.g., flyer.png), commit the new file immediately.
- Use `git diff --stat` to verify the binary changed before pushing.
- Large files (>5MB): consider Git LFS.

## Deployment
- **Vercel project:** `jazz-party-site` (auto-deploys from `main` on push)
- **Domain:** 512wchesapeake.com
- After pushing, allow ~60s for Vercel to rebuild.

## What Went Wrong (2026-04-10)
Two separate clones existed on the same machine. Feraindo (OpenClaw) updated the flyer
in one clone but never committed. Claude Code pushed from the other clone with the old
flyer. Result: live site reverted to the original graphic.

**Fix:** Consolidated to one repo + symlink. This file exists to prevent a repeat.
