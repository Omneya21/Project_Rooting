# Project Rooting — Week 3

## Focus

Week 3 focuses on preprocessing, patient-level dataset splitting, and MONAI-ready dataset construction for the ultrasound branch of Project Rooting.

This week builds directly on Week 2 outputs, which produced validated intra-DICOM paired panel candidates and temporal clip manifests.

## Input

- Week 2 paired panel candidates: 77
- Patients: 10
- Paired panel files: 154
- Temporal clip files: 100

## Preprocessing Policy

- Convert panels to grayscale
- Percentile normalization using 1st–99th percentiles
- Resize with aspect-ratio preservation
- Pad to 256 × 256
- Save outputs as PNG uint8 images

## Dataset Split

Patient-level splitting was used to avoid data leakage between training, validation, and test sets.

| Split | Items |
|---|---:|
| Training | 43 |
| Validation | 22 |
| Test | 12 |

## Outputs

- `data-manifests/week3_preprocessed_pairs.csv`
- `data-manifests/week3_preprocessing_qc_metrics.csv`
- `data-manifests/week3_patient_split.csv`
- `data-manifests/week3_patient_level_split_summary.csv`
- `exports/week3_preprocessing_policy.json`
- `exports/week3_monai_datalist.json`
- `exports/week3_validation_report.json`
- `exports/week3_summary.json`
- `qc/week3_preprocessed_pair_contact_sheet.png`

## Validation

Week 3 validation status: PASS

Validation checks included:

- Input pair count check
- Preprocessed output count check
- File existence check
- Image size check
- Patient-level leakage check
- MONAI datalist consistency check
- MONAI loader smoke test
- QC contact sheet generation

## Scientific Boundary

Week 3 constructs a preprocessed MONAI-ready dataset from Week 2 validated candidate panel pairs.

The paired panels should still be interpreted as candidate intra-DICOM paired panels, not confirmed ground-truth B-mode/CEUS modality labels.

This stage does not estimate stiffness, elastography values, or biomechanical parameters.
