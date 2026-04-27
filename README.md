# The Constitutional Trilemma

Shuo Li Liu, Princeton University, Department of Economics

This repository contains a research note on a constraint that can arise in multi-critic Constitutional AI systems.

The claim is modest: when a system tries to aggregate several constitutional critics, three desirable properties can conflict:

- Aggregation rationality: the aggregator satisfies standard Arrovian conditions such as unanimity, IIA, and non-dictatorship.
- Strategic robustness: critics do not benefit from strategically changing paraphrase-equivalent reports.
- Truthful prior alignment: the mechanism remains Bayesian incentive compatible when the operator's constitutional prior differs from the population's.

Under the model studied here, the three desiderata cannot all be satisfied at once when the action space, critic set, priors, and incentive constraints meet the stated assumptions. The KL-regret note describes one way to measure the cost of relaxing a leg. The goal is to make the tradeoff explicit, not to criticize Constitutional AI as a whole.

## What is here

- `docs/master_theorem.md`: current argument sketch and supporting assumptions.
- `docs/theorem_t51_kl_regret.md`: companion KL-regret diagnostic note.
- `docs/citations_verified.md`: reference notes and attribution checks.
- Optional supplemental materials, if added later, will be listed here.

## How to inspect

There is no runnable training or evaluation pipeline in this repository yet. To review the current public notes:

1. Read `docs/master_theorem.md` for the main argument and assumptions.
2. Read `docs/theorem_t51_kl_regret.md` for the regret diagnostic.
3. Check `docs/citations_verified.md` against the cited papers.

If code or empirical results are added later, this README should be updated with exact reproduction commands.

## Current limits

- This is a theoretical research note, not a deployed safety method.
- Any empirical protocol will need to be added separately; completed results should not be inferred from this repository.
- The main claim depends on formal assumptions about the action space, critic reports, priors, and incentive constraints.
- The KL-regret bound is a diagnostic for the model class described in the note, not a general safety guarantee.

## Citation

```bibtex
@unpublished{liu2026trilemma,
  author = {Liu, Shuo Li},
  title  = {The Constitutional Trilemma: Aggregation, Strategy, and Truth in Constitutional AI},
  note   = {Research note, Princeton Economics, 2026},
  url    = {https://github.com/liusulldel/constitutional-trilemma},
}
```

## Related work

- Bai et al. 2022, Constitutional AI, [arXiv:2212.08073](https://arxiv.org/abs/2212.08073)
- Findeis et al. 2024, Inverse Constitutional AI, [arXiv:2406.06560](https://arxiv.org/abs/2406.06560)
- Huang et al. 2024, Collective Constitutional AI, [arXiv:2406.07814](https://arxiv.org/abs/2406.07814)
- Conitzer et al. 2024, Social choice for AI alignment, [arXiv:2404.10271](https://arxiv.org/abs/2404.10271)
- Ge et al. 2024, Axiomatic foundations of RLHF, [arXiv:2405.14758](https://arxiv.org/abs/2405.14758)
- Prelec 2004, Bayesian Truth Serum, Science 306
- Witkowski and Parkes 2012, Peer Prediction without a Common Prior, AAAI
- Irving, Christiano, and Amodei 2018, AI Safety via Debate, [arXiv:1805.00899](https://arxiv.org/abs/1805.00899)
- Mossel and Racz 2015, A quantitative Gibbard-Satterthwaite theorem without neutrality, Combinatorica 35(3):339-387

## License

Manuscript text is under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Code, if added, is intended to be under MIT.
