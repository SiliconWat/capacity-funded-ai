# Plan

*Living document; history in git. The pre-registration, when it exists, is a separate file that is never
edited.*

## Steps

1. **Model design** (below, draft). Reviewed before anything is fixed.
2. **Prior-art check** of the modeling questions: donor influence on grantees, anonymous giving,
   crowding out, statistical de-anonymization of payments. What is already known is cited, not re-derived.
3. **`PREREGISTRATION.md`**: the model, the parameter ranges, the predictions, and what would count against
   the paper, pushed before any model code. Timestamped (OpenTimestamps and RFC 3161).
4. **The formal model** in `MODEL.md`, then the **simulation** (Python, agent-based), with a control that
   the code reproduces a case whose answer is known in closed form.
5. **Results and a paper**, submitted for peer review.
6. **An empirical arm**, if one can be found: the questions above need real behavior to calibrate against.

## Model design (draft, not the pre-registration)

**Agents.** One AI funder with a budget per period and a noisy estimate of where funds do good
(misjudgment rate ε). *N* human directors, each with a container and preferences of their own. *M*
recipients.

**Regimes.**

- *S* (sole agent): the AI pays recipients by its own estimate.
- *B* (approval bottleneck): the AI proposes; an approver handles *k* proposals per period and approves
  the rest at a rubber-stamp rate ρ.
- *C* (capacity-funded, anonymous): the AI adds to containers; directors pay recipients by their own
  preferences.
- *C′* (capacity-funded, attributed): as *C*, but directors see the AI's contribution and shift toward its
  revealed preferences with strength λ.

**Leakage arm.** AI contributions are drawn from one distribution of amounts and timing, human
contributions from another. An observer tries to tell them apart (a likelihood-ratio test or a classifier).
The effective pull is λ times the probability of correct attribution, so *C* becomes *C′* to the degree
anonymity leaks.

**Outcomes.** A soft-control index (how closely flows track the AI's preferences beyond what directors'
own preferences predict) · losses from misjudgment · throughput · concentration · the response to gaming.

**Candidate predictions, to be fixed in the pre-registration:** the threshold λ\* at which *C′* loses its
advantage over *B*; the number of contributions after which an observer attributes AI funds reliably when
the two distributions differ, which would make matching the human distribution a design requirement.

## Grants

Anthropic's Economic Futures Program (announced June 2025) offered research grants and API credits for work
on AI's economic effects. Before applying: confirm the program is still open and what it funds. As
described in 2025 it favored empirical research, so a simulation alone is a weaker fit; step 6 matters. A
grant also needs a named recipient, an individual or an organization, to be settled first.
