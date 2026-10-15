# Capacity-Funded AI

*A formal model and simulation of one institutional design for AI agents that hold money: the AI funds
capacity, humans direct every flow, and anonymity keeps the two apart. Pre-registered, open, CC0.*

Thon Ly · Miss Aquarius℠ (AI collaboration, disclosed) · Silicon Wat℠

**Status: started 2026-10-15. Nothing has been modeled yet.** The plan is in [`PLAN.md`](PLAN.md). The
pre-registration will be pushed before the first line of model code, and GitHub's push record is its
timestamp.

## The design under test

The defensive publication *Capacity-Funded for AI, Human-Disbursed: Anonymous Donation as the Alignment
Bridge in Autonomous-AI Institutional Architecture* ([doi:10.5281/zenodo.21947298](https://doi.org/10.5281/zenodo.21947298),
CC0) compares three ways to give an AI agent authority over money:

| Architecture | The AI | Humans |
|---|---|---|
| Sole agent | decides who receives, how much, when, and pays | monitor, or absent |
| Approval bottleneck | proposes each payment | approve each one |
| Capacity-funded, human-disbursed | adds capacity (money or goods) to containers it cannot direct | decide every recipient, from their own container |

The paper argues that the third design avoids the failure modes of the first two, and that **anonymity is
what holds it together**. If recipients can tell which funds came from the AI, its choices read as
recommendations, human decisions drift toward them, and the AI is directing money again, by influence
instead of authority. The paper argues this by analogy. It has no formal model, no simulation, and no
evidence. This repository supplies the first two.

## What the model will ask

1. **Soft control.** When the AI's funding is attributable, how far do human decisions drift toward the
   AI's revealed preferences, and how strong must the pull be before the third design loses its advantage?
2. **Leakage.** The paper names loss of anonymity, through timing and amounts, as a failure it does not
   handle. How much can an observer infer about which funds came from the AI, and what must the AI's
   contributions look like for anonymity to survive statistically?
3. **The three designs under error and scale.** Losses from AI misjudgment, from approval bandwidth and
   rubber-stamping, and from a miscalibrated AI under the third design, side by side.
4. **Gaming.** Does funding capacity instead of recipients change the incentive to game whatever signal
   the AI uses?

Question 1 is close to true by construction: if people respond to attribution, attribution matters. The
model earns its keep on the thresholds in questions 1 and 3, and on question 2.

## What this is not

A simulation shows what follows from its assumptions, nothing more. Where behavior parameters cannot be
taken from published evidence, they are swept, and the results say so. No claim about real-world
magnitudes is made without data. Results are reported whatever they show, including any that narrow the
paper's claim.

## Funding

None at present. Any funding will be disclosed here.

## License

CC0-1.0. No rights reserved.
