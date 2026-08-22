CEPA Logic — Technical Overview
Version 1.0 — © 2026 AdBuster Development Team, Dublin

1. What is CEPA Logic
CEPA (Contextual Event Pattern Analysis) is a contextual decision engine that evaluates
ML audio classification, stabilizer behavior, reaction frequency and event patterns to
produce stable, human‑like automation decisions.

2. Core Decision Types
BOOST  — strong reaction when advertisement is detected
BLOCK  — prevent reaction during dialog
DELAY  — prevent over‑reaction when actions occur too frequently
SMOOTH — reduce reaction intensity when system is overloaded
ALLOW  — normal operation when no special conditions apply

3. Real‑Time Data Flow
CEPA receives new data every ~100 ms:
- ml_data (ad/dialog/music/noise)
- stabilizer_data (correction history)
- timestamp (current time)
CEPA returns a single decision which the stabilizer executes.

4. Human‑Like Behavior Model
CEPA mimics how a real user reacts with a remote control:
- waits before reacting again
- avoids spammy volume changes
- reacts strongly only when needed
- ignores false positives
- stabilizes behavior over time

5. Example Code (Python)
class CEPA:
    def __init__(self):
        self.enabled = False
        self.last_action_time = 0
        self.min_reaction_interval = 0.25
        self.smoothing_factor = 0.5
        self.max_corrections_per_min = 20
        self.corrections_history = []

    def toggle(self):
        self.enabled = not self.enabled
        return self.enabled

    def evaluate(self, ml_data, stabilizer_data, timestamp):
        if not self.enabled:
            return "ALLOW"

        if timestamp - self.last_action_time < self.min_reaction_interval:
            return "DELAY"

        self._cleanup_history(timestamp)
        if len(self.corrections_history) > self.max_corrections_per_min:
            return "SMOOTH"

        if ml_data.get("is_ad", False):
            return "BOOST"

        if ml_data.get("is_dialog", False):
            return "BLOCK"

        return "ALLOW"

    def register_correction(self, timestamp):
        self.corrections_history.append(timestamp)
        self.last_action_time = timestamp

    def _cleanup_history(self, timestamp):
        self.corrections_history = [
            t for t in self.corrections_history
            if timestamp - t < 60
        ]

6. Step‑By‑Step Example
Event 1 — Dialog → BLOCK
Event 2 — Advertisement → BOOST
Event 3 — Too soon → DELAY
Event 4 — Too many corrections → SMOOTH
Event 5 — Normal content → ALLOW

7. Purpose
CEPA ensures stable, predictable, context‑aware automation suitable for real‑world use.
