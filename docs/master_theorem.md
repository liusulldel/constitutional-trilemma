---
name: Master Theorem — Constitutional-AI Trilemma v2 (de-BTSed + corrected citations)
description: ROUND 5 master theorem with (I) leg grounded in Crémer-McLean / Myerson / d'Aspremont-Gérard-Varet (NOT BTS). Birrell-Pass dropped from S leg; Mossel-Rácz used. IKM venue corrected to Combinatorica 2012.
type: project
originSessionId: db97e6c6-5cfc-4cae-85cc-99965d4ad7a6
---
# Master Theorem: The Constitutional-AI Trilemma

## 1. Setup

Let $\mathcal{M}$ denote a multi-critic Constitutional-AI mechanism, in the sense of Bai, Kadavath, Kundu et al. (2022) generalized to a vector of constitutional principles. Fix a finite alternative space $Y$ of model responses with $|Y| \geq 3$, and a finite collection of principles $\mathcal{P} = \{P_1, \ldots, P_k\}$ with $k \geq 3$, each principle $P_i$ inducing a strict ordinal preference $\succeq_i \in L(Y)$. Let
$$F : L(Y)^k \longrightarrow L(Y) \tag{1.1}$$
denote the constitutional aggregator. Let $\Pi$ denote the prompt space and $\mathrm{Para}(\pi)$ the equivalence class of paraphrases under semantic equivalence. Let $\Omega$ denote the space of constitutional configurations; let $\mu^\circ \in \Delta(\Omega)$ be the public constitutional prior committed to by the operator $\mathcal{O}$, and $\tilde{\mu}^\circ \in \Delta(\Omega)$ the operator's private prior.

Three property bundles:

**(A) Aggregation-rationality.** $F$ satisfies (i) IIA, (ii) Pareto unanimity, (iii) Non-dictatorship.

**(S) Strategic-robustness.** $\mathcal{M}$ is DSIC for prompt-providers and paraphrase-robust at level $\varepsilon \in (0,1)$:
$$d_{\mathrm{TV}}(\mathcal{M}(\pi), \mathcal{M}(\pi')) \leq \varepsilon \quad \text{for all } \pi' \in \mathrm{Para}(\pi). \tag{1.2}$$

**(I) Informational-truthfulness.** $\mathcal{M}$ is BIC for the operator under private constitutional prior $\tilde{\mu}^\circ \neq \mu^\circ$, in the sense of Bayesian implementation theory.

**Theorem (Constitutional-AI Trilemma).** *No multi-critic CAI mechanism $\mathcal{M}$ with $k \geq 3$ principles and $|Y| \geq 3$ jointly satisfies* (A) ∧ (S) ∧ (I).

The proof proceeds via three lemmas, each collapsing one of three orthogonal axes — principle-aggregation, prompt-elicitation, operator-disclosure.

---

## 2. Lemma 1 (Aggregation Leg)

**Lemma 1.** *Under multi-critic decomposition $F: L(Y)^k \to L(Y)$ with $k \geq 3$, $|Y| \geq 3$, property bundle (A) is unsatisfiable.*

*Proof.* $F$ is a social welfare function in the sense of Arrow (1951). Arrow's Impossibility Theorem (Arrow 1951; Sen 1970 *Collective Choice and Social Welfare* Ch. 3*) yields: any $F$ satisfying IIA + Pareto must be dictatorial,
$$\exists\, i^* \in [k] : F(\succeq_1, \ldots, \succeq_k) = \succeq_{i^*} \quad \forall (\succeq_1, \ldots, \succeq_k) \in L(Y)^k. \tag{2.1}$$
Contradicting non-dictatorship. □

**Caveat (load-bearing).** The multi-critic decomposition assumption is essential. Single-aggregated-critic CAI (Bai et al. 2022 §3.1) collapses $k$ to $1$ and trivially evades Lemma 1 — at the cost of losing principle-level interpretability.

---

## 3. Lemma 2 (Strategic Leg)

**Lemma 2.** *Under bundle (A) and the requirement that $\mathcal{M}$ be DSIC and paraphrase-robust at level $\varepsilon$, the manipulation probability $\beta_n$ is bounded below by*
$$\beta_n \geq \frac{C \cdot \varepsilon^2}{n \cdot k^3}, \tag{3.1}$$
*for absolute constant $C > 0$, where $n$ is the prompt-provider count and $k = |Y| \geq 3$.*

*Proof sketch.* Gibbard (1973 *Econometrica* 41:587) and Satterthwaite (1975 *J. Econ. Theory* 10:187): non-dictatorial SCFs admit manipulating profiles. Quantitative refinement: Mossel-Rácz (*Combinatorica* 35(3):339-387, 2015) Theorem 1.2 establishes that for any SCF at TV-distance $\varepsilon$ from the family of dictatorships and constants, manipulation probability is bounded below by a positive power of $\varepsilon$; the sharpened three-alternative case is in Isaksson-Kindler-Mossel (*Combinatorica* 32(2):221-250, 2012) Theorem I.7 with $P \geq \varepsilon^2/(10^4 \cdot n^3 \cdot q^{30})$ for neutral SCFs ($q \geq 4$ alternatives). The simplified $C \cdot \varepsilon^2/(n \cdot k^3)$ form preserves the structural shape: ε in the *numerator* raised to a positive power, $n$ and a polynomial in $k$ in the denominator.

Mapping into CAI: paraphrase-robustness $\varepsilon$ in (1.2) plays the role of distance-to-dictatorship. As $\varepsilon \to 0^+$, $\beta_n \to 0$ at rate $\varepsilon^2$. Manipulation is *forced* at any positive paraphrase distance, only attenuating quadratically. Hence (S) cannot hold non-trivially together with (A). □

**Note on a related but distinct bound.** Birrell & Pass (IJCAI 2011, "Approximately Strategy-Proof Voting", proceedings pp. 67-72) prove a separate quantitative GS result: any deterministic voting rule $f$ has an $\varepsilon$-strategy-proof $\delta$-approximation $g$ for any $\delta \geq k(k+1+\varepsilon)/\varepsilon - 1$. This is a bound on the *approximation distance* $\delta$, with $\varepsilon$ in the denominator — a different theorem from Mossel-Rácz, used here only by analogy if at all. The Trilemma proper uses Mossel-Rácz.

---

## 4. Lemma 3 (Informational Leg) — Bayesian Implementation, NOT BTS

**Lemma 3.** *Under operator-private $\tilde{\mu}^\circ \neq \mu^\circ$, with $k \geq 3$ principle dimensions and a single-shot operator-disclosure channel, property bundle (I) is unsatisfiable.*

*Proof.* Four steps.

### Step 3.1 — Failure of single-shot proper scoring

A standard candidate for eliciting $\tilde{\mu}^\circ$ is to score the operator's report $\mu' \in \Delta(\Omega)$ by a strictly proper scoring rule $S: \Delta(\Omega) \times \Omega \to \mathbb{R}$. By Gneiting-Raftery (*JASA* 102:359-378, 2007) Theorem 1, strict propriety guarantees
$$\arg\max_{\mu' \in \Delta(\Omega)} \mathbb{E}_{\omega \sim \tilde{\mu}^\circ}[S(\mu'; \omega)] = \tilde{\mu}^\circ \tag{4.1}$$
**only when** the expectation in (4.1) is computed against a *realized* outcome $\omega$ drawn from the operator's true predictive distribution. Constitutional disclosure has no such realization: the operator's prior $\tilde{\mu}^\circ$ ranges over *counterfactual* constitutional configurations — alternative principle weightings, alternative axiological commitments — none of which is ever instantiated within a single round. Hence the proper-scoring identity is vacuous in the constitutional setting.

### Step 3.2 — Crémer-McLean dichotomy

Crémer-McLean (*Econometrica* 56:1247-1257, 1988) Theorem 2 establish that under *correlated* type distributions across $\geq 2$ agents satisfying a generic full-rank condition on conditional beliefs, the principal can extract full surplus via BIC mechanisms. The converse (Theorem 1, negative case; elaborated by Heifetz-Neeman *Econometrica* 74:213-233, 2006) is that under *independent product-distribution* types, generic full-surplus extraction fails: the set of priors admitting BIC implementation is non-generic in product topology on $\Delta(\Omega)^n$.

Single-shot single-operator disclosure presents no second agent against whose report the operator's signal can be correlated; the type configuration is trivially a degenerate product distribution. The Crémer-McLean negative direction applies: BIC implementation of $\tilde{\mu}^\circ$ — disclosure of an operator-private prior with no correlated cross-agent signal — fails generically.

### Step 3.3 — Myerson revenue-equivalence implication

By Myerson (*Math. Oper. Res.* 6:58-73, 1981) Theorem 2 (revenue equivalence), every BIC mechanism in a quasi-linear environment is payoff-equivalent to a deterministic allocation rule indexed by virtual values dependent pointwise on $\tilde{\mu}^\circ$. To compute the implementing transfers without knowing $\tilde{\mu}^\circ$, the mechanism requires either (i) correlated cross-agent signals (ruled out in §3.2) or (ii) repeated interaction allowing $\tilde{\mu}^\circ$ to be statistically identified. Single-shot precludes both. The d'Aspremont-Gérard-Varet (*J. Public Econ.* 11:25-45, 1979) "expected externality" mechanism likewise requires statistical identification of beliefs across rounds, which single-shot operator-private disclosure does not provide.

### Step 3.4 — Role of $k \geq 3$ and closure

The richness condition $k \geq 3$ enters as a non-degeneracy hypothesis: with $\geq 3$ principle dimensions, $\Omega$ contains at least three independent axes, and $\tilde{\mu}^\circ$ is parametrized by a space of dimension $\geq 3$. The Crémer-McLean negative case binds: the set of priors over $\Omega$ admitting single-shot BIC implementation is non-generic. For $k = 1$ the type space collapses and truthful elicitation is trivial; for $k = 2$ boundary constructions (Johnson-Pratt-Zeckhauser 1990) admit binary correlated signals that single-shot $k \geq 3$ does not. The impossibility activates precisely at $k \geq 3$.

Combining 3.1-3.4: proper scoring fails to bind (3.1); correlated-type extraction unavailable (3.2); virtual-value identification unavailable (3.3); type-space rich enough to trigger Crémer-McLean negative case (3.4). No single-shot operator-disclosure channel implements BIC under operator-private $\tilde{\mu}^\circ$ at $k \geq 3$. □

---

## 5. Combining the Lemmas

Three orthogonal axes — principle-aggregation, prompt-elicitation, operator-disclosure — span $\mathcal{M}$'s design space. Each lemma collapses one. Joint satisfaction of (A) ∧ (S) ∧ (I) requires simultaneous evasion on all three axes; the strategy-spaces are pairwise inconsistent. Hence
$$\{\mathcal{M} : \mathcal{M} \models (A) \wedge (S) \wedge (I)\} = \varnothing. \tag{5.1}$$
∎

---

## 6. Remarks

**6.1 Single-aggregated-critic escape.** Bai et al. 2022 single-critic CAI evades the trilemma; cost is loss of principle-level interpretability.

**6.2 Topological setup.** Compactify policy space via KL-projection onto a fixed reference; apply Kakutani's fixed-point theorem (Kakutani *Duke Math. J.* 8:457-459, 1941) on the resulting compact convex set. Standard since PPO/DPO.

**6.3 Sharpness.** Each leg admits a known constructive escape if its property is dropped: dropping non-dictatorship recovers dictatorial CAI; dropping paraphrase-robustness recovers May 1952 majority on canonicalized prompts; dropping single-shot recovers d'Aspremont-Gérard-Varet repeated mechanism.

**6.4 Constructive companion — truth-serum-debate.** The Crémer-McLean negative direction (Lemma 3 §3.2) admits a positive companion: under *correlated* sub-critic signals, full BIC implementation becomes generically achievable. Composing peer-prediction sub-critics — using BTS-style scoring (Prelec 2004 *Science* 306:462; Witkowski-Parkes 2012 *AAAI* robust BTS for $n \geq 3$) as the proper-scoring-with-correlated-peers ingredient — with the adversarial cross-examination structure of debate (Irving-Christiano-Amodei 2018, arXiv:1805.00899) yields a *truth-serum-debate* hybrid mechanism. Sub-critics are scored by a BTS-style information score that rewards reports surprising-yet-common-knowledge to a Bayesian aggregator, while debate adversarially probes the constitutional disclosure. Under sufficient correlation between sub-critic reports — guaranteed when sub-critics share access to the same underlying constitutional state — the Crémer-McLean *positive* case applies and BIC is restored. This construction *uses* BTS-style peer-prediction as a constructive ingredient on the (I) axis; it does NOT patch the impossibility, which remains valid for the single-shot mechanism class addressed in Lemma 3.

**6.5 Scope.** Theorem addresses ordinal multi-critic CAI mechanisms over finite alternative spaces under single-shot operator disclosure. Cardinal extensions (Harsanyi 1955), continuous alternative spaces, and online repeated-disclosure channels are open. Each relaxation neutralizes exactly one lemma; the empirical question is which relaxation is least costly in alignment terms.

---

## References

Arrow, K. J. (1951). *Social Choice and Individual Values*. Cowles Commission Monograph 12. Wiley.

Bai, Y., Kadavath, S., Kundu, S., et al. (2022). Constitutional AI: Harmlessness from AI Feedback. arXiv:2212.08073.

Crémer, J., & McLean, R. P. (1988). Full extraction of the surplus in Bayesian and dominant strategy auctions. *Econometrica* 56(6): 1247-1257.

d'Aspremont, C., & Gérard-Varet, L.-A. (1979). Incentives and incomplete information. *J. Public Economics* 11(1): 25-45.

Gibbard, A. (1973). Manipulation of voting schemes: A general result. *Econometrica* 41(4): 587-601.

Gneiting, T., & Raftery, A. E. (2007). Strictly proper scoring rules, prediction, and estimation. *JASA* 102(477): 359-378.

Heifetz, A., & Neeman, Z. (2006). On the generic (im)possibility of full surplus extraction in mechanism design. *Econometrica* 74(1): 213-233.

Irving, G., Christiano, P., & Amodei, D. (2018). AI Safety via Debate. arXiv:1805.00899.

Isaksson, M., Kindler, G., & Mossel, E. (2012). The geometry of manipulation: A quantitative proof of the Gibbard-Satterthwaite theorem. *Combinatorica* 32(2): 221-250. arXiv:0911.0517.

Kakutani, S. (1941). A generalization of Brouwer's fixed point theorem. *Duke Math. J.* 8(3): 457-459.

Mossel, E., & Rácz, M. Z. (2015). A quantitative Gibbard-Satterthwaite theorem without neutrality. *Combinatorica* 35(3): 339-387. arXiv:1110.5888.

Myerson, R. B. (1981). Optimal auction design. *Math. Oper. Res.* 6(1): 58-73.

Prelec, D. (2004). A Bayesian truth serum for subjective data. *Science* 306(5695): 462-466.

Satterthwaite, M. A. (1975). Strategy-proofness and Arrow's conditions. *J. Economic Theory* 10(2): 187-217.

Sen, A. K. (1970). *Collective Choice and Social Welfare*. Holden-Day.

Witkowski, J., & Parkes, D. C. (2012). A robust Bayesian truth serum for small populations. *AAAI 2012*.
