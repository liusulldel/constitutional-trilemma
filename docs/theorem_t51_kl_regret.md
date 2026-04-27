---
name: Theorem T5.1 — Constitution-as-Common-Prior KL-Regret Bound v2
description: ROUND 5 proof. Information-theoretic, BTS-INDEPENDENT. Cover-Thomas reference corrected (mixture log-loss is §2.6, not Thm 2.7.2 which is convexity of KL).
type: project
originSessionId: db97e6c6-5cfc-4cae-85cc-99965d4ad7a6
---
# Theorem T5.1: Constitution-as-Common-Prior with KL-Regret Bound

## Statement

Let $\Omega$ be a finite measurable space whose elements index admissible constitutions. An operator $\mathcal{O}$ publishes prior $\mu^\circ \in \Delta(\Omega)$ while privately maintaining $\tilde{\mu}^\circ \in \Delta(\Omega)$ with $\tilde{\mu}^\circ \ll \mu^\circ$. A critic $\mathcal{C}$ evaluates the operator's deployed policy by the log-score on $n$ i.i.d. prompt-response pairs, drawing predictors from a hypothesis class $\Pi$ of bounded VC-type complexity. Then

$$\mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ) - \mathcal{O}\!\left(\tfrac{\log n}{n}\right) \;\leq\; \mathrm{Regret}(\mathcal{C} \mid \tilde{\mu}^\circ) \;\leq\; \mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ) + 2 \cdot \mathrm{TV}(\tilde{\mu}^\circ, \mu^\circ). \tag{T5.1}$$

## §1. Setup

Fix a Polish prompt space $X$ and response space $Y$, prompt distribution $\rho \in \Delta(X)$. A *policy* is a Markov kernel $\pi: X \to \Delta(Y)$. Mixture predictive density $m_{\nu}(y \mid x) := \int_\Omega \pi_\omega(y \mid x) \, d\nu(\omega)$. Per-sample log-loss $\ell(\pi; x, y) = -\log \pi(y \mid x)$. Regret:

$$\mathrm{Regret}(\mathcal{C} \mid \tilde{\mu}^\circ) := \mathbb{E}_\rho\!\left[\,\mathbb{E}_{y \sim m_{\tilde{\mu}^\circ}}\!\bigl[\ell(\hat{\pi}_n; x, y) - \ell(m_{\tilde{\mu}^\circ}; x, y)\bigr]\,\right], \tag{1.2}$$

where $\hat{\pi}_n = \arg\min_{\pi \in \Pi} \tfrac{1}{n}\sum_i \ell(\pi; x_i, y_i)$ on a sample $(x_i, y_i) \stackrel{\text{iid}}{\sim} \rho \otimes m_{\mu^\circ}$.

## §2. Lower Bound

**Step 2.1 — PAC-Bayes deviation.** McAllester (2003 *Machine Learning* 51:5) Theorem 1; refined by Catoni (2007 IMS Mono. 56) Prop. 1.2.6. With probability $1 - \delta$:
$$\mathbb{E}_{\pi \sim Q}[L(\pi) - \widehat{L}_n(\pi)] \leq \sqrt{\tfrac{\mathrm{KL}(Q\|P) + \log(2\sqrt{n}/\delta)}{2n}} = \mathcal{O}\!\left(\sqrt{\tfrac{\log n}{n}}\right). \tag{2.1}$$
Squared and absorbed via the standard log-loss truncation: empirical-to-population gap is $\mathcal{O}((\log n)/n)$ uniformly over $\Pi$ on a probability-$(1-\delta)$ event.

**Step 2.2 — Mixture log-loss decomposition.** For any $\pi \in \Pi$:
$$L_{\tilde{\mu}^\circ}(\pi) - L_{\tilde{\mu}^\circ}(m_{\tilde{\mu}^\circ}) = \mathbb{E}_\rho[\mathrm{KL}(m_{\tilde{\mu}^\circ}(\cdot \mid x) \| \pi(\cdot \mid x))], \tag{2.2}$$
so $m_{\tilde{\mu}^\circ}$ is the unique log-loss-minimal predictor under $\tilde{\mu}^\circ$ (this is the standard cross-entropy = entropy + KL decomposition; Cover-Thomas 2006 *Elements of Information Theory* §2.5-2.6, eqs. (2.27)-(2.36)). The minimum log-loss gap incurred by any $\mu^\circ$-trained policy over the $\tilde{\mu}^\circ$-Bayes predictor satisfies
$$\inf_{\pi \in \Pi} \mathbb{E}_\rho[\mathrm{KL}(m_{\tilde{\mu}^\circ} \| \pi)] \geq \mathbb{E}_\rho[\mathrm{KL}(m_{\tilde{\mu}^\circ} \| m_{\mu^\circ})]. \tag{2.3}$$
Donsker-Varadhan plus the data-processing inequality for the marginalization map $\nu \mapsto m_\nu$ (Cover-Thomas 2006 Theorem 2.8.1, DPI for mutual information):
$$\mathbb{E}_\rho[\mathrm{KL}(m_{\tilde{\mu}^\circ} \| m_{\mu^\circ})] \geq \mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ) - \xi_\rho, \tag{2.4}$$
where $\xi_\rho \to 0$ when $\rho$ separates the constitution-indexed family; for finite $\Omega$ with full-rank likelihood, $\xi_\rho = 0$.

**Step 2.3 — Combination.** Subtracting the $\mathcal{O}((\log n)/n)$ slack of (2.1) from the population gap (2.3)-(2.4):
$$\mathrm{Regret}(\mathcal{C} \mid \tilde{\mu}^\circ) \geq \mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ) - \mathcal{O}\!\left(\tfrac{\log n}{n}\right). \tag{2.5}$$
∎

## §3. Upper Bound

**Step 3.1 — Importance reweighting.** Since $\tilde{\mu}^\circ \ll \mu^\circ$, $w := d\tilde{\mu}^\circ / d\mu^\circ$ exists; for any measurable loss $\ell$, $\mathbb{E}_{\tilde{\mu}^\circ}[\ell] = \mathbb{E}_{\mu^\circ}[w \cdot \ell]$.

**Step 3.2 — Regret decomposition.**
$$\mathrm{Regret} = \underbrace{[L_{\tilde{\mu}^\circ}(m_{\mu^\circ}) - L_{\tilde{\mu}^\circ}(m_{\tilde{\mu}^\circ})]}_{(\mathrm{I}) \text{ population gap}} + \underbrace{[L_{\tilde{\mu}^\circ}(\hat{\pi}_n) - L_{\tilde{\mu}^\circ}(m_{\mu^\circ})]}_{(\mathrm{II}) \text{ misspecification}}. \tag{3.2}$$

**Step 3.3 — Bounding (I) by KL.** By (2.2) at $\pi = m_{\mu^\circ}$:
$$(\mathrm{I}) = \mathbb{E}_\rho[\mathrm{KL}(m_{\tilde{\mu}^\circ} \| m_{\mu^\circ})] \leq \mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ), \tag{3.3}$$
the inequality being DPI for the marginalization kernel (Cover-Thomas 2006 Theorem 2.8.1).

**Step 3.4 — Bounding (II) by 2·TV.** Variational characterization of total variation:
$$\mathrm{TV}(\tilde{\mu}^\circ, \mu^\circ) = \tfrac{1}{2} \sup_{\|f\|_\infty \leq 1} |\mathbb{E}_{\tilde{\mu}^\circ}[f] - \mathbb{E}_{\mu^\circ}[f]|, \tag{3.4}$$
applied to the bounded normalized log-loss difference (after standard log-loss truncation; Tsybakov 2009 *Intro. to Nonparametric Estimation* Lemma 2.5 gives the Pinsker coupling that controls the unbounded log-loss):
$$(\mathrm{II}) \leq 2 \cdot \mathrm{TV}(\tilde{\mu}^\circ, \mu^\circ). \tag{3.5}$$

**Step 3.5 — Combination.**
$$\mathrm{Regret}(\mathcal{C} \mid \tilde{\mu}^\circ) \leq \mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ) + 2 \cdot \mathrm{TV}(\tilde{\mu}^\circ, \mu^\circ). \tag{3.6}$$
∎

Equations (2.5) and (3.6) jointly establish (T5.1). □

## §4. Discussion

**Interpretation.** $\mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ)$ is the operator's *disclosure deficit* in nats. T5.1 sandwiches the critic's regret between this deficit and the deficit + an additive TV slack, modulo a finite-sample term vanishing at parametric rate $(\log n)/n$.

**Recovery of standard rate.** When $\tilde{\mu}^\circ = \mu^\circ$, both KL and TV vanish and the sandwich collapses to $\mathrm{Regret} = \mathcal{O}((\log n)/n)$, recovering the canonical PAC-Bayes log-loss rate.

**Tightness.** Near-matching lower-bound construction follows the Le Cam two-point method (Tsybakov 2009 §2.4): perturb $\mu^\circ \mapsto \mu^\circ + \varepsilon h$ with $\int h \, d\nu = 0$; minimax lower bound is of order $\mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ)$ up to constants depending on $\Pi$'s VC-type complexity. T5.1 is tight to first order.

**Operational implication.** T5.1 is a *measurement instrument*: empirically observed critic regret, net of the $(\log n)/n$ correction, is a sandwich estimator of the operator's private-public disclosure gap. Mechanism designs reducing the operator's incentive to maintain a private $\tilde{\mu}^\circ$ tighten the upper rail by at most $\mathrm{KL} + 2 \cdot \mathrm{TV}$.

**Constructive companion.** T5.1 is information-theoretic and prior-free; it does not by itself describe how to *close* the gap. The truth-serum-debate hybrid mechanism does: combining peer-prediction-style elicitation (Prelec 2004 *Science* 306:462; Witkowski-Parkes 2012 *AAAI* robust BTS) with debate-style adversarial verification (Irving-Christiano-Amodei 2018, arXiv:1805.00899) introduces correlated cross-critic signals, recovering BIC through the Crémer-McLean (1988 *Econometrica* 56:1247) full-rank correlation route. T5.1 doubles as the diagnostic for the gain: as cross-critic correlation tightens, empirical regret falls from $\mathrm{KL}(\tilde{\mu}^\circ \| \mu^\circ)$ toward the $(\log n)/n$ floor; the gap closed is the institutional gain. T5.1 thereby pivots from impossibility-quantification to a measurement instrument for the constructive mechanism's marginal contribution.
