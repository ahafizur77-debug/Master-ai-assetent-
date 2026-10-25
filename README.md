# Master AI Assistant

A separate, mobile-first, free-first AI assistant. It is independent from Earnova AI and MoneyMind AI V6.

## Deployment

This repository is connected to the Render web service `master-ai-assistant-hafizur`. The server requires HTTP Basic Authentication.

Render environment variables required:
- `APP_USER`: login username
- `APP_PASSWORD`: strong password with at least 20 characters

The server fails closed with HTTP 503 if these are missing or the password is too short. Never commit credentials to GitHub. The app should not be shared publicly; this is a single-admin starter, not a multi-user product.

## Current features

- Responsive mobile dashboard
- Voice dictation through browser Speech Recognition where supported
- Spoken replies using browser speech synthesis where supported
- Local task checklist stored in the current browser
- Planner, Researcher, Builder and Quality Checker task templates
- Demo chat that clearly labels itself as demo mode
- Optional server-side OpenAI-compatible AI provider using `AI_BASE_URL`, `AI_API_KEY`, and `AI_MODEL` environment variables
- Automation dry-run only; no external workflow is triggered

## Limitations

- Real AI responses require a configured provider. Provider quotas and free availability vary; unlimited free AI is not promised.
- Agent roles generate checklists; they are not autonomous background agents and do not run while the app is closed.
- Tasks are saved only in the browser on the current device, not synced across devices.
- Voice controls depend on browser support and microphone permission; Chrome on Android is a practical option.
- No connection to Earnova, MoneyMind, or n8n has been made.
- Free hosting may sleep after inactivity and take time to wake up.

## Run locally

Requires Node.js 20 or newer.

```bash
npm start
```

Set `APP_USER` and `APP_PASSWORD` in the environment before opening the app. For real AI, configure the optional provider variables server-side. Do not put API keys in browser code or commit them to GitHub.
