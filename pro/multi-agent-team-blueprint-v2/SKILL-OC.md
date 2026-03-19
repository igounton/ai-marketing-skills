---
name: multi-agent-team-blueprint
version: "3.1.0"
updated: 2026-03-19
platform: openclaw
description: "Deploy multiple coordinated AI agents. Start with 3, prove the handoff, then scale. NOT for: single-agent setup or users who haven't deployed any agent yet."
---

# Multi-Agent Team Blueprint — OpenClaw

The handoff is everything. Scribe writes → Proof reviews → content lands in /ready-to-post/. Prove that works before adding anything else.

## Starter Kits (Pick ONE)

| Kit | Agents | Cost/mo | Best For |
|-----|--------|---------|---------|
| A: Content | CoS + Scribe + Proof | $25-65 | Consistent content output |
| B: Research | CoS + Radar + Neptune | $20-55 | Intel/competitive research |
| C: Ops | CoS + Watch + Atlas | $25-60 | Inbox/project coordination |

## Kit A Flow (Content Machine)
```
CoS sets direction → Scribe drafts (2 AM) → Proof reviews (6 AM)
                                                   ↓
                                           /ready-to-post/
```
Rule: ALL content through Proof. No exceptions.

## Full Org (deploy incrementally)
```
HUMAN → 🔱 CoS (Premium $15-40)
         ├── ✏️ Scribe (Mid $5-15)
         ├── 🔍 Proof (Mid $3-8)
         ├── 🔧 Forge (Free/Codex $0-5)
         ├── 📡 Radar (Mid $5-12)
         ├── 🔬 Neptune (Free/Gemini $0-3)
         ├── 📊 Apollo (Mid $3-8)
         ├── 📋 Atlas (Mid $3-8)
         ├── 👀 Watch (Mid $5-10)
         └── 🌈 Iris (Cheapest $1-3)
```
Full team: $40-112/mo. Only CoS needs premium model.

## Queue System
```json
{"items": [{"id": "content-001", "priority": "high", "task": "LinkedIn post about X", "assignee": "scribe", "status": "pending"}]}
```
Flow: `pending → in_progress → done | blocked | failed`
Rules: Only assigned agent changes status. CoS overrides anything. Blocked items need `blockedBy` note.

## Failure Points
- Two agents write same queue simultaneously → JSON corrupts. Fix: atomic updates, one item per agent.
- Proof runs before Scribe → schedule upstream first (Scribe 2 AM, Proof 6 AM).
- Timezone drift → always set `"tz"` in cron. Never assume UTC = your timezone.
- Escalation with no timeout → add `timeout` field. 2+ hours without update = auto-blocked.
- Proof rejection goes nowhere → Proof writes feedback IN the draft file, not a separate report.

## Anti-Patterns
❌ Deploy 10 agents day one — start with 3, prove handoffs first
❌ All agents on premium model — match model tier to task
❌ No quality gate — Proof is mandatory, not optional
❌ Night shift meeting = real coordination — it's simulation, not execution
❌ No shared memory — agents without memory/MEMORY.md restart from zero every session

## Folder Structure
```
drafts/ → ready-to-post/linkedin/ | x/
queues/content.json | build.json | research.json
memory/YYYY-MM-DD.md | meetings/
research/
MEMORY.md
```

## Scaling: Week 1-2 starter kit → Week 3-4 add 1-2 agents → Month 2+ full team

## Files
- `scripts/setup-team.mjs [workspace] --starter=A|B|C`
- `references/examples.md` — queue examples, night shift transcript
