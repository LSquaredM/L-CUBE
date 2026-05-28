# L-CUBE: Long-Context Utilization Benchmark
 
**Isolating Long-Context Capacity from Knowledge with Controllable Mutual Information Scaling**
 
*Zhuo Chen\*, Oriol Mayné i Comas\*, Zhuotao Jin, Di Luo, Marin Soljačić*
 
**ICML 2026** — Proceedings of the 43rd International Conference on Machine Learning, Seoul, South Korea.
 
[\[Paper\]](https://openreview.net/forum?id=U3QqOOZK6P) [\[ICML Page\]](https://icml.cc/)
 
---
 
## ⚠️ Code Availability
 
> **The code for this project is currently withheld due to a pending patent application.** The full codebase — including the L-CUBE generator, evaluation pipeline, and experiment configurations — will be publicly released prior to the ICML 2026 conference. We appreciate your patience and interest.
>
> For questions or collaboration inquiries in the meantime, please contact: **chenzhuo@mit.edu**
 
---
 
## Overview
 
Evaluating long-context language models on natural language conflates a model's architectural capacity to capture long-range dependencies with its semantic knowledge and vocabulary statistics. When models fail at long contexts, we cannot determine whether failures stem from fundamental architectural limitations or insufficient domain knowledge.
 
**L-CUBE** is a synthetic benchmark that cleanly separates these two factors. It generates hierarchical Gaussian sequences with controllable bipartite mutual information scaling, providing exact ground-truth conditionals for unconfounded evaluation. This enables practitioners to test whether a particular architecture will maintain long-context capability at target sequence lengths *before* committing to expensive training on real data.
 
### Key Features
 
- **Isolates capacity from knowledge** — Continuous Gaussian sequences eliminate vocabulary and domain semantics as confounders.
- **Exact ground-truth conditionals** — Enables direct computation of conditional KL divergence rather than relying on perplexity alone.
- **Controllable information scaling** — Parameterized bipartite mutual information $I^{\text{BP}} \sim L^{\beta}$, matching the sub-volume power-law growth ($\beta \approx 0.7\text{–}0.8$) observed in natural language.
- **Efficient and scalable** — $O(L)$ time and space for generation and evaluation in the default sub-volume configuration.
- **Utilization metric** — Quantifies how much of the available predictive information a model extracts as context grows.
## Summary of Results
 
We evaluate representative architectures spanning transformers (GPT-2, GPT-NeoX, Qwen3), state space models (Mamba, Mamba2, RWKV-7), log-linear attention (LLA), and windowed attention (Mistral), with model sizes from 64M to 1.4B parameters and sequence lengths from 256 to 16,384 tokens.
 
- **Full-attention transformers** track ground-truth bipartite mutual information across all tested lengths.
- **State space models** plateau and decline as sequence length increases, confirming the failure mode predicted by fixed history state capacity (L²M theory).
- **Log-linear attention** performs better than SSMs but still falls short at longer lengths.
- **Windowed attention** tracks ground truth within its window but degrades sharply beyond it.
- When viewed through **computational complexity**, all architecture families exhibit surprisingly similar scaling in utilized context length vs. compute.
## Citation
 
```bibtex
@inproceedings{
anonymous2026lcube,
title={L-{CUBE}: Isolating Long-Context Capacity from Knowledge with Controllable Mutual Information Scaling},
author={Anonymous},
booktitle={Forty-third International Conference on Machine Learning},
year={2026},
url={https://openreview.net/forum?id=U3QqOOZK6P}
}
```
 
## Acknowledgements
 
This work is supported by the NSF AI Institute for Artificial Intelligence and Fundamental Interactions (PHY-2019786), the MIT Generative AI Impact Consortium, the MathWorks Fellowship, and the Henry W. Kendall (1955) Fellowship Fund. Compute resources provided in part by AWS, the FASRC cluster at Harvard University, and DeltaAI (NSF OAC 2320345).
 
## License
 
*License details will be provided upon code release.*
