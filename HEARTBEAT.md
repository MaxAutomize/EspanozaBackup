# HEARTBEAT.md

## Daily GitHub Backup (24h interval)

Run once per day:
- Check git status
- If changes exist: `git add -A && git commit -m "Daily backup: $(date)" && git push origin master`
- If no changes: skip commit, just confirm backup check ran
