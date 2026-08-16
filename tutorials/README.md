<!-- Maintained upstream in the RealSub app repository; do not edit here directly.
     One file per language (English / 简体中文 / 繁體中文 / 日本語) — change one, change all four. -->

# Tutorials

**English** · [简体中文](README.zh.md) · [繁體中文](README.zh-TW.md) · [日本語](README.ja.md)

Optional setups for RealSub. **None of these are required** — RealSub works out of the box with
the bundled models and the default translation source. These guides are for people who want a
translator that is faster, cheaper, or fully offline.

> **Status: planned.** The articles below are not written yet. Watch this repository or check back
> after a release to see them appear.

---

## Planned articles

### 1. Local LLM translation with llama-server (Sakura and friends)

Running a translation model on your own machine and pointing RealSub at it, so that **no text
leaves your computer at all** and there is no per-request latency over the internet.

Planned scope:

- installing `llama.cpp` / `llama-server` on Windows and picking a quantized model file;
- VRAM budgeting when the recognition model is already resident on the same GPU;
- the exact RealSub settings (Settings → Translation → source = **Local**, address
  `http://127.0.0.1:8178`), and how to verify it is actually being used;
- realistic latency expectations, and when a local translator is *not* worth it.

**Licensing note (important):** models such as Sakura are distributed under terms that
**prohibit commercial use**, which is why RealSub does not bundle or ship any of them. This guide
will explain how to deploy a model **you obtained yourself**; complying with that model's license
is your responsibility.

### 2. Using a free Zhipu (bigmodel.cn) API key as the translation source

For users in mainland China who want lower latency than the default source, or anyone who wants
to plug an OpenAI-compatible endpoint into RealSub.

Planned scope:

- registering at bigmodel.cn and issuing an API key (a mainland phone number is required);
- filling in Settings → Translation → source = **LLM (OpenAI-compatible)**:
  API URL `https://open.bigmodel.cn/api/paas/v4`, your key, model name `glm-4-flash`;
- what to do when a request fails (RealSub falls back to the default source and says so);
- **the free tier, the model name and the endpoint are the vendor's to change** — the article will
  be dated and must be re-checked against the vendor's own documentation.

RealSub does not bundle, pre-fill or proxy any third-party account. This is the same procedure
summarized in [FAQ Q2](../faq.md).

---

## Contributing

Have a setup worth writing up? Post it in
[Discussions](https://github.com/realsub/realsub/discussions) — good write-ups can be adopted
here with credit.
