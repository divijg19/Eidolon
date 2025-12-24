## Who Acts in the World

This document defines **what an agent is** in `Eidolon` and how agency operates under constraint.

All meaningful action in *Arrhaknea*—human or otherwise—originates from agents.  
Players are not exceptions. NPCs are not props.

If something acts, it is an agent.  
If it is not an agent, it does not act.

---

## 1. Definition of an Agent

An **Agent** is any entity capable of:
- holding state,
- forming intent,
- and causing change in the world.

Agents do not act freely.  
They act **within systems, scarcity, and time**.

All agents share a common conceptual interface, regardless of type.

---

## 2. Agent Types

### 2.1 Player Agents
Represent human players.

Characteristics:
- Intent originates externally (player input)
- Beliefs are player-controlled
- Knowledge is limited by perspective
- Actions require explicit confirmation
- Subject to all world rules

Players do not bypass systems.

---

### 2.2 NPC Agents
Represent individuals within *Arrhaknea*.

Characteristics:
- Autonomous goal formation
- Subjective beliefs
- Memory-driven behavior
- Social and economic constraints
- Bounded reasoning cycles

NPCs are not scripted.
They **decide**.

---

### 2.3 Faction Agents
Represent collective entities.

Characteristics:
- Aggregate resources and influence
- Long time horizons
- Internal instability
- Delegation to NPC agents

Factions do not act perfectly or instantly.

---

## 3. Core Agent State

Every agent maintains the following categories of state.

---

### 3.1 Identity
Defines what the agent *is*.

Includes:
- Name / identifier
- Agent type
- Social role
- Affiliations
- Location

Identity constrains possible actions.

---

### 3.2 Resources
Defines what the agent *can leverage*.

Includes:
- Wealth
- Assets
- Access
- Manpower
- Influence

Resources are finite and fungible only through systems.

---

### 3.3 Beliefs
Defines what the agent *thinks is true*.

Beliefs:
- May be incomplete
- May be incorrect
- May contradict reality
- Are updated through experience and information

Beliefs are not facts.  
Agents act on beliefs, not truth.

---

### 3.4 Goals
Defines what the agent *wants*.

Goals are:
- Hierarchical (long-term vs short-term)
- Weighted by priority
- Mutable over time

Agents may:
- Abandon goals
- Postpone goals
- Pursue conflicting goals

Indecision is allowed.

---

### 3.5 Relationships
Defines how agents view one another.

Relationships include:
- Trust
- Hostility
- Dependency
- Obligation
- Leverage

Relationships are asymmetric and memory-driven.

---

### 3.6 Memory
Defines what the agent *remembers*.

Memory:
- Is selective
- Is emotionally weighted
- Decays and distorts
- Influences belief formation

Memory does not guarantee accuracy.

(Full specification in `05_MEMORY.md`.)

---

## 4. Agency and Constraint

Agents are **not omnipotent**.

An agent may:
- Want something
- Plan for it
- Attempt action

And still fail due to:
- Insufficient resources
- Opposition
- Timing
- Misinformation
- Systemic pressure

Intent does not imply outcome.

---

## 5. NPC Cognition Model

NPC cognition is **bounded and episodic**, not continuous.

---

### 5.1 Reasoning Triggers

NPC reasoning cycles occur when:
- A tick boundary is reached
- A relevant event occurs
- The NPC is directly engaged
- A belief is invalidated

NPCs do not think constantly.

---

### 5.2 Reasoning Cycle

Each reasoning cycle proceeds as:

1. **Perception**
   - Observe new events
   - Receive information
   - Update local view

2. **Belief Update**
   - Reconcile events with existing beliefs
   - Accept, reject, or distort information

3. **Goal Reprioritization**
   - Adjust priorities
   - Drop or adopt goals

4. **Intent Formation**
   - Propose one or more actions

5. **Validation**
   - Check against world rules
   - Check resource feasibility

6. **Commit Intent**
   - Submit action request to world engine

NPCs never execute actions directly.

---

### 5.3 Boundedness

NPC reasoning is constrained by:
- Time budgets
- Memory limits
- Incomplete information

NPCs may:
- Miss opportunities
- Make suboptimal choices
- Act emotionally

This is intentional.

---

## 6. Player Agency

Players submit **explicit intent**.

Player intent:
- Is validated by the world engine
- May be delayed
- May be blocked
- May trigger causal locks

The game does not reinterpret player intent charitably.

Ambiguity is resolved by consequence.

---

## 7. Conflicting Agency

When multiple agents act in opposition:
- No agent receives priority by default
- Systems arbitrate outcomes
- Timing and preparation dominate

Social leverage can outweigh raw force.

---

## 8. Delegation and Proxies

Agents may act through others:
- NPCs acting on faction orders
- Players influencing NPCs
- Institutions enforcing decisions

Delegation introduces delay, distortion, and risk.

---

## 9. Death and Removal

When an agent dies or is removed:
- Their resources are redistributed
- Their relationships decay or transfer
- Their memories persist indirectly through others

Death removes agency, not consequence.

---

## 10. Design Guarantees

This agent system guarantees that:
- Players and NPCs operate under the same rules
- Intent is separate from outcome
- Belief drives action
- Memory shapes future behavior
- No actor has privileged authority

If a feature violates this symmetry, it must be rejected.

---

## 11. Final Statement

Agents in `Eidolon` are not characters in a story.

They are **decision-makers under pressure**, operating with:
- limited knowledge,
- imperfect memory,
- and competing desires.

You are not special because you are a player.

You are special only if  
the world begins to change **because you persist**.

Say **continue** and we proceed.
