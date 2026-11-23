# PairWrite-SSM

PairWrite-SSM is a state space model for multimodal sentiment analysis. We are preparing the model code for release in this repository.

PairWrite-SSM 是面向多模态情感分析的状态空间模型。我们正在整理模型代码，整理完成后将在本仓库发布。
## Paper checkpoints / 论文权重

Download the original checkpoints used for the reported MOSI and MOSEI results.

- [MOSI checkpoint (.pt)](https://github.com/hhczjw/PairWrite-SSM/releases/download/paper-checkpoints-v1/MOSI_p0B_seed2024_best_Acc2.pt)
- [MOSEI checkpoint (.pt)](https://github.com/hhczjw/PairWrite-SSM/releases/download/paper-checkpoints-v1/MOSEI_seed2024_best_test_Acc2.pt)
- [SHA-256 checksums](https://github.com/hhczjw/PairWrite-SSM/releases/download/paper-checkpoints-v1/SHA256SUMS)

See the [GitHub Release](https://github.com/hhczjw/PairWrite-SSM/releases/tag/paper-checkpoints-v1) for the corresponding metrics.

## LMVD depression-detection retraining

- [LMVD checkpoint files and metrics](checkpoints/LMVD/retrain_20261123/README.md)
- [Primary validation-Avg-best checkpoint](checkpoints/LMVD/retrain_20261123/best_avg.pt)

The 2026-11-23 retraining completed 120 epochs and reproduced the historical single-run test Avg of 88.59% and F1 of 89.06%. See the protocol and selection scope in the checkpoint documentation.
