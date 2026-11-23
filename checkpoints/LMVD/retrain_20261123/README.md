# LMVD retrained checkpoints (2026-11-23)

These checkpoints were retrained on GPU1 with the historical best coupled_Bi_mamba3 configuration, seed 42. Training completed all 120 epochs without early stopping. They reproduce the historical primary test metrics; they are newly trained weights, not recovered copies of the deleted original files.

## Primary checkpoint

Use [best_avg.pt](best_avg.pt), selected by validation Avg at epoch 10. Testing was performed after completion of all 120 epochs.

| Accuracy | Precision | Recall | F1 | Avg |
|---:|---:|---:|---:|---:|
| 86.79% | 85.07% | 93.44% | 89.06% | 88.59% |

Avg is the arithmetic mean of Accuracy, Precision, Recall and positive-class F1. Threshold: 0.5; video-level evaluation; test n=106. The test confusion matrix [[TN, FP], [FN, TP]] is [[35, 10], [4, 57]]. Full-precision metrics for all five checkpoint selections are in [metrics.json](metrics.json).

## Files

- `best_avg.pt`: primary validation-Avg best, epoch 10.
- `best_accuracy.pt`, `best_precision.pt`, `best_f1.pt`: respective validation-best checkpoints, epoch 10.
- `best_recall.pt`: validation-Recall best, epoch 18; an auxiliary checkpoint, not the primary reported result.
- `SHA256SUMS`: SHA-256 checksums of the five PT files.
- `configuration.json`: training settings with local manifest/output paths omitted.
- `source_hashes.json`: original training source hashes.

PT dictionaries contain `state_dict`, `model_config`, `epoch`, `configuration`, `valid_metrics`, `selection_metric` and optimizer state. The original PT files are unmodified and retain local path metadata. Load `state_dict` with the compatible depression model implementation; these are not standalone TorchScript models. Model code is not included in this checkpoint upload.

## Protocol and scope

LMVD mapped subset: 1116 videos, split 888 train / 122 validation / 106 test. Audio features: 768 dimensions; visual features: 18 dimensions. Normalization is fitted on training data. Participant-disjointness and alignment were not independently verified. The remaining 707 unmapped videos are not included.

Within each run, validation Avg selects the primary epoch/PT. The historical configuration was chosen among validation-selected checkpoints using test Avg across runs. This retraining repeats that configuration; it is not an independent untouched-test confirmation or a multi-seed mean.

Configuration: learning rate 2e-5, dropout 0.6, weight decay 1e-4, d_model=64, d_state=32, ISM depth=2, interaction layers=1, batch size=8, window=128, audio+visual, bidirectional. Environment recorded at training: PyTorch 2.9.0+cu128, NVIDIA RTX 3070.

Weights are provided for research use; no clinical diagnostic validity is established by these experiments.
