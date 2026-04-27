# KL-Regret Diagnostic Note

This note records a diagnostic bound used by the project. It is not a general
safety guarantee. The bound is meaningful only under the stated finite-space,
bounded-loss, and identifiability assumptions.

## Bound

Let `Omega` be a finite set of admissible constitutional states. An operator
publishes a prior `mu0` while privately maintaining `mut0`, with `mut0`
absolutely continuous with respect to `mu0`. A critic observes `n` independent
prompt-response samples and evaluates predictors under bounded log-loss after a
fixed truncation level.

Under a finite hypothesis class or a VC-type class with uniform convergence, and
under a separation condition that lets the prompt distribution distinguish the
constitution-indexed predictive family, the critic's regret is approximately
controlled by the private-public prior gap:

```text
KL(mut0 || mu0) - xi_rho - finite_sample(n)
    <= regret
    <= KL(mut0 || mu0) + 2 * TV(mut0, mu0) + truncation_slack
```

Here `xi_rho` is an identifiability slack term. It is zero only when the prompt
distribution separates the relevant constitution-indexed predictive family. The
finite-sample term depends on the class complexity and the chosen confidence
level.

## Assumptions That Matter

- The constitutional state space is finite.
- The private prior is absolutely continuous with respect to the public prior.
- The log-loss is bounded by truncation or by a lower-bounded predictive density.
- The hypothesis class admits the stated uniform convergence rate.
- The prompt distribution is sufficiently separating; otherwise `xi_rho` remains
  in the lower bound.

## Interpretation

The bound is a measurement device. It says that, in this stylized model,
critic regret can reflect the gap between the operator's public and private
constitutional priors. It does not show that a real CAI system exposes such a
gap, nor that reducing this regret solves alignment.

The useful empirical question is therefore modest: when a public constitution
and an operator-adapted critic differ, does measured regret move in the direction
predicted by the prior-gap diagnostic?

## References Used

- Cover, T. M., and Thomas, J. A. (2006). *Elements of Information Theory*.
- McAllester, D. A. (2003). PAC-Bayesian stochastic model selection.
- Catoni, O. (2007). *PAC-Bayesian Supervised Classification*.
- Tsybakov, A. B. (2009). *Introduction to Nonparametric Estimation*.
