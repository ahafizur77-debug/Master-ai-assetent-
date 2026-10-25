# Master AI Assistant

A separate, mobile-friendly, free-first personal AI command center. It does not modify or connect to Earnova AI, MoneyMind AI V6, or any existing n8n workflow by default.

## What works without paid services

- Mobile-first dashboard and installable PWA shell (HTTPS is needed for service-worker installation).
- Voice input via browser Speech Recognition when supported, and spoken replies via browser speech synthesis.
- Local task board, agent-role templates, task steps, history and chat history stored in this browser.
- Demo chat mode that clearly says it is simulated.
- Automation dry-runs that do not call an external service.
- Optional server-side OpenAI-compatible AI provider and optional n8n webhook.

## Run locally

Requires Node.js 20 or newer. No npm packages are required.

1. Copy `.env.example` to `.env` if you use a local environment loader, or set environment variables in your terminal/host.
2. Start with `npm start`.
3. Open `http://localhost:3000` on your phone or computer. For a phone on the same Wi-Fi, use the computer's local IP and port 3000.
4. Use demo mode without any API credentials.

This server does not load `.env` automatically. Set environment variables in your shell or hosting dashboard. Example variables:
- `AI_BASE_URL`: provider's OpenAI-compatible base URL, commonly ending in `/v1`
- `AI_API_KEY`: secret API key, stored server-side only
- `AI_MODEL`: exact model name supported by your provider
- `N8N_WEBHOOK_URL`: optional HTTPS webhook URL

Never put secrets in frontend code, commit them to Git, or paste them into local browser storage. Free model availability and quotas vary; the app does not promise unlimited free AI.

## Important security and scope notes

- The built-in agent roles currently generate plans/checklists. They are not independent background agents and do not run while the app is closed.
- A real AI reply occurs only when server-side provider variables are configured. Otherwise the chat returns a clearly labelled demo response.
- Automation is dry-run by default. A real webhook request requires the user to untick dry-run, confirm the request, and configure `N8N_WEBHOOK_URL` on the server. The receiving workflow must still be configured and verified separately.
- This starter server has no user authentication or multi-user isolation. **Do not expose it to the public internet as-is.** Before public deployment, add authentication, CSRF/origin protections, per-user rate limiting, audit controls and HTTPS. Prefer a private/local deployment for initial testing.
- The app cannot prevent screenshots or screen recording.
- Voice input depends on browser support and microphone permission; Chrome on Android is a practical first option.
- Tasks and chat history are stored in local browser storage and are not synced across devices.
- No billing, purchases, paid API dependency or existing project integration is included.

## Files

- `server.js`: tiny Node HTTP server with optional server-side AI proxy and explicitly confirmed webhook endpoint.
- `public/`: responsive PWA frontend.
- `.env.example`: names of optional server environment variables.
