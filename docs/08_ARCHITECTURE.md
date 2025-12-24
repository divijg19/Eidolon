## How the System Fits Together

This document describes **how `Eidolon` is built**, end to end, translating intent into structure.

---

## 1. Architectural Principles

`Eidolon`’s architecture adheres to the following principles:

- **Single Authority**  
  There is exactly one authoritative source of world state.

- **Separation of Concerns**  
  Simulation, cognition, and presentation are isolated.

- **Determinism First**  
  Given the same inputs, the world must resolve identically.

- **Replaceability**  
  AI models, clients, and storage backends must be swappable.

- **Persistence by Default**  
  Worlds are long-lived and continuously saved.

If a component violates these principles, it is incorrectly placed.

---

## 2. High-Level Overview

```

┌──────────────────────────────┐
│          Client(s)           │
│   (TUI / 2D / Remote)        │
└───────────────┬──────────────┘
↓
┌──────────────────────────────┐
│   World Engine (Go)          │
│   - Time & ticks             │
│   - Systems                  │
│   - Event resolution         │
│   - Multiplayer locks        │
└───────────────┬──────────────┘
↓
┌──────────────────────────────┐
│   AI Service (Python)        │
│   - NPC reasoning            │
│   - Planning                 │
│   - Memory summarization     │
└───────────────┬──────────────┘
↓
┌──────────────────────────────┐
│   Persistence Layer          │
│   - Postgres (facts/events)  │
│   - Vector DB (memory)       │
└──────────────────────────────┘

```

All arrows represent **data flow**, not authority transfer.

---

## 3. World Engine (Go)

### 3.1 Responsibilities

The world engine is responsible for:
- World creation and seeding
- Tick progression
- System execution
- Event ordering and persistence
- Validation of all intent
- Multiplayer synchronization

Nothing else mutates world state.

---

### 3.2 Core Modules

- `world/`  
  World lifecycle, clock, snapshots

- `agents/`  
  Agent state models (player, NPC, faction)

- `systems/`  
  Economy, factions, combat, information, law

- `events/`  
  Event definitions, queues, causal locks

- `multiplayer/`  
  Session management, lock coordination

- `persistence/`  
  Event sourcing, snapshots, recovery

---

### 3.3 Event-Sourced Core

All state changes occur through:
1. Validated intent
2. Event generation
3. Event application
4. Snapshot update

Snapshots are derivatives.  
Events are truth.

---

## 4. AI Service (Python)

### 4.1 Role

The AI service provides **cognitive assistance** only.

It:
- Never writes to world state directly
- Never resolves outcomes
- Never advances time

It returns **proposals**.

---

### 4.2 Communication Pattern

- World engine sends:
  - Agent context (limited)
  - Relevant memories
  - Current goals
  - Recent events

- AI service returns:
  - Proposed intents
  - Belief updates
  - Memory summaries
  - Dialogue text

All outputs are validated by the world engine.

---

### 4.3 Statelessness

The AI service is:
- Logically stateless
- Restartable
- Replaceable

Long-term memory lives in persistence, not in process.

---

## 5. Persistence Layer

### 5.1 Canonical Storage (Relational)

Stores:
- World metadata
- Agents
- Factions
- Events
- Contracts and treaties

Properties:
- Transactional
- Append-only where possible
- Replayable

---

### 5.2 Memory Storage (Vector)

Stores:
- Narrative memory embeddings
- Emotional summaries
- Relationship impressions

This store is:
- Non-authoritative
- Loss-tolerant
- Rebuildable from events

---

## 6. Clients

### 6.1 Client Role

Clients are:
- Views into the world
- Input devices for intent
- Perspective-limited

Clients never:
- Resolve actions
- Modify world state
- Bypass validation

---

### 6.2 Client Types

- Terminal UI (v0.1)
- 2D client (v0.2+)
- Remote client (future)

All clients speak the same intent/query protocol.

---

## 7. Multiplayer Architecture

### 7.1 Sessions

A multiplayer session:
- Maps players to a world instance
- Manages connections
- Coordinates locks

Sessions do not duplicate state.

---

### 7.2 Causal Locks

Causal locks are enforced at the world engine level.

Locks:
- Pause world time
- Block conflicting intents
- Require resolution before progression

Clients are notified but do not arbitrate.

---

## 8. Failure and Recovery

### 8.1 Crash Recovery

On crash:
- Reload latest snapshot
- Replay events
- Resume tick progression

No player action is lost.

---

### 8.2 AI Failure

If AI is unavailable:
- NPCs act conservatively
- Systems continue
- World remains valid

Silence is preferable to corruption.

---

## 9. Testing and Verification

Testing focuses on:
- Determinism
- Replay accuracy
- Event ordering
- Lock correctness
- System stability under load

AI outputs are tested for:
- Schema validity
- Constraint compliance
- Boundedness

---

## 10. Extension Points

The architecture explicitly supports:
- New systems
- New agent types
- New AI models
- New client UIs
- New persistence backends

Extensions must not weaken authority boundaries.

---

## 11. Design Guarantees

This architecture guarantees:
- Single source of truth
- Long-lived worlds
- Replaceable cognition
- Multiplayer without dilution
- Maintainability over years

If a shortcut compromises these guarantees, it is not worth taking.

---

## 12. Final Statement

`Eidolon` is not held together by clever prompts or UI tricks.

It is held together by:
- strict authority,
- slow time,
- persistent state,
- and bounded intelligence.

Everything else is negotiable.
