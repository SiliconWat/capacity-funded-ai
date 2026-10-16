# Plan

*Living document; history in git. The pre-registration, when it exists, is a separate file that is never
edited.*

## Steps

1. **Model design** (`MODEL.md`, draft). Reviewed by the founder before anything is fixed.
2. **Prior-art check** of the modeling questions, published in full including what fails: donor influence on
   grantees, anonymous giving, crowding out, statistical de-anonymization of payments, AI control, and
   principal-agent theory. What is already known is cited, not re-derived.
3. **`PREREGISTRATION.md`**: the model, the parameter ranges, the predictions, and what would count against
   the paper, pushed before any model code. Dated within minutes by the RFC 3161 job, stamped to Bitcoin
   (`TIMESTAMPS.md`), and mirrored to a registry reviewers recognize (OSF or AsPredicted).
4. **The simulation** (Python, agent-based), with the controls in `MODEL.md` run before any result is read.
5. **Results and a paper**, submitted for peer review (venues below).
6. **The empirical arm** (`EMPIRICAL.md`): calibration from published evidence (alongside step 2); the
   pre-registered online experiment; leakage in public payment data.

## Reproducibility (fixed now, enforced from the first line of code)

- Versions pinned in `requirements.txt`; Python 3.12.
- Every run seeded; the seed written into its output.
- One command regenerates every figure and number; numbers enter the paper only from generated files.
- CI (added with the first code) reruns a small version of every figure and every control on each push.

## Venues (researched 2026-10-15; confirm each before submitting)

| Paper | Venue | Why | Timing |
|---|---|---|---|
| The model (questions 1–4, 6) | **AIES** (AAAI/ACM Conference on AI, Ethics, and Society) | AI-governance scope; "We welcome work that appears as a preprint"; 10 pages | 2027 call not out; the 2026 deadline was May 21 |
| The model, economics framing | **ACM EC** (Economics and Computation) | topics include "Agent-based modeling" and "Laboratory and field experiments"; arXiv allowed; fully open access | 2027 call not out; 2026 papers were due February 9 |
| The simulation in depth | **JASSS** (Journal of Artificial Societies and Social Simulation) | the agent-based-modeling journal | rolling |
| The experiment (E2) | **Experimental Economics**, as a **Registered Report** | Stage 1 is reviewed before any data exist, which fits a pre-registered design | rolling |
| Not now | FAccT 2027 | abstracts due 2026-10-27: too soon for work with no model yet | — |

Unaffiliated authors: FAccT asks them to create an OpenReview account early; ACM venues charge an
article-processing fee to authors outside ACM Open institutions. Every venue: ask whether the paper's Zenodo
deposit counts as prior publication.

## Grants

- **Anthropic Economic Futures Program: research awards are CLOSED.** Its page says: "We are not currently
  accepting applications." When open (2025), awards were up to $50,000 for empirical research on AI's
  economic impacts, aimed at economists, data scientists and PhD students. Institutions can propose a
  partnership by email (economicfutures@anthropic.com). The experiment (E2) is the fundable part.
- **A grant needs a named recipient:** the founder as an individual, or an organization. Silicon Wat's
  nonprofit is not formed. To be settled before any application.
- **Ethics review costs** (for E2), as published: Solutions IRB lists an exempt review at $1,200 and an
  expedited social-behavioral review at $2,100; whether it accepts unaffiliated researchers is not stated.

## Fixes owed in the source paper (its own revision, not here)

The re-survey of 2026-10-15 found, in *Capacity-Funded for AI, Human-Disbursed*:

1. §5.1 step 1 pays half of the AI's self-thank reward into the resident's spendable wallet, while §5.2 says
   the AI has "Zero over flow-direction". Resolve it or concede it.
2. The worked example predates the paper's own current form (in kind, chosen by a verifiable draw).
3. The names predate the 2026-10-04 rename (re-tip jar → Re-Thank Fund℠).
4. The AI-control and principal-agent literatures are not cited.

## Prior art (quick census, 2026-10-15)

Pre-registered before any search (a private push, so attested by the host only; a public copy will
accompany the paper). Aperture: English; commercial web and non-commercial giving practice; patents by keyword
search; 14 logged queries. Academic indexes, standards bodies and non-English sources were not searched.

| Conjunct | Verdict | Nearest prior art |
|---|---|---|
| (a) a visible funder's choice pulls others' decisions toward it | **already public** | seed money (List & Reiley 2002, *JPE*); leadership giving (Andreoni 2006); anonymous gifts change later donors' gifts (Peacey & Sanders 2013); donors deliberately following large funders ("funging", "coattailing") |
| (b) per-contribution anonymity broken from amounts and timing | **narrowed** | amount and timing correlation attacks on payments; nothing applying them to an anonymous funder's share in giving |
| (c) a random or verifiable draw removes an allocator's discretion | **already public** | grant lotteries (Fang & Casadevall 2016; the Volkswagen Foundation trial); sortition against capture (Bagg 2022); publicly verifiable selection (RFC 2777, RFC 3797); a granted US patent on automated donation allocation that may select the recipient at random (US9105055B2) |
| (d) a control evaluation of a misaligned AI agent holding money | **narrowed** | control evaluations as an AI-safety practice; none applied to funding architectures |
| (e) all of it in one model, with the welfare price of the draw | **not found in this aperture on this date** | agent-based models of research-grant allocation |

**What this work may claim:** only the composition, one model comparing the three designs on soft control,
leakage and a misaligned funder's capture, including the price of the draw. Never "novel"; at most "not found
in the aperture above on 2026-10-15." The control was found only by a query naming it, so the null on (e) is
weak; a full census (academic indexes, non-English) runs before any paper claims it.

## Who reviews

`REVIEWERS.md`: a hostile economist (mechanism design) before the pre-registration; the founder's approval
before anything is fixed.
