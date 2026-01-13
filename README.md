# claude-sessions

CLI to manage Claude Code sessions and agents.

## Install

```bash
curl -fsSL https://raw.githubusercontent.com/llm-cli/claude-sessions/main/claude-sessions -o ~/.local/bin/claude-sessions
chmod +x ~/.local/bin/claude-sessions
```

## Usage

```bash
claude-sessions help
```

### Reading sessions

```bash
claude-sessions list [project] [n]        # List recent sessions
claude-sessions history [project] [n]     # Show conversation history
claude-sessions search <keyword>          # Full-text search
```

### Running agents

```bash
claude-sessions open <dir> [prompt]       # Open Claude in new terminal
claude-sessions resume <project>          # Resume last session
claude-sessions send <pid> <message>      # Send message to agent
```

### Agent supervision (loopback)

```bash
pid=$(claude-sessions open --loopback ~/project "Fix the bug")
claude-sessions wait 300 $pid    # Wait for agent signal
claude-sessions history $pid 5   # Read what it said
claude-sessions send $pid "Continue"
```

## Requirements

- Bash
- [Kitty terminal](https://sw.kovidgoyal.net/kitty/) with remote control enabled
- jq, ripgrep

### Kitty config

```bash
# ~/.config/kitty/kitty.conf
allow_remote_control yes
listen_on unix:/tmp/kitty-remote
```

## Part of [llm-cli](https://github.com/llm-cli)

LLM-first CLI tools optimized for AI agents.
