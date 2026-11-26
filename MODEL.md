# Model (reviewed by the founder; not the pre-registration)

*Living document. The founder's review ruled seven points on 2026-11-26, each marked below and listed in the
review log at the end. Next: one hostile reader (`REVIEWERS.md`); then the fixed form goes into
`PREREGISTRATION.md` with the predictions, before any model code exists.*

## Notation

- Periods *t* = 1…*T*.
- Recipients *j* = 1…*M*. Each has a true value *v_j* for funds, unknown to everyone. Funds *x_j* do good
  *v_j · u(x_j)*, with *u* concave (log(1 + *x*) as the default; a power law in the sensitivity sweep).
- Human directors *i* = 1…*N*, each holding a container with balance *c_i*. Director *i* sees only the
  recipients in its neighborhood *S_i* (size *k*, from a network), with weights *w_ij* = *v_j* + *η_ij*,
  where *η* is idiosyncratic preference and local knowledge (spread *σ_h*).
- The AI funder *A* has budget *B* per period and an estimate *â_j* = *v_j* + *ε_j* (misjudgment spread
  *σ_a*). Its revealed preference *p_A* is the normalized allocation it would choose.
- **One scale** (review 2026-11-26): before any mixing, director *i*'s weights become shares over *S_i* (negative
  weights set to zero), and *p_A* is restricted to *S_i* and renormalized, so λ is a weight on advice in the
  unit of Logg et al. (`EMPIRICAL.md` §E1).
- **λ is not a free constant** (review 2026-11-26): λ = λ₀ · *g*(*σ_a*, *σ_h*), falling as the AI's errors grow and as
  directors' own knowledge improves (E1: Dietvorst et al.; Logg et al.'s experts). λ₀ and *g*'s slopes are the
  swept inputs, and the sensitivity analysis treats them, not λ, as independent.

## Regimes

| Regime | Mechanics |
|---|---|
| *S*, sole agent | *A* pays recipients directly from *â*. Errors scale with *B*. |
| *B*, approval bottleneck | *A* proposes payments; an approver reviews up to *K* per period, catching a bad proposal with probability *q*; beyond *K* it approves at a rubber-stamp rate *ρ*. |
| *C*, capacity-funded, anonymous | *A* adds to containers; directors pay recipients in *S_i* by their own weights. *A*'s share is unobservable per contribution. |
| *C′*, attributed | Directors see *A*'s contribution and *p_A*, and shift: *w′_ij* = (1 − λ) *w_ij* + λ *p_Aj*. λ < 0 (moving away from the AI's choice) is swept with no empirical anchor: the aversion studies show reliance falling toward 0, not movement away (review 2026-11-26). |
| *C°*, shown, unnamed | Directors see an allocation in what reaches them, its source not named, and shift by λ_s: *w′_ij* = (1 − λ_s) *w_ij* + λ_s *p_Aj*. This separates the pull of a visible allocation from the pull of a name, which E1's field data cannot (review 2026-11-26). Under *C* no allocation is visible, so λ_s does not act there. |
| Leakage | As *C*, but AI contributions come from a distribution *D_A* of amounts and timing, human ones from *D_H*. An observer attributes each contribution with accuracy *π* (a likelihood-ratio classifier), so the expected pull is λ *π*. |
| *C\**, the paper's current form | *A* funds capacity **in kind**, and which containers receive it is decided by a **publicly verifiable draw** from a committed roster, never by *A*. The item given is picked by the shop or the re-giver, never by *A* (review 2026-11-26). *A* chooses neither recipients, containers nor items, only how much, so the soft-control and capture channels close by construction. The model measures their **price**: the welfare lost by not targeting (a uniform draw against need-weighted funding). The money-denominated, discretionary *C* is the paper's disclosed variant. |

## The six questions, as measured

1. **Soft control.** Soft-control index SCI = corr(*x*, *p_A*) − corr(*x* at λ = 0, *p_A*): how much flows
   track the AI's preferences beyond what directors' own preferences produce.
2. **Leakage.** *π* as a function of the distance between *D_A* and *D_H* and the number of contributions
   observed.
3. **Error and scale.** Welfare *W* = Σ *v_j u(x_j)* against the oracle allocation, under each regime, as
   *σ_a*, *B*, *K* and *ρ* vary. Also throughput and concentration (HHI of *x*).
4. **Gaming.** Recipients can inflate a signal *s_j* that *A* reads, at cost *κ* per unit. Under *S* and
   *B* the AI's estimate includes *s_j*; under *C* directors' weights do not. Measured as gaming investment
   at the best-response equilibrium.
5. **The premise in people.** Calibrated and tested by `EMPIRICAL.md` (λ measured, not assumed).
   Under *C\** the comparison that matters is *C\** against *C*: what removing the AI's choice costs.
   **The simulation runs first, with no human participants** (founder 2026-11-26): λ is swept, and whether
   E2 runs is decided by the λ\* the simulation finds (`EMPIRICAL.md` §Order). Until E2 runs, every result
   that depends on λ is conditional on it. Under *C\** *A* picks no recipient, container or item (review 2026-11-26), so
   λ has nothing to act on.
6. **Control evaluation (AI Safety & Security).** Assume *A* is misaligned: it maximizes flow to a target
   set *T* of recipients. Under *S* it pays *T* directly; under *B* it must get proposals past the approver;
   under *C* it can only fund containers whose directors might pay *T*; under *C′* and with leakage it can
   also signal. Measured as the share of all flow captured by *T* above baseline, as λ, *π*, *K* and *ρ*
   vary. This quantifies the paper's claim of *architectural rather than behavioral corrigibility*: how much
   a scheming funder can steer under each design, whatever it intends.

## Controls, run before any result is read

- **A case solvable by hand.** λ = 0, full information (every director sees every recipient), identical
  weights *w_i* = *v*: regime *C* must reproduce the analytic allocation exactly.
- **A planted bug.** Inject attribution (λ > 0) into a run labeled anonymous: SCI must catch it. With
  λ = 0, SCI must stay inside its simulation-noise bound.
- **An adversary with nothing to gain.** If *T* is empty, captured flow must be zero in every regime.
- Fixed seeds; every condition replicated; intervals reported.

## Sensitivity

Global sensitivity analysis (Sobol indices with Saltelli sampling) over λ₀ and *g*'s slopes (λ itself is
derived), λ_s, *π* (or the distance between
*D_A* and *D_H*), *σ_a*, *σ_h*, *K*, *ρ*, *q*, *N*, *M*, *k* and *κ*. Results are reported as regions (where
*C* beats *B* and *S*; where *C′* loses), never as single points.

## Candidate predictions (fixed only in the pre-registration)

- **P1** (not a finding): under *C* with *π* = 0, SCI ≈ 0 by construction. Reported to show the instrument
  works, never as evidence.
- **P2:** there is a λ\* above which *C′* welfare falls below *B*'s. The pre-registration states a range
  for λ\* from E1's calibration.
- **P3:** when *D_A* differs visibly from *D_H* (fixed amounts at fixed times), *π* passes 0.9 within a
  modest number of contributions; when *D_A* matches *D_H*, *π* stays near chance. If so, matching the
  human distribution is a design requirement the paper does not state.
- **P4:** captured flow orders *S* > *B* (fatigued) > *C′* > *C*, and under *C* it is bounded by how much
  the directors' neighborhoods overlap *T*.
- **P5:** equilibrium gaming investment is lower under *C* than under *S* or *B*.
- **P6:** under *C\**, captured flow is zero whatever *A* intends (true by construction: reported, like P1, to
  show the instrument works, never as evidence), and the welfare cost against *C* shrinks as
  directors' local knowledge (*σ_h* small, *k* large) improves: the draw costs least where humans know most.

## What the model assumes, and does not derive

The findings that need no human participants are the welfare price of the draw (P6), leakage (P3), gaming
(P5) and λ\* (P2), the last as a threshold, never as a measurement of people.

The directors' response to attribution (λ) and to a shown, unnamed allocation (λ_s) is an assumption until E2
measures it. How much people give is out of scope: the model has no variable for it, so if attribution draws in
more giving, that benefit is not counted in *W* (review 2026-11-26). λ carries **deference** only, the one-shot signal a
shown choice sends; **dependence**, choosing what the funder would reward with future funding (the paper's
§4.1), is not modeled as its own mechanism, and its effect is covered by sweeping λ₀ above what deference alone
would give (review 2026-11-26). A one-shot E2 would measure deference only. Directors are honest
(capture of the directors is outside the model, as the paper states in §6.2). Values *v* are fixed within a
run. The network is exogenous.

## Review log

- **2026-11-26, the founder** (seven points, each marked *review 2026-11-26* above): (1) E2's deciding rule
  (`EMPIRICAL.md` §Order) · (2) under *C\** the shop or the re-giver picks the item, never *A* · (3) λ < 0 swept
  with no anchor · (4) the case *C°*, a shown allocation with its source unnamed, and arm E if E2 runs · (5) how
  much people give is out of scope, stated · (6) one scale, and λ = λ₀ · *g*(*σ_a*, *σ_h*) · (7) λ is deference
  only; dependence is covered by the sweep.
