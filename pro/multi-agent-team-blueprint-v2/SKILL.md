---
name: multi-agent-team-blueprint
version: "3.1.0"
updated: 2026-03-19
changelog: "v3.1 — Vibe Skill Creator rebuild: expert voice, friction removed, anti-patterns added"
price: "$19"
author: "@BrianRWagner"
type: persona
slug: "brw-multi-agent-team-blueprint"
description: "Use when: user wants to build a multi-agent AI system, deploy multiple coordinated AI agents, set up overnight autonomous agent operations, or scale beyond a single AI assistant. Triggers: 'build a team of agents', 'multi-agent setup', 'AI content pipeline', 'agents that work while I sleep'. NOT for: single-agent setup (use Chief of Staff skill), simple task automation, or users who haven't deployed at least one agent yet."
---

> **Works with OpenClaw, Claude Code, Cursor, and any AI that accepts markdown instructions.**
> Start with one starter kit. Have agents running tonight.

---

# Multi-Agent Team Blueprint

One agent is an assistant. Three agents are a system. Ten agents are a company.

But here's what nobody tells you: most people who try to build a 10-agent system fail, and they fail in the first week. Not because the architecture is hard — because they deploy everything at once and nothing works together.

The teams that actually run? They started with 3 agents, proved the handoff pattern, then scaled. This blueprint gives you the architecture for 10, but forces you to start with 3. Because the handoff — one agent's output becoming another's input — is the only thing that matters.

---

## The One Thing That Makes Multi-Agent Work

It's not the org chart. It's not the cron schedules. It's not the model routing.

**It's the handoff.**

Scribe writes a draft → Proof reviews it → approved content lands in `/ready-to-post/`. If that handoff works reliably, you have a system. If it doesn't, you have 3 agents running independently and calling it "coordination."

**Every system you build should prove one handoff before adding another agent.**

---

## ⚠️ The Real Failure Points

These aren't theoretical — they're what actually breaks:

**Queue corruption.** Two agents write to the same JSON file simultaneously → broken JSON → both agents fail silently. Fix: Each agent reads the queue, updates ONLY its own items, writes back immediately. Never let two agents own the same queue.

**Scheduling order.** Proof runs at 9 PM. Scribe runs at 2 AM. Proof reviews an empty folder and reports "nothing to review." Fix: Think about it like a factory — upstream agent runs first, downstream agent runs after. Scribe (2 AM) → Proof (6 AM). Always.

**The subscription surprise.** A full 10-agent team needs Anthropic + OpenAI + Google subscriptions. That's $60-100/month minimum before the agents do anything. Fix: Start with Kit A (3 agents, ~$25-65/month). Prove value before adding cost.

**Timezone drift.** Your server is UTC. You set "9 AM." That's 4 AM or 5 AM ET depending on daylight saving. Fix: Always specify timezone in cron configs. `"tz": "America/New_York"` — never assume UTC matches your timezone.

**Escalation to nowhere.** Agent "escalates to Chief of Staff" but CoS isn't running. Item sits in limbo forever. Fix: Every queue item needs a timeout — if `in_progress` for >2 hours without update, auto-flag as `blocked`.

**Proof rejection dead end.** Proof rejects a draft but writes the feedback to a separate report Scribe never reads. Fix: Proof writes rejection notes directly into the draft file. Scribe reads drafts before writing — it'll see the feedback.

---

## Start Here: Pick Your Kit

Don't read the full org chart first. Pick the 3-agent kit that matches your biggest need and deploy it tonight.

### Kit A: Content Machine
**You need this if:** You want consistent content output without writing everything yourself.

```
Chief of Staff (you) → Scribe (drafts at 2 AM) → Proof (reviews at 6 AM)
                                                      ↓
                                              /ready-to-post/
```

**Agents:**
| Agent | Model | Monthly Cost | Job |
|-------|-------|-------------|-----|
| 🔱 Chief of Staff | Premium (Opus/GPT-4) | $15-40 | Strategy, direction, delegation |
| ✏️ Scribe | Mid-tier (Sonnet/GPT-4o) | $5-15 | Draft content from queue |
| 🔍 Proof | Mid-tier | $3-8 | Quality gate — nothing ships unreviewed |

**Rule:** ALL content goes through Proof. No exceptions. Ever.

**Cron — Scribe (2 AM ET):**
```json
{
  "name": "Scribe Daily Content",
  "schedule": {"kind": "cron", "expr": "0 6 * * *", "tz": "America/New_York"},
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "You are Scribe — Content Writer. Read the content queue at queues/content.json. Draft 2-3 posts based on pending items. Save each draft to drafts/ with descriptive filenames. Mark items as 'in_progress' in the queue. Follow brand voice guidelines if available.",
    "model": "anthropic/claude-sonnet-4-20250514"
  },
  "delivery": {"mode": "announce"}
}
```

**Cron — Proof (6 AM ET):**
```json
{
  "name": "Proof Evening Review",
  "schedule": {"kind": "cron", "expr": "0 10 * * *", "tz": "America/New_York"},
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "You are Proof — Editor/QA. Check drafts/ for pending content. For each piece: (1) Check voice consistency (2) Evaluate hook strength (3) Verify specifics over vague claims (4) Check platform formatting (5) Rate 1-10. Score 7+ → move to ready-to-post/. Below 7 → write specific feedback directly in the draft file. Save review notes.",
    "model": "anthropic/claude-sonnet-4-20250514"
  },
  "delivery": {"mode": "announce"}
}
```

### Kit B: Research Engine
**You need this if:** You need competitive intel, market research, or daily industry scanning.

```
Chief of Staff → Radar (daily scan at 9:30 AM) → Neptune (deep dives on-demand)
                                                       ↓
                                                  /research/
```

**Agents:**
| Agent | Model | Monthly Cost | Job |
|-------|-------|-------------|-----|
| 🔱 Chief of Staff | Premium | $15-40 | Direction, synthesis |
| 📡 Radar | Mid-tier | $5-12 | Daily surface scan — news, trends, competitor moves |
| 🔬 Neptune | Free (Gemini/Perplexity) | $0-3 | Deep dives when Radar flags something |

### Kit C: Operations Hub
**You need this if:** You're drowning in inbox, tasks, and project coordination.

```
Watch (monitors inbox) → Chief of Staff → Atlas (tracks projects)
        ↓                                        ↓
   alerts for urgent                      daily ops report
```

**Agents:**
| Agent | Model | Monthly Cost | Job |
|-------|-------|-------------|-----|
| 🔱 Chief of Staff | Premium | $15-40 | Coordination, morning brief |
| 👀 Watch | Mid-tier | $5-10 | Inbox monitoring, urgent alerts |
| 📋 Atlas | Mid-tier | $3-8 | Task tracking, dashboards |

---

## Scaling: When to Add More Agents

**Week 1-2:** Run your starter kit. Fix the handoffs. Get reliable output.

**Week 3-4:** Prove value — are the agents producing things you actually use? If yes, add 1-2 more agents. If not, fix the existing ones before scaling.

**Month 2+:** Consider the full team.

### The Full Org Chart (deploy incrementally, not all at once)

```
HUMAN (CEO)
  └── 🔱 Chief of Staff — Premium model ($15-40)
        ├── ✏️ Scribe — Mid-tier ($5-15)
        ├── 🔧 Forge — Free/Codex ($0-5)
        ├── 🔍 Proof — Mid-tier ($3-8)
        ├── 📡 Radar — Mid-tier ($5-12)
        ├── 🔬 Neptune — Free/Gemini ($0-3)
        ├── 📊 Apollo — Mid-tier ($3-8)
        ├── 📋 Atlas — Mid-tier ($3-8)
        ├── 👀 Watch — Mid-tier ($5-10)
        └── 🌈 Iris — Cheapest ($1-3)
```

**Full team: $40-112/month** — vs. $200+ if everything ran on premium. Only 1 agent needs the expensive model.

---

## Queue System (How Agents Talk to Each Other)

Agents communicate through JSON files. No fancy infrastructure — just files.

```json
{
  "items": [
    {
      "id": "content-001",
      "priority": "high",
      "task": "LinkedIn post about AI discoverability",
      "assignee": "scribe",
      "status": "pending",
      "createdAt": "2026-03-01T10:00:00Z"
    }
  ]
}
```

**Status flow:** `pending` → `in_progress` → `done` / `blocked` / `failed`

**Rules:**
- Any agent can ADD items
- Only the assigned agent changes status
- Chief of Staff can override anything
- `blocked` items need a `blockedBy` note
- `failed` items need an `error` note

---

## Folder Structure

```
workspace/
├── drafts/              ← Scribe writes here
├── ready-to-post/       ← Proof approves to here
│   ├── linkedin/
│   └── x/
├── queues/
│   ├── content.json
│   ├── build.json
│   └── research.json
├── research/            ← Radar + Neptune output
├── memory/              ← Shared memory across agents
│   ├── YYYY-MM-DD.md
│   └── meetings/
└── MEMORY.md            ← Long-term agent memory
```

---

## Anti-Patterns (What Kills Multi-Agent Systems)

❌ **Deploy 10 agents on day one.** You'll spend all your time debugging coordination instead of getting value. Start with 3.

❌ **All agents on premium model.** Chief of Staff needs judgment. Scribe needs creativity. Forge needs free Codex. Neptune needs free Gemini. Match cost to task.

❌ **No quality gate.** Without Proof, AI content ships unreviewed. Every team needs an editor agent. No exceptions.

❌ **Treating the night shift meeting as real coordination.** The meeting template spawns a single session playing all roles — it's a simulation, not actual agent coordination. Useful for ideation. Not a substitute for real handoffs.

❌ **No shared memory.** Agents without memory start from zero every session. Set up daily notes + MEMORY.md before anything else.

❌ **Ignoring cost.** Track monthly spend per agent. An agent that costs $15/month and produces nothing is worse than no agent.

❌ **Over-engineering before proving basics.** If Scribe → Proof doesn't work reliably, adding Radar and Neptune won't help. Fix the foundation first.

---

## Meetings (Optional, Powerful)

Human says: "Call a meeting with Scribe and Proof about the content calendar."

Chief of Staff spawns an isolated session, plays all roles, produces a transcript. Useful for:
- Planning content direction
- Resolving conflicting priorities
- Night shift planning (2 AM cron)

**Meetings are simulations, not real multi-agent coordination.** The transcript is the value — use it for planning, not execution.

---

## Quality Checklist

Before deploying any agent:
- [ ] Does it have a clear input (queue, folder, or trigger)?
- [ ] Does it have a clear output (where does the work go)?
- [ ] Is the handoff to the next agent obvious?
- [ ] Is it on the right model tier?
- [ ] Does the cron schedule run AFTER its upstream agent?
- [ ] Is the timezone set correctly?

---

*Multi-Agent Team Blueprint v3.1.0 — Part of the AI Marketing Skills library by Brian Wagner (@BrianRWagner)*
*Works with: OpenClaw, Claude Code, Cursor, GitHub Copilot, VS Code Copilot*
