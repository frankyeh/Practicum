# DSI Studio Minimal Preprocessing Pipeline

Preprocessing of diffusion MRI data refers to the steps taken to prepare the data for analysis. Preprocessing typically includes a combination of correction for technical issues and noise reduction techniques.

## Outline

1. MRI Data Acquisitions
2. From NIFTI/DICOM to SRC files
3. Preprocessing DWI data in SRC files
4. Reconstruct SRC into FIB files

## Session 1: Diffusion MRI Acquisitions

- Recommendation 1: get enough diffusion contrast 
  - b-value > 1,000 mm2/s for human studies
  - No post-acquisition solution
  
- Recommendation 2: acquire isotropic resolutions
  - slice thickness = inplane resolution
  - regrid data to isotropic resolution 

- Recommendation 3: additional reverse-phase b0 
  - for correcting suscetibility distortion
  - Some tools allows using T1w for correction
  - Sequence solution available

- Recommendation 4: multiple b-values

  - HCP-like: three b-values at 1000 (20 dir),2000 (40 dir),3000 (60 dir)
  - DSI-like: b-values = 0 to 3000 at 256 directions

---

## From NIFTI/DICOM to SRC files

Download [OpenNeuro ds002087 dataset](https://openneuro.org/datasets/ds002087) `datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI`



## Identify quality problems due to

- **Motion artifacts**: These occur when the subject moves during the scan, which can cause blurring or distortion in the images.
- **Eddy current artifacts**: These are caused by currents induced in the subject by the MRI's magnetic field gradients. They can cause distortion and signal loss in the images.
- **Susceptibility artifacts**: These are caused by differences in the magnetic properties of different tissues, which can cause signal loss or distortion in the images.

## Options

- FSL's topup:
  - need reversed phase encoding b0
  - Sucetibility distortion correction: This involves correcting for geometric distortions in the images caused by the MRI's magnetic field.
  
- FSL's eddy:
  - need enough DWI for each b-value
  - Eddy current + motion correction: This involves correcting for distortions caused by currents induced in the subject by the MRI's magnetic field gradients.

- DSI Studio's motion correction 

## Recommended Pipelines

Choices in priority
- FSL's TOPUP/EDDY
- FSL's EDDY
- DSI Studio's motion correction

- [DWI](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
- [DWI_PA](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
- [BVAL](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
- [BVEC](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)  

