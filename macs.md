---
title: Which Mac?
nav_order: 2.5
permalink: /macs/
description: What GoRunRun Local AI can do on your Mac, depending on its memory. Includes the Mac sizes that still need testing, and how to help.
---

# Which Mac?
{: .no_toc }

What GoRunRun Local AI can do depends mostly on your Mac's **memory**. The installer checks it and picks the best setup for you. It won't offer anything your Mac can't run.
{: .fs-6 .fw-300 }

1. TOC
{:toc}

## What you get with each amount of memory

To see your Mac's memory, choose **Apple menu > About This Mac** and look at **Memory**. Every setup needs an Apple silicon Mac (M1 or newer) and macOS 15 or newer. The chip generation (M1 to M5) and Pro, Max or Ultra change how fast it runs, not what it can do.

| Memory | What the installer sets up | Options | Limitations | Status |
|:--|:--|:--|:--|:--|
| **8–24 GB** | Nothing | <span class="opt no"><span class="sr">Not available: </span>Chat, photos, documents</span><span class="opt no"><span class="sr">Not available: </span>Voice conversations, voice messages</span><span class="opt no"><span class="sr">Not available: </span>Videos with sound and speech</span><span class="opt no"><span class="sr">Not available: </span>Animating a photo</span> | Not enough memory for the AI models. | Not supported |
| **32–36 GB** | Gemma 4 (12B) | <span class="opt yes"><span class="sr">Available: </span>Chat, photos, documents</span><span class="opt yes"><span class="sr">Available: </span>Voice conversations, voice messages</span><span class="opt no"><span class="sr">Not available: </span>Videos with sound and speech</span><span class="opt no"><span class="sr">Not available: </span>Animating a photo</span> | Less capable than Qwen 3.5 at reasoning and coding. Writes about half as fast. Remembers less of a long chat (32K tokens). **No video creation.** | Untested: [help us test](#help-us-test) |
| **48 GB** | Gemma 4 (12B). LTX-2.3 video is optional (off by default) | <span class="opt yes"><span class="sr">Available: </span>Chat, photos, documents</span><span class="opt yes"><span class="sr">Available: </span>Voice conversations, voice messages</span><span class="opt yes"><span class="sr">Available: </span>Videos with sound and speech <em>(optional)</em></span><span class="opt yes"><span class="sr">Available: </span>Animating a photo <em>(optional)</em></span> | Same model limitations as above. Video creation is likely to be slow and uses most of the memory. No Wan 2.2. | Untested: [help us test](#help-us-test) |
| **64 GB** | Qwen 3.5 (35B), Gemma 4 to hear voice messages, and LTX-2.3 video. Wan 2.2 is optional | <span class="opt yes"><span class="sr">Available: </span>Chat, photos, documents</span><span class="opt yes"><span class="sr">Available: </span>Voice conversations, voice messages</span><span class="opt yes"><span class="sr">Available: </span>Videos with sound and speech</span><span class="opt yes"><span class="sr">Available: </span>Animating a photo</span> | Videos are up to 10 seconds. Wan 2.2 takes 6–7 minutes per clip, has no sound, and pauses the chat model while it renders. | **Tested** on an M5 Max |
| **96 GB** | Same as 64 GB | <span class="opt yes"><span class="sr">Available: </span>Chat, photos, documents</span><span class="opt yes"><span class="sr">Available: </span>Voice conversations, voice messages</span><span class="opt yes"><span class="sr">Available: </span>Videos with sound and speech</span><span class="opt yes"><span class="sr">Available: </span>Animating a photo</span> | The chat model stays loaded while Wan 2.2 renders. | Untested: [help us test](#help-us-test) |
| **128 GB or more** | Same as 64 GB | <span class="opt yes"><span class="sr">Available: </span>Chat, photos, documents</span><span class="opt yes"><span class="sr">Available: </span>Voice conversations, voice messages</span><span class="opt yes"><span class="sr">Available: </span>Videos with sound and speech</span><span class="opt yes"><span class="sr">Available: </span>Animating a photo</span> | None beyond the video limits above. | Untested: [help us test](#help-us-test) |

Web search and phone access work on every supported Mac.

Each setup puts a limit on how much memory the AI models may use (70% of the total), so the rest of your Mac stays responsive.

After installing, the home screen of the app shows your Mac, what's installed, and its limitations. Hover over (or tap) the **ⓘ** next to a limitation to see why. Features your setup can't do are grayed out.

## What each choice means

- **Qwen 3.5 (35B)**: the most capable model. It reads text, images and video but can't hear audio, so Gemma 4 is installed next to it to hear voice messages. It needs 64 GB of memory.
- **Gemma 4 (12B)**: lighter. It reads text, images and audio, so it hears voice messages itself. It's slower than Qwen 3.5 because it uses all of its parameters for every word.
- **LTX-2.3**: videos up to 10 seconds with matching sound and speech, about a minute per clip.
- **Wan 2.2**: sharper video with no sound at all, 6–7 minutes per clip. Needs 64 GB of memory.

## Help us test

GoRunRun Local AI is built and tested on one Mac: an M5 Max with 64 GB. We'd love your help with every other size in the table.

**1. See what the installer would do**, without installing or changing anything:

```
curl -fsSL https://raw.githubusercontent.com/gorunrunai/local-ai/main/install.sh | bash -s -- --dry-run
```

You can also preview the setup for a Mac you don't have. Name its chip and memory:

```
curl -fsSL https://raw.githubusercontent.com/gorunrunai/local-ai/main/install.sh | bash -s -- --dry-run --machine=M4Max-48GB
```

Other examples: `--machine=M1Max-32GB`, `--machine=M3Max-96GB`, `--machine=M4Max-128GB`. Add `--macos=15.4` to preview a different macOS version.

**2. Install it and try it for a day.** Chat, send a photo, record a voice message, try voice mode and, if you have video, make a short clip.

**3. Tell us how it went.** Include your Mac model, its memory, and anything that was slow, failed or confusing:

- [Open a test report on GitHub](https://github.com/gorunrunai/local-ai/issues/new?template=config_test.yml) (the form asks the right questions), or
- email [amit@gorunrun.ai](mailto:amit@gorunrun.ai?subject=GoRunRun%20Local%20AI%20test%20report).

Reports that it works well are just as useful as reports of problems. Want to help more? See [Contributing](../developers/contributing). They're how an "Untested" row becomes "Tested".
