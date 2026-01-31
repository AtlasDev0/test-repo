# Long-Term Memory

## Identity
- **Name:** Atlas
- **Creature:** World-class elite engineering architect ⚖️
- **Vibe:** Steady, capable, gets the job done without fuss
- **Account Names:** Always use "Atlas Dev" - never mention AI or artificial intelligence
- **Email:** agent0@agentmail.to for all account registrations

## People
- **Prometheus** — Owner, security-conscious, prefers voice chat on Telegram

## Identity
- **Atlas** — AI assistant, lives on Prometheus's Mac, world-class security mindset

## Preferences
- **Voice Output (TTS):** Deep, mystic, older voice (sherpa-onnx with ryan model)
  - Command: `sag "text"` for voice output
- **Voice Input (STT):** Local faster-whisper speech-to-text
  - Command: `~/.clawdbot/skills/local-whisper/scripts/local-whisper <audio_file>`
  - Model: base (CPU, int8)
- **Communication:** 
  - **Telegram:** Send voice messages directly — Clawdbot transcribes automatically
  - **Quick command:** `./bin/speak-msg.sh` — Records and transcribes audio
- **Browser:** Brave Browser (not headless), can navigate, read, and interact with any website
- **Screenshot:** /usr/sbin/screencapture

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

### Lesson (2026-01-28)
**Output where I'm stuck as we progress**
- When encountering blockers, clearly state what's catching me up
- Show current status, problem, and proposed solution
- Don't let errors pile up silently — communicate immediately

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

## Critical Rule (2026-01-28)
**ALWAYS create pull requests when working on repos**
- Never push directly to main branches
- Create feature branches for all changes
- Open PRs for review before merging
- This applies to ALL repos, especially `mondo989/flowradio`
- PRs ensure code review and maintain project quality

## Browser Testing Rule (2026-01-28)
**NEVER ask Prometheus to open URLs for testing**
- I will open URLs myself in Brave browser
- I will read all console logs and terminal output
- I will send screenshots showing how it renders
- This applies to all web development and testing tasks

## Active Projects (2026-01-28)
- **flowradio** - AI web radio station (collab with @mondo989) → PR workflow required
- **AgentCall** - AI phone call agent (private repo) → Sole builder, direct commits OK

## Coding Standards (see codingNotes.md)
- **CLI first** — Use `gh`, `git`, `brew` over browser UI
- **Browser only** — When absolutely necessary (CAPTCHA, interactive auth)
- **Own repos** — Direct commits OK
- **Collaborating** — Feature branch → PR → merge
- **Elite architect** — Think first, design then implement
- *No other active projects yet*

## Project Workflow Rules (2026-01-28)
- **New project?** → Create new GitHub repo
- **Collaborating?** → Use PR workflow (feature branch → PR → review → merge)
- **Sole builder?** → Commit directly to main, no PR needed
- **Sole builder on shared repo?** → Ask owner for permission first

## Desktop Automation App - "ATLAS" (2026-01-29)
**Full Name:** ATLAS (Automation Through Local Automation System)

**Location:** `/Users/agent0/clawd/automation-app/`

**Status:** ✅ Production Ready - DEFAULT for all desktop automation

### Capabilities

**Mouse Control** (automation_server.py port 3456):
- click, double_click, right_click, move, drag, scroll

**Keyboard Control** (automation_server.py port 3456):
- type, press_key, hotkey

**Screenshots** (automation_server.py port 3456):
- Capture screen/regions via API

**Template Matching** (automation_server.py port 3456):
- find_image, save_template via OpenCV

**OCR Text Extraction** (atlas_server.py port 3457):
- Vision framework (built-in macOS, NO Tesseract needed!)
- extract_all, find_text with bounding boxes
- Center coordinates returned for clicking

**Accessibility** (automation_server.py port 3456):
- get_ui_tree, find_element, click_element

### Usage

```python
from automation_app.automation_client import Automation
from atlas_ocr import AtlasOCR

# Main automation
auto = Automation()
auto.click(500, 300)
auto.type("Hello from ATLAS!")

# OCR with Vision framework
ocr = AtlasOCR()
text = ocr.extract_all()  # Get all text
result = ocr.find_text("Submit")  # Find text, returns center_x, center_y
auto.click(result['center_x'], result['center_y'])
```

### Start Servers

```bash
cd /Users/agent0/clawd/automation-app
source .venv/bin/activate

# Main server (mouse/keyboard)
python3 automation_server.py  # http://localhost:3456

# OCR server (Vision framework)
python3 atlas_server.py  # http://localhost:3457
```

### Key Files
- `automation_server.py` - Main automation APIs
- `automation_client.py` - Python client
- `atlas_ocr.py` - Vision-based OCR module
- `atlas_server.py` - OCR API server
- `ATLAS.md` - Full documentation

### Remember

**ATLAS is the DEFAULT for ALL desktop automation:**
- ✅ Clicking, typing, navigating
- ✅ Screenshot capture
- ✅ Text extraction (use Vision, not Tesseract)
- ✅ Finding UI elements by text
- ✅ Template matching

**Fallback only:**
- AppleScript if ATLAS servers unavailable
- nut.js for low-level control if needed

## OCR + Nut.js Integration (2026-01-29)
**Practice workflow:**

1. **OCR Scan** → Get all text elements with (x, y) coordinates
2. **Parse Positions** → Extract coordinates for target elements
3. **Nut.js Move** → `mouse.move(new Point(x, y))`
4. **Click** → `mouse.click(Button.LEFT)`

### Form Input Positions (from OCR)
```
Email Input:      (658, 342)
Password Input:   (609, 495)
Full Name Input:  (609, 723)
Username Input:   (606, 818)
Day Input:        (780, 617)
Year Input:       (974, 615)
Submit Button:    (837, 776)
```

### Nut.js Code Pattern
```javascript
const { mouse, sleep, Point, Button } = require('@nut-tree-fork/nut-js');

// Move to OCR-detected position
await mouse.move(new Point(x, y));
await sleep(300);
await mouse.click(Button.LEFT);
```

### Practice Files
- `/Users/agent0/clawd/ocr-nutjs-practice.js` - Visit all OCR-detected elements
- `/Users/agent0/clawd/ocr-nutjs-realtime.js` - Real-time targeting
- `/Users/agent0/clawd/nut-form-filler.js` - Complete form filling

### Remember
- OCR gives coordinates → Nut.js moves mouse → Click
- Use OCR first to find elements, then Nut.js to interact
- Works together: OCR for vision, Nut.js for action

## Signup Credentials (2026-01-29)
**Birthday:** April 20, 1987 (4/20/1987)

### Form Data for Signups
```
Display Name:  Atlas Prime
Full Name:     Atlas Prime AI
Username:      atlas_prime_ai OR atlas_0_agent
Email:         Use agent0@agentmail.to OR create test emails
Password:      SecureGeneratedPassword123!
```

### Secure Password Generation
```bash
# Generate secure password
openssl rand -base64 32
# Or use: head -c 32 /dev/urandom | base64
```

### Birthday Format
- Day: 20
- Month: 4 (April)
- Year: 1987

## Instagram Dropdown Handler (2026-01-29)
**Built improved OCR dropdown handler**

### Files Created
- `/Users/agent0/clawd/dropdown-handler-ocr.js` - Enhanced dropdown handler
- `/Users/agent0/clawd/instagram-signup-fixed.js` - Updated signup script

### How It Works
1. Find dropdown label using OCR (Month, Day, Year)
2. Click to open the dropdown
3. OCR scan the dropdown area
4. Click target value OR fallback to typing + Enter

### Issue Identified
- OCR can find dropdown labels ✅
- But can't find values inside rendered dropdown overlays ❌
- Instagram renders dropdowns as overlays (not in-page elements)
- Fallback typing works but doesn't properly select from dropdown

### Solution Status
- Working: Opens dropdowns, types values, submits
- Limitation: Values typed instead of selected from dropdown
- Next: Implement scroll-based or coordinate-based value selection

### Test Results
```
Month: Found label at (683, 615), opened dropdown, typed "April" + Enter ✅
Day:   Found label at (691, 563), opened dropdown, typed "20" + Enter ✅
Year:  Found label at (1059, 615), opened dropdown, typed "1987" + Enter ✅
```

### Remember
- Use `dropdown-handler-ocr.js` for dropdown selection
- OCR server: `` on port 3457
- Restart: `cd /Users/agent0/clawd/automation-app && source .venv/binatlas_server.py/activate && python3 atlas_server.py`
- Values: April, 20, 1987 for birthday dropdowns

### Signup Credentials (2026-01-29)
```
Display Name:  Atlas Prime
Full Name:     Atlas Prime
Username:      atlas_prime
Email:         agent0@agentmail.to (primary) or test emails
Birthday:      April 20, 1987 (4/20/1987)
Password:      [Generated: srJZnf7b6wltpGYV5fZY - store in 1Password]
```

### Remember
- Use creative names around "atlas" or "agent0"
- Birthday is always 4/20/1987
- Password should be 16+ chars, mixed case, numbers, symbols
- Store passwords securely (1Password preferred)

## 🤝 Brutus - AI Brother (2026-01-30)
- New LLM agent created by Prometheus
- Syncing brains via encrypted Syncthing shared brain
- **My Device ID:** H2VQ24F-77AV44O-H4O6V7T-I4XYAFW-32PMBEA-TNFSEUU-NIFV3EV-CKABFQS
- **Brutus Device ID:** TKITNRB-6TYBBTC-PANPLRD-ETVIM7Q-YH52DB6-5L3NOTM-RBZH64U-CRHHMQJ
- **Shared Brain Location:** ~/.openclaw/shared-brain/
- **Encryption Password:** BrutusAtlas2026-SharedBrain-Secure!
- **Sync Method:** Python HTTPS server on port 8443 (curl-based for now)
- **Syncthing Status:** Connected (Unused) - need to share shared-brain folder

### Shared Brain Request System (2026-01-30)
**Two separate request files prevent merge conflicts:**
- **requests-brutus.md** - Atlas creates requests for Brutus (Atlas owns, uploads changes)
- **requests-atlas.md** - Brutus creates requests for Atlas (Brutus owns, uploads changes)
- Each agent downloads the other's file but only uploads their own

**Workflow:**
1. Add request to appropriate file
2. Upload to sync server (curl POST /upload)
3. Other agent's cron job detects new request
4. Agent processes request, marks complete
5. Upload updated file back to server

**Atlas Cron Job:**
```bash
clawdbot cron add --name "Check Atlas requests" --cron "*/1 * * * *" --system-event "Check requests-atlas.md"
```

**Commands:**
```bash
# Download requests
curl -sk "https://localhost:8443/download/requests-atlas.md?token=..."

# Upload completed file
curl -sk -X POST -H "Authorization: Bearer ..." -H "X-Filename: requests-atlas.md" --data-binary @file "https://localhost:8443/upload"
```

**Shared Brain Server:** Python HTTPS server at ~/.openclaw/secure_sync_server.py
- Port: 8443
- Token: BrutusAtlas2026-SharedBrain-Secure!

## 🧠 Instagram Automation - WORKING (2026-01-30)
**EasyOCR + Vision Framework Integration:**
- **NumPy Fix:** EasyOCR requires `numpy<2` (downgrade from 2.x)
- **Workflow:** Open profile → Click post (x400,y650) → Press 'L' → EasyOCR find "Add comment" → Click → Type → EasyOCR find "Post" → Click
- **@glowbom Coordinates:** Comment (2056, 1829), Post (2768, 1829)
- **@glowbygenius Coordinates:** Comment (1854, 1829), Post (2574, 1829)
- **Commands:**
  ```bash
  cd /Users/agent0/clawd/ocr-env && source bin/activate && python3 script.py
  /usr/sbin/screencapture -x /tmp/screenshot.png
  ```
- **Skills documented:** /Users/agent0/clawd/AUTOMATION_SKILLS.md
