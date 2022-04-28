# Diffusion MRI Processing

## Before practicum on Friday, please complete following:

### Diffusion MRI basics

- Read through Dr. Yeh's [review paper](Materials/paper/review.pdf) on diffusion MRI, which also can be found under the shared folder. Pay special attention to part 3 (tractography methods), 5.2 (model-free methods), part 6 (fiber tracking methods) and part 7 (DTI tractography in brain tumors).

- Diffusion MRI acquisition

<iframe width="560" height="315" src="https://www.youtube.com/embed/VGD1dwtTyEk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- Diffusion tensor imaging

<iframe width="560" height="315" src="https://www.youtube.com/embed/h44z9_xX8ig" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

## During practicum on Friday:

- Introduction to DSI Studio 
  - [create SRC files from NIFTI or DICOM](https://dsi-studio.labsolver.org/doc/gui_t1.html)
  - [reconstruct DWI data](https://dsi-studio.labsolver.org/doc/gui_t2.html)
  - [fiber tracking](https://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html)

- Diffusion MRI quality control:

<iframe width="896" height="504" src="https://www.youtube.com/embed/stL4GMeTC1I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Assignment :

### Task 1: Process dMRI data

1. Download dwi data from [OpenNeuro](https://openneuro.org/datasets/ds002087/versions/1.0.0)

run 1:
  - [NIFTI](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.nii.gz)
  - [BVAL](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bval)
  - [BVEC](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bvec)

run 2:
  - [NIFTI](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.nii.gz)
  - [BVAL](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bval)
  - [BVEC](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bvec)

2. [Generate SRC file](http://dsi-studio.labsolver.org/doc/gui_t1.html) for run 1 and run 2, respectively, and check if there is any quality issue. [(youtube)](https://www.youtube.com/embed/stL4GMeTC1I).

4. Apply [Eddy Correction] to run 2 SRC file at [Step T2][Correction] and save it as a new SRC.gz file

5. compare the raw images with/without [Eddy Correction]

6. Move all SRC.gz files (run1, run2, run2 after eddy) to a folder, and use [Step T1a Quality Control] to get a report. Identify metrics that show quality issues.

7. Compare whole brain tractogram with/without [Eddy Correction].

### Task 2: Automated fiber tracking

1. Run [automatic fiber tracking](http://dsi-studio.labsolver.org/doc/gui_t3_atk.html) on left arcuate fasciculus and compare it with manual result (on DTI and GQI fib files).

