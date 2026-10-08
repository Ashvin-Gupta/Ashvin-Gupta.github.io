---
# Blog posts live in _posts/. Add a new file named YYYY-MM-DD-title.md
title: "Block Diffusion for Longitudinal EHR: Accuracy, Efficiency, and Representation Trade-offs"
date: 2026-10-02
permalink: /posts/2026/10/02/BlockDiffusion/
excerpt: "Training masked language diffusion models on EHR data for benchmarking performance in comparison to autoregressive models"
---
## Problem
Foundation models for structured electronic health record (EHR) data have predominantly adopted autoregressive (AR) sequence modelling. By generating possible future patient trajectories, these models have demonstrated strong zero-shot performance across clinical prediction tasks, in some settings approaching or exceeding task-specific supervised baselines. However, AR modelling imposes a strict left-to-right factorisation with each event generated conditionally on all preceding events before subsequent events can be considered. Longitudinal EHRs are only partly sequential in this sense. Clinical activity often occurs in temporally concentrated bursts, making groups of nearby events a natural target for partially parallel generation. 

![ARvsBD_Diagram](/images/BlockDiffusion/ARvsBD_Diagram.png)
*Illustration of AR and block-diffusion decoding for longitudinal EHR trajectories. Clinical events frequently occur in temporally clustered groups. AR generates each event sequentially, whereas BD preserves causal generation across blocks while jointly denoising multiple positions within the active block.*


[Discrete diffusion language models](https://arxiv.org/abs/2406.07524) use the principles from diffusion models applied to images, but on discrete tokens instead. As they learn to generate tokens over a certian number of steps, they might be well-suited for EHR modelling and in this work, we benchmark [block diffusion](https://arxiv.org/abs/2503.09573) (BD) EHR models in comparison to AR models. 

## Method
EHR is represented as a discrete token sequence $x = (x\_1, \ldots, x\_L)$, where each token corresponds to a clinical event, quantised measurement, demographic attribute, or discretised time interval from a vocabulary $\mathcal{V}$. Both AR and BD models operate on this same temporally ordered sequence. For an understanding of how block diffusion works, I would recommend reading [Kuleshov's blog](https://kuleshov-group.github.io/blog/blog/2026/how-to-build-a-diffusion-language-model/), but the basic idea is that during training, a fixed block size $B$ is chosen, and within a sequence of tokens, a certain number of tokens within each block are replaced with a `[MASK]` token depending on a noise level $t$. The model predicts the noise level, and during inference, tokens of length $B$ can be generated in parallel over a number of steps, $S$. As inference is memory-bound rather than compute-bound, the parallel nature of discrete diffusion models offers an advantage here.


We train separate BD models with block sizes $B \in \\{2, 4, 8, 16, 32, 64, 128\\}$ and assess:
- How AUROC and AUPRC vary over a varying $S/B$ denoising budget
- How AUROC and AUPRC vary when applying a linear probe on the last hidden state for AR vs BD
- How AUROC, AURPC and time vary when the denoising budget $S/B$ is fixed at 0.5
- Whether any alternative decoding strategies, including [confidence-based unmasking](https://arxiv.org/abs/2508.15487) and [ReMDM-style unmasking](https://arxiv.org/abs/2503.00307) help with rollout performance

We conduct our analysis using the MIMIC-IV dataset with ICU mortality, ICU readmission, ICU admission and hospital mortality as downstream tasks.


## Results

![BD_Results](/images/BlockDiffusion/BD_results.png)
*Quality, efficiency, and representation trade-offs of block diffusion. **Top-left:** BD–AR AUROC difference under rollout and linear probing. **Top-right:** AUROC across denoising budgets. **Bottom:** ICU mortality AUROC and evaluation time across block sizes at S/B = 0.5. Dashed lines denote AR.*

We see that these models follow similar trends as those in language. Performance is lower than AR models, regardless of the block size, but BD models do offer a speedup in evaluation time, up till a certain block size. Interestingly, linear probes on AR vs BD perform almost identically, despite the AR doing much better in the rolloutout evaluation. No alternatice masking strategy boosted performance. 


| Strategy           | AUROC                    | AUPRC                    |
|--------------------|--------------------------|--------------------------|
| Random             | 0.8476 [0.8331, 0.8614]  | 0.3440 [0.3123, 0.3792]  |
| ReMDM η = 0.05     | 0.8421 [0.8268, 0.8562]  | 0.3338 [0.3028, 0.3679]  |
| ReMDM η = 0.10     | 0.8446 [0.8307, 0.8590]  | 0.3515 [0.3176, 0.3871]  |
| ReMDM η = 0.20     | 0.8433 [0.8287, 0.8580]  | 0.3474 [0.3158, 0.3800]  |
| Confidence         | 0.8089 [0.7921, 0.8257]  | 0.3487 [0.3154, 0.3844]  |

*Table: AUROC and AUPRC for different block diffusion rollout strategies on the main test task. Values in brackets denote 95% confidence intervals.*



## Discussion and conclusion

Our results suggest that AR is still the superior to BD for modelling for for prediction tasks from EHR data. However, diffusion models could still be useful in the EHR setting. One way could be through their ability to do infilling and therefore in the generation of counterfactuals.
Another could be by generating events between successive time markers jointly, treating temporally co-occurring events as unordered or partially ordered sets

<!-- ## BibTeX

```
@article{https://doi.org/10.1002/lrh2.70114,
author = {Gupta, Ashvin and Prociuk, Denys and Russo, Alessandra and Delaney, Brendan C.},
title = {Automatic Conversion of NICE Guidelines to an Executable Computational Model Using Large Language Models},
journal = {Learning Health Systems},
volume = {10},
number = {4},
pages = {e70114},
keywords = {computational model, LLM, NICE guidelines},
doi = {https://doi.org/10.1002/lrh2.70114},
url = {https://onlinelibrary.wiley.com/doi/abs/10.1002/lrh2.70114},
eprint = {https://onlinelibrary.wiley.com/doi/pdf/10.1002/lrh2.70114},
note = {e70114 1014853},
year = {2026}
} -->



