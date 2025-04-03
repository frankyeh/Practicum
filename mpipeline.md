# DSI Studio Minimal Preprocessing Pipeline

Preprocessing of diffusion MRI data refers to the steps taken to prepare the data for analysis. Preprocessing typically includes a combination of correction for technical issues and noise reduction techniques.

## Outline

1. MRI Data Acquisitions
2. From NIFTI/DICOM to SRC files
3. Preprocessing DWI data in SRC files
4. Reconstruct SRC into FIB files

## Session 1: MRI Data Acquisitions

- Recommendation 1: b > 1,000 mm2/s for human studies
  No post-acquisition solution
    
- Recommendation 2: isotropic resolutions
  - slice thickness = inplane resolution
  - regrid data to isotropic resolution 

**Additional Improvements**

- One reverse-phase b0 for correcting suscetibility distortion
  - AP + PA (b0 only)
  - Some tools allows using T1w for correction
  - Sequence solution available

**High Quality Acquisition**

- HCP-like: three b-values at 1000 (20 dir),2000 (40 dir),3000 (60 dir)
- DSI-like: b = 0 to 3000 at 256 directions

---

## Session 2: From NIFTI/DICOM to SRC files

- DICOM files
  - DICOM rename
  - DICOM to SRC files
    
- NIFTI files
  - Download [OpenNeuro ds002087 dataset](https://openneuro.org/datasets/ds002087) `datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI`
  - 





### Diffusion MRI quality control:

Diffusion MRI quality control refers to the steps taken to ensure that the diffusion MRI data is of sufficient quality for the intended analysis. Quality control is an important step in the diffusion MRI process, as poor quality data can affect the accuracy and reliability of the results.

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

### Artifacts in diffusion MRI

Artifacts in diffusion MRI includes distorted images and deviated signals that are not representative of the true underlying tissue structure. They can be caused by a variety of factors, including technical issues with the MRI scanner or the data acquisition process, subject movement during the scan, and other sources of noise or interference.

Some common types of artifacts that can occur in diffusion MRI include:

  - **Motion artifacts**: These occur when the subject moves during the scan, which can cause blurring or distortion in the images.
  - **Eddy current artifacts**: These are caused by currents induced in the subject by the MRI's magnetic field gradients. They can cause distortion and signal loss in the images.
  - **Susceptibility artifacts**: These are caused by differences in the magnetic properties of different tissues, which can cause signal loss or distortion in the images.

Artifacts in diffusion MRI can affect the quality and accuracy of the resulting data and should be carefully corrected or accounted for in the data analysis process.


Some common steps in the preprocessing of diffusion MRI data include:

- Motion correction: This involves aligning the images acquired at different time points to correct for subject movement during the scan
- Eddy current correction: This involves correcting for distortions caused by currents induced in the subject by the MRI's magnetic field gradients.
- Distortion correction: This involves correcting for geometric distortions in the images caused by the MRI's magnetic field.

Other optional preprocessing include:

- Denoising: This involves applying techniques such as spatial smoothing or noise reduction filters to reduce the amount of noise in the data.
- Bias field correction: This involves correcting for intensity inhomogeneities in the images caused by the MRI's magnetic field.


### Diffusion MRI Preprossing

Preprocessing of diffusion MRI data refers to the steps taken to prepare the data for analysis. Preprocessing typically includes a combination of correction for technical issues and noise reduction techniques.

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
