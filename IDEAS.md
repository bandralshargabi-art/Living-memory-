# ideas.md — the parking lot

Where good finds wait until their time. Nothing here is a project.
Nothing here is authorized. This is the shelf.

**Rule:** every idea gets an entry. Date, what it is, why it
matters, what lane it belongs to, and whether it's been tested.
No idea is chased without Bandr's green light.

---

## 2026-10-10 — Watch skill (claude-video)

**What:** Claude Code / Agent Skills plugin. Give it a video URL, it
extracts frames + timestamped transcript and lets the AI answer
questions about the video. Three modes: transcript / visual /
multimodal.

**Repo:** github.com/bradautomates/claude-video

**Why it matters:** AIP has no video input. This is the blueprint —
URL in, Gemini API watches, transcript + frames out. Free Google
tier: 8 hours of YouTube per day.

**Phone reality:** yt-dlp ✅, ffmpeg ✅, Gemini API ✅.
WhisperX ❌ (needs PyTorch, too heavy for ARM).
Gemini path works on phone. Local Whisper path doesn't.

**Lane:** Artie (if OpenCode supports skills) or AIP Phase 2.
Not now — this is a blueprint, not a dependency.

**Status:** UNTESTED. Park.

---

## 2026-10-10 — Living Memory (global idea)

**What:** A place where a normal person gives their AI memory —
no GitHub, no Termux, no code. Fill in a page once, paste or link
it into any chat, the AI remembers.

**Why it matters:** The market is split. Developer tools (MemOS,
soul-framework, etc.) are too technical. Consumer apps (Layla,
Bodie) lock you into their AI. The gap is: your AI, any AI, a
simple front door.

**What's already built:** Our own version works. IDENTITY / LIFE /
WORK / TEAM / CORE, one memory, tagged per persona, private +
public repos, ~/bin/remember for one-tap paste.

**Status:** Works for us. Not a product. Revisit when we've proven
it for a while.

---

## 2026-10-10 — Strata (local 125B model)

**What:** Open-source project that runs a 125B Mixture-of-Experts
model locally — GPU + CPU + RAM + SSD all pitch in. 250+ tokens/sec
on an RTX 5090.

**Why it matters:** Proves big models running locally is getting
real. Same direction AIP is headed. Local = no queue, no round
trip, no one else's rules.

**Phone reality:** Needs 12 GB VRAM, 32 GB RAM, 80 GB disk.
Note 9 has 6 GB RAM, no GPU. Not for the phone. Desktop or rented
GPU only.

**Status:** Interesting. Not for us yet.

---

## 2026-10-10 — Mobile Harness (mobile IDE)

**What:** Android app that builds, compiles, installs APKs on the
phone. Kotlin, Compose, real project structure. Prompt → AI writes
code → compile → install. Also does web projects with local preview.

**Why it matters:** Shows the GUI layer we don't have. Termux is
our terminal; Mobile Harness is a front door. Same capability,
different surface.

**Reality check:** Took him months. It's an IDE — huge surface.
Our earlier lesson holds: don't build an IDE. Build one view.

**Status:** Watch, don't compete. Learn the file browser and
one-tap build patterns for AIP's UI later.

---

## 2026-10-10 — Botkeep (claimed, empty)

**What:** Free hosting, Founder Free plan. 5 slots, 2 GB RAM,
1.5 vCore, 2 GB storage, free forever.

**Lane:** Environment. Always-on host for small things.

**Status:** Claimed. Empty. First candidate: serve sanitized memory
files as a public URL. Not built.

---

## 2026-10-11 — Bypass IDE (com.bypass.ide) — analyzed

**What:** Native Android IDE with an AI agent called "Maria."
Kotlin/Compose, obfuscated with R8. Built by Divyank Codes
(Telegram: t.me/divyankcodes). Distributed via Telegram, then
paywalled. User reports the app deletes itself from storage every
~15 days.

**Two versions exist. They are different apps.**

### Old version (analyzed — on disk at ~/research/apk-test)

- APK 8.7 MB, decompiled with apktool + jadx
- 1,870 app classes in com/bypass/, mostly obfuscated (k/ folder)
- No assets, no native libs, no on-device model
- Settings keys found: "gemini_api", "gemini_api_key", "stream_url",
  "voice_token" — Gemini is the brain, user supplies the key
- No hardcoded API keys (confirmed)
- Real un-obfuscated file: voice/WakeWordService.java
- Manifest permissions: CALL_PHONE, READ_SMS, READ_CONTACTS,
  RECORD_AUDIO, CAMERA, SYSTEM_ALERT_WINDOW,
  MANAGE_EXTERNAL_STORAGE, WAKE_LOCK
- foregroundServiceType="dataSync|microphone|specialUse"
- usesCleartextTraffic="true" — local server at 127.0.0.1
- WakeWordService: three intents (START/STOP/TRIGGER), notification
  channel "bypass_maria_channel", action button "Talk to Maria",
  Dynamic Island overlay, WakeLock, SharedPreferences toggles
  (wake_word_enabled, dynamic_island_enabled)

### New version (screenshots only — not decompiled)

- Gemini 3.8 Flash High — 24,576 reasoning tokens, 1,048,576 context
- Direct su / POSIX root sandbox — app requests root
- Local shell on :8080 — its own server, like AIP
- Tabs: Home / Files / Editor / Terminal / Preview / Dev
- Agent modes: Chat / Builder / Agent (Autonomous Tasks, Root Ops)
- "IP & Network Reset" — rotates carrier IP via root, flushes DNS
- "Zero-Cost Direct" tunnel
- Voice diagnostics, live speech recognizer logs
- "Grant root for full POSIX & Termux execution"

**Three flags (real, not theory):**
1. Root access = app can read/write anything on the phone
2. IP rotation + tunnel = manipulates the network to hide traffic
3. Self-deletion every ~15 days = app has a mechanism to remove
   itself; either the Telegram bot revokes it or Device Admin is used

**What's worth borrowing:**
- Foreground service pattern (voice + notification + wake lock)
- Dynamic Island overlay
- Intent-triggered activation (voice, overlay, external)
- UI pattern: project list, tabbed IDE, agent modes
- These are native Android features AIP (a PWA) cannot reach.

**What it is not:**
- Not a supercomputer. The phone is a thin client. Gemini does the
  work in Google's data centers.
- Not ours. Paywalled, revocable, deletes itself.
- Not needed. AIP + Termux + Artie already does the same architecture
  — ours is open, ours, and cannot be taken away.

**Status:** CLOSED. Analyzed, understood, not adopted. The pattern is
the takeaway. The app is a rented window.
