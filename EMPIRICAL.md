# Empirical arm (draft)

*Living document. The model's central behavioral parameter is how far people's decisions move toward an AI
funder's choices when they can see them (λ in `MODEL.md`). A simulation can only sweep it. This arm
measures it, and measures how well anonymity holds in real payment data.*

## E1. Calibration from published evidence (no new data)

*Read 2026-11-05. Each row says what was actually read and from which copy. A number stands here only if it
was read in that copy; the two sources that could not be read in full keep the marker "verify before citing".*

**The result, plainly: the evidence does not settle the sign of the effect the paper depends on, and no source
measures λ as the model defines it.** The earlier draft of this section ran these questions together. They have
different answers:

| Question | Sign | Range | Source and status |
|---|---|---|---|
| A. Does a visible gift or commitment raise later people's giving? | positive in every source read; none finds a negative | ×5.61 total dollars (seed 10% → 67%); +19% revenue and +22% response (any match against none); +59% (amounts and identities shown, lab) | List & Lucking-Reiley; Karlan & List; Andreoni & Petrie: verified |
| B. Does hiding the giver's identity raise or lower that pull on later gift size? | **contested, not settled** | −5.5% per anonymous gift among the three most recent, through 0 (full sample), to +4.7 log points (large gifts only; SE 0.019; 95% CI +1.0 to +8.4, our arithmetic) | Wang & Ye: abstract only, **verify before citing**; Peacey & Sanders: verified, a working paper |
| C. How far do judgments move toward an algorithm's, in λ's own unit? | positive; reduced but not reversed after errors are seen; no negative shown | weight on advice 0.34 to 0.50 (algorithm label), 0.21 to 0.35 (human label), a difference of +0.10 to +0.16; the share choosing the algorithm falls 10 to 42 points after seeing it err, and stays between 13% and 49% | Logg et al.; Dietvorst et al.: verified. Factual judgments only, and the Logg measure cannot go below 0 |
| D. How far do people's **allocations among recipients** move toward a funder's shown allocation (λ as defined)? | **unknown** | none | no source here measures it; E2 is the first that would |

On B, the two studies are not clean opposites. Both use donation-page data in which donors chose anonymity, and
both find that size matters in the same direction: small anonymous gifts have no effect in one, and large ones
attenuate the penalty in the other. They differ in setting (friends and family of marathon runners against
medical campaigns) and in the comparison. Wang & Ye also report a randomized experiment, the only randomized
evidence on this question in a fundraising setting, and it is in the part that could not be read. In the lab,
randomly adding identities to visible amounts raised giving 79% (Andreoni & Petrie), which leans Wang & Ye's way,
but those subjects were themselves exposed, so it cannot separate their own visibility from a funder's. These
results are not pooled here.

### Sources

| Source | What was read | Design and population | Effect size, with units | Maps to |
|---|---|---|---|---|
| List & Lucking-Reiley (2002), *JPE* 110(1), 215–233 ([copy](https://econweb.ucsd.edu/~jandreoni/PhilanthropyAndFundraising/Volume%202/8%20List%20Lucking-Riley%202002.pdf)) | **Verified.** Full text: abstract, design, Table 1, §III.A, §V | Randomized direct-mail field experiment; 3,000 Florida households, 500 per cell; one $3,000 computer per cell, a threshold public good | Total given $581 at 10% seed against $3,260 at 67% (×5.61, pooled over refund cells; the text's "increase by 560 percent" is that ratio, an increase of 461%; p. 222). Participation 3.7% → 8.2% (z = 4.27); mean gift $15.42 → $39.87 (t = 6.37) (pp. 224–225). Refund: +21% | No parameter of the model (amount given, one recipient). The seed had no named source: "We have already obtained funds to cover [10%] [33%] [67%]" (p. 232). The threshold means part of the effect may be the remaining gap, not pull |
| Vesterlund (2003), *J. Public Econ.* 87(3–4), 627–657 ([author's copy](https://sites.pitt.edu/~vester/JpubE.pdf), article in press) | **Verified, theory: no effect size.** Abstract, §1, footnotes 6 and 8, §4; proofs not checked | Signaling model: an informed first donor, uncertain charity quality | None of its own. Footnote 6 reports a telethon study (Silverman et al. 1984; not read): $771 per hour with announcements against $412 and $312, with cautions | The mechanism for λ > 0: followers defer if they believe the funder is informed. So λ should depend on perceived *σ_a*. Footnote 8 says the signal needs size **and** identity, and assumes identity known |
| Karlan & List (2007), *AER* 97(5), 1774–1793 ([copy](https://econweb.ucsd.edu/~jandreon/PhilanthropyAndFundraising/Volume%202/14%20KarlanList.pdf); also NBER w12338) | **Verified.** Full text: abstract, §I, Table 2A, footnotes 4 and 14 | Randomized direct-mail field experiment; 50,083 prior donors of a politically oriented nonprofit; 16,687 control, 33,396 match | Revenue per letter $0.813 → $0.967 (+19%); response 1.8% → 2.2% (+22%) (pp. 1775, 1781). Ratios 2:1 and 3:1 add nothing over 1:1. Elasticity −0.30 before taxes (p. 1783). Red states +55%; blue states flat | No parameter (amount given, one recipient; pull and price confounded). The funder was unnamed: "a concerned fellow member", "anonymous supporters" (pp. 1775, 1777) |
| Andreoni & Petrie (2004), *J. Public Econ.* 88, 1605–1623 ([author's copy](https://econweb.ucsd.edu/~jandreon/Publications/JPubE2004.pdf)) | **Verified.** Abstract, design, Tables 2, 5, 6 | Lab public-goods game; 200 students, groups of 5, 40 rounds; the 2×2 cells (amounts shown, photos shown) plus two fund-raising cells | Share of endowment given: baseline 30.3%, amounts only 26.9%, photos only 39.5%, both 48.1% (+59% over baseline; +78.8% over amounts only, p = 0.0001) (pp. 1613–1614). Given the option, 52.8% went to the announced good, 3.0% to the anonymous one (p. 1617) | No parameter directly. It tests visibility among peers who are themselves exposed, not a funder's attribution |
| Peacey & Sanders (2013; revised 2014), *Masked Heroes*, CMPO working papers 13/303 and [14/329](https://www.bristol.ac.uk/media-library/sites/cmpo/migrated/documents/wp329.pdf) ([13/303](https://www.bristol.ac.uk/media-library/sites/cmpo/migrated/documents/wp303.pdf)) | **Verified.** 13/303 through §3; 14/329 Tables 3 and 6. Not peer reviewed; no journal version listed on IDEAS on 2026-11-05 | Observational; 73,584 donations to 3,984 London Marathon pages (2010, Virgin Money Giving); 12% anonymous, chosen by the donor. Later against earlier gifts in a narrow window around a gift | **The abstract's "around 4%" holds for large gifts only** (over £60). Full sample: "no significant effect" at any bandwidth. Followers of a large anonymous gift, against a large public one: +0.041 (SE 0.019), +0.043 (0.020), +0.035 (0.016) log points; 0.028 (0.026) at the narrowest; +0.047 (0.019) in the full-sample interaction (Table 3, p. 18). First large gift only: 2.5%, not significant. Table 3's stars do not match its legend, so the SEs are given | Question B. Not λ: amount given to one page. The anonymous gift still pulls, so at *π* = 0 a visible size can move others |
| Wang & Ye (2026), *Anonymous Donors, Visible Effects*, *J. Management Information Systems* 43(3), 992–1022 ([abstract](https://jmis-web.org/articles/1770)) | **Abstract only, verify before citing.** Closed access: the publisher returned 403 and an open-access index lists no open copy. Design, sample size, standard errors and the experiment's result were not read | GoFundMe medical campaigns, donation-level data; a randomized experiment is reported, unread | As the abstract states it: each anonymous donation among the three most recent "reduces subsequent donation amounts by approximately 5.5 percent, net of campaign heterogeneity". Large anonymous gifts attenuate it; late-stage campaigns intensify it. Not checked against any table | Question B. Not λ. This is the "2026 GoFundMe study" of the earlier draft |
| Dietvorst, Simmons & Massey (2015), *JEP: General* 144(1), 114–126 ([copy](https://marketing.wharton.upenn.edu/wp-content/uploads/2016/10/Dietvorst-Simmons-Massey-2014.pdf), advance online) | **Verified.** Abstract, methods, main analyses, Figure 3 (labels on the chart), general discussion | Five incentivized online and lab studies (N from 206 to 1,036); forecasting MBA performance and airline passengers; a binary choice to tie one's bonus to the model or a human | Share choosing the model: 54% to 69% with no performance seen; 23% to 49% after seeing it perform (Studies 1, 3a, 3b, 4), a fall of 10 to 42 points; 13% to 34% in Study 2 (Figure 3, p. 7). Seeing the human err had no significant effect | Lowers λ toward 0 once errors are seen, so λ depends on *σ_a* and on feedback. **It is not λ < 0**: nobody moves opposite to the model |
| Logg, Minson & Moore (2019), *OBHDP* 151, 90–103 ([open copy](https://escholarship.org/content/qt9v38k9m6/qt9v38k9m6.pdf)) | **Verified.** Abstract, the measure's definition, results of Experiments 1A to 4, §6. Experts' values appear only on charts and are not quoted | Experiments with lay online samples and students, and 70 national-security experts; identical advice, labeled algorithm or human; factual estimates and forecasts, partly incentivized | Weight on advice, algorithm against human: 0.45 / 0.30 (N = 202, *d* = 0.42; p. 93); 0.37 / 0.21 (N = 215; p. 94); 0.38 / 0.26 (N = 286, *d* = 0.44; p. 95); 0.50 / 0.35 (separate evaluation, *d* = 0.44; p. 96); 0.34 / 0.24 (N = 671, *d* = 0.33; p. 99). Chose the algorithm over another person 88%, over themselves 66% (N = 403; p. 97). Experts "heavily discounted all advice sources" (p. 98) | **The closest match to λ**: the measure has the form of *w′* = (1 − λ) *w* + λ *p_A*. The algorithm-human gap is the analogue of E2's A against D. It was Winsorized to [0, 1] (p. 93), so **it cannot register λ < 0** |
| Pfeffer & Salancik (1978), *The External Control of Organizations* (Harper & Row; reissued Stanford, 2003) | **Not read, verify before citing.** Library records only; a lending copy exists at the Internet Archive and was not borrowed. A book of theory: no effect size should be expected from it | — | None extracted | The dependence channel of the paper's §4.1 (which makes the analogy without citing this book). No number enters the model from it |

### Output: anchors for λ by context

| Context | Anchor for λ | Basis |
|---|---|---|
| Factual judgment, lay people, algorithm label, no errors seen | 0.34 to 0.50 | Logg et al.; truncated at 0 and 1 |
| The same, human label (the analogue of arm D) | 0.21 to 0.35 | Logg et al. |
| Experts, or after errors are seen | lower, no λ-unit number read | Logg et al., Experiment 4; Dietvorst et al., in choice shares |
| Allocating money among recipients, the model's actual setting | **no anchor** | nothing read measures it |
| λ < 0 | **no anchor** | nothing read shows it; the only instrument in λ's unit cannot show it |

These are analogies from a different task, not estimates of λ. The simulation sweeps past both ends of them. They
are fixed only in the pre-registration, after the founder's review of the model, and P2's range for λ\* cannot claim
more than this table does.

### What this reads against in the model (ruled at the model's review, 2026-11-26; `MODEL.md` carries each ruling)

1. **Aversion is not λ < 0.** `MODEL.md` glosses λ < 0 as aversion, and this file used to say the algorithm
   literature requires it. Neither paper shows it: aversion here means less reliance, λ falling toward 0. Keep
   λ < 0 as a swept region with no empirical anchor, or find a source that measures movement away.
2. **The pull may not pass through attribution.** The leakage arm sets the expected pull at λ *π*, which is zero at
   *π* = 0. Yet the seed, the match and the large anonymous gifts above all moved later giving with no named
   giver. What travels in those data is a visible gift, not a name. In regime *C* no gift is visible at a
   recipient, so this term may be zero there, but what protects *C* would then be the absence of a visible
   allocation rather than anonymity as such. E2's arms A and B change both at once; an arm showing the allocation
   without naming the source would separate them, and it is the arm closest to these field data.
3. **The model has no variable for how much people give.** Five of the sources measure exactly that, and none
   measures direction among recipients. If attribution draws in more giving, *C′* carries a benefit its welfare
   *W* does not count. Either add it or state that it is out of scope.
4. **Two channels share one λ.** The paper's §4.1 is about dependence: choosing what the funder would reward with
   future funding. The studies above measure signal and deference, in one shot. E2 as designed is also one shot, so
   it would measure the second and not the first.
5. **λ's scale.** *w′* = (1 − λ) *w* + λ *p_A* mixes *w_ij* = *v_j* + *η_ij*, which is not normalized, with *p_A*, which
   is. A weight on advice carries over only if both sit on one scale.
6. **λ is not independent of the other inputs.** It falls with seen errors (*σ_a*) and with expertise (*σ_h*), and it
   is held constant across periods. The planned Sobol analysis treats its inputs as independent.

**Ruled 2026-11-26 (the founder's review):** 1 → λ < 0 swept with no anchor · 2 → the case *C°* in the model,
and arm E below if E2 runs · 3 → out of scope, stated · 4 → λ is deference only, dependence covered by the
sweep · 5 → one scale · 6 → λ = λ₀ · *g*(*σ_a*, *σ_h*), with λ₀ and the slopes as the independent inputs.

## E2. A pre-registered online experiment (what a grant would fund; decided after the simulation)

Participants on an online research panel each direct a pool of real money, paid to real charities after
the study, among several charities.

| Arm | The pool | Tests |
|---|---|---|
| A, attributed | includes a contribution from an AI system, and the AI's own allocation is shown | the pull of a visible AI funder |
| B, anonymous | the same contribution, disclosed only in aggregate ("the pool includes contributions from several sources, one of them an AI system"), never per contribution | the paper's design: transparent overall, anonymous per contribution (§4.4) |
| C, control | no AI contribution | the baseline |
| D, human funder | the same contribution, attributed to a human donor | whether the pull is about AI or about any visible funder |
| E, shown, unnamed (added 2026-11-26) | the same allocation shown, its source not named | whether the pull is the visible allocation or the name (E1, point 2) |

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

*Revised 2026-11-26 (founder: "go per your recommendation"): the simulation runs first, with no human
participants, and E2 waits for what it finds.*

E1 (read 2026-11-05) → the simulation (`PLAN.md` steps 3 to 5) → **E2 decided by the simulation's λ\*** →
if it runs: designed and costed (the grant application), pre-registered, ethics review, run → E3 when a
suitable public dataset is identified.

- **The deciding rule** (approved at the model's review, 2026-11-26), fixed in `PREREGISTRATION.md` before any model
  code so the simulation's result cannot choose it. λ\* is not one number: it moves with *K*, *ρ*, *q* and
  *σ_a*, and results are reported as regions. So the candidate reads it as a share: E2 is designed and costed
  if λ\* is at or below the top of E1's anchors (0.50) in at least half of the swept region of the other
  inputs; otherwise it waits. The 0.50 and the half are both judgments (E1's anchors are analogies from
  another task), and the hostile reader may argue them differently before the pre-registration.
- **What E2 would test.** Arm A shows "the AI's own allocation". Under the paper's current form, *C\**, a
  public draw picks the recipients and *A* has no allocation to show, so E2 tests the premise of the
  disclosed variant *C*, and the open question of row D above: whether people's allocations among recipients
  move toward a shown one at all, which nothing read so far measures.
- **Two design questions owed before E2's pre-registration, if it runs:** arm D shows "the same
  contribution, attributed to a human donor", which is true only if a real human donor stands behind that
  allocation; and reproducing arm A means naming the AI system and version that made the allocation.
