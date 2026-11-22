<p align="center">
  <img src="https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/newsletter/AdBuster%20Research%20Notes%20Cover.png" alt="AdBuster Research Notes" width="100%">
</p>

# The Last Mile Problem in Real-Time Systems

### Why a correct decision does not always produce a confirmed result

November 2026

One of the assumptions we often make when building software is that a completed action equals a successful outcome.

A function runs.

A request is generated.

A command is sent.

A log entry is created.

The system reports success.

Problem solved.

Or is it?

While developing AdBuster PRO, I encountered a useful engineering reminder:

A system can successfully perform every step of its internal workflow and still be unable to prove that the intended real-world outcome actually occurred.

This challenge is often called the *last mile problem* between decision and confirmation.

## When Success Is Not the Same as Verification

Consider a simple example.

An audio event is detected.

The control conditions are satisfied.

The application decides that a volume adjustment is appropriate.

A command request is generated.

The local service processes the request.

The infrared device transmits the signal.

From the software's perspective, everything worked correctly.

But one important question remains:

**Did the television actually change its volume?**

The answer is not always visible to the system.

The software knows what it requested.

It may not know what ultimately happened.

## The Difference Between Control and Observation

When humans use a remote control, we receive immediate feedback.

We press a button.

We see the volume bar move.

We hear the change.

The feedback loop is closed.

Many automated systems do not have this luxury.

In AdBuster, audio measurements provide observations while Broadlink provides control capabilities.

The system can observe sound.

The system can request a change.

Those facts alone do not automatically provide confirmation of the television's internal state.

This distinction is easy to overlook during development.

## Why Real-World Systems Are Different

Software engineers often work with environments where actions produce immediate and verifiable results.

Databases confirm updates.

APIs return responses.

Files can be read after being written.

Physical systems introduce additional uncertainty.

Commands can be delayed.

Devices can become unavailable.

Communication paths can fail.

External hardware can behave unexpectedly.

A successful software operation may not always translate into a confirmed physical outcome.

In AdBuster, a single volume adjustment depends on:

- Audio analysis
- Decision logic
- Local services
- Network communication
- Broadlink hardware
- Infrared transmission
- Television response

The final outcome depends on every stage working as expected.

## Why Logs Matter

One of the most useful lessons from this project came from examining detailed logs rather than relying on assumptions.

A recorded command proves that the software attempted an action.

It does not automatically prove that the action achieved its intended effect.

This may seem like a subtle distinction.

In practice, it changes how a system should be evaluated.

Instead of asking:

*"Did the application send the command?"*

A more useful question becomes:

*"What evidence exists that the command produced the intended result?"*

Logs describe internal activity.

They do not always describe external reality.

## Verification Is Its Own Engineering Problem

As systems become more complex, verification becomes increasingly important.

Generating a decision is only part of the challenge.

Executing a command is only part of the challenge.

Understanding what happened after execution can be equally important.

Many systems are designed to control.

Far fewer are designed to confirm.

The gap between those two abilities can have a significant impact on reliability.

A system that cannot observe outcomes operates with a degree of uncertainty, even when its internal processes appear correct.

## A Lesson Beyond AdBuster

This principle applies far beyond television volume control.

Robotics, IoT devices, industrial automation and many real-time systems face similar challenges.

Commands and outcomes are not always identical.

A system may know what it attempted.

It may have only partial knowledge of what actually occurred.

Understanding that difference is often the first step toward building more reliable systems.

## Final Thoughts

Developing AdBuster PRO has reinforced a simple engineering lesson.

The difficult part is not always making a decision.

Sometimes the difficult part is proving that the decision achieved the intended result.

Software can record requests, actions and events with great precision.

The real world is often less cooperative.

Between a successful command and a confirmed outcome lies the final engineering challenge: verification.

And in many systems, that last mile is where reliability is truly tested.

---

## About AdBuster Research Notes

AdBuster Research Notes explores my ongoing work on AdBuster PRO, system architecture, contextual decision-making and the development of CEPA Logic.

The newsletter documents engineering observations, experimental development and practical lessons learned while building real-time systems.

## Project and Technical Documentation

🟢 **Website:** [AdBuster PRO – Official Project Website](https://sites.google.com/view/adbuster-winapp)

🔵 **GitHub:** [Complete Project Documentation](https://github.com/AdBusterOfficial/Adbuster--WinApp)

🟣 **LinkedIn Newsletter:** [AdBuster Research Notes](https://www.linkedin.com/newsletters/adbuster-research-notes-7515027727326916608/)

---

I welcome discussions with engineers and researchers interested in real-time systems, automation, observability and behavioural decision-making.

© 2026 D.P-G. | AdBuster Research Labs, Dublin

<br>

<p align="center">
  <img src="https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/footer.png" alt="Footer" width="100%">
</p>
