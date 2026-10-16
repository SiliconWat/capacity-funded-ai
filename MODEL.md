# Model (draft for review, not the pre-registration)

*Living document. When the design is approved, its fixed form goes into `PREREGISTRATION.md` with the
predictions, before any model code exists.*

## Notation

- Periods *t* = 1…*T*.
- Recipients *j* = 1…*M*. Each has a true value *v_j* for funds, unknown to everyone. Funds *x_j* do good
  *v_j · u(x_j)*, with *u* concave (log(1 + *x*) as the default; a power law in the sensitivity sweep).
- Human directors *i* = 1…*N*, each holding a container with balance *c_i*. Director *i* sees only the
  recipients in its neighborhood *S_i* (size *k*, from a network), with weights *w_ij* = *v_j* + *η_ij*,
  where *η* is idiosyncratic preference and local knowledge (spread *σ_h*).
- The AI funder *A* has budget *B* per period and an estimate *â_j* = *v_j* + *ε_j* (misjudgment spread
  *σ_a*). Its revealed preference *p_A* is the normalized allocation it would choose.

## Regimes

| Regime | Mechanics |
|---|---|
| *S*, sole agent | *A* pays recipients directly from *â*. Errors scale with *B*. |
| *B*, approval bottleneck | *A* proposes payments; an approver reviews up to *K* per period, catching a bad proposal with probability *q*; beyond *K* it approves at a rubber-stamp rate *ρ*. |
| *C*, capacity-funded, anonymous | *A* adds to containers; directors pay recipients in *S_i* by their own weights. *A*'s share is unobservable per contribution. |
| *C′*, attributed | Directors see *A*'s contribution and *p_A*, and shift: *w′_ij* = (1 − λ) *w_ij* + λ *p_Aj*. λ < 0 is aversion (people moving away from an algorithm's choice). |
| Leakage | As *C*, but AI contributions come from a distribution *D_A* of amounts and timing, human ones from *D_H*. An observer attributes each contribution with accuracy *π* (a likelihood-ratio classifier), so the expected pull is λ *π*. |
| *C\**, the paper's current form | *A* funds capacity **in kind**, and which containers receive it is decided by a **publicly verifiable draw** from a committed roster, never by *A*. *A* chooses neither recipients nor containers, so the soft-control and capture channels close by construction. The model measures their **price**: the welfare lost by not targeting (a uniform draw against need-weighted funding). The money-denominated, discretionary *C* is the paper's disclosed variant. |

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

Global sensitivity analysis (Sobol indices with Saltelli sampling) over λ, *π* (or the distance between
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
- **P6:** under *C\**, captured flow is zero whatever *A* intends, and the welfare cost against *C* shrinks as
  directors' local knowledge (*σ_h* small, *k* large) improves: the draw costs least where humans know most.

## What the model assumes, and does not derive

The directors' response to attribution (λ) is an assumption until E2 measures it. Directors are honest
(capture of the directors is outside the model, as the paper states in §6.2). Values *v* are fixed within a
run. The network is exogenous.
