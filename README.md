# Eidolon
### A Living-World GenAI RPG set in *Arrhaknea*

**`Eidolon`** is a systems-driven role-playing game where the world is not scripted, quests are not authored, and destiny is not assigned.

Set in the fractured continent of ***Arrhaknea***, `Eidolon` simulates a living world of people, factions, economies, and conflicts that evolve continuously—whether the player intervenes or not. Narrative emerges from **pressure, choice, and consequence**, not from predefined storylines.

This project explores what happens when:
- NPCs are autonomous agents with memory and goals
- The world advances in time regardless of player presence
- Multiple players can coexist in the same unfolding reality
- Generative AI is used for *reasoning and interpretation*, not authority

`Eidolon` is not a traditional RPG.  
It is a **persistent simulation of human ambition under constraint**.

---

## Core Principles

- **Systems First**  
  Deterministic world systems define what is possible. AI operates strictly within those boundaries.

- **No Prescribed Destiny**  
  There is no main quest, no optimal path, and no guaranteed outcome.

- **Persistent Consequence**  
  Actions accumulate. Waiting is meaningful. Absence has effects.

- **Subjective Reality**  
  Information is local, delayed, and biased. Memory is incomplete.

- **Shared Fate (Optional Multiplayer)**  
  Multiple players may inhabit the same world, negotiate decisions, and stall time when destinies intersect—similar to a tabletop RPG played together over a call.

---

## What `Eidolon` Is Not

- ❌ A scripted RPG with branching dialogue trees  
- ❌ A content-generation sandbox  
- ❌ A power fantasy or progression grind  
- ❌ An MMO  

`Eidolon` does not guide the player toward success.  
It responds to what the player attempts to build.

---

## The World of *Arrhaknea*

*Arrhaknea* is a continent shaped by:
- Fallen empires and surviving institutions
- Rival city-states and trade networks
- Political factions competing for legitimacy
- Religious orders guarding selective truths
- Peripheral regions where power is unstable

Nothing here is static.  
Stability itself is something to be created—or dismantled.

---

## Gameplay Overview

At a high level, play consists of:

```

Assess the current world state
↓
Choose an action (travel, negotiate, trade, influence, fight, wait)
↓
Agents update beliefs and plans
↓
World systems advance in time
↓
Consequences propagate
↓
New pressures emerge

```

There are no quest markers.  
Only situations.

---

## Shared Fate Mode (Multiplayer)

`Eidolon` supports an optional multiplayer mode where:
- All players inhabit the same world instance
- Each player has their own character, goals, and interface
- Time advances globally
- Certain irreversible actions trigger **causal locks**, pausing the world until affected players respond

This mode is designed to mirror how tabletop RPGs are played socially:
- Players discuss choices externally (voice/video call)
- The game enforces consequences and consistency
- Cooperation, disagreement, and delay are all meaningful

The world acts as the dungeon master.

---

## Technical Overview

`Eidolon` is built with a strict separation of concerns:

- **Go** — Authoritative world simulation  
  - Time progression  
  - Economy, factions, combat  
  - Event resolution  
  - Multiplayer synchronization  

- **Python** — AI reasoning layer  
  - NPC decision-making  
  - Memory summarization  
  - Belief updates  
  - Dialogue generation  

- **Persistence**  
  - Relational database for canonical world facts  
  - Vector store for subjective memory  

Clients (TUI / 2D UI) are **views**, not sources of truth.

---

## Repository Structure (High-Level)

```

`Eidolon`/
├── cmd/            # Entrypoints
├── internal/       # World engine, systems, agents
├── ai/             # AI reasoning service & prompts
├── client/         # Player interfaces
├── docs/           # Canonical design documentation
└── scripts/        # Dev & tooling scripts

```

Detailed architecture is documented in `/docs`.

---

## Documentation

All design decisions are formalized and ordered in `/docs`:

1. Vision & non-negotiables  
2. World model & time  
3. Agent system  
4. Core systems  
5. Memory & subjectivity  
6. Multiplayer (Shared Fate)  
7. AI boundaries  
8. Architecture  
9. Roadmap  

If code conflicts with documentation, the documentation takes precedence.

---

## Project Status

**Early development / architectural phase**

Current focus:
- Core world simulation
- Deterministic systems
- Agent models
- Memory and consequence propagation

Visual fidelity and content density come later.

---

## Closing

**Arrhaknea** does not offer a path.

It offers leverage, risk, and opportunity.

What you carve out of it—  
power, wealth, influence, peace, obscurity, or collapse—  
is not decided for you to experience, but to build yourself.

`Eidolon` shapes who you want to be, balanced against the slope of **what you are willing to pursue, and what you are willing to lose.**

---

Dedicated to the Highlanders. With apologies and condolences.
