# Project Rooting — Week 4

## Focus

Week 4 focuses on ultrasound-specific augmentation and final dataset quality control.

This week builds directly on Week 3 outputs, which created a preprocessed, patient-level split, MONAI-ready paired panel dataset.

## Week 4 Goal

The goal is to create an AI-ready augmented dataset while preserving scientific boundaries.

This week does not perform model training, domain adaptation, stiffness estimation, or biomechanics simulation.

## Input

- Week 3 preprocessed paired panel candidates: 77
- Patients: 10
- Input package: `week3_full_outputs_for_week4.zip`

## Augmentation Policy

Augmentation is applied only to the training split.

Validation and test splits are kept original to avoid evaluation contamination.

### Spatial augmentations

- Small rotation
- Small translation
- Small zoom

The same spatial transform parameters are applied to panel A and panel B in each pair.

### Intensity augmentations

- Gamma variation
- Gain variation
- Offset variation
- Speckle-style multiplicative noise

## Output Counts

| Output | Count |
|---|---:|
| Original Week 3 pairs | 77 |
| Training original pairs | 43 |
| Augmented training items | 129 |
| Final manifest items | 206 |
| MONAI training items | 172 |
| MONAI validation items | 22 |
| MONAI test items | 12 |

## Key Outputs

- `data-manifests/week4_augmented_pairs_manifest.csv`
- `data-manifests/week4_augmentation_qc_metrics.csv`
- `exports/week4_augmentation_policy.json`
- `exports/week4_monai_augmented_datalist.json`
- `exports/week4_validation_report.json`
- `exports/week4_summary.json`
- `qc/week4_augmented_pair_contact_sheet.png`
- `notebooks/week4-project-rooting.ipynb`

## Validation

Week 4 validation status: PASS

Validation checks include:

- Original Week 3 count preservation
- Augmented training item count
- Final manifest count
- Image file existence
- 256 × 256 image size check
- Patient-level split leakage check
- No augmentation in validation/test splits
- MONAI datalist consistency
- MONAI loader smoke test
- QC contact sheet generation

## Scientific Boundary

The paired panels remain candidate intra-DICOM paired panels.

They are not confirmed ground-truth B-mode/CEUS modality labels.

Week 4 does not create stiffness values, elastography maps, biomechanical parameters, or clinical interpretations.
