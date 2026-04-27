# The Constitutional Trilemma: Aggregation, Strategy, and Truth in Constitutional AI

**Shuo Li Liu** — Princeton University, Department of Economics

> **Framing.** This paper extends Constitutional AI (Bai et al. 2022) into the multi-critic regime opened by Inverse CAI (Findeis et al. 2024) and Collective CAI (Huang et al. 2024). The trilemma is a *design constraint* a multi-critic CAI deployment must price, not a critique of the original Bai et al. pipeline; the constructive truth-serum-debate companion shows which leg can be bought back and at what cost in nats. The result tightens the case for Constitutional AI by making its safety budget auditable.

## Abstract

This paper characterizes a structural three-way tension in multi-critic Constitutional AI: no deployable aggregator can jointly satisfy **(A)** aggregation rationality (Arrovian unanimity, IIA, non-dictatorship), **(S)** strategic robustness (DSIC under paraphrase-equivalent reports), and **(I)** Bayesian incentive compatibility when the operator's private constitutional prior generically misaligns with the population's. The result holds for *k* ≥ 3 principles and |Y| ≥ 3 candidate responses. The (S) leg uses the Mossel-Rácz quantitative Gibbard-Satterthwaite bound; the (I) leg derives from standard Bayesian implementation theory (Crémer-McLean, Myerson, d'Aspremont-Gérard-Varet). A companion proposition (T5.1) gives a two-sided KL-regret bound on the residual welfare loss, pricing the relaxed leg in nats — converting "which axiom does this deployment cede" from qualitative concern to auditable diagnostic. A constructive truth-serum-debate hybrid restores the (I) leg at the cost of one extra forward pass by injecting cross-critic correlation that activates Crémer-McLean's positive case. A pre-registered $2,300 / 8-week TruthfulQA-MC1 protocol operationalizes the headline comparison.

## Status

Working paper. Target venues: EC 2027, NeurIPS 2026 ML Safety Workshop. April 2026 version.

## Repository contents

- `trilemma_proposal.pdf` — 2-page research proposal
- `docs/master_theorem.md` — extended proof of the trilemma with all three lemmas (Mossel–Rácz S-leg; Crémer–McLean / Myerson / dAGV I-leg)
- `docs/theorem_t51_kl_regret.md` — companion proposition T5.1: two-sided KL-regret bound on residual welfare loss when one leg is relaxed
- `docs/citations_verified.md` — auditor-verified reference list with attribution corrections
- `empirical_plan.pdf` — pre-registered TruthfulQA-MC1 protocol with power analysis (forthcoming)
- `references.bib` — BibTeX bibliography (forthcoming)

## How to cite

```bibtex
@unpublished{liu2026trilemma,
  author = {Liu, Shuo Li},
  title  = {The Constitutional Trilemma: Aggregation, Strategy, and Truth in Constitutional AI},
  note   = {Working paper, Princeton Economics, 2026},
  url    = {https://github.com/liusulldel/constitutional-trilemma},
}
```

## Related work

- **Constitutional AI** — Bai et al. 2022, [arXiv:2212.08073](https://arxiv.org/abs/2212.08073)
- **Inverse Constitutional AI** — Findeis et al. 2024, [arXiv:2406.06560](https://arxiv.org/abs/2406.06560)
- **Collective Constitutional AI** — Huang et al. 2024, [arXiv:2406.07814](https://arxiv.org/abs/2406.07814)
- **Social choice for AI alignment** — Conitzer et al. 2024, [arXiv:2404.10271](https://arxiv.org/abs/2404.10271)
- **Axiomatic foundations of RLHF** — Ge et al. 2024, [arXiv:2405.14758](https://arxiv.org/abs/2405.14758)
- **Bayesian Truth Serum** — Prelec 2004, *Science* 306; Witkowski & Parkes 2012, *AAAI*
- **AI Safety via Debate** — Irving, Christiano & Amodei 2018, [arXiv:1805.00899](https://arxiv.org/abs/1805.00899)
- **Quantitative Gibbard-Satterthwaite** — Mossel & Rácz 2015, *Combinatorica* 35(3):339-387

## Companion repo

- [truth-serum-debate](https://github.com/liusulldel/truth-serum-debate) — constructive complement implementing the (A)+(T) corner of the trilemma.

## Contact

Shuo Li Liu — Princeton University, Department of Economics

## License

Manuscript text under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); code (when added) under MIT.
