# openclaw-voice

Voice control for OpenClaw agents via Siri Shortcuts and Alexa Skills.

> "Hey Siri, Ask OpenClaw what's on my calendar"

## What's Included

- **Siri Shortcut** — Works on iOS/macOS, ready to import
- **Alexa Skill** — (Coming soon) Lambda-based skill for Echo devices

## Prerequisites

- OpenClaw running with HTTP API enabled
- Your API token (from gateway config)
- For Siri: iOS 15+ or macOS 12+
- For Alexa: AWS account + Alexa Developer account

## Quick Start

### 1. Enable OpenClaw HTTP API

Add to your `~/.clawdbot/moltbot.json`:

```json
{
  "gateway": {
    "http": {
      "endpoints": {
        "chatCompletions": { "enabled": true }
      }
    }
  }
}
```

Restart the gateway: `moltbot gateway restart`

### 2. Find Your API Token

Your token is in the gateway config:

```bash
grep -A2 '"auth"' ~/.clawdbot/moltbot.json
```

Look for `gateway.auth.token`.

### 3. Install Siri Shortcut

1. Download [`siri/ask-openclaw.shortcut`](siri/ask-openclaw.shortcut)
2. Double-click to open in Shortcuts app
3. You'll be prompted for:
   - **API URL**: Usually `http://localhost:18789/v1/chat/completions`
   - **API Token**: Enter as `Bearer YOUR_TOKEN` (include "Bearer " prefix)
4. Tap "Add Shortcut"

### 4. Use It

- **Siri**: "Hey Siri, Ask OpenClaw"
- **Shortcuts app**: Tap to run
- **Rename it**: Change "Ask OpenClaw" to your agent's name ("Ask Jarvis", "Hey Friday", etc.)

## Tips

### Voice Mode

The shortcut includes a system prompt optimized for voice:
- Concise responses (1-3 sentences)
- No emojis (they get spoken literally)
- No markdown formatting

### Best Use Cases

**Great for:**
- Quick questions ("What's the capital of France?")
- Simple lookups ("What's on my calendar?")
- Brief tasks with instant answers

**Use chat instead for:**
- Complex tasks (reservations, research)
- Multi-step workflows
- Anything requiring back-and-forth

### Timeout

Siri has a ~30 second timeout. If your agent needs to do complex work (tool calls, searches), the request may time out. Keep voice queries simple.

## Customization

### Change the Voice

In Shortcuts app:
1. Open "Ask OpenClaw"
2. Find the "Speak" action at the bottom
3. Change Voice to your preference (Siri Voice 4 recommended)

### Adjust System Prompt

Edit the system message in the shortcut's JSON body to change how your agent responds to voice queries.

## Alexa Setup

See [`alexa/README.md`](alexa/README.md) for Lambda deployment instructions.

## Troubleshooting

**"Unauthorized" error:**
- Make sure token includes "Bearer " prefix
- Check token matches your gateway config

**Request times out:**
- Query was too complex
- Keep voice queries simple and direct

**No response / silent:**
- Check API URL is correct
- Verify gateway is running: `moltbot gateway status`

## License

MIT
