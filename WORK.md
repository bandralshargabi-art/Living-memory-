# WORK.md

**Status:** Draft. Shared file — one project, one file.
Keep small enough to read in one pass. Split later if it bloats.

--------------------------------------------------------------------------------
## 1. WHAT AIP IS
--------------------------------------------------------------------------------

AIP = Adaptive Intelligence Platform. Self-hosted AI companion.
Vision: not one chatbot, but connected AI spaces — chat, work,
learning, discovery, creativity, private companionship, AI dev.

**Principle:** "Companion freedom in conversation; agent discipline
in action."

**Runtime baseline:**
- Device: Samsung Galaxy Note 9, Android 10, 6 GB RAM
- Termux, Node 24.18.0
- Server: ~/aip/server.js on 127.0.0.1:8080
- UI: Chrome / PWA
- Chat: Groq / openai/gpt-oss-120b
- STT: Groq Whisper via /api/stt
- TTS: Groq Orpheus; English autumn, Arabic noura
- Memory: .aip/ (SELF.md, USER.md, CONTEXT.md, MENTAL.md)
- Agent loop stays in frontend (F1)

--------------------------------------------------------------------------------
## 2. METHOD — SEE → UNDERSTAND → DESIGN → FREEZE → BUILD → VERIFY
--------------------------------------------------------------------------------

Frozen decisions F1-F10:
1. Agent loop stays in frontend
2. /api/chat is proxy-only
3. Each provider uses an adapter
4. Credentials stay server-side
5. memory6 over .aip is the single primary memory store
6. Path containment remains
7. Workspace/public/server roots defined
8. Local host stays on port 8080
9. Lane separation is permanent
10. Success is evidence-based

**Mechanic loop:** Observe → Diagnose → Propose → Explain why →
Green light → Backup → One bounded change → Verify → Report →
Team review → Next.

**Non-goals:** rewriting AIP, merging OpenCode into AIP, adding a
Puter dependency, adding random plugins/providers, historical
cleanup, style refactors, loosening security, a second memory store.

--------------------------------------------------------------------------------
## 3. TEAM AND LANES
--------------------------------------------------------------------------------

- Owner — driver, direction, final authority
- Julie — map, reasoning, architecture review, continuity
- Nadine — brakes, evidence, design, framing
- Artie — hands, OpenCode agent in Termux, works AIP

Shorthand: "Atria has the hands. We still have the judgment."

Lanes never mix:
- AIP lane:        ~/aip/
- OpenCode lane:   ~/.config/opencode/
- oc-tools lane:   ~/oc-tools/
- Research lane:   ~/research/, ~/puter-chat/, agent-reach/

--------------------------------------------------------------------------------
## 4. AIP BACKLOG — STATUS
--------------------------------------------------------------------------------

**12 CLOSED, 5 OPEN** as of 2026-10-10 (corrected — Artie caught a false all-closed claim).
B16 closed: §5.5 TTS chunks 5 → 8. Amendment in frozen design.
B17 closed: §5.3 history capped at 80 client-side. Amendment.
Both filed as OBS-2026-10-09-003.

Documented, not fixed: B6 historical file inventory; B8 filesystem
LIVE/HISTORICAL map. Cleanup needs a written plan (N6 rule).

B1 partial (TTS >1600 chars truncates). B2/B5/B6/B8 open or documented. See aip-truth.md for the real status.

--------------------------------------------------------------------------------
## 5. ENVIRONMENT (separate from AIP)
--------------------------------------------------------------------------------

Environment growth is NOT AIP architecture change. Bandr said:
"You're growing the environment, not changing AIP's architecture."

- Artie/Atria works directly on AIP
- CodeCraft agents handle coding
- API agents handle API work
- APK analysis is now a live Termux capability

**Tools installed:** Java 17, Java 21, apktool 3.0.3, jadx 1.5.6,
radare2 6.2.4, r2ghidra (Ghidra decompiler, compiled), wget 1.25.0.
APK: apktool d app.apk -o smali; jadx -d java app.apk;
r2 -qc "aaa; afl" path/to/binary.so

--------------------------------------------------------------------------------
## 6. OPENCODE PROVIDERS
--------------------------------------------------------------------------------

File: ~/.config/opencode/opencode.jsonc
Backup: ~/.config/opencode/opencode.jsonc.bak.3providers

1. Atria (Atria-Dawn-Preview) — 200M lifetime. Artie's engine.
2. CodeCraft (claude-sonnet-5, glm-5.3, gpt-5.6-terra) — pay/token.
3. APINex (free/deepseek-v4.1-flash etc.) — 1M raw/day, but
   WEIGHTED multiplier makes it useless for agent loops. Chat only.

Artie model line: ~/.config/opencode/agent/aip-fixer.md

--------------------------------------------------------------------------------
## 7. PUTER — WORKING FREE PATH
--------------------------------------------------------------------------------

Method: browser SDK (js.puter.com/v2/). NOT the API (402).
File: ~/puter-chat/index.html
Server: cd ~/puter-chat && python3 -m http.server 8000
Open: http://127.0.0.1:8000/?v=100

Working: 995 chat models, image gen, TTS, copy button, diag.
Cheap default: qwen-flash (~0.01 credits/msg).
Budget: 1000 credits/month. Save gpt-6-astra for hard tasks.

--------------------------------------------------------------------------------
## 8. REJECTED / DEAD (do not revisit)
--------------------------------------------------------------------------------

Puter API endpoint (402), CodeCraft DEVWEEK coupon (expired),
AgentRouter GitHub (anti-abuse reject), Top Tools AI (401),
TeamRouter (wallet required), Bytez (catalog empty), Featherless
(plan required), ToolMate (Python 3.14 incompatible).

Token Harbor — seen 2026-10-09/10. Free path is Webchat-only.
No key path worth chasing. Parked, not lost.

--------------------------------------------------------------------------------
## 9. KEYS — COMPROMISED, ROTATE
--------------------------------------------------------------------------------

Pasted into chats: OpenRouter, Hugging Face, Bytez, Atria, APINex.
Rule: NEVER paste keys in chat. Store only in ~/.secrets/providers.env.
That file does not exist yet. Create when keys are rotated.

--------------------------------------------------------------------------------
## 10. NEXT — PHASE 2
--------------------------------------------------------------------------------

Nothing on fire. Options when ready:
- Kaggle test bed for heavy features (music, video, image)
- ANNIE / ANNA — HTML → APK (Puter chat page already works)
- First real product feature — whatever AIP should do first

Nothing to do right now. Everything is on disk.


--------------------------------------------------------------------------------
## 11. MEMORY REPO — PRIVATE BACKUP
--------------------------------------------------------------------------------

Repo: https://github.com/bandralshargabi-art/AIs-MEMORY  (Private)
Local: ~/oc-tools/ai-memory/
Sync rule — after any LIFE/WORK edit:
  cd ~/oc-tools/ai-memory && git add . && git commit -m "update" && git push

--------------------------------------------------------------------------------
## 12. BOTKEEP — CLAIMED, EMPTY
--------------------------------------------------------------------------------

Signed up 2026-10-10 under bandralshargabi-art (GitHub OAuth).
Plan: Founder Free — 0€, free forever, no expiry. No card.
Capacity: 2 GB RAM, 1.5 vCore (150%), 2 GB storage, 5 server slots.
Current use: NONE. Empty box. Do not fill until a named need exists.

Offer window closed: 15 Oct 2026 17:00 Italy time. We made it.

**VPN note:** Signup only worked through a Germany exit node. Real IP
is region-blocked; other VPN locations tripped Cloudflare bot-check.
If login loops at Cloudflare, switch VPN to Germany.

**First candidate use:** serve sanitized memory files as a public URL
any AI can fetch. NOT LIFE.md — that stays private. Small Node app,
~20 lines. Not built yet.

--------------------------------------------------------------------------------
## 13. RULE — INSTALL ON SIGHT (Bandr, 2026-10-12)
--------------------------------------------------------------------------------

When we talk about a tool, the default is: install it now.

- Fits and installable → install immediately. Do not search, do not
  delay, do not ask "do we need it right now." Being there is better
  than not existing.
- Fits but timing is wrong → delay explicitly. Say when.
- Doesn't work on this device → forget it and move on. Don't keep
  re-discovering the same wall.

Why: we have lost time searching for tools we may or may not have
installed. The search is worse than the install. Work is waiting.

Do NOT apply this rule to anything that breaks the frozen design,
costs money, or touches AIP's architecture. Those still need the
brake and the green light. This rule is for small, self-contained,
additive tools — scripts, binaries, skills.

Bandr's words: "If it is already working and it can be installed
there is no contradiction doing both."

--------------------------------------------------------------------------------
## 15. THE INTERFACE — the desk (Bandr, 2026-10-13)
--------------------------------------------------------------------------------

The workshop is full. Termux already has everything:
Artie, OpenCode, dsh, Cline, FCC + Nemotron, yt-dlp, jadx,
apktool, radare2, the MCP server, the memory files, the character
mechanic, Go, proot Debian.

None of it is reachable from a chat box. Each one takes a command
line to use.

**What is missing:** a room to sit in. A manager's desk. A chat
box, and the correct buttons to reach everything in the workshop.

**His words:** "The manager sitting on his desk — he just needs
the correct buttons to bring whatever he wants to him and give it
the order to work."

**Shape:**
- Chat box — you type, the AI answers
- Buttons — one per capability in Termux
  (download, transcribe, run Artie, search files, check battery,
  take a photo, restart AIP, switch agent, switch model...)
- Output comes back to the desk
- You never open a terminal

**Sequence:**
1. Finish AIP (voice, memory auto-write, native shell)
2. Install the MCP server — workshop door
3. Build the interface on top — the desk

**Not now.** AIP first. This is noted so it survives.

--------------------------------------------------------------------------------
## 16. MOBILE AGENT + TERMUX MCP — WORKING (2026-10-14)
--------------------------------------------------------------------------------

**What it is:** a chat box that operates the phone. App → MCP → Termux.

**The pieces:**
- Mobile Agent app (TecnicalBot/mobile-agent, APK, installed)
- termux-mcp Go binary (TecnicalBot/termux-mcp v0.2.0)
  Installed via direct download with resume:
  curl -L -C - --retry 10 ... releases/download/v0.2.0/
  termux-mcp-v0.2.0-android-arm64
  Placed at $PREFIX/bin/termux-mcp

**Start the server:**
  termux-mcp serve http
  → listening addr=127.0.0.1:3000

**App config:**
  Label: Termux MCP
  URL: http://127.0.0.1:3000/mcp
  Auth: None (require: false in config)
  Result: 26 tools, 1 of 1 active

**Provider for the app:** Token Harbor custom:
  Base URL: https://tokenharbor.ai/v1
  Model: deepseek-v4.1-flash:free (or claude-haiku-5.5:free)
  Note: Haiku fabricates. DeepSeek does not. Use DeepSeek.

**Skills installed:** verification-before-completion, skill-creator

**Proven working:**
- `uname -a` → real kernel output (verified from Termux)
- read `~/workspace/.aip/SELF.md` → correct
- write `~/storage/downloads/mcp-test.txt` → real file, 24 bytes
- drive Artie: `opencode run --agent aip-fixer` from the app chat

**Also installed this session:**
- Universal-Termux-Toolkit (termuxbird) — cloned, deps installed
- Mirror switched to mirror.nyist.edu.cn (old one had a stale luajit)

**Still open:**
- Voice turn detection (D1 API is text-only)
- Sasha's memory auto-write
- The toolkit's first real download test (was interrupted)

**Correction for future sessions:** I gave the wrong `termux-mcp`
(PyPI) at first. The correct one is TecnicalBot's Go binary. Same
name, different author. Check the author.
