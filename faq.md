<!-- Maintained upstream in the RealSub app repository; do not edit here directly.
     One file per language (English / 简体中文 / 繁體中文 / 日本語) — change one, change all four. -->

# RealSub FAQ

**English** · [简体中文](faq.zh.md) · [繁體中文](faq.zh-TW.md) · [日本語](faq.ja.md)

> App 1.0.0 / last updated 2026-08-13. Free tiers, model names and endpoints of third-party
> services are the vendors' to change; their own documentation is authoritative.

---

## Q1. Does translation work from mainland China? How do I make it faster?

- **The default "Microsoft Translator" source works from mainland China.** We tested the full request flow from a mainland node on 2026-08-13 and got translations back in about 1.2 seconds. Nothing extra to configure.
- **For lower latency inside China, you can plug in a free domestic LLM endpoint.** Register at Zhipu's open platform (bigmodel.cn; a mainland phone number is required), get an API key, then in RealSub go to **Settings → Translation → Translation source → "LLM (OpenAI-compatible)"** and fill in:
  - API URL: `https://open.bigmodel.cn/api/paas/v4` (stop at `/v4`; the rest of the path is appended automatically)
  - API key: the key you were issued
  - Model name: `glm-4-flash`

  That model is **free at the time of writing**, but the vendor decides its free tier and model naming and may change either — **always check the vendor's own documentation**. RealSub neither bundles nor proxies any third-party account. If the endpoint URL is left empty, RealSub silently falls back to Microsoft Translator (Edge).
- **Do not pick "Google Translate" in mainland China** — it times out there in our tests and will simply keep failing.
- **The DeepL source needs your own API key** and does nothing without one.
- If a translation source fails, RealSub falls back to the default source and tells you in the UI; transcription is never blocked. **Recognition is fully offline — subtitles keep coming even with no network at all.**

## Q2. Why are no subtitles appearing?

Check these in order of likelihood:

1. **What is playing is singing, pure music, or a voice with radio/walkie-talkie processing.** Those do not produce subtitles at the moment.
2. **The wrong audio source is selected.** If you picked a specific app under Settings → Transcription → Audio source, only that app is transcribed. Switch back to "Entire system (default)" to capture everything.
3. **The app you want is not in the list.** Windows only creates an audio session for an app once it has actually made a sound — play something first, then refresh the list. Per-app capture also requires Windows 10 version 2004 or newer.
4. **System volume is at zero or the app is muted.** There is no audio to capture while muted.
5. **Transcription is not running.** Check whether the tray menu shows Start or Stop, or toggle it with `Ctrl+Alt+S`.
6. **The subtitle window is hidden or off-screen.** Toggle it with `Ctrl+Alt+H`, or use "Reset window position" under Settings → Hotkeys & More → Window (the tray menu has the same entry).
7. **Only the translated line is missing.** The free version does not include translation; the recognized text still appears normally. Translation is unlocked by the Full Version DLC.

If none of that helps, use "Export diagnostics…" in the tray menu and send the resulting zip with a short description to our support address.

## Q3. Should I buy the Full Version DLC?

**Use the free version first, then decide.** That is a real recommendation, not a formality:

- The base app is free and gives you **complete live transcription**, with no usage counter. Installing it answers the three questions that actually matter: is recognition accurate enough for your content, does it run smoothly on your GPU, and do you like the overlay format.
- A **7-day full-featured trial** (once per Steam account) also starts the first time you use RealSub, so translation and history export are available during that week.
- When the trial ends, the app switches to the free version automatically.
- Only once you are satisfied does buying the DLC make sense. That order removes almost every "bought it, then found out it was not for me" refund.

If you have already decided to refund, that is completely fine. We would just ask you to spend a few minutes with the free version first — several common surprises (no subtitles for singing, some GPUs may not get acceleration) are stated openly in the "what it does not do" section on the store page.

## Q4. What GPU do I need? What if I don't have an NVIDIA GPU?

- **NVIDIA GTX 10-series or newer, from 2 GB of VRAM; 4 GB or more is more comfortable.** The default recognition model needs a little over 2 GB, so a card with exactly 2 GB can get tight when other programs are also using VRAM. **If the model fails to load on the GPU — not enough VRAM, driver trouble — RealSub switches to CPU mode automatically**, so there is nothing to set up in advance.
- **We strongly recommend an NVIDIA GPU** — that is where RealSub performs at its best. Other GPUs go through Vulkan on a **best-effort** basis: the first run does a short performance test (tens of seconds) and only enables it if it passes. We have verified it on some GPU models, but cannot promise every card. If the test fails or Vulkan errors at runtime, RealSub falls back automatically, shows a tray notification, rewrites the device setting to what is actually running, and you can run "Re-test GPU performance" in Settings any time.
- **Four device options: "Auto" / "GPU (NVIDIA)" / "AMD / Intel GPU (Vulkan)" / "CPU".** Auto prefers NVIDIA, then **tries** Vulkan, then CPU. Vulkan is best-effort, so **some GPUs may not get acceleration**.
- Without an NVIDIA GPU and without usable Vulkan acceleration — or if the GPU fails to initialize or the model fails to load — RealSub automatically switches to **CPU mode** (and tells you via a tray balloon and the subtitle status line): it uses a smaller recognition model, accuracy is lower than on a GPU, latency is clearly higher, and the in-progress preview line rarely appears. **It works, but it is plainly a second-class experience** — please factor that in before buying the DLC.
- The hard CPU requirement is a **4-core processor from the last decade with AVX2 support**.
- You can pin the compute device to "Auto" / "GPU (NVIDIA)" / "AMD / Intel GPU (Vulkan)" / "CPU" under Settings → Transcription, and run the Vulkan check again with "Re-test GPU performance".

## Q5. Does it need the internet? Is my audio uploaded?

- **Audio is processed entirely on your machine and never leaves it.** The recognition model (Whisper) and the voice-activity model (Silero VAD) are bundled with the app; recognition needs no network at all.
- **Only translation goes online**: while it is enabled, the recognized **subtitle text** (text only) is sent to the translation service you selected in order to get a translation back. With the local translation source, even that stays on your machine.
- No telemetry, no account, no usage statistics, no automatic crash reporting. A diagnostics zip is only created when you click Export yourself, and it stays local; API keys, your Windows user name and file paths inside it are masked automatically.
- The full details are in the privacy policy bundled with the app and linked from the store page.

## Q6. Which languages are supported?

- **Speech that can be recognized**: Japanese, Chinese (Simplified), Chinese (Traditional), English. You can also choose Auto and let the app decide (detection is sticky, so it does not flip back and forth; Auto writes Chinese in Simplified characters — pick "Chinese (Traditional)" explicitly if you want Traditional).
- **Translation targets**: English, Simplified Chinese, Traditional Chinese, Japanese.
- **Interface languages**: English, Japanese, Simplified Chinese, Traditional Chinese, following your system language by default (Traditional for Taiwan / Hong Kong / Macau systems).
- The three settings are independent — you can run an English interface, recognize Japanese, and translate into English.
- The recognition and translation models could in theory cover more language combinations; to keep quality up, only the languages we have tested thoroughly are offered for now. The settings pages inside the app are the authoritative list.

## Q7. What happens when the 7-day trial ends?

The app switches to the **free version** automatically:

- Kept: complete live transcription (recognition languages, bundled models, overlay appearance, hotkeys, per-app capture) plus **read access to history you already recorded**.
- Locked: translation (the translated line), saving new history and recordings, SRT / TXT export.
- Buying the Full Version DLC restores all of it immediately — no reinstall and no restart needed. If it does not apply right away, use "Purchased? Refresh" in the purchase dialog.
- The trial is tied to your Steam account: reinstalling the app, wiping its data, or switching to another PC does **not** grant a new trial.

## Q8. Can I use the exported subtitles directly on a video?

Yes — you can export **SRT subtitles** or **plain TXT** (Full Version required). Note that:

- Timestamps are anchored to **when you listened**, not to the video file's own timeline. If you played the file from the start without pausing or seeking, the two line up closely; otherwise you will need to shift them.
- Merging of short segments and de-duplication can shift individual cue boundaries by a second or two.
- The text is machine-recognized and machine-translated. **Proofread before publishing anything.**

## Q9. Why does the translation always lag behind the original text?

That is how sentence-level translation works — it is not a network fault. The original text streams in while the speaker is still talking; the translation is only requested once a sentence boundary is found, and the result takes another second or two to come back.

- Normal dialogue: sentences end in natural pauses, so the translation usually trails by only 2–3 seconds.
- Near-continuous speech (commentary, lectures, live streams, fast talkers): when no pause can be found, the app waits up to about 10 seconds before force-cutting a sentence, so the translation lags noticeably.

The original (white/grey) line stays real-time and is not affected. Only if translations stop appearing entirely or go missing frequently is the translation service itself likely unreachable — try a different source under Settings → Translation.
