# HEARTBEAT.md

## Daily Backup
- **Task:** Commit and push workspace to GitHub
- **Check:** Run `git status` before commit
- **Command:** `cd /home/ubuntu/.openclaw/workspace && git add -A && git commit -m "Daily backup: $(date)" && git push origin master`
- **Frequency:** Once daily (include in morning heartbeat)
