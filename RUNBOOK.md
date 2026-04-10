# RUNBOOK.md — Jazz Party Site Critical Commands

## Single Lineage
- **One repo. One branch (`main`). One deploy target (Vercel).**
- Canonical path: `/Users/mac/Documents/neighborhood-jazz-party`
- Never clone elsewhere. Symlink if needed.

## Quick Reference

### Check status
```bash
cd /Users/mac/Documents/neighborhood-jazz-party
git status
git log --oneline -5
```

### Commit & deploy (every change, every time)
```bash
git add -A
git commit -m "description of change"
git push origin main
```

### View what's live vs local
```bash
git diff origin/main --stat
```

### Restore a file to last committed version
```bash
git checkout HEAD -- <filename>
```

### Revert entire site to a previous commit
```bash
git log --oneline -10          # find the commit hash
git revert <commit-hash>       # safe: creates a new undo commit
git push origin main
```

### Roll back flyer specifically
```bash
git log --oneline -- flyer.png   # see flyer history
git checkout <commit-hash> -- flyer.png
git add flyer.png
git commit -m "Revert flyer to <commit-hash>"
git push origin main
```

### Check Vercel deployment status
```bash
npx vercel ls 2>/dev/null | grep jazz
```

### Force Vercel redeploy (if auto-deploy stalls)
```bash
npx vercel --prod
```

### View file history
```bash
git log --follow --oneline -- <filename>
```

### Compare any two versions
```bash
git diff <older-hash> <newer-hash> -- <filename>
```

### Emergency: site is broken, go back to last known good
```bash
git log --oneline -10            # pick the good commit
git reset --hard <commit-hash>
git push --force origin main     # ⚠️ destructive, last resort
```
