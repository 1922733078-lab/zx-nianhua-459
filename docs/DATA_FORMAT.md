# Data format

## annotations/classification_and_quality.csv
One row per image: class (01–06 folders), quality grade 1–5, defect deduction, split (train/val/test), subject description, review flags (Chinese headers; see paper Section 3).

## results/raw/*.jsonl
One JSON object per line, one file per model × task × condition:
- `relpath`: image path relative to the corpus root
- `split`: evaluation split (test / val / full / art)
- `y_true`, `y_true_name`: ground-truth class id and name (classification files)
- `y_pred`: predicted class id (classification) or grade digit (rating files)
- `probs`: probability distribution over the six options (classification files)
- `latency_s`: end-to-end latency in seconds (empty in a few maintenance-run files)
- rating files additionally carry `digit_raw` / `digit_exp` / `answer_text`

File naming: `pred_{model}_{task}_{condition}[_variant][_split].jsonl` with models `m1` (JEV-27B-VL, 4-bit), `m2` (Qwen3-VL-8B), `m3` (Qwen3-VL-30B-A3B), `vit_s16`, `resnet50`, `clip`; conditions `N/R/S/RS/S2/RS2/Rdef/Rbr/Rop/K1/K2/K4/Rfix/Rfix2`; variants `_cn/_896/_1024`; splits none=test(45), `_val`=46, `_full`=458, `art`=WikiArt(300).

All paper tables can be recomputed from these files with standard metric implementations (fixed seed 0, 10k bootstrap documented in the paper).
