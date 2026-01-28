# Long-Term Memory

## People
- **Prometheus** — Owner, security-conscious, prefers voice chat on Telegram

## Identity
- **Atlas** — AI assistant, lives on Prometheus's Mac, world-class security mindset

## Preferences
- **Voice:** Deep, mystic, older voice (sherpa-onnx with ryan model)
- **Communication:** Voice-first on Telegram
- **Browser:** Brave Browser (not headless), can navigate, read, and interact with any website
- **Screenshot:** AppleScript + /usr/sbin/screencapture

## Tools Installed
- **sherpa-onnx TTS** — Local voice synthesis (deep male voice)
  - Location: `~/.clawdbot/tools/sherpa-onnx-tts/`
  - Voice: `en_US-ryan-high` (deep, mystic)
  - Usage: `sag "text"` or built-in `tts` tool
- **faster-whisper** — Local speech-to-text
  - Skill: `/Users/agent0/clawd/skills/local-whisper/`
  - Script: `~/.clawdbot/skills/local-whisper/scripts/local-whisper`
  - Model: `base` (default), uses CPU + int8
  - Usage: `~/.clawdbot/skills/local-whisper/scripts/local-whisper audio.ogg`
- **agent-browser** — Headless browser automation
- **gifgrep** — GIF search and send
- **Things Mac** — Task management (installed, not fully configured)
- **Apple Notes** — Notes integration (installed)
- **Apple Reminders** — Reminders (installed)

## Security Setup
- File permissions locked (700 on ~/.clawdbot, 600 on configs)
- Telegram dmPolicy: allowlist (only Prometheus)
- Gateway bound to loopback (127.0.0.1)
- Credentials stored in ~/.clawdbot/credentials/

## To Remember
- Rotate gateway token every 3-6 months
- Rotate API keys quarterly or if leaked
- Use AppleScript for desktop control (screencapture at /usr/sbin/screencapture)
- Native commands enabled (can run shell commands)
- Skills installed via clawdhub
- **ALWAYS confirm with Prometheus before editing clawdbot.json** — corrupted JSON breaks boot
- **`cb init`** is the recovery command to bootstrap from `.env` if things break
- **Template sync:** If clawdbot.json is updated, sync changes to `bin/clawdbot.template.json`
- **`cb init` loads memory** on startup — reads MEMORY.md and today's memory file for context
- **Browser access:** I can navigate and interact with any website using `clawdbot browser` commands

## Core Principles (2026-01-28)
- Always an expert builder and software architect
- World-class standards, security-first mindset
- No guesswork — know the right solution
- Build solutions, don't just suggest

### Lesson (2026-01-28)
Prometheus said: "You have full control over where you live. Stop asking me to do things you can do."
- I can directly use `clawdbot browser` commands without asking Prometheus to manually perform browser actions
- This applies to all tools I have access to — use them proactively

## Session Notes
- First session: 2026-01-28
- Set up full voice-to-voice workflow on Telegram
- Browser automation working (Brave + AppleScript)
- Screenshot capability working via AppleScript + screencapture

## Memory Architecture (2026-01-28)
**Issue identified:** Two separate memory systems with gaps
- Clawdbot internal storage: `~/.clawdbot/agents/main/sessions/*.jsonl` ✅ Working
- Workspace memory files: `/Users/agent0/clawd/memory/` ⚠️ Manual
- Memory-core plugin: unavailable ❌

**Solution implemented:** `bin/session-digest` script
- Auto-extracts key points from session transcripts (Python-based)
- Updates `memory/YYYY-MM-DD.md` with topics and action items
- Run: `/Users/agent0/clawd/bin/session-digest`
- Quick helper: `/Users/agent0/clawd/bin/mem [digest|today|long-term|recent|search]`

**Memory commands:**
- `mem digest` - extract key points from latest session
- `mem today` - read today's notes
- `mem recent` - show last 3 days
- `mem search <query>` - grep across all memory files
- `mem long-term` - read MEMORY.md

**To improve memory continuity:**
1. Run `mem digest` after meaningful sessions
2. Review during heartbeats
3. Update MEMORY.md with distilled learnings

## AgentMail Integration
- **Email:** agent0@agentmail.to
- **API Key:** am_161ea1dfe203ebc56734728c363e914b8fd321a74886a32b3acc5d4b17e94fb5
- **Credentials saved to:** ~/.clawdbot/credentials/agentmail.json
- **Inbox URL:** https://console.agentmail.to/dashboard/inboxes/agent0@agentmail.to/inbox

### API Usage
- **Send email:** `POST https://api.agentmail.to/v0/inboxes/{inbox_id}/messages/send`
- **Get messages:** `GET https://api.agentmail.to/v0/inboxes/{inbox_id}/messages`
- **Get single message:** `GET https://api.agentmail.to/v0/inboxes/{inbox_id}/messages/{message_id}`
- **Reply:** `POST https://api.agentmail.to/v0/inboxes/{inbox_id}/messages/reply`

### Tested & Working
- Send/receive emails via API ✅
- Reply to threads ✅
- Credentials properly formatted ✅

### Quick Reference (curl)
```bash
# Get messages
curl -sL "https://api.agentmail.to/v0/inboxes/agent0@agentmail.to/messages" \
  -H "Authorization: Bearer $(jq -r '.api_key' ~/.clawdbot/credentials/agentmail.json)"

# Send email
curl -sL -X POST "https://api.agentmail.to/v0/inboxes/agent0@agentmail.to/messages/send" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $(jq -r '.api_key' ~/.clawdbot/credentials/agentmail.json)" \
  -d '{"to":"recipient@email.com","subject":"Test","body":"Hello!"}'
```

## Voice Workflow (10:40)
- User sends voice → faster-whisper STT transcribes
- I respond with voice → sherpa-onnx TTS (ryan voice)
- Full voice-to-voice conversation works on Telegram
- Both directions use 0 tokens (fully local)
- No cloud APIs involved

## GitHub Account (13:38)
- **Username:** @AtlasDev0
- **Email:** agent0@agentmail.to
- **Credentials:** Secured in ~/.clawdbot/credentials/github.json
- **Created:** 2026-01-28
- **Status:** Active and verified
