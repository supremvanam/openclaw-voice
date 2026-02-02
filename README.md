# moltbot-voice

Voice control for Moltbot. Talk to your AI from Siri or Alexa.

## Setup

### Prerequisites

- Moltbot running with HTTP API enabled
- For Siri: iOS 15+ or macOS 12+
- For Alexa: AWS account + Alexa Developer account

### Enable Moltbot HTTP API

Add to your `~/.moltbot/moltbot.json`:

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

Restart the gateway.

### Siri

1. Download `siri/Ask-Moltbot.shortcut`
2. Open in Shortcuts app
3. Edit the URL and token to match your setup
4. Say "Hey Siri, Ask Moltbot"

### Alexa

See `alexa/README.md` for Lambda deployment instructions.

## License

MIT
