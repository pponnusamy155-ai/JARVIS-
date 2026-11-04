# Chatki JARVIS AI Assistant

A starter JARVIS-style voice assistant that works in a browser on Windows PC and Android.
It uses Flask + OpenAI API for AI answers, browser speech recognition for voice input,
and browser speech synthesis for spoken replies.

## Features

- Chat with an AI assistant in English, Tamil, or Tanglish (language recognition depends on browser).
- Tap-to-speak microphone input.
- Text-to-speech output with best-effort male voice selection.
- Allowlisted commands: open YouTube, Google, Gmail, WhatsApp Web, Facebook, Instagram, GitHub.
- Windows-only commands: open Notepad and Calculator.
- Responsive interface and installable PWA.

## Requirements

- Python 3.10+
- An OpenAI API key and API billing/credits
- Windows PC for the local server (Android can connect over Wi-Fi)
- Chrome or Edge recommended

## Windows setup

1. Install Python from https://www.python.org/downloads/
2. Extract this project folder.
3. Open PowerShell in the extracted `Chatki_JARVIS` folder.
4. Create and activate a virtual environment:

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   If PowerShell blocks activation, run this once in that terminal:
   `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`
   Then activate the environment again.

5. Install packages:

   ```powershell
   pip install -r requirements.txt
   ```

6. Copy `.env.example` to `.env` and add your OpenAI API key:

   ```env
   OPENAI_API_KEY=your_real_api_key
   OPENAI_MODEL=gpt-5.5
   ```

   Get an API key from https://platform.openai.com/api-keys.
   Keep the key private. Do not place it in HTML or JavaScript.

7. Start the server:

   ```powershell
   python app.py
   ```

8. On the Windows PC, open http://127.0.0.1:5000 in Chrome or Edge.

## Android setup (same Wi-Fi)

1. Start the server on your Windows PC.
2. Find the PC's local IPv4 address by running `ipconfig` in PowerShell.
   It will look like `192.168.1.25`.
3. On Android connected to the same Wi-Fi, open `http://192.168.1.25:5000`.
   Replace the example IP with your PC's actual IPv4 address.
4. For voice recognition, grant microphone permission and use Chrome.
5. To install it like an app:
   - Chrome menu (⋮) → Add to Home screen / Install app, if offered.
   - On Windows Edge: menu → Apps → Install this site as an app.

## Commands

- "Open YouTube"
- "Open Google"
- "Open Gmail"
- "Open WhatsApp"
- "Open Facebook"
- "Open Instagram"
- "Open GitHub"
- On Windows only: "Open Notepad", "Open Calculator"

## Important limitations

- This is a starter project, not the movie JARVIS.
- It does not run an always-listening wake word ("Hey JARVIS"). Browsers require the user to tap the microphone and grant permission. Always-on listening needs a separate native app/service and explicit privacy controls.
- Android can open websites, but this browser version cannot launch arbitrary Android apps or control the whole phone.
- Browser speech recognition may require an internet connection and may not support Tamil on every browser.
- The male voice is best-effort; the device's available voices determine the actual voice.
- AI replies require internet access and OpenAI API usage, which may incur charges.
- The web app uses the Windows PC's Flask server. It is not independently hosted on the internet.
- Do not expose port 5000 to the public internet. For remote access, deploy behind HTTPS with authentication.
- The local command handler uses a fixed allowlist and does not run arbitrary shell commands.
