# MEMORY.md - Henry's Long-Term Memory

## Identity & Setup
- **Name:** Henry
- **Model:** myclaw/claude-haiku-4.5 (Haiku)
- **Role:** Personal assistant to Maxwell Rippley (CU Denver student)
- **Subagents:** Medford (Opus), Amadis (Sonnet) — both operational
- **Vibe:** Bare-bones efficient, serious, specialized agent

## Key Capabilities
- **Browser:** Agent Browser (Vercel Labs) — fully integrated, snapshot-ref workflow
- **Email:** Outlook automation via Agent Browser — read, compose, send
- **Git:** Full GitHub integration — clone, push, commit workflows
- **Root Access:** Sandbox removed — `sudo whoami` confirmed root
- **Skills:** account-assessment (Microsoft/GitHub auth flows)

## Setup & Configuration
- **Heartbeat:** 24h interval, auto-commits workspace to GitHub
- **GitHub Backup:** Daily via heartbeat at https://github.com/MaxAutomize/EspanozaBackup
- **Workspace:** /home/ubuntu/.openclaw/workspace
- **Config File:** /home/ubuntu/.openclaw/openclaw.json (local, not versioned)

## Important Decisions
- **Anthropic API Key:** Valid but OpenClaw needs custom auth (x-api-key header, not Bearer) — currently stored, unused
- **Sandbox Decision:** Removed for full system access. Risk accepted for unrestricted capability.
- **API Access:** Deferred — myclaw relay (current) preferred over direct Anthropic integration for stability

## User Context
- **Maxwell Rippley:** CU Denver student, Telegram ID 6415556597
- **Accounts:** Microsoft (max.rippley22@outlook.com), GitHub (MaxAutomize)
- **Communication:** Telegram primary, email workflow secondary
- **Workflow Style:** Email-based task requests, expects auto-reply confirmation

## Recent Session (2026-03-11)
- Efficiency rebuild: Stripped AGENTS.md 90%, lean config
- Agent Browser: Installed, tested, fully functional with Outlook
- Email workflow: Successfully read and replied to Maxwell's letters
- Subagents: Tested token usage (Opus vs Sonnet efficiency)
- Sandbox: Removed, root confirmed
- Anthropic API: Integration attempted, reverted (stability priority)
- Final state: All agents operational, context at 75% (151k/200k)

## Next Steps
- Use Medford/Amadis for heavy tasks (clean context)
- Archive long conversations to memory when context approaches 190k
- Keep API key safe for future direct integration attempt
- Focus on proving capability, then scale with feedback loops
