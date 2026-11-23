# Results summary (generated automatically from the computed results)

Data: 2298 images, 1373 patients, 1891 lesions (1641 distinct lesion-identifier values), 6 classes (ACK, BCC, MEL, NEV, SCC, SEK). Protocol: 1 × 5-fold patient-grouped stratified cross-validation; backbone convnext_tiny.fb_in1k; configuration 6bef845303cf. Intervals are 95% patient-level bootstrap intervals (10000 resamples) of pooled out-of-fold estimates; 'a [l–u]; m ± s' means pooled estimate a with interval l–u, and mean m ± SD s over the test folds. BA = balanced accuracy. MD, modality-dropout training (for the gradient-boosting model: training with missingness-augmented copies).

## RQ1. Discrimination
- Image only: BA 0.644 [0.612–0.676]; 0.645 ± 0.030; macro AUROC 0.893 [0.877–0.908]; 0.909 ± 0.013; cancer sensitivity 0.813, specificity 0.851.
- Metadata only (GBM): BA 0.633 [0.596–0.669]; 0.631 ± 0.010; macro AUROC 0.911 [0.899–0.922]; 0.913 ± 0.011; cancer sensitivity 0.900, specificity 0.863.
- Metadata only (GBM) + MD: BA 0.633 [0.596–0.669]; 0.635 ± 0.029; macro AUROC 0.909 [0.898–0.920]; 0.911 ± 0.012; cancer sensitivity 0.898, specificity 0.851.
- Early concatenation: BA 0.704 [0.671–0.735]; 0.705 ± 0.012; macro AUROC 0.929 [0.918–0.939]; 0.940 ± 0.008; cancer sensitivity 0.918, specificity 0.873.
- Early concatenation + MD: BA 0.683 [0.653–0.714]; 0.677 ± 0.032; macro AUROC 0.920 [0.908–0.932]; 0.931 ± 0.008; cancer sensitivity 0.889, specificity 0.867.
- Late fusion: BA 0.726 [0.692–0.758]; 0.732 ± 0.051; macro AUROC 0.934 [0.924–0.944]; 0.946 ± 0.008; cancer sensitivity 0.912, specificity 0.899.
- Late fusion + MD: BA 0.723 [0.690–0.755]; 0.727 ± 0.035; macro AUROC 0.932 [0.923–0.942]; 0.943 ± 0.006; cancer sensitivity 0.902, specificity 0.891.
- Cross-attention: BA 0.671 [0.639–0.703]; 0.673 ± 0.020; macro AUROC 0.914 [0.903–0.925]; 0.926 ± 0.007; cancer sensitivity 0.934, specificity 0.854.
- Cross-attention + MD: BA 0.650 [0.618–0.683]; 0.652 ± 0.027; macro AUROC 0.889 [0.870–0.907]; 0.913 ± 0.020; cancer sensitivity 0.896, specificity 0.859.
- MetaBlock-style: BA 0.717 [0.685–0.749]; 0.721 ± 0.032; macro AUROC 0.940 [0.931–0.948]; 0.944 ± 0.008; cancer sensitivity 0.949, specificity 0.859.
- MetaBlock-style + MD: BA 0.714 [0.683–0.743]; 0.712 ± 0.032; macro AUROC 0.935 [0.926–0.943]; 0.938 ± 0.008; cancer sensitivity 0.910, specificity 0.885.
- Highest pooled BA: Late fusion (0.726); lowest: Metadata only (GBM) + MD (0.633).
- Paired comparisons (Δ BA = A − B, Holm-adjusted bootstrap p):
  - Metadata only (GBM) vs Image only: Δ = -0.011 [-0.060 to 0.037], p = 1.000 (interval includes zero).
  - Metadata only (GBM) + MD vs Image only: Δ = -0.011 [-0.056 to 0.033], p = 1.000 (interval includes zero).
  - Early concatenation vs Image only: Δ = 0.059 [0.027–0.092], p = 0.009 (interval excludes zero).
  - Early concatenation + MD vs Image only: Δ = 0.039 [0.011–0.066], p = 0.064 (interval excludes zero).
  - Late fusion vs Image only: Δ = 0.082 [0.053–0.111], p = 0.003 (interval excludes zero).
  - Late fusion + MD vs Image only: Δ = 0.079 [0.054–0.105], p = 0.003 (interval excludes zero).
  - Cross-attention vs Image only: Δ = 0.027 [-0.012 to 0.066], p = 1.000 (interval includes zero).
  - Cross-attention + MD vs Image only: Δ = 0.006 [-0.028 to 0.040], p = 1.000 (interval includes zero).
  - MetaBlock-style vs Image only: Δ = 0.073 [0.036–0.110], p = 0.005 (interval excludes zero).
  - MetaBlock-style + MD vs Image only: Δ = 0.070 [0.038–0.101], p = 0.003 (interval excludes zero).
  - Metadata only (GBM) + MD vs Metadata only (GBM): Δ = -0.000 [-0.020 to 0.022], p = 1.000 (interval includes zero).
  - Early concatenation + MD vs Early concatenation: Δ = -0.021 [-0.051 to 0.008], p = 1.000 (interval includes zero).
  - Late fusion + MD vs Late fusion: Δ = -0.003 [-0.017 to 0.012], p = 1.000 (interval includes zero).
  - Cross-attention + MD vs Cross-attention: Δ = -0.021 [-0.056 to 0.013], p = 1.000 (interval includes zero).
  - MetaBlock-style + MD vs MetaBlock-style: Δ = -0.003 [-0.029 to 0.022], p = 1.000 (interval includes zero).
- Wilcoxon signed-rank test not run: with 5 folds the minimum two-sided p-value is 0.0625; set N_REPEATS >= 2 to enable it.

## RQ2. Robustness to missing metadata
- Image only: BA 0.644 at 0%, 0.644 at 50% and 0.644 at 100% randomly missing fields; drop 0%→100% = 0.000 [0.000–0.000].
- Metadata only (GBM): BA 0.633 at 0%, 0.365 at 50% and 0.167 at 100% randomly missing fields; drop 0%→100% = 0.467 [0.429–0.502].
- Metadata only (GBM) + MD: BA 0.633 at 0%, 0.493 at 50% and 0.164 at 100% randomly missing fields; drop 0%→100% = 0.469 [0.428–0.509].
- Early concatenation: BA 0.704 at 0%, 0.607 at 50% and 0.470 at 100% randomly missing fields; drop 0%→100% = 0.233 [0.201–0.266].
- Early concatenation + MD: BA 0.683 at 0%, 0.658 at 50% and 0.615 at 100% randomly missing fields; drop 0%→100% = 0.068 [0.050–0.086].
- Late fusion: BA 0.726 at 0%, 0.618 at 50% and 0.507 at 100% randomly missing fields; drop 0%→100% = 0.219 [0.183–0.254].
- Late fusion + MD: BA 0.723 at 0%, 0.681 at 50% and 0.642 at 100% randomly missing fields; drop 0%→100% = 0.081 [0.054–0.109].
- Cross-attention: BA 0.671 at 0%, 0.576 at 50% and 0.444 at 100% randomly missing fields; drop 0%→100% = 0.228 [0.197–0.257].
- Cross-attention + MD: BA 0.650 at 0%, 0.635 at 50% and 0.607 at 100% randomly missing fields; drop 0%→100% = 0.043 [0.027–0.060].
- MetaBlock-style: BA 0.717 at 0%, 0.584 at 50% and 0.422 at 100% randomly missing fields; drop 0%→100% = 0.295 [0.264–0.325].
- MetaBlock-style + MD: BA 0.714 at 0%, 0.669 at 50% and 0.630 at 100% randomly missing fields; drop 0%→100% = 0.084 [0.061–0.110].
- Fusion models with BA at 100% missing metadata below the image-only model (0.644): Early concatenation, Early concatenation + MD, Late fusion, Late fusion + MD, Cross-attention, Cross-attention + MD, MetaBlock-style, MetaBlock-style + MD.
- Modality dropout minus standard, Metadata only (GBM), 0% missing: Δ BA = -0.000 [-0.020 to 0.022], Holm-adjusted p = 1.000 (interval includes zero).
- Modality dropout minus standard, Metadata only (GBM), 100% missing: Δ BA = -0.003 [-0.021 to 0.017], Holm-adjusted p = 1.000 (interval includes zero).
- Modality dropout minus standard, Early concatenation, 0% missing: Δ BA = -0.021 [-0.051 to 0.008], Holm-adjusted p = 0.956 (interval includes zero).
- Modality dropout minus standard, Early concatenation, 100% missing: Δ BA = 0.145 [0.112–0.179], Holm-adjusted p = 0.002 (interval excludes zero).
- Modality dropout minus standard, Late fusion, 0% missing: Δ BA = -0.003 [-0.017 to 0.012], Holm-adjusted p = 1.000 (interval includes zero).
- Modality dropout minus standard, Late fusion, 100% missing: Δ BA = 0.135 [0.105–0.165], Holm-adjusted p = 0.002 (interval excludes zero).
- Modality dropout minus standard, Cross-attention, 0% missing: Δ BA = -0.021 [-0.056 to 0.013], Holm-adjusted p = 1.000 (interval includes zero).
- Modality dropout minus standard, Cross-attention, 100% missing: Δ BA = 0.164 [0.130–0.197], Holm-adjusted p = 0.002 (interval excludes zero).
- Modality dropout minus standard, MetaBlock-style, 0% missing: Δ BA = -0.003 [-0.029 to 0.022], Holm-adjusted p = 1.000 (interval includes zero).
- Modality dropout minus standard, MetaBlock-style, 100% missing: Δ BA = 0.208 [0.173–0.241], Holm-adjusted p = 0.002 (interval excludes zero).
- Scenario 'no diameter' (2 fields missing): Metadata only (GBM) 0.621; Metadata only (GBM) + MD 0.635; Early concatenation 0.699; Early concatenation + MD 0.682; Late fusion 0.729; Late fusion + MD 0.722; Cross-attention 0.666; Cross-attention + MD 0.652; MetaBlock-style 0.710; MetaBlock-style + MD 0.703.
- Scenario 'no symptoms' (6 fields missing): Metadata only (GBM) 0.425; Metadata only (GBM) + MD 0.472; Early concatenation 0.681; Early concatenation + MD 0.644; Late fusion 0.623; Late fusion + MD 0.674; Cross-attention 0.662; Cross-attention + MD 0.631; MetaBlock-style 0.664; MetaBlock-style + MD 0.692.
- Scenario 'smartphone triage' (12 fields missing): Metadata only (GBM) 0.390; Metadata only (GBM) + MD 0.431; Early concatenation 0.497; Early concatenation + MD 0.626; Late fusion 0.540; Late fusion + MD 0.613; Cross-attention 0.457; Cross-attention + MD 0.590; MetaBlock-style 0.445; MetaBlock-style + MD 0.591.

## RQ3. Calibration and selective prediction
- Image only: ECE 0.125 before and 0.023 after temperature scaling (change -0.102 [-0.114 to -0.072]); Brier 0.446 → 0.416; AURC 0.159; error 0.294 at full coverage and 0.242 at 81.5% coverage (threshold from validation data, target 80%).
- Metadata only (GBM): ECE 0.026 before and 0.033 after temperature scaling (change 0.007 [-0.017 to 0.027]); Brier 0.424 → 0.424; AURC 0.150; error 0.309 at full coverage and 0.244 at 79.3% coverage (threshold from validation data, target 80%).
- Metadata only (GBM) + MD: ECE 0.032 before and 0.040 after temperature scaling (change 0.008 [-0.022 to 0.026]); Brier 0.426 → 0.426; AURC 0.153; error 0.317 at full coverage and 0.239 at 79.0% coverage (threshold from validation data, target 80%).
- Early concatenation: ECE 0.099 before and 0.027 after temperature scaling (change -0.072 [-0.075 to -0.049]); Brier 0.386 → 0.365; AURC 0.122; error 0.272 at full coverage and 0.193 at 77.4% coverage (threshold from validation data, target 80%).
- Early concatenation + MD: ECE 0.117 before and 0.027 after temperature scaling (change -0.090 [-0.098 to -0.066]); Brier 0.385 → 0.360; AURC 0.118; error 0.264 at full coverage and 0.188 at 80.0% coverage (threshold from validation data, target 80%).
- Late fusion: ECE 0.042 before and 0.023 after temperature scaling (change -0.020 [-0.034 to 0.007]); Brier 0.309 → 0.300; AURC 0.088; error 0.211 at full coverage and 0.135 at 80.8% coverage (threshold from validation data, target 80%).
- Late fusion + MD: ECE 0.036 before and 0.023 after temperature scaling (change -0.013 [-0.030 to 0.012]); Brier 0.320 → 0.314; AURC 0.092; error 0.215 at full coverage and 0.152 at 81.3% coverage (threshold from validation data, target 80%).
- Cross-attention: ECE 0.133 before and 0.039 after temperature scaling (change -0.094 [-0.097 to -0.078]); Brier 0.420 → 0.390; AURC 0.131; error 0.298 at full coverage and 0.229 at 79.3% coverage (threshold from validation data, target 80%).
- Cross-attention + MD: ECE 0.164 before and 0.032 after temperature scaling (change -0.131 [-0.135 to -0.113]); Brier 0.439 → 0.391; AURC 0.144; error 0.286 at full coverage and 0.221 at 81.4% coverage (threshold from validation data, target 80%).
- MetaBlock-style: ECE 0.020 before and 0.034 after temperature scaling (change 0.015 [-0.005 to 0.025]); Brier 0.369 → 0.363; AURC 0.112; error 0.279 at full coverage and 0.203 at 79.3% coverage (threshold from validation data, target 80%).
- MetaBlock-style + MD: ECE 0.033 before and 0.042 after temperature scaling (change 0.009 [-0.005 to 0.020]); Brier 0.398 → 0.397; AURC 0.129; error 0.312 at full coverage and 0.242 at 79.5% coverage (threshold from validation data, target 80%).

## RQ4. Fairness across subgroups
- Fitzpatrick type, Image only: BA gap between subgroups with at least 30 images = 0.083 [0.051–0.362] (lowest: 3; highest: 4; eligible subgroups: 1, 2, 3, 4).
- Fitzpatrick type, Late fusion: BA gap between subgroups with at least 30 images = 0.157 [0.063–0.348] (lowest: 4; highest: 1; eligible subgroups: 1, 2, 3, 4).
- Age band (years), Image only: BA gap between subgroups with at least 30 images = 0.152 [0.051–0.335] (lowest: <40; highest: ≥80; eligible subgroups: <40, 40–59, 60–79, ≥80).
- Age band (years), Late fusion: BA gap between subgroups with at least 30 images = 0.164 [0.056–0.299] (lowest: <40; highest: 60–79; eligible subgroups: <40, 40–59, 60–79, ≥80).
- Sex, Image only: BA gap between subgroups with at least 30 images = 0.018 [0.001–0.111] (lowest: FEMALE; highest: MALE; eligible subgroups: FEMALE, MALE).
- Sex, Late fusion: BA gap between subgroups with at least 30 images = 0.058 [0.003–0.144] (lowest: FEMALE; highest: MALE; eligible subgroups: FEMALE, MALE).
- Subgroups below the minimum size (reported, not interpreted): Fitzpatrick type 5 (n = 10); Fitzpatrick type 6 (n = 1).

## Metadata-missingness audit
- 804 of 2298 images have at least 50% of their metadata fields missing: 0 of 1089 cancer images and 804 of 1209 non-cancer images.
- The rule 'mostly missing ⇒ non-cancer', which uses no clinical content, has cancer sensitivity 1.000 [1.000–1.000] and specificity 0.665 [0.627–0.702].
- Metadata-only model, All fields with missingness indicators (metadata-only baseline): BA 0.633 [0.596–0.669]; cancer sensitivity 0.900, specificity 0.863.
- Metadata-only model, Missingness pattern only (one indicator per field, no values): BA 0.343 [0.316–0.368]; cancer sensitivity 0.975, specificity 0.683.
- Metadata-only model, Low-missingness fields only (age, region, itch, hurt, bleed, elevation): BA 0.525 [0.488–0.562]; cancer sensitivity 0.686, specificity 0.753.
- Images with recorded metadata (n = 1494), Image only: BA 0.597 [0.550–0.641]; cancer sensitivity 0.813, specificity 0.686.
- Images with recorded metadata (n = 1494), Metadata only (GBM): BA 0.507 [0.464–0.553]; cancer sensitivity 0.900, specificity 0.590.
- Images with recorded metadata (n = 1494), Metadata only (GBM) + MD: BA 0.496 [0.453–0.539]; cancer sensitivity 0.898, specificity 0.556.
- Images with recorded metadata (n = 1494), Early concatenation: BA 0.612 [0.568–0.657]; cancer sensitivity 0.918, specificity 0.622.
- Images with recorded metadata (n = 1494), Early concatenation + MD: BA 0.581 [0.537–0.624]; cancer sensitivity 0.889, specificity 0.622.
- Images with recorded metadata (n = 1494), Late fusion: BA 0.668 [0.620–0.711]; cancer sensitivity 0.912, specificity 0.711.
- Images with recorded metadata (n = 1494), Late fusion + MD: BA 0.653 [0.603–0.696]; cancer sensitivity 0.902, specificity 0.699.
- Images with recorded metadata (n = 1494), Cross-attention: BA 0.551 [0.508–0.596]; cancer sensitivity 0.934, specificity 0.563.
- Images with recorded metadata (n = 1494), Cross-attention + MD: BA 0.560 [0.515–0.604]; cancer sensitivity 0.896, specificity 0.605.
- Images with recorded metadata (n = 1494), MetaBlock-style: BA 0.621 [0.573–0.667]; cancer sensitivity 0.949, specificity 0.578.
- Images with recorded metadata (n = 1494), MetaBlock-style + MD: BA 0.648 [0.603–0.690]; cancer sensitivity 0.910, specificity 0.667.

## Sensitivity analysis: restricted metadata
- Models marked (R) use only the low-missingness fields (age, region, itch, hurt, bleed, elevation).
- Image only: BA 0.644 [0.612–0.676]; cancer sensitivity 0.813, specificity 0.851; among images with recorded metadata 0.813 / 0.686.
- Metadata only (GBM) (R): BA 0.525 [0.488–0.562]; cancer sensitivity 0.686, specificity 0.753; among images with recorded metadata 0.686 / 0.640; Δ BA vs image only -0.120 [-0.170 to -0.069], Holm-adjusted p = 0.002 (interval excludes zero); Δ BA vs Metadata only (GBM) -0.109 [-0.153 to -0.063], Holm-adjusted p = 0.002.
- Early concatenation (R): BA 0.703 [0.672–0.734]; cancer sensitivity 0.882, specificity 0.824; among images with recorded metadata 0.882 / 0.649; Δ BA vs image only 0.059 [0.027–0.090], Holm-adjusted p = 0.004 (interval excludes zero); Δ BA vs Early concatenation -0.001 [-0.035 to 0.033], Holm-adjusted p = 1.000.
- Late fusion (R): BA 0.643 [0.609–0.678]; cancer sensitivity 0.826, specificity 0.873; among images with recorded metadata 0.826 / 0.726; Δ BA vs image only -0.001 [-0.030 to 0.028], Holm-adjusted p = 1.000 (interval includes zero); Δ BA vs Late fusion -0.082 [-0.118 to -0.046], Holm-adjusted p = 0.002.
- Cross-attention (R): BA 0.626 [0.591–0.661]; cancer sensitivity 0.794, specificity 0.848; among images with recorded metadata 0.794 / 0.709; Δ BA vs image only -0.018 [-0.050 to 0.013], Holm-adjusted p = 1.000 (interval includes zero); Δ BA vs Cross-attention -0.045 [-0.086 to -0.003], Holm-adjusted p = 0.187.
- MetaBlock-style (R): BA 0.653 [0.619–0.687]; cancer sensitivity 0.865, specificity 0.859; among images with recorded metadata 0.865 / 0.686; Δ BA vs image only 0.009 [-0.023 to 0.040], Holm-adjusted p = 1.000 (interval includes zero); Δ BA vs MetaBlock-style -0.064 [-0.098 to -0.031], Holm-adjusted p = 0.002.

## Leakage analysis
- Image only: BA 0.644 with patient-grouped splits and 0.672 with image-level splits; difference 0.027 [-0.003 to 0.058] (interval includes zero).
- Metadata only (GBM): BA 0.633 with patient-grouped splits and 0.703 with image-level splits; difference 0.069 [0.037–0.100] (interval excludes zero).

## Explainability (supporting material)
- Grad-CAM not produced: best weights of image_only are not on disk for folds [1, 2, 3, 4] (they were not kept when it was trained: set KEEP_BEST_WEIGHTS to 'gradcam_model' or 'all', delete that model's _DONE.json files for these folds and rerun Part 6).
- Metadata fields with the largest mean |SHAP| in the metadata-only model: fitspatrick (0.343), itch (0.263), age (0.242), elevation (0.179), grew (0.165).
- These analyses are plausibility checks and do not establish clinical validity.

## Outputs not produced
- Figure F10: best weights of image_only are not on disk for folds [1, 2, 3, 4] (they were not kept when it was trained: set KEEP_BEST_WEIGHTS to 'gradcam_model' or 'all', delete that model's _DONE.json files for these folds and rerun Part 6)
- Table T8: the literature file literature_baselines.csv has no rows yet; fill it from the original papers and rerun Parts 15-17
