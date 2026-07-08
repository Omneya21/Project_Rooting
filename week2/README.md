# Week 2 - Ultrasound Processing, QC, and Pairing Pipeline

## Overview

Week 2 extends the initial ultrasound data foundation developed in Week 1 into a controlled end-to-end processing and validation pipeline.

The workflow focuses on reliable DICOM processing, temporal structure analysis, quality control, dual-panel split validation, pairing-candidate generation, temporal clip extraction, and MONAI compatibility testing.

## Workflow

1. Controlled TCIA series selection
2. Series download and ZIP verification
3. Extraction and raw file indexing
4. DICOM header parsing
5. Image and non-image filtering
6. Pixel decoding and QC
7. Single-frame and multi-frame characterization
8. Representative-frame extraction
9. Wide-layout candidate detection
10. Dual-panel split estimation
11. Confidence scoring
12. Manual split audit
13. Pairing-candidate generation
14. Temporal clip extraction
15. MONAI-compatible draft datalist generation
16. Final validation tests

## Key Results

| Metric | Result |
|---|---:|
| Selected series | 10 |
| Raw indexed files | 109 |
| Valid image DICOM objects | 99 |
| Successfully decoded images | 99/99 |
| Single-frame objects | 50 |
| Multi-frame cine objects | 49 |
| Total represented frames | 3,501 |
| Wide-layout candidates | 83 |
| Accepted split candidates | 77 |
| Rejected split candidates | 6 |
| Pairing candidates | 77 |
| Paired cases | 10 |
| Temporal frame pairs | 50 |
| MONAI-compatible draft items | 77 |
| Validation tests passed | 8/8 |

## Important Scientific Boundary

The 77 exported pairs are validated intra-DICOM panel-pair candidates.

They are not treated as confirmed ground-truth B-mode/CEUS pairs unless explicit modality annotation is available.

The current Week 2 pipeline does not estimate tissue stiffness, Young's modulus, or biomechanical material parameters from B-mode or CEUS images.

## Main Week 2 Finding

A wide ultrasound image cannot automatically be assumed to contain two valid ultrasound panels.

Manual review identified cases in which one side of the image was an ultrasound view while the other side contained device controls or user-interface content.

For this reason, split estimation was combined with confidence scoring and manual validation before pairing candidates were accepted.

## Outputs

### Data manifests

Contains:

- controlled batch selection records
- download logs
- raw file index
- DICOM manifests
- excluded non-image records
- QC metrics
- split validation results
- manual audit results
- pairing candidates
- paired-case summaries
- temporal clip manifest
- MONAI-compatible draft items

### QC

Contains:

- patient contact sheets
- split audit examples
- split audit contact sheet
- pairing QC examples

### Exports

Contains:

- daily Week 2 summaries
- validation report
- MONAI draft dataset metadata
- package inventory

## Next Step

Week 3 will focus on:

- normalization strategy
- resize and padding policy
- standardized 2D paired samples
- 2.5D temporal clip preparation
- patient-level train/validation/test splitting
- final MONAI dataset construction
- loader and transform validation

## Status

**Week 2: Complete - GO**