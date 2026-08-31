# CEPA Logic — Real-Time Decision v2

This diagram illustrates the real-time behaviour engine used inside **AdBuster PRO**.  
It shows how CEPA interprets the audio environment deterministically and decides how the system should control loudness in a stable, predictable way.

## Real-Time Decision Model
![CEPA Logic — Real-Time Decision v2](https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/labs/CEPA_real_time_decision.jpg)

### Overview
CEPA Logic operates as a behaviour-driven decision layer.  
The ML classifier provides only the initial context (**AD / NORMAL**), while CEPA evaluates the behaviour of the signal and determines how the system should react.

### Pipeline Breakdown
- **Continuous Signal Feed**  
  Real-time RMS, MFCC and spectral metrics extracted from the incoming audio.

- **Feature Extraction Layer**  
  Deterministic feature set used for ML context and behaviour analysis.

- **ML Classification (AD / NORMAL)**  
  The classifier provides the high-level context used by CEPA.

- **CEPA Decision Engine**  
  Evaluates:
  - loudness trend  
  - timing stability  
  - reaction history  
  - contextual consistency  
  Declares: **Trigger / Hold / Ignore**

- **Reaction Control**
  Behaviour-driven loudness control:
  - IR volume commands  
  - stabilization  
  - timing synchronization

- **Continuous Adaptation**
  CEPA updates its internal state based on behaviour patterns, ensuring stable and reversible reactions.

### Purpose
This model ensures that AdBuster PRO reacts only to meaningful behavioural changes, not random spikes or noise.  
It provides deterministic, context-aware loudness control without relying on predictive ML behaviour.
