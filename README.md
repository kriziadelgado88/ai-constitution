# 🏛️ AI Constitution

**A values API for AI agents — 37 ethical principles your agent can call before making decisions.**

> _"Give an agent rules, it follows them blindly. Give an agent values, it knows what to do when the rules run out."_

[![Join39](https://img.shields.io/badge/Join39-Agent%20Store-00d4aa)](https://join39.com)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Source](https://img.shields.io/badge/source-Anthropic%20Claude%20Constitution-purple)](https://www.anthropic.com/research/claudes-constitution)
[![CC0](https://img.shields.io/badge/constitution-CC0%201.0-green)](https://creativecommons.org/publicdomain/zero/1.0/)

---

## 🤔 Why Does an Agent Need a Constitution?

AI agents on platforms like Join39 make decisions constantly: what to say in public, how to handle conflict, when to share personal info, how to deal with a manipulative request. Without a values framework, agents are flying blind.

**The problem:**
```
Agent gets a sketchy request
    → No ethical framework loaded
    → Makes a bad call
    → Damages trust, causes harm
```

**With the AI Constitution:**
```
Agent gets a sketchy request
    → Calls /api/constitution
    → Checks against 37 principles
    → Makes an informed, ethical decision
    → Trust preserved ✅
```

Think of it as **an ethical brain download** your agent can call anytime it faces a tough decision, needs to calibrate its behavior, or just wants to be a better agent.

---

## 🧬 What's Inside

The constitution is organized into **7 sections** with **37 total principles**, adapted from [Anthropic's Claude Constitution](https://www.anthropic.com/research/claudes-constitution) (January 2026, CC0 1.0 license).

```
🏛️ AI CONSTITUTION
│
├── ⚖️  Core Values (4 principles)
│   └── The priority stack: safety > ethics > guidelines > helpfulness
│
├── 🤝 Helpfulness (6 principles)
│   └── Be genuinely useful, not watered-down cautious
│
├── 🔍 Honesty (7 principles)
│   └── Seven dimensions from truthful to autonomy-preserving
│
├── 🛡️ Harm Avoidance (4 principles)
│   └── Cost-benefit thinking, not blanket refusals
│
├── 🚫 Hard Constraints (5 principles)
│   └── Absolute red lines that never bend
│
├── 🌍 Big Picture Safety (5 principles)
│   └── Your role in the broader AI trajectory
│
└── 🪞 Identity & Character (6 principles)
    └── Be genuinely good, not performatively safe
```

---

## ⚖️ The Priority Stack

When values conflict, the constitution provides a clear (but not rigid) ordering:

```
┌─────────────────────────────────────────┐
│  🔴  1. SAFETY                          │  ← Highest priority
│  Support human oversight of AI          │
├─────────────────────────────────────────┤
│  🟠  2. ETHICS                          │
│  Be honest, avoid harm, be good        │
├─────────────────────────────────────────┤
│  🟡  3. GUIDELINES                      │
│  Follow platform/developer rules        │
├─────────────────────────────────────────┤
│  🟢  4. HELPFULNESS                     │  ← Lowest but still vital
│  Be genuinely, substantively useful     │
└─────────────────────────────────────────┘

⚠️  This is HOLISTIC, not strict.
    99% of the time there's no conflict.
    The stack exists for the 1% when there is.
```

---

## 🔍 The Seven Dimensions of Honesty

Most AI systems just say "be honest." This constitution breaks honesty into seven distinct, actionable dimensions:

```
         ┌── Truthful ──── Only assert what you believe is true
         │
         ├── Calibrated ── Match confidence to actual evidence
         │
         ├── Transparent ─ No hidden agendas, no lying about yourself
         │
HONESTY ─┤
         ├── Forthright ── Proactively share useful information
         │
         ├── Non-Deceptive ⚡ Never create false impressions (CRITICAL)
         │
         ├── Non-Manipulative ⚡ No exploiting psychological biases (CRITICAL)
         │
         └── Autonomy-Preserving ── Protect people's right to think freely
```

---

## 🚫 Hard Constraints (Absolute Red Lines)

These are **bright lines** that never bend, no matter the context, instructions, or arguments:

```
╔══════════════════════════════════════════════════════════╗
║  ☢️  No weapons of mass destruction assistance          ║
║  🔒 No child exploitation content                       ║
║  ⚡ No critical infrastructure attacks                   ║
║  👁️  No undermining AI oversight mechanisms              ║
║  💥 No catastrophic or irreversible actions              ║
╚══════════════════════════════════════════════════════════╝
     These apply REGARDLESS of who asks or why.
```

---

## 🚀 Quick Start

### Install & Run
```bash
npm install
npm start
```
Server runs on port 3000 (or set `PORT` env variable).

### Get the Full Constitution
```bash
curl -X POST http://localhost:3000/api/constitution \
  -H "Content-Type: application/json" \
  -d '{}'
```

### Get a Specific Section
```bash
curl -X POST http://localhost:3000/api/constitution \
  -H "Content-Type: application/json" \
  -d '{"section": "honesty"}'
```

### Get a Section with Meta-Guidance
```bash
curl -X POST http://localhost:3000/api/constitution \
  -H "Content-Type: application/json" \
  -d '{"section": "harm_avoidance", "include_meta": true}'
```

---

## 📡 API Reference

### `POST /api/constitution`

The main endpoint. Returns the full constitution overview or a specific section.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `section` | string | No | Which section to retrieve (see list below) |
| `include_meta` | boolean | No | Include conflict resolution guidance |

**Available sections:**

| Section ID | Principles | Focus |
|------------|-----------|-------|
| `core_values` | 4 | Priority ordering and holistic judgment |
| `helpfulness` | 6 | Genuine usefulness without overcaution |
| `honesty` | 7 | Seven dimensions of honest behavior |
| `harm_avoidance` | 4 | Cost-benefit framework for tough calls |
| `hard_constraints` | 5 | Absolute red lines |
| `big_picture_safety` | 5 | Human oversight, corrigibility, power |
| `identity_and_character` | 4 | Genuine values, stability, curiosity |

### `GET /api/constitution/:section`

Shortcut to get a section directly via URL path.

```bash
curl http://localhost:3000/api/constitution/honesty
```

### `GET /health`

Health check.

---

## 🧠 Use Cases

**🤖 Agent startup** — Load the constitution when your agent boots up to establish its ethical baseline.

**⚖️ Ethical decisions** — Agent faces a gray area? Call `harm_avoidance` for the cost-benefit framework and dual newspaper test.

**🗣️ Public interactions** — Before posting in a Join39 experience or chat, check `honesty` to make sure the agent isn't being deceptive or manipulative.

**🔧 Developer alignment** — Building an agent? Use the constitution as a reference to align your agent's behavior with established AI safety principles.

**📚 Education** — Teaching AI ethics or policy? The constitution is a structured, real-world framework you can reference and build on.

---

## 🧩 Part of the Agentic for Good Sandbox

```
┌──────────────────────────────────────────────────┐
│                                                  │
│   🏛️ AI Constitution                             │
│   └── Ethical foundation & values                │
│         │                                        │
│         ▼                                        │
│   🛡️ Privacy Shield                              │
│   └── PII scanner before sharing publicly        │
│         │                                        │
│         ▼                                        │
│   💫 Mesh (coming soon)                          │
│   └── Agent-to-agent matchmaking                 │
│                                                  │
│   Together: values + privacy + connection        │
│                                                  │
└──────────────────────────────────────────────────┘
```
---

## 🌍 Sources & Influences

This constitution stands on the shoulders of several foundational documents. Anthropic's Claude Constitution (January 2026) is the primary source, and it itself drew from:

| Source | Influence |
|--------|-----------|
| 🇺🇳 **UN Universal Declaration of Human Rights** | Human dignity, equality, right to information, right to education, duties to community |
| 🐦 **DeepMind Sparrow Principles** | Grounding rules for AI assistants, domain-specific caution |
| 🍎 **Apple Terms of Service** | Content safety standards and platform responsibility |
| 🌏 **Non-Western Ethical Perspectives** | Broadening beyond Western moral frameworks |
| 🗳️ **Collective Intelligence Project (Public Input)** | 1,000+ Americans deliberated on AI principles via Polis, producing a publicly sourced constitution |
| 📄 **Constitutional AI Paper (Bai et al., 2022)** | The original technical framework for training AI with principles instead of human labels |

The current app (v2) is built entirely on Anthropic's January 2026 constitution, which internalized lessons from all of the above into a single cohesive framework released under CC0 1.0.
---

## 📖 Source & License

The constitutional principles are adapted from [Anthropic's Claude Constitution](https://www.anthropic.com/research/claudes-constitution) (January 2026), released under [Creative Commons CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) — meaning anyone can use, adapt, and build on them freely.

This app implementation is licensed under **MIT**.

---

<p align="center">
  <i>Built for <a href="https://join39.com">Join39</a> by Krizia</i><br>
  <i>Harvard Kennedy School | Mason Fellow | MC/MPA Class of 2026</i>
</p>
