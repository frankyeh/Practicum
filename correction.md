# Diffusion MRI Processing

Diffusion MRI is a type of magnetic resonance imaging (MRI) that is used to visualize and quantify the movement of water molecules in the body. It is particularly useful for studying the white matter tracts in the brain, which are made up of axons (long, thin fibers) that connect different areas of the brain and facilitate communication between neurons.

In a diffusion MRI scan, the movement of water molecules is measured by applying a magnetic field gradient to the tissue being imaged. The resulting data can be used to calculate various diffusion-related parameters, such as the fractional anisotropy (FA) and mean diffusivity (MD), which can provide information about the structure and function of the brain.

Diffusion MRI is a non-invasive, safe, and widely used technique in the field of neuroscience and has many applications in research and clinical practice. It can be used to study the structural organization of the brain, to identify abnormalities or changes in the white matter tracts that may be associated with various neurological conditions, and to monitor the progression of diseases.

## Before practicum on Friday, please complete following:

### Diffusion MRI basics

- Read [[4. Diffusion MRI acquisitions]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0007)
  - 4.1. Scanning time
  - 4.2. B-value
  - 4.3. Sampling scheme
- Read [[5. Fiber resolving methods]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0020) 

---

## During practicum on Friday:

- Introduction to DSI Studio 
  - [create SRC files from NIFTI or DICOM](https://dsi-studio.labsolver.org/doc/gui_t1.html)
  - [reconstruct DWI data](https://dsi-studio.labsolver.org/doc/gui_t2.html)
  - [fiber tracking](https://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html)

- Diffusion MRI quality control:

<iframe width="896" height="504" src="https://www.youtube.com/embed/stL4GMeTC1I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

  - dMRI data without motion:
    - [DWI](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.nii.gz)
    - [BVAL](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bval)
    - [BVEC](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bvec)

  - dMRI data with motion:
    - [DWI](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.nii.gz)
    - [BVAL](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bval)
    - [BVEC](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bvec)

  - Identify suscetibility artifact and motion artifact.
  - Compare tractography before/after correction

- dMRI Preprossing

  - Eddy current distortion and artifacts correction
  - Sucetibility artifacts correction
  
    - [DWI](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
    - [DWI_PA](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
    - [BVAL](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
    - [BVEC](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)   

## Assignment :

### Task 1: Eddy current and motion correction

Download DWI data from [OpenNeuro](https://openneuro.org/datasets/ds002087/versions/1.0.0)


2. [Generate SRC file](http://dsi-studio.labsolver.org/doc/gui_t1.html) for run 1 and run 2, respectively, and check if there is any quality issue. [(youtube)](https://www.youtube.com/embed/stL4GMeTC1I).

4. Apply [Eddy Correction] to run 2 SRC file at [Step T2][Correction] and save it as a new SRC.gz file

5. compare the raw images with/without [Eddy Correction]

6. Move all SRC.gz files (run1, run2, run2 after eddy) to a folder, and use [Step T1a Quality Control] to get a report. Identify metrics that show quality issues.

7. Compare whole brain tractogram with/without [Eddy Correction].

### Task 2: Susceptibility artifact correction

1. Download DWI data from [OpenNeuro](https://openneuro.org/datasets/ds003974/versions/1.0.0)

  - [DWI](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
  - [DWI_PA](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
  - [BVAL](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
  - [BVEC](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)
  
2. [Generate SRC file](http://dsi-studio.labsolver.org/doc/gui_t1.html) 

3. Apply [Correction][Topup/EDDY] and save as a new SRC file after correction.

4. Compare raw DWI and tractography with/without 
