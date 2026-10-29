# ZX-Nianhua-459: An Expert-Annotated Benchmark of Zhuxian Woodblock New Year Prints

ZX-Nianhua-459 是首个公开的朱仙镇木版年画（国家级非物质文化遗产）专家标注图像基准，随包发布判定标准原文与逐样本实验输出。它支撑论文《基于"规则即标准"的系统一决策模型专家鉴赏力研究——以朱仙镇木版年画为例》(Encoding Expert Connoisseurship in System One Decision Models through Rules as Criteria) 的全部数字复算。

Zhuxian woodblock New Year prints are one of the oldest production centres of Chinese nianhua and a national intangible cultural heritage. This repository releases the first expert-annotated image benchmark of the genre: **459 museum photographs** over **six typological classes**, each labelled with an expert **visual-quality grade (1–5)** and **defect metadata**, together with the **verbatim written criteria** (class definitions, boundary rules, grading scale) used by the annotating expert, a frozen few-shot exemplar manifest, and the **complete per-sample evaluation outputs** of the paper (116 result files, analysis tables).

## Contents

| Path | Description |
|---|---|
| `annotations/classification_and_quality.csv` | Ground truth: class, quality grade (1–5), defect deductions, train/val/test split (367/46/45), per-image metadata (Chinese) |
| `annotations/fewshot_manifest.json` | Frozen few-shot exemplar list (2 per class, deterministic ordering) |
| `annotations/exclusions.json` | Documented exclusions (one truncated file; policy against the duplicate "curated selection" folder) |
| `criteria/` | Verbatim expert criteria texts (six-class definitions, boundary rules R1–R7, five-grade quality scale; plus WikiArt control criteria) |
| `results/raw/` | 116 per-sample prediction files (JSON Lines), one per model×task×condition |
| `results/metrics.csv` | Aggregated metrics for all runs |
| `results/analysis/` | Significance tests (bootstrap 95% CIs + exact McNemar), calibration, stratified, boundary-case and efficiency tables |
| `docs/wikiart_bench_manifest.csv` | Frozen 320-item WikiArt control manifest (WikiArt images are NOT redistributed here due to third-party rights; obtain them from WikiArt sources) |
| Release asset `zx-nianhua-459-images-v1.0.0.zip` | All 459 photographs (six class folders) + the annotation CSV |

**Images are distributed as a GitHub Release asset** (see [Releases](../../releases)); the git tree carries only metadata and results. Download the zip, verify against `docs/SHA256SUMS-images.txt`, and extract next to this repository.

## Dataset card

- **Collection**: 459 photographs of Zhuxian woodblock New Year prints, museum documentation campaign (April 2026), fixed capture settings. Photographs deliberately retain desk backgrounds, fingers, shadows, colour casts and creases; these defects are annotated and are part of the task.
- **Typology (six classes)**: (a) martial door gods 114; (b) infant/child motifs 84; (c) ladies/beauties 17; (d) civil-official deities 86; (e) opera scenes 124; (f) auspicious non-figural 34. Split: train 367 / val 46 / test 45 (effective; see exclusions).
- **Quality grades**: per-image expert grade 1–5 per the released scale in `criteria/criteria_quality_scale.txt`.
- **Known issues / erratum**: an earlier internal count of 460 included one truncated file (excluded; see `annotations/exclusions.json`) — the public release is the corrected 459-image corpus. A byte-identical "curated selection" duplicate folder (12 files) exists in the source collection and is excluded from the release; do not mix it in.
- **Reproducibility**: every number in the paper is recomputable from `results/raw/` per-sample outputs alone (macro-F1, accuracy, MAE, ECE, bootstrap CIs, McNemar tests). See `docs/DATA_FORMAT.md`. Evaluation **code** is not part of this release and will be released upon paper acceptance.

## License

Released under **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** — see `LICENSE`. You may use, share and adapt the material for non-commercial purposes with attribution. **Commercial use in any form (including commercial products, paid services, commercial model training, or commercial evaluation) requires prior written permission** — contact: 1922733078@qq.com.

## Citation

Paper under review; a formal citation (and arXiv DOI) will be added here upon posting. Until then, please cite this repository.
