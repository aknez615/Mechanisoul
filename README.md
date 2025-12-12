# Mechromancer Boss AI - Unity Behavior Graph

A phase-based boss AI implemented using Unity's Behavior Graph. It features a distance weighted attack selection, animation-drive synchronization, and modular boss architecture. This project focuses on gameplay AI design, clean system integration and scalable behavior.
---
## Overview

The Mechromancer is a boss enemy designed for an action game scenario. Its behavior is driver by a custom Unity Behavior Graph that utilizes:
- Player tracking and navigation
- Weighted attack selection based on player distance
- One-time resurrection mechanics
- AI logic and animation synchronization

The system uses data-driven behavior, modularity, and designer-friendly tuning
---
## Behavior Graph Architecture

The Unity Behavior Graph (1.0.13) is structured around a main control loop that utilizes:
- Blackboard references
- Waits for player activation
- Runs navigation, resurrection logic, and combat in parallel
- Delegates attack decisions to a custom weighted composite node

### Key Graph Features
- 'Repeat' and 'Repeat Until Success' nodes for long-running behaviors
- Parallel execution for navigation and combat logic
- Blackboard-drive state flags
      - 'attackFinished'
      - 'comboLanded'
      - 'alreadyResurrected'
- Separation between decision logic and execution

**Behavior Graph screenshots are included in the repository for reference.**
---
## Custom Node: 'WeightedSequence'

The core combat logic is handled by a custom Behavior Graph composite node

### Purpose
Selects an attack based on:
- Player distance
- Contextual combat availability (combo, lunge, lightning)
- Weighted randomness for unpredictability

'''csharp
Agent attacks based off of PlayerTransform distance and random weights
