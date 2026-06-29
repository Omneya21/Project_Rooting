# Week 1 Sample QC Report

## Project
Ultrasound Data Foundation for TCIA B-mode and CEUS Liver Collection

## Environment
Platform: Kaggle Notebook  
Raw data source: TCIA NBIA API  
Collection: B-mode-and-CEUS-Liver

## Generated at
2026-06-29 19:19:02

## Sample download summary
- Total TCIA series available: 120
- Downloaded sample series: 5
- Raw files indexed: 104
- DICOM candidate files before cleaning: 104
- Valid image DICOM files after cleaning: 99
- Excluded non-image files: 5

## DICOM metadata parsing
- Parsed DICOM headers successfully: 104
- Failed DICOM header parses: 0

## Image type summary
image_type
single_frame_image       65
multi_frame_cine_loop    34

## Layout summary
layout_v1
wide_static_candidate            41
dual_panel_cine_candidate        25
single_panel_static_candidate    24
single_panel_cine_candidate       9

## Ultrasound role summary
ultrasound_role_v1
wide_static_ultrasound_candidate        41
ceus_bmode_dual_panel_cine_candidate    25
static_bmode_candidate                  24
cine_ultrasound_candidate                9

## Series-level summary
- Unique patients: 5
- Unique studies: 5
- Unique series: 5
- Scanner manufacturer: ['GE Healthcare']
- Scanner model: ['LOGIQE9']

## Pilot frame extraction
- Selected preview DICOM files: 10
- Extracted PNG preview frames: 20
- Pilot extraction log: /kaggle/working/liver_digital_twin/data/manifests/pilot_frame_extraction_log_clean.csv
- Contact sheet: /kaggle/working/liver_digital_twin/data/qc/pilot_frames_contact_sheet_clean.png

## Interpretation
This sample confirms that the TCIA B-mode-and-CEUS-Liver collection can be accessed directly from Kaggle through the TCIA NBIA API and processed inside /kaggle/working without local download.

The sample contains both single-frame ultrasound images and multi-frame cine loops. Visual QC suggests that some cine frames may contain dual-panel layouts with B-mode and CEUS displayed side by side. Therefore, later stages should include visual QC and possible panel-splitting/cropping before model training.

## Current status
Week 1 data foundation sample pipeline is working.

## Next steps
1. Inspect dual-panel cine candidates visually.
2. Add panel-splitting logic for wide frames if confirmed.
3. Build a more systematic sampling strategy for downloading smaller series first.
4. Expand from 5 sample series to a larger controlled batch.
5. Prepare MONAI-compatible dataset records after pairing/cropping rules are confirmed.


## Dual-panel split preview

A first-pass dual-panel split preview was created for selected cine candidates.

- Dual-panel cine candidate files: 25
- Files used for split preview: 5
- Split preview PNGs generated: 30
- Split preview folder: /kaggle/working/liver_digital_twin/data/panel_split_preview
- Split preview contact sheet: /kaggle/working/liver_digital_twin/data/qc/dual_panel_split_preview_contact_sheet.png
- Split log: /kaggle/working/liver_digital_twin/data/manifests/dual_panel_split_preview_log.csv

Interpretation:
Visual QC confirms that some CEUS cine frames use a dual-panel layout. The left side is treated as a B-mode candidate and the right side as a CEUS candidate for preview purposes only. This split should be manually verified before being used as a final preprocessing rule.
