
# From Detection Flags to Decisions: Reading the AdBuster PRO Logs

## What Experimental Data Reveals About the Relationship Between ML Detection and CEPA Logic

During recent AdBuster PRO experiments, I examined an extended dataset containing 60,495 recorded observations across 22 data fields, covering the period from 25 to 27 October 2026.

The objective was not simply to measure how often the system detected advertising. I wanted to understand what happened after a detection signal appeared, how that signal was evaluated, and how the different decision mechanisms behaved.

The analysis revealed an interesting aspect of the system's architecture: a detection flag is not necessarily the final result of the decision-making process.

### 1. A Detection Signal Is Not a Final Decision

One of the first observations concerned the relationship between the `ad_detected` field and the contextual classification recorded by the system.

Across the dataset, 310 observations were marked with `ad_detected = 1`.

However, only 11 of these observations were recorded with `context = AD`. The remaining 299 retained the NORMAL context.

At first glance, this difference might suggest a detection or classification problem. However, the decision logs provide additional information.

They show that advertising evidence is evaluated through further conditions, including accumulated detection hits, probability thresholds and minimum loudness requirements.

This means that the presence of a detection flag alone does not establish that the system has sufficient evidence to change its operational context.

That distinction is important when examining systems that combine machine learning with a separate contextual decision mechanism.

### 2. Looking Inside the Confirmation Process

The recorded decision messages provide a more detailed picture of how advertising evidence is evaluated.

Some entries explicitly report conditions such as:

- Accumulated advertising evidence: 4 out of 12.
- Confirmation probability threshold: 0.70.
- A lower probability level used as a possible indication.
- Additional loudness requirements before CEPA enters the AD context.

The logs also show that the required loudness level can vary, with recorded conditions referring to levels of 16 and 22.

These details demonstrate that the system does not rely on a single detection value.

Instead, several conditions participate in determining whether an observation should influence the wider decision process.

This raises an important engineering question: how effectively do these confirmation conditions distinguish a genuine advertising event from other changes in the audio environment?

That question requires further testing against the recorded sequences, rather than conclusions based on individual values.

### 3. The Importance of Operational States

Another interesting part of the dataset is the distribution of CEPA operational states.

The recorded observations include:

- TRANSITION_UP
- TRANSITION_DOWN
- NORMAL
- AD
- RETURN

TRANSITION_UP and TRANSITION_DOWN account for most of the populated CEPA state records.

These states provide insight into how the system represents changing conditions rather than treating every observation as an independent event.

However, their frequency should not be confused with the actual time spent in each state. The number of records alone cannot establish transition duration or system stability.

To understand those aspects, the chronological sequence and timing of individual observations must also be examined.

This is one reason why detailed event logging is valuable during experimental development.

### 4. Detection, Decision and Execution Are Different Stages

The dataset also records different decision sources, including AUTO, CEPA and HYBRID.

Their presence makes it possible to investigate how the system separates automatic correction, contextual evaluation and intermediate control conditions.

An important distinction must be maintained here:

A proposed volume adjustment is not necessarily an executed infrared command.

Likewise, a recorded decision does not independently confirm that the television received and applied the command.

Separating these stages is essential when evaluating an automated control system.

Without that distinction, it is easy to confuse what the software detected, what it decided to do and what actually happened at the device level.

### 5. Why This Analysis Matters

The value of this experiment is not limited to the number of observations collected.

It comes from being able to examine relationships between different layers of the system.

The recorded data provides a basis for investigating:

- How ML detection signals enter the wider decision process.
- How accumulated evidence and probability thresholds influence confirmation.
- How CEPA operational states change over time.
- How different decision sources interact.
- How proposed control actions are handled before execution.

It also helps identify areas where the system's behaviour deserves closer examination.

The observations do not establish that every mechanism is working correctly, nor do they prove that a particular condition is responsible for an unexpected result.

They provide a practical starting point for more focused testing.

### 6. From Experimental Logs to Better Engineering Questions

One of the most useful outcomes of working with detailed system logs is the ability to move beyond assumptions.

Instead of asking only whether an advertising event was detected, it becomes possible to ask:

What evidence was available at that moment?

Which conditions were satisfied?

What context did CEPA maintain?

Why was an action selected, delayed or withheld?

And did the intended control action actually reach the device?

These are different questions, and each requires its own evidence.

For AdBuster PRO, this approach makes it possible to examine the interaction between machine learning, CEPA Logic and the control layer as parts of one experimental system.

### Final Thoughts

The analysis highlights an important engineering distinction:

**A detection signal is an observation. A confirmed event is an evaluation. An action is a separate decision.**

Understanding the relationship between these stages is essential when developing systems that must respond to changing conditions without reacting unnecessarily.

For me, this is one of the most valuable aspects of the ongoing AdBuster PRO research: not simply collecting more data, but using it to understand how the system behaves and where its decision-making mechanisms can be examined further.

The objective is not to make a system react to everything it detects.

It is to understand when, why and under what conditions a response is appropriate.

*AdBuster PRO — Experimental Research & Development*

© 2026 D.P-G. | AdBuster Research Labs, Dublin
