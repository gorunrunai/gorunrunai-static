---
title: Privacy
nav_order: 6
description: What stays on your Mac and what doesn't.
---

# Privacy

GoRunRun Local AI is built so your conversations never leave your computer.

**Stays on your Mac, always:**
- Your chats, attachments, voice recordings, memories and settings
- The AI processing itself: the models run on your Mac's own chip
- Created videos and mini apps

**Leaves your Mac only when you use these features:**
- **Installing and updating** downloads the app from GitHub and the AI models from Hugging Face.
- **Check for updates** (Settings → Updates) reads one public file on GitHub, only when you press the button. Nothing about you or your chats is sent.
- **Web search** sends your search words to public search engines (through a search tool running on your Mac).
- **Reading a web page** fetches that page, like a browser would.
- **Phone access**, if you turn it on, connects your phone to your Mac over your own private Tailscale network, protected by a login token.

**Never:**
- The app has no account, no analytics, no crash reports and no advertising
- The app never sends your data to an AI company

The app's server only answers on your own Mac (`127.0.0.1`). Other computers on your network can't reach it unless you turn on phone access.

Everything is open source, so anyone can [check these claims in the code](https://github.com/gorunrunai/local-ai).

## This website

This website (not the app) counts visits with [Umami](https://umami.is), a privacy-focused analytics service. It uses no cookies and collects no personal information: only anonymous totals such as page views, the referring site, the browser and device type, and the country.
