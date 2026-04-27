---
name: Citation auditor verified reference list
description: Round 5 citation audit. All major references verified. Critical findings on Birrell-Pass (different theorem from Mossel-Rácz), Ge et al. author list, Sun-Cen-Lee-Procaccia (wrong attribution), IKM venue.
type: reference
originSessionId: db97e6c6-5cfc-4cae-85cc-99965d4ad7a6
---
# Verified Reference List + Critical Findings

## Critical findings (must read before submission)

1. **Birrell-Pass IJCAI 2011 has ε in DENOMINATOR** — but it's a DIFFERENT theorem from Mossel-Rácz. Birrell-Pass: δ ≥ k(k+1+ε)/ε - 1 where δ is the *approximation distance* for an ε-strategy-proof approximation. Mossel-Rácz: P[manipulation] ≥ ε^c/poly(n,k) where ε is *distance from dictatorship*. Both are quantitative GS results but bound different objects. The Trilemma uses Mossel-Rácz form (ε in numerator) for the (S) leg.

2. **arXiv:1106.0066 is a physics paper**, not Birrell-Pass. Birrell-Pass has NO arXiv preprint — only IJCAI 2011 proceedings PDF + DTIC report ADA582553.

3. **Isaksson-Kindler-Mossel is in *Combinatorica* 32(2):221-250 (2012)**, NOT *Annals of Math*. arXiv:0911.0517.

4. **Mossel-Rácz is in *Combinatorica* 35(3):339-387 (2015)**. arXiv:1110.5888. Theorem 1.2 has the relevant bound.

5. **Ge et al. NeurIPS 2024 author list**: Ge, **Halpern, Micha, Procaccia, Shapira, Vorobeychik, Wu** — NOT "Ge, Tang, Procaccia, Zampetakis." Title: "Axioms for AI Alignment from Human Feedback." arXiv:2405.14758.

6. **arXiv:2503.09561 is by Kleine Buening, Gan, Mandal, Kwiatkowska**, NOT Sun-Cen-Lee-Procaccia. Title: "Strategyproof Reinforcement Learning from Human Feedback" (NeurIPS 2025). No "Sun-Cen-Lee-Procaccia" paper exists at this ID.

7. **Cover-Thomas Theorem 2.7.2 is convexity of KL**, not mixture log-loss. Mixture log-loss decomposition is in §2.5-2.6 (cross-entropy = entropy + KL). Cite §2.5-2.6, not Thm 2.7.2.

8. **Conitzer et al. 2024 full author list**: Conitzer, Freedman, Heitzig, Holliday, Jacobs, Lambert, Mossé, Pacuit, Russell, Schoelkopf, Tewolde, Zwicker. arXiv:2404.10271. Subtitle "in dealing with diverse human feedback" is part of the title.

9. **Findeis et al. 2024 author list**: Findeis, Kaufmann, Hüllermeier, Albanie, Mullins. arXiv:2406.06560. ICLR 2025.

10. **Huang et al. Collective CAI author list**: Huang, Siddarth, Lovitt, Liao, Durmus, Tamkin, Ganguli. arXiv:2406.07814. FAccT 2024.

## Verified references

| # | Reference |
|---|---|
| 1 | Arrow, K. J. (1951). *Social Choice and Individual Values*. Cowles Commission Monograph 12. Wiley. (Specify edition when citing.) |
| 2 | Bai, Y., Kadavath, S., Kundu, S., et al. (2022). Constitutional AI: Harmlessness from AI Feedback. arXiv:2212.08073. |
| 3 | Birrell, E., & Pass, R. (2011). Approximately strategy-proof voting. *Proceedings IJCAI 2011*, pp. 67-72. (NO arXiv; IJCAI proceedings only. Theorem 4.1 gives δ ≥ k(k+1+ε)/ε - 1 — different theorem from Mossel-Rácz.) |
| 4 | Casper, S., et al. (2023). Open Problems and Fundamental Limitations of RLHF. arXiv:2307.15217. TMLR 2023. |
| 5 | Catoni, O. (2007). *PAC-Bayesian Supervised Classification*. IMS Lecture Notes-Monograph Series 56. arXiv:0712.0248. DOI: 10.1214/074921707000000391. |
| 6 | Conitzer, V., Freedman, R., Heitzig, J., Holliday, W. H., Jacobs, B. M., Lambert, N., Mossé, M., Pacuit, E., Russell, S., Schoelkopf, H., Tewolde, E., & Zwicker, W. S. (2024). Social Choice Should Guide AI Alignment in Dealing with Diverse Human Feedback. arXiv:2404.10271. |
| 7 | Cover, T. M., & Thomas, J. A. (2006). *Elements of Information Theory* (2nd ed.). Wiley. ISBN 978-0-471-24195-9. (Mixture log-loss in §2.5-2.6; Theorem 2.7.2 is KL convexity; Theorem 2.8.1 is DPI for mutual information.) |
| 8 | Crémer, J., & McLean, R. P. (1988). Full extraction of the surplus in Bayesian and dominant strategy auctions. *Econometrica* 56(6): 1247-1257. JSTOR: 1913096. |
| 9 | d'Aspremont, C., & Gérard-Varet, L.-A. (1979). Incentives and incomplete information. *J. Public Economics* 11(1): 25-45. DOI: 10.1016/0047-2727(79)90043-4. |
| 10 | Dai, J., & Fleisig, E. (2024). Mapping Social Choice Theory to RLHF. arXiv:2404.13038. |
| 11 | Findeis, A., Kaufmann, T., Hüllermeier, E., Albanie, S., & Mullins, R. (2024). Inverse Constitutional AI. arXiv:2406.06560. ICLR 2025. |
| 12 | Ge, L., Halpern, D., Micha, E., Procaccia, A. D., Shapira, I., Vorobeychik, Y., & Wu, J. (2024). Axioms for AI Alignment from Human Feedback. *NeurIPS 2024*. arXiv:2405.14758. |
| 13 | Gibbard, A. (1973). Manipulation of voting schemes: A general result. *Econometrica* 41(4): 587-601. |
| 14 | Gneiting, T., & Raftery, A. E. (2007). Strictly proper scoring rules, prediction, and estimation. *JASA* 102(477): 359-378. DOI: 10.1198/016214506000001437. |
| 15 | Guan, M. Y., et al. (2024). Deliberative Alignment: Reasoning Enables Safer Language Models. arXiv:2412.16339. |
| 16 | Hadfield-Menell, D., Dragan, A., Abbeel, P., & Russell, S. (2016). Cooperative Inverse Reinforcement Learning. *NeurIPS 2016*. arXiv:1606.03137. |
| 17 | Heifetz, A., & Neeman, Z. (2006). On the generic (im)possibility of full surplus extraction in mechanism design. *Econometrica* 74(1): 213-233. |
| 18 | Huang, S., Siddarth, D., Lovitt, L., Liao, T. I., Durmus, E., Tamkin, A., & Ganguli, D. (2024). Collective Constitutional AI. arXiv:2406.07814. FAccT 2024. |
| 19 | Irving, G., Christiano, P., & Amodei, D. (2018). AI Safety via Debate. arXiv:1805.00899. |
| 20 | Isaksson, M., Kindler, G., & Mossel, E. (2012). The geometry of manipulation. *Combinatorica* 32(2): 221-250. arXiv:0911.0517. |
| 21 | Kakutani, S. (1941). A generalization of Brouwer's fixed point theorem. *Duke Math. J.* 8(3): 457-459. |
| 22 | Kleine Buening, T., Gan, J., Mandal, D., & Kwiatkowska, M. (2025). Strategyproof Reinforcement Learning from Human Feedback. arXiv:2503.09561. NeurIPS 2025. |
| 23 | Lee, H., et al. (2023). RLAIF vs. RLHF: Scaling Reinforcement Learning from Human Feedback with AI Feedback. arXiv:2309.00267. (General RLAIF context only — do NOT cite Table 4 for self-consistency.) |
| 24 | Lin, S., Hilton, J., & Evans, O. (2022). TruthfulQA: Measuring how models mimic human falsehoods. *ACL 2022*: 3214-3252. arXiv:2109.07958. |
| 25 | McAllester, D. A. (2003). PAC-Bayesian Stochastic Model Selection. *Machine Learning* 51(1): 5-21. |
| 26 | Mossel, E., & Rácz, M. Z. (2015). A quantitative Gibbard-Satterthwaite theorem without neutrality. *Combinatorica* 35(3): 339-387. arXiv:1110.5888. |
| 27 | Myerson, R. B. (1981). Optimal auction design. *Math. Oper. Res.* 6(1): 58-73. |
| 28 | Prelec, D. (2004). A Bayesian truth serum for subjective data. *Science* 306(5695): 462-466. |
| 29 | Procaccia, A. D., Schiffer, B., & Zhang, S. (2025). Clone-Robust AI Alignment. arXiv:2501.09254. |
| 30 | Satterthwaite, M. A. (1975). Strategy-proofness and Arrow's conditions. *J. Economic Theory* 10(2): 187-217. |
| 31 | Sen, A. K. (1970). *Collective Choice and Social Welfare*. Holden-Day. |
| 32 | Tsybakov, A. B. (2009). *Introduction to Nonparametric Estimation*. Springer. (Lemma 2.5: Pinsker.) |
| 33 | Witkowski, J., & Parkes, D. C. (2012). A robust Bayesian truth serum for small populations. *AAAI 2012*: 1492-1498. |
