# RealSub Privacy Policy

Last updated: 2026-08-13

RealSub is a real-time subtitle tool that runs entirely on your own computer.
**Speech recognition happens locally; your audio never leaves your machine.**
This document explains what data RealSub handles, when anything is sent to an outside
service, and where things are stored.

## 1. What we do not do

- **No telemetry, no usage statistics, no automatic crash reporting.** RealSub never sends
  anything back to us in the background.
- **No accounts.** No sign-up, and we do not collect your name, e-mail address, or any
  identifying information.
- **No microphone access.** RealSub captures the sound your system is playing (or the sound
  of one application you select); it does not record microphone input.
- **No advertising, no profiling, and no sale or sharing of personal data with third parties.**

## 2. Audio and subtitles

- Audio is read through Windows system loopback capture (WASAPI loopback) and fed straight
  into a local speech recognition model in memory.
- Both the speech recognition model (Whisper) and the voice activity detection model
  (Silero VAD) are **installed locally together with the application**; recognition requires
  no internet connection.
- **Audio is never uploaded to any server** and is never sent to us.

## 3. Translation (the only feature that sends text outside)

Translation is enabled by default. **When translation is on, the recognized subtitle text
(text only — never audio) is sent to the translation service you selected in Settings** in
order to retrieve the translation. The available services and their recipients are:

| Translation source in Settings | Text is sent to | Applicable privacy policy |
|---|---|---|
| Microsoft Translator (default) | Microsoft Bing translation service (`www.bing.com`) | [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement) |
| Google Translate | Google translation service (`translate.google.com`) | [Google Privacy Policy](https://policies.google.com/privacy) |
| DeepL | DeepL (requires your own API key) | [DeepL Privacy Policy](https://www.deepl.com/privacy) |
| OpenAI-compatible endpoint | **The address you enter yourself** (any compatible or self-hosted service) | Determined by that service's provider |
| Local translation | A translation service running on your own machine (`127.0.0.1`); **it never leaves your computer** | Not applicable |

Notes about translation requests:

- A request contains only the **subtitle text to translate** and the target language. It contains
  no account information, no device identifier, and no audio.
- For the Microsoft and Google options, RealSub uses their public web translation endpoints.
  Whether those services log requests is up to them and outside our control.
- If you choose DeepL or an OpenAI-compatible endpoint, the API key you enter is **stored only in
  the local configuration file** and is used solely to call the service you specified.
- **With translation turned off, RealSub sends nothing to any external service** and runs fully offline.
- The free version does not include translation, so no text leaves your machine when using it.

## 4. Data stored on your computer

The following is stored locally only and is never uploaded:

| Content | Location |
|---|---|
| Configuration (interface, model, translation settings, including any API key you enter) | `%APPDATA%\RealSub\config.toml` |
| Runtime state (window position, trial start timestamp, etc.) | `%APPDATA%\RealSub\state.toml` |
| Application logs (for troubleshooting; under the default configuration they do not contain subtitle text) | `%APPDATA%\RealSub\logs\` |
| Transcript history (subtitle text and timings) and optional audio recordings (MP3) | `%APPDATA%\RealSub\history\` |

- History and recording are features you **can turn off in Settings**. Existing records can be
  deleted from the History window, or by deleting the folders above.
- Old history is pruned automatically according to the retention period you set.
- Uninstalling does not automatically remove `%APPDATA%\RealSub`; delete that folder manually if
  you want everything gone.

## 5. The Steam version

- RealSub is distributed through Steam. The Steam client itself handles your account, purchase, and
  playtime data; that is governed by the
  [Valve Privacy Policy](https://store.steampowered.com/privacy_agreement/), and we have no access
  to your Steam account information.
- The only things RealSub reads through the Steam interface are: **whether the full-version DLC has
  been purchased**, whether Steam is currently logged in, and the Steam server time (used for trial
  timing so that changing the system clock has no effect).
- RealSub stores one file, `trial.dat`, in **Steam Cloud**. It contains nothing but the
  **timestamp of your first run** (a single number), so that the trial period stays consistent when
  you move to another computer. It contains no subtitles, no audio, and no personal information.

## 6. Diagnostic export

RealSub offers an "Export diagnostics" button. It creates a local zip file **only when you click it**
and **never sends it anywhere automatically**. Whether to send it to us is entirely your choice.
The zip contains:

- `config.redacted.toml` — your configuration, with any API key replaced by `***`;
- `state.toml` — window position, trial timing, and similar runtime state;
- `logs/` — logs of the last 3 sessions (model loading, device switching, errors; under the default
  configuration, no subtitle text);
- `env.txt` — application version, Windows version, Python version, GPU model, compute device,
  license state, and the **install paths of the CUDA runtime libraries**.

All four items are **scrubbed of your user name and the paths containing it** before they are
written into the zip:
your user profile directory is replaced by the literal `%USERPROFILE%`, and any remaining path of
the form `C:\Users\yourname\...` becomes `C:\Users\***\...`. You can still open the zip and review
it before sending.

## 7. Children's privacy

RealSub is not directed at children under 13, and we do not knowingly collect personal information
from children (in fact, the software collects no personal information at all).

## 8. Changes to this policy

If this policy changes, we will update the date at the top of this page and mention it in the
release notes.

## 9. Contact

For privacy questions, contact: `realsub.support@gmail.com` (you can also use the developer contact
information on the Steam store page).

— RealSub
