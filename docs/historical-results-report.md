# Historical Evaluation Report

An English report reconstructed from the team's 2026 COMP9517 presentation. This is shared team work; the table is a historical reported result, not a new training run or independently verified benchmark.

## Protocol

The presentation describes 500 species selected with seed 9517, with 40 training, 10 validation, and 10 test images per species. Training and validation come from train_mini; held-out test images come from the official validation data. Each method uses the same splits.

Traditional pipelines compare colour histograms, LBP, HOG, and SIFT-BoVW. Deep models progress from scratch CNNs to ImageNet transfer and a validation-selected ResNet50/ConvNeXt ensemble.

## Reported base results

| Model | Top-1 accuracy |
|---|---:|
| HOG + SVM | 2.98% |
| SimpleCNN | 18.76% |
| ResNet18 | 66.08% |
| ResNet50 | 78.26% |
| ConvNeXt-Tiny | 82.72% |
| Ensemble | 83.78% |

The presentation reports ensemble Top-5 accuracy of 94.90% and macro-F1 of 83.63%. It separately reports a controlled 50-epoch initialization study with 26.60% versus 64.56% Top-1; these are different runs and must not be substituted for the base comparison.

## Controlled studies

Reported changes relative to the controlled baseline include pretraining +37.96 percentage points, strong augmentation -1.42, label smoothing +0.42, MixUp +0.64, and horizontal-flip TTA +1.48.

The class-scaling study uses approximately 20,000 training images while increasing class count from 500 to 1,000 to 2,500. Top-1 accuracy is reported as 64.56%, 50.32%, and 26.94%. Matched 500-class controls reduce images per class, helping separate sample scarcity from additional class competition.

## Error analysis and my contribution

The presentation assigns Jiawei Dong the confusion/failure analysis, discussion, and conclusion. Examples include Indian White-eye versus Warbling White-eye, related cormorants, and forget-me-not species. Distant organisms and cluttered backgrounds recur in mistakes.

My contribution statement in the README covers the unified evaluation workflow and artifact consistency checks. The model comparisons remain team outcomes, not exclusively my implementation.

## Limits

The presentation contains an unfilled demo screenshot placeholder. It reports no Grad-CAM attribution, so it does not verify whether the model attends to the organism rather than the background. A balanced 500-class subset is not the full long-tailed iNaturalist distribution.

Complete trained checkpoints, prediction records, and original plots are not bundled here. The numbers above are attributed to the historical presentation and have not been independently reconciled against a complete result archive or reproduced during this update.
