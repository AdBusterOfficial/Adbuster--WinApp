# From DSP To CEPA

## Original Goal

Reduce disruptive TV advertisements.

## Phase 1 – RMS

Simple threshold detection.

Worked:
- loud ads

Failed:
- music
- dialogue
- scene transitions

## Phase 2 – Feature Analysis

Added:
- RMS
- STD
- DELTA
- RANGE

Improved detection.

Still lacked context.

## Phase 3 – Machine Learning

Added:
- AD classification

Improved identification.

Still could not explain decisions.

## Phase 4 – Context

Introduced:
- ADS
- MUSIC
- DIALOG
- NORMAL

Behaviour became more predictable.

## Phase 5 – Behaviour Analysis

Focus shifted from:

"How loud is it?"

to:

"How is it behaving?"

New concepts:
- drift
- stability
- trend
- transitions

## Phase 6 – CEPA

Observation
→ Context
→ Behaviour
→ Decision

CEPA emerged as a behavioural decision engine.

## Current State

Research prototype.

Still evolving.

Built around:
- deterministic decisions
- context awareness
- behaviour modelling
- real-time validation
