# How to watch Japanese video that has no subtitles (Windows)

**English** · [日本語](english-video-japanese-subtitles.ja.md) · [简体中文](japanese-video-chinese-subtitles.zh.md) · [繁體中文](japanese-video-chinese-subtitles.zh-TW.md)

A lot of Japanese video simply has no subtitle track. Streaming services in Japan often ship
none at all, live streams never have them, and for older shows, lectures, interviews and
podcasts there was never a subtitle file to begin with. Machine translation is good enough now
that you can follow along — the hard part is getting the words off the screen in the first
place.

This page is about how to do it on Windows: what to judge these tools by, and how to set up
the one I build — including the parts of it that do not work.

---

## What to look for in a solution

Whatever you end up using — and there are several options, including one that ships with
Windows — these are the things that decide whether it actually works for the way you watch:

- **Where the audio comes from.** Some tools only see video inside a browser tab. That rules out
  desktop players, downloaded files, streaming clients, games and calls. Being able to take
  system audio covers everything; being able to point at **one specific app** additionally keeps
  notification sounds and a second window out of your subtitles.
- **Whether you see the original as well as the translation.** Reading the Japanese with a
  translation underneath is a different activity from reading a translation alone, and if any
  part of why you are doing this is learning the language, it is the difference that matters.
- **Which target languages exist.** Most tools translate into English. Fewer translate into
  Japanese or into Chinese, and fewer still distinguish Simplified from Traditional.
- **Whether anything is kept.** Live captions that vanish are fine for watching. If you want to
  review a lecture later, or hand someone a transcript, you need history and an export.
- **Where the recognition runs.** On your machine means no upload, no per-minute bill, and no
  dependency on a service staying online. In the cloud usually means better hardware but your
  audio leaving the building.
- **What it demands of your PC.** Some features are gated on a hardware class you cannot add
  later; others just want a graphics card you probably already own.

### Try what you already have first

Windows has live captions built in — **Win + Ctrl + L** — and depending on your hardware and
Windows version it may cover part of what you need, at no cost. Its capabilities change with
each Windows release, so check
[Microsoft's own page](https://support.microsoft.com/en-us/windows/use-live-captions-to-better-understand-audio-b52da59c-14b8-4031-aeeb-f6a47e6055df)
rather than any third-party comparison, including this one. If it does what you want, you are
done and you do not need another app.

Browser extensions are worth a look if everything you watch is in a browser tab; be aware that
many of them send the audio to a server. Cloud transcription services are accurate but work on
uploaded files after the fact, so they do not help you watch something tonight.

## Setting up RealSub

[RealSub](https://store.steampowered.com/app/5227410/) captures what your PC is playing,
recognizes the speech **on your own machine**, optionally translates it, and draws a
click-through subtitle bar on top of everything else. The base app is free and there is no
usage counter on transcription.

**1. Install and run the first-time wizard.** It checks your hardware and asks for two
languages: the one you are listening to, and the one you want to read. Recognition models are
bundled in the app — nothing to download, no account, no API key.

**2. Pick where the sound comes from.** Either the whole system, or **one specific app**. The
per-app option is the one worth learning: pick your player or your browser and only its audio is
transcribed, so Discord pings and a second video in another window stay out of your subtitles.
An app only appears in the list once it has made a sound.

**3. Start playing something and place the bar.** The subtitle bar ignores clicks, so it never
blocks the player underneath. Hover over it to reveal a frame you can drag and resize; font,
size, colour and opacity are all in Settings.

You should see the recognized Japanese appear while the speaker is still talking, with the
translated line following a beat behind.

### Hardware, honestly

Recognition runs on your GPU. It starts at **2 GB of VRAM on a GTX 10-series card**; 4 GB or
more is more comfortable. AMD and Intel GPUs go through a Vulkan backend on a best-effort basis —
the first run does a short performance test and only enables it if it passes. With no usable
GPU it falls back to CPU mode with a smaller model, which works but is noticeably less accurate
and slower. There is no cloud tier to fall back on, by design: the audio never leaves your PC.

---

## What this approach cannot do

Worth knowing before you install anything:

- **Translation runs one beat behind the original.** It translates whole sentences, so it waits
  for a sentence to end. In ordinary dialogue that is a few seconds. During continuous speech —
  commentary, a lecture, a stream — it can trail by up to about ten seconds. That is the cost of
  translating sentences instead of fragments, not a network problem.
- **Singing and pure music produce nothing.** Anime openings, songs, and voices processed to
  sound like a radio broadcast are classified as non-speech and never reach the recognizer.
- **Recognition is offline; translation is not.** Translation goes through a service, unless you
  run a translation server on your own PC or LAN. Only the recognized text is sent — never audio.
- **It is machine recognition plus machine translation.** It makes mistakes, and on accented,
  overlapping or very fast speech it makes more of them. Treat it as help understanding, not as
  a transcript of record.
- **Windows only** (10 version 2004 or newer, 64-bit). A macOS version is planned, with no date
  to announce yet.

## Accuracy, and what that number means

Measured against a benchmark built from TED talks, news broadcasts, anime, lectures and stream
recordings: **92% Japanese, 98% English, 93% Chinese**. These are internal numbers from my own
test set, not an official score, and the figure you get depends entirely on your material —
clear single-speaker audio scores far above that, a noisy group conversation with background
music scores below it.

The honest way to find out is to run the free version on **your own** content for ten minutes.
Transcription is free with no counter precisely so you can do that before deciding whether the
translation is worth paying for.

---

## Frequently asked

**Does it work with any player?**
It takes the audio Windows is playing, so the player does not matter — desktop players, browsers,
streaming clients, downloaded files, games.

**Can I get Japanese subtitles rather than a translation?**
Yes, and that is the free part. Turn translation off and you get the spoken Japanese as text,
which is what most people learning the language actually want.

**Does anything get uploaded?**
Audio, never. With translation enabled, the recognized text goes to the translation service you
picked. With translation off or pointed at your own local server, nothing leaves the machine.
The [privacy policy](../privacy.en.md) spells out each path.

**What does it cost?**
The base app is free: full live transcription, no time limit, no usage counter. Translation and
history export are unlocked by a one-time DLC. A 7-day full-featured trial starts the first time
you run it.

---

**[Get RealSub on Steam](https://store.steampowered.com/app/5227410/)** · [FAQ](../faq.md) ·
[Tutorials](../tutorials/)
