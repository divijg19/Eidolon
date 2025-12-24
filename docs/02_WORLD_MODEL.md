## How Reality Works in `Eidolon`

This document defines **the physical rules of *Arrhaknea***.  
Everything—agents, systems, AI, multiplayer—operates *inside* this model.

If an idea violates the rules in this file, it is not a feature.  
It is a contradiction.

---

## 1. World Instances

### 1.1 Definition

A **World Instance** is a single, authoritative simulation of *Arrhaknea*.

Each world instance has:
- A unique identifier
- A deterministic seed
- A global clock
- A persistent state store
- An ordered event history
- A set of active agents (NPCs, players, factions)

There is **no global meta-world**.  
Each instance is self-contained.

---

### 1.2 Authority

The world engine is the sole authority on:
- What exists
- What happens
- When it happens
- In what order it happens

Clients, AI systems, and players **submit intent**.  
The world decides what resolves.

---

## 2. Time Model

### 2.1 Discrete Time

Time in `Eidolon` advances in **discrete ticks**.

- One tick represents a fixed in-world duration (e.g. one hour)
- Tick duration is constant within a world instance
- Tick rate may differ between instances, but not within one

There is no real-time simulation drift.  
Time advances only through ticks.

---

### 2.2 World Clock

The world clock:
- Starts at world creation
- Advances one tick at a time
- Is monotonic (never rewinds under normal operation)

Rollback may occur only for:
- Crash recovery
- Debug replay
- Determinism verification

Rollback is never a gameplay mechanic.

---

## 3. Tick Lifecycle

Each tick executes in a **strict, deterministic order**.

### 3.1 Tick Phases

1. **System Phase**
   - Resource production and consumption
   - Economic updates
   - Population changes
   - Environmental effects

2. **Agent Planning Phase**
   - NPC belief updates
   - Goal reprioritization
   - Action intent generation
   - Player-submitted actions collected

3. **Resolution Phase**
   - Movement resolution
   - Trades executed
   - Conflicts resolved
   - Contracts enforced
   - Deaths applied

4. **Memory Phase**
   - Events recorded
   - Memories summarized
   - Emotional deltas applied
   - Information propagation scheduled

No phase may observe the results of a later phase.

---

### 3.2 Determinism Guarantee

Given:
- The same initial seed
- The same ordered inputs
- The same tick count

The world **must** reach the same state.

AI outputs are treated as **inputs** and must be:
- Validated
- Normalized
- Deterministically applied

---

## 4. Events

### 4.1 Event Definition

An **Event** is an immutable record of something that occurred.

Properties:
- Timestamp (tick number)
- Event type
- Involved agents
- Affected systems
- Canonical facts only

Events do not contain interpretation or emotion.

---

### 4.2 Event Ordering

Events are:
- Totally ordered within a tick
- Persisted before memory summarization
- Never deleted

Narrative interpretation happens later.

---

## 5. World State

### 5.1 Canonical State

The canonical world state includes:
- Geography
- Resources
- Ownership
- Agent status
- Faction control
- Active contracts and treaties

This state is:
- Objective
- System-owned
- Not directly visible to players in full

---

### 5.2 Perspective State

Each agent has a **perspective**:
- Partial view of the world
- Based on location, access, and information flow
- Possibly incorrect

Perspective is not authoritative.

---

## 6. Waiting

### 6.1 Waiting as a First-Class Action

Waiting is:
- A deliberate player action
- A valid NPC strategy
- A system-level concept

Waiting allows:
- Information to propagate
- Situations to resolve
- Pressure to accumulate

There is no penalty for waiting other than consequence.

---

### 6.2 World Waiting (Time Stall)

The world clock may **pause** only under strict conditions:
- A causal lock is active (see Multiplayer)
- A critical irreversible action requires acknowledgment
- Administrative intervention (debug/testing)

World waiting is global and visible.

---

## 7. Absence

### 7.1 Player Absence

If a player is absent:
- The world continues
- NPCs act
- Systems progress
- Consequences accumulate

Absence is not protected.

---

### 7.2 NPC Absence

NPCs do not “sleep” unless systemically required.
They always exist as agents, even if not simulated at full fidelity.

---

## 8. Irreversibility

### 8.1 Irreversible Actions

Some actions permanently alter the world:
- Death
- War declarations
- Territory loss
- Institutional collapse

These actions:
- Cannot be undone
- May trigger causal locks
- Are clearly marked before confirmation

---

### 8.2 Soft vs Hard Irreversibility

- **Hard**: Cannot be reversed (death)
- **Soft**: Can be countered, but not erased (reputation damage)

The system distinguishes between the two.

---

## 9. Failure States

The world does not end because:
- A player loses power
- A faction collapses
- A city falls

The world ends only if:
- No agents remain capable of action
- Systemic collapse renders progression impossible
- The instance is explicitly terminated

Collapse is a valid outcome.

---

## 10. Design Guarantees

This world model guarantees that:
- Time matters
- Order matters
- Actions are bounded
- Information is imperfect
- Consequences persist

If a mechanic violates any of these, it must be rejected or redesigned.

---

## 11. Final Statement

*Arrhaknea* is not reactive scenery.

It is a **machine under pressure**, advancing one tick at a time.

You do not pause it by existing.  
You do not control it by acting once.

You influence it only by:
- committing,
- waiting,
- and accepting what the next tick brings.
