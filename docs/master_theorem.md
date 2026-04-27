# The Constitutional Trilemma: Working Theorem Sketch

This note states the current public version of the argument. It is a working
theorem sketch, not a completed general impossibility proof for all
Constitutional AI systems.

## Setup

Consider a multi-critic Constitutional AI mechanism that aggregates reports from
several constitutional critics over a finite set of candidate responses. The
project studies tensions among three desiderata:

- Aggregation rationality: the aggregation rule satisfies standard social-choice
  conditions such as Pareto unanimity, independence of irrelevant alternatives,
  and non-dictatorship.
- Strategic robustness: prompt providers or critics cannot benefit from
  strategically changing reports that are paraphrase-equivalent under the model.
- Informational truthfulness: the operator has no incentive to misrepresent a
  private constitutional prior in a single-shot disclosure channel.

The conservative claim is that these three goals impose incompatible pressures
under the model assumptions below. The strongest current result is an Arrow-style
aggregation obstruction; the strategic and informational legs are best read as
diagnostics for what becomes costly when one relaxes the aggregation conditions.

## Lemma 1: Aggregation Obstruction

If the critic-level aggregation rule is a social welfare function over at least
three alternatives and satisfies IIA, Pareto unanimity, and non-dictatorship,
then Arrow's theorem rules it out. This leg is load-bearing and should not be
read as a new theorem independent of Arrow. It identifies when a multi-critic
CAI design has imported the classic social-choice problem.

## Lemma 2: Strategic-Robustness Cost

Gibbard-Satterthwaite-style results and quantitative refinements imply that
non-dictatorial aggregation rules are vulnerable to manipulation under suitable
domains. In this project, paraphrase robustness is treated as an analogy to
distance from manipulable reporting behavior.

The current public version does not claim a universal closed-form lower bound
for CAI manipulation probability. Any numeric bound requires a proved reduction
from the CAI reporting model to the assumptions of the cited quantitative
Gibbard-Satterthwaite theorem.

## Lemma 3: Informational-Truthfulness Cost

Single-shot operator disclosure is difficult to make Bayesian incentive
compatible when the operator's private constitutional prior differs from the
public prior. Mechanism-design results such as Cremer-McLean, Myerson, and
d'Aspremont-Gerard-Varet are relevant because they show how strongly truthfulness
depends on type structure, correlated signals, transfers, and repeated
identification.

The current public version treats this as a modeling obstruction, not as a
standalone theorem. A complete proof would need explicit utilities, allocation
rules, transfers or scoring payoffs, type spaces, and belief assumptions.

## Combined Reading

The project should be read as a map of tradeoffs:

- If the design keeps full Arrow-style aggregation rationality, the aggregation
  leg alone creates an impossibility.
- If the design relaxes aggregation rationality, the strategic leg asks what
  manipulation or paraphrase-instability cost is paid.
- If the design relaxes single-shot disclosure, the informational leg asks what
  repeated, correlated, or externally audited signal is needed for truthful
  elicitation.

This framing is intentionally narrower than a claim that all Constitutional AI
pipelines must fail. It says that a particular formalization of multi-critic
aggregation makes the price of pluralism explicit.

## References Used

- Arrow, K. J. (1951). *Social Choice and Individual Values*.
- Gibbard, A. (1973). Manipulation of voting schemes.
- Satterthwaite, M. A. (1975). Strategy-proofness and Arrow's conditions.
- Isaksson, M., Kindler, G., and Mossel, E. (2012). The geometry of
  manipulation.
- Mossel, E., and Racz, M. Z. (2015). A quantitative Gibbard-Satterthwaite
  theorem without neutrality.
- Cremer, J., and McLean, R. P. (1988). Full extraction of the surplus in
  Bayesian and dominant strategy auctions.
- Myerson, R. B. (1981). Optimal auction design.
- d'Aspremont, C., and Gerard-Varet, L.-A. (1979). Incentives and incomplete
  information.
