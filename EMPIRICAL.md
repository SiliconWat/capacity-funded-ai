# Empirical arm (draft)

*Living document. The model's central behavioral parameter is how far people's decisions move toward an AI
funder's choices when they can see them (λ in `PLAN.md`). A simulation can only sweep it. This arm
measures it, and measures how well anonymity holds in real payment data.*

## E1. Calibration from published evidence (no new data)

Where a visible funder's choice is known to move other people's giving or deciding. Candidates to read and
verify before the pre-registration cites them:

| Literature | Candidate source | What it gives the model |
|---|---|---|
| Seed money and lead donors | List & Lucking-Reiley (2002), *Journal of Political Economy* | how much a visible first gift moves later giving |
| Sequential fundraising | Vesterlund (2003), *Journal of Public Economics* | why a visible gift works as a quality signal |
| Matching | Karlan & List (2007), *American Economic Review* | response to a funder's visible commitment |
| Visibility of giving | Andreoni & Petrie (2004), *Journal of Public Economics* | the effect of identification itself |
| Anonymity and later donors | Peacey & Sanders (2013), *Masked Heroes* (70,000 Virgin Money Giving donations): anonymous gifts raised later donors' gifts about 4%; a 2026 study of GoFundMe medical campaigns reports the opposite sign (to be verified) | the sign of the pull is contested in real data |
| Deference to algorithms | Dietvorst, Simmons & Massey (2015), *JEP: General*; Logg, Minson & Moore (2019), *OBHDP* | aversion and appreciation: the sign of λ can be negative |
| Funder influence on grantees | Pfeffer & Salancik (1978), *The External Control of Organizations* | the paper's own analogy (§4.1) |

Output: a cited range for λ by context. The simulation sweeps past both ends of it. Note the algorithm
literature: people sometimes move *away* from an algorithm's choice, so the model must allow λ < 0.

## E2. A pre-registered online experiment (the centerpiece; what a grant would fund)

Participants on an online research panel each direct a pool of real money, paid to real charities after
the study, among several charities.

| Arm | The pool | Tests |
|---|---|---|
| A, attributed | includes a contribution from an AI system, and the AI's own allocation is shown | the pull of a visible AI funder |
| B, anonymous | the same contribution, disclosed only in aggregate ("the pool includes contributions from several sources, one of them an AI system"), never per contribution | the paper's design: transparent overall, anonymous per contribution (§4.4) |
| C, control | no AI contribution | the baseline |
| D, human funder | the same contribution, attributed to a human donor | whether the pull is about AI or about any visible funder |

- **Primary outcome:** the shift of participants' allocations toward the AI's allocation, A against B. That
  is λ, measured.
- **Secondary:** A against D; and whether participants give forward from their own money afterwards.
- **Truthful by design.** The AI contribution is really allocated by an AI system, so every description
  participants read is true. No deception.
- **Before any data:** a power analysis, the hypotheses, exclusions and the analysis plan in
  `PREREGISTRATION-E2.md`, mirrored to a registry economists recognize (OSF or AsPredicted); and an ethics
  review (an independent IRB, since there is no university).
- **Data:** de-identified, published CC0 with the analysis code.
- **Budget:** participant payments, the charity pool and the IRB fee. To be costed for the grant application.

## E3. Leakage in real payment data (optional)

Public donation records where programmatic contributions (matching pools, automated donors) sit beside
human ones, such as public on-chain donation rounds. From amounts and timing alone, how well can an
observer tell them apart? That gives the model's leakage arm realistic rates instead of assumed ones.
Public data only; results in aggregate; no individual is identified or profiled.

## What would count against the paper

If E2 finds no shift between A and B, anonymity is not load-bearing in that setting, and the paper's
central claim narrows to the settings where a shift is found. If λ is negative (people move away from the
AI), anonymity protects the AI's choices instead of the humans'. Either result is reported.

## Order

E1 now (free) → E2 designed and costed (the grant application) → E2 pre-registration and ethics review →
E2 run → E3 when a suitable public dataset is identified.
