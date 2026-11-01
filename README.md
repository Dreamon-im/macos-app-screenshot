# macOS App Screenshot 📸

An [Agent Skill](https://agentskills.io) that captures a **retina, shadow-free
screenshot of any macOS app's window — by app name**. No window-id hunting, no
shadow cropping, no manual resizing.

```bash
scripts/shot Deckhand                     # → ~/Desktop/Deckhand-<timestamp>.png
scripts/shot preview ~/shots/preview.png  # partial names work too
```

One command resolves the app's frontmost window via the CoreGraphics window
list and captures it at 2× retina (e.g. 2000×1280) with the drop shadow
omitted — ready for documentation, marketing pages, or bug reports.

## What the skill does

When installed, your coding agent (Claude Code, Codex, Cursor, …) can take
app screenshots for you on request: *"screenshot Deckhand"* or *"capture
Safari and convert it to WebP"*. The skill teaches the agent:

- how to run the bundled script, and how to resolve window IDs by name when
  the script isn't enough;
- the gotchas — **Screen Recording** permission (the terminal must be granted
  it), windows must be visible (minimized fails), window IDs change on every
  relaunch so they are never cached;
- marketing-quality tips: pin the window size for consistent shots, stage
  realistic content, convert to WebP for the web.

## Install

**npx (auto-detects Claude Code, Codex, Cursor, and 20+ agents):**

```bash
npx skills add airbob/macos-app-screenshot
```

**OpenAI Codex / ChatGPT plugin:** add
[airbob/macos-app-screenshot-plugin](https://github.com/airbob/macos-app-screenshot-plugin)
as a plugin marketplace and install *macos-app-screenshot* from the Plugins
Directory.

**Claude Code / Codex / any agent, by hand:** copy or symlink this folder into
that agent's skills directory:

```bash
git clone https://github.com/airbob/macos-app-screenshot
mkdir -p ~/.claude/skills   # or ~/.codex/skills, ~/.agents/skills, …
ln -s "$PWD/macos-app-screenshot" ~/.claude/skills/macos-app-screenshot
```

**Manual (no agent):** the script works standalone from any terminal with
Screen Recording permission:

```bash
./scripts/shot Safari
```

## Requirements

- macOS, with **Screen Recording** permission granted to your terminal app
  (System Settings → Privacy & Security → Screen Recording; restart the
  terminal after granting).
- The app window must be on screen (not minimized).

## Files

```
SKILL.md        the skill: usage, gotchas, and fallbacks for the agent
scripts/shot    the capture script
```
