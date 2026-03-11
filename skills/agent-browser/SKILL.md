# Agent Browser Skill

Browser automation via Vercel Labs' agent-browser CLI. Fast Rust-based headless browser with AI-agent workflow optimized for snapshot-ref interaction.

## Installation

```bash
npm install -g agent-browser
agent-browser install  # Download Chromium
```

Or via Homebrew (macOS):
```bash
brew install agent-browser
agent-browser install
```

## Quick Start

**Core Workflow:**
1. `agent-browser open <url>` - Navigate
2. `agent-browser snapshot -i` - Get interactive elements with refs (@e1, @e2, etc.)
3. `agent-browser click @e1` / `agent-browser fill @e2 "text"` - Interact using refs
4. Repeat snapshot after page changes

## Key Commands

### Navigation
- `agent-browser open <url>` - Navigate to URL
- `agent-browser back` - Go back
- `agent-browser forward` - Go forward
- `agent-browser reload` - Reload page

### Interaction
- `agent-browser click <sel>` - Click element
- `agent-browser fill <sel> <text>` - Clear and fill input
- `agent-browser type <sel> <text>` - Type into element
- `agent-browser select <sel> <val>` - Select dropdown
- `agent-browser check <sel>` - Check checkbox
- `agent-browser press <key>` - Press key (Enter, Tab, etc.)

### Retrieval
- `agent-browser snapshot -i` - Interactive elements only (refs)
- `agent-browser snapshot -i -c` - Compact snapshot
- `agent-browser get text <sel>` - Get text content
- `agent-browser get value <sel>` - Get input value
- `agent-browser screenshot [path]` - Take screenshot
- `agent-browser screenshot --annotate` - Annotated screenshot with ref labels

### Refs Pattern
- `agent-browser snapshot` returns elements with refs like `@e1`, `@e2`
- Use refs for deterministic interaction: `agent-browser click @e2`
- Refs remain valid until next navigation/reload

## Typical Agent Workflow

```bash
# 1. Open page
agent-browser open https://example.com

# 2. Get snapshot with interactive elements
agent-browser snapshot -i
# Output includes refs like:
# [1] @e1 button "Login"
# [2] @e2 textbox "Email"

# 3. Interact using refs
agent-browser fill @e2 "user@example.com"
agent-browser click @e1

# 4. Wait and get new snapshot
agent-browser wait --load networkidle
agent-browser snapshot -i

# 5. Continue interaction or screenshot
agent-browser screenshot result.png
```

## Advanced Features

### Sessions (isolated browser instances)
```bash
agent-browser --session agent1 open site-a.com
agent-browser --session agent2 open site-b.com
```

### Persistent state (cookies, localStorage)
```bash
agent-browser --profile ~/.myapp-profile open myapp.com
# Login once, then reuse authenticated session
agent-browser --profile ~/.myapp-profile open myapp.com/dashboard
```

### Custom headers (skip login flows)
```bash
agent-browser open api.example.com --headers '{"Authorization": "Bearer <token>"}'
```

### Wait strategies
```bash
agent-browser wait <selector>  # Wait for element
agent-browser wait 1000  # Wait 1 second
agent-browser wait --text "Success"  # Wait for text
agent-browser wait --load networkidle  # Wait for network idle
```

### JSON output (machine-readable)
```bash
agent-browser snapshot --json
agent-browser get text @e1 --json
```

## Configuration

Optional `agent-browser.json` in project root:

```json
{
  "headed": true,
  "profile": "./browser-data",
  "userAgent": "my-agent/1.0",
  "ignoreHttpsErrors": true
}
```

Or environment variables:
- `AGENT_BROWSER_SESSION` - Session name
- `AGENT_BROWSER_PROFILE` - Profile path
- `AGENT_BROWSER_TIMEOUT` - Default timeout (ms)
- `AGENT_BROWSER_HEADED` - Show browser window

## When to Use

- **Snapshot-ref workflow** - Best for AI agents needing deterministic element selection
- **Multi-step workflows** - Chain commands with `&&`
- **Session/profile persistence** - Keep login state across commands
- **CI/CD automation** - Fast, reliable headless browser

## Integration with OpenClaw

Execute via shell commands in skills or tasks:

```bash
agent-browser open https://outlook.live.com
agent-browser snapshot -i --json | jq '.data.snapshot'
agent-browser click @e1
```

Or use subagents to parallelize multiple browser sessions.

## Troubleshooting

- **Chromium not found:** Run `agent-browser install` to download
- **Timeout on slow sites:** Set `AGENT_BROWSER_TIMEOUT=45000` (milliseconds)
- **Need JavaScript execution:** Use `agent-browser eval "<js-code>"`
- **For fast local testing:** Use `--headed` to see browser window
