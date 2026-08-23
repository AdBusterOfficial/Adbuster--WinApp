# CEPA Logic — Real-Time Decision v2

This diagram illustrates the real-time behaviour engine used inside **AdBuster PRO**.  
It shows how CEPA interprets the audio environment deterministically and decides how the system should control loudness in a stable, predictable way.

## Real-Time Decision Model

![CEPA Logic — Real-Time Decision v2](docs/img/CEPA_RealTimeDecision_v2.png)

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
  Evaluates
