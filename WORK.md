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

**ALL 17 CLOSED** as of 2026-10-09/10.
B16 closed: §5.5 TTS chunks 5 → 8. Amendment in frozen design.
B17 closed: §5.3 history capped at 80 client-side. Amendment.
Both filed as OBS-2026-10-09-003.

Documented, not fixed: B6 historical file inventory; B8 filesystem
LIVE/HISTORICAL map. Cleanup needs a written plan (N6 rule).

**AIP backlog is finished.** Foundation complete.

--------------------------------------------------------------------------------
## 5. ENVIRONMENT (separate from AIP)
--------------------------------------------------------------------------------

Environment growth is NOT AIP architecture change. The Owner said:
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
