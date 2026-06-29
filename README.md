# Project Rooting

Kaggle-based Week 1 ultrasound data foundation pipeline for the TCIA B-mode and CEUS Liver collection.

## Overview

This repository contains a reproducible Week 1 sample pipeline for accessing, indexing, auditing, and quality-checking the TCIA B-mode-and-CEUS-Liver collection from a Kaggle Notebook.

The project is part of an ultrasound data foundation workflow for a Liver Digital Twin research direction.

The repository includes:
- Kaggle notebook workflow
- TCIA series manifest
- DICOM metadata manifests
- Clean file-level foundation manifest
- QC contact sheets
- Dual-panel CEUS split preview
- Week 1 QC report

This repository does not include raw DICOM files.

## Repository structure

notebooks/        : Kaggle notebook files
data-manifests/   : CSV metadata manifests and logs
qc/               : QC reports, contact sheets, and preview images
exports/          : Notes about release assets
README.md         : Project overview
.gitignore        : Files excluded from Git
requirements.txt  : Python dependencies

## Data access

Raw imaging data are not redistributed in this repository.

The notebook accesses TCIA at runtime through the NBIA API and targets the collection:

B-mode-and-CEUS-Liver

## Reproduction on Kaggle

1. Open the notebook in Kaggle.
2. Turn Internet ON.
3. Run the notebook cells in order.
4. Start with the controlled sample download.
5. Review generated manifests and QC outputs.

## Week 1 status

The Week 1 sample pipeline successfully:
- connected to TCIA from Kaggle
- retrieved the TCIA series manifest
- downloaded a controlled sample of 5 series
- indexed raw files
- parsed DICOM metadata
- excluded non-image files
- classified single-frame ultrasound images and cine loops
- identified dual-panel CEUS cine candidates
- generated pilot QC frames and contact sheets
- generated dual-panel split previews
- created final Week 1 deliverables

## Current limitation

The current release is based on a controlled sample of 5 series.
Dual-panel splitting is preview-level only and will be confirmed in Week 2 before final preprocessing.

## License

Code is released under the MIT License.

TCIA data are not redistributed here.