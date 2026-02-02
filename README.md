# openclaw-voice

Voice control for OpenClaw. Talk to your AI from Siri or Alexa.

## Setup

### Prerequisites

- OpenClaw running with HTTP API enabled
- For Siri: iOS 15+ or macOS 12+
- For Alexa: AWS account + Alexa Developer account

### Enable OpenClaw HTTP API

Add to your config:

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

1. Download `siri/Ask-OpenClaw.shortcut`
2. Open in Shortcuts app
3. Edit the URL and token to match your setup
4. Say "Hey Siri, Ask OpenClaw"

### Alexa

See `alexa/README.md` for Lambda deployment instructions.

## License

MIT
