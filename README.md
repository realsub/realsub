<!-- Maintained upstream in the RealSub app repository; do not edit here directly.
     One file per language (English / 简体中文 / 繁體中文 / 日本語) — change one, change all four. -->

# RealSub

**Live subtitles for audio your PC is playing — recognized locally, translated optionally,
shown in a floating bar on top of everything.**

**English** · [简体中文](README.zh.md) · [繁體中文](README.zh-TW.md) · [日本語](README.ja.md)

> This repository is the **public home of RealSub**: downloads, documentation, tutorials,
> the privacy policy, and the place to report bugs or ask questions.
> **It does not host the application source code.**

---

## What RealSub is

RealSub is a Windows app that captures whatever your PC is playing — or the sound of **one
specific app** you pick — recognizes the speech **locally on your own machine**, optionally
translates it, and shows the result in a floating subtitle bar over any other window.

Japanese video with no subtitles, foreign-language streams, lectures, podcasts, interviews,
game dialogue: if the sound comes out of this PC, it can be subtitled — including the places a
player plugin can never reach.

- **NVIDIA GTX 10-series or newer, from 2 GB of VRAM** (4 GB or more is more comfortable).
  **We strongly recommend an NVIDIA GPU** — that is where RealSub performs at its best. Other
  GPUs go through Vulkan on a **best-effort** basis: the first run does a short performance test
  (tens of seconds) and only enables it if it passes. We have verified it on some GPU models,
  but cannot promise every card. If the test fails or Vulkan errors at runtime, RealSub falls
  back automatically, shows a tray notification, rewrites the device setting to what is actually
  running, and you can run "Re-test GPU performance" in Settings any time.
- **No NVIDIA GPU? RealSub tries Vulkan first, and switches to CPU mode automatically** if Vulkan
  is unavailable, does not pass the performance test, or the model fails to load — accuracy is
  lower than on a GPU and latency is clearly higher, but it works. You get a notice when it
  happens; nothing to set up in advance (you can still pin the compute device yourself under
  Settings → Transcription).
- **Models ship inside the app.** Nothing to download, no account, no API key to get started.
- **Recognizes Japanese, Chinese (Simplified or Traditional) and English** (or detects the
  language for you) and **translates into English, Simplified Chinese, Traditional Chinese or
  Japanese**. The recognition and translation models could in theory cover more language
  combinations; to keep quality up, only the languages we have tested thoroughly are offered for
  now.
- **Interface in English, Japanese, Simplified Chinese and Traditional Chinese**, following your
  system language.

## What it does not do

- **Singing, pure music and radio-effect voices do not produce subtitles at the moment.**
- **Translations run one beat behind the original.** Translation works sentence by sentence and
  only appears once a sentence is complete; with near-continuous speech (commentary, lectures,
  live streams) it can trail by around 10 seconds. That is by design, not a network fault.
- **Four device options: "Auto" / "GPU (NVIDIA)" / "AMD / Intel GPU (Vulkan)" / "CPU".**
  Auto prefers NVIDIA, then **tries** Vulkan, then CPU. Vulkan is best-effort: **some GPUs may
  not get acceleration** and run in CPU mode instead, where accuracy is lower and latency is
  clearly higher.
- **Recognition is fully offline; translation needs an internet connection** (unless you run a
  translation service on your own machine). Audio is never sent anywhere — only subtitle text,
  and only while translation is enabled.
- **It captures what your PC plays, not your microphone.**
- **Windows only** (10 version 2004 or newer, 64-bit). No macOS or Linux build.
- Subtitles are machine-recognized and machine-translated, so they contain errors.

## Download

**[Get RealSub on Steam](https://store.steampowered.com/app/5227410/)**

The base app is **free**: complete live transcription, with no usage counter.
The **Full Version DLC** unlocks translation (bilingual subtitles) and session history +
SRT / TXT export. A **7-day full-featured trial** starts the first time you use RealSub (once per
Steam account — reinstalling or changing PCs does not reset it); when the trial ends,
the app switches to the free version automatically.

## Documentation

- **[FAQ](faq.md)** — hardware requirements, why no subtitles appear, translation inside
  mainland China, what happens after the trial, export accuracy.
- **[Tutorials](tutorials/)** — optional setups: running a local LLM translator, using a free
  third-party translation endpoint.
- **Privacy policy** — [English](privacy.en.md) · [简体中文](privacy.zh.md) ·
  [繁體中文](privacy.zh-TW.md) · [日本語](privacy.ja.md)
- **Third-party licenses** — the full text of every bundled open-source component ships with the
  app; open it from **Settings → About → Third-party licenses**.

## Feedback and support

- **Bug reports** → [open an issue](https://github.com/realsub/realsub/issues/new/choose) using the bug report template.
- **Questions, ideas, showing off your setup** → [Discussions](https://github.com/realsub/realsub/discussions).
- **Private matters** (purchase problems, anything you would rather not post publicly) →
  `realsub.support@gmail.com`.

**API keys, your Windows user name and file paths are masked automatically in the diagnostics
zip** (paths become `%USERPROFILE%` / `\Users\***`), and it contains no subtitle text. Before
attaching it to a public issue it is still worth opening it and checking for anything else you
consider sensitive. If you would rather not publish it, e-mail it to us instead.
