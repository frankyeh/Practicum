# DSI Studio Minimal Preprocessing Pipeline

Preprocessing of diffusion MRI data refers to the steps taken to prepare the data for analysis. Preprocessing typically includes a combination of correction for technical issues and noise reduction techniques.

## Outline

1. MRI Data Acquisitions
  - Recommendations
  
3. Preprocessing DWI data in SRC files
  - motion correction & eddy current distortion correction
  - suscetibility artifact correction

3. Diffusion Models: resolving fibers and quantifying anisotropy
   - DTI/GQI/QSDR


## Session 1: Diffusion MRI Acquisitions (15 minutes)

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

## Session 2: Diffusion MRI Preprocessing (15 minutes)

Download [OpenNeuro ds002087 dataset](https://openneuro.org/datasets/ds002087) `datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI`

## Identify quality problems due to

Starting from largest quality affecting problems

- **Motion artifacts**: These occur when the subject moves during the scan, which can cause blurring or distortion in the images.
  - use QC to drop outlier scans instead of correcting it.
    
- **Eddy current artifacts**: These are caused by currents induced in the subject by the MRI's magnetic field gradients. They can cause distortion and signal loss in the images.
  - sequence-based solution available (bipolar pulse)
  - increamental improvement nowadays because of sequence improvement
   
- **Susceptibility artifacts**: These are caused by differences in the magnetic properties of different tissues, which can cause signal loss or distortion in the images.
  - sequence-based solution available (readout segmentation)
  - very limited improvement
  - cannot get the missing region back

- **noise reduction**
  - not really needed for DTI and GQI/QSDR
  - impossible to keep all meaningful information 

- **Gibbs ringing**
  - SNR too low at DWI to see them. 

## Tools

- FSL's topup:
  - need reversed phase encoding b0
  - Sucetibility distortion correction: This involves correcting for geometric distortions in the images caused by the MRI's magnetic field.
  
- FSL's eddy:
  - need enough DWI for each b-value
  - Eddy current + motion correction: This involves correcting for distortions caused by currents induced in the subject by the MRI's magnetic field gradients.

- DSI Studio's motion correction 

- Hands-on
  - Download .sz files from Fiber Data Hub's [OpenNeuro][ds002087]
  - Compare .sz with/without corrections
  - Compare .fz with/without corrections
  - Compare arcuate fasciculus with/without corrections
  
## Recommended Pipelines

Choices in priority
- FSL's TOPUP/EDDY
- FSL's EDDY
- DSI Studio's motion correction

- [DWI](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
- [DWI_PA](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
- [BVAL](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
- [BVEC](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)  

---

## Session 3: Diffusion Modeling Methods  (15 minutes)

- my two cents: the angular resolution issue is overrated
  FACT 1: angular resolution does not help resolving crossing from kissing pattern: we never get groundtruth pattern just from the DWI data
  FACT 2: higher **spatial** resolution handles most of the problem: at higher resolution we CAN distinguish crossing from kissing.
  FACT 3: we only have ~180 mostly low-SNR data points. overfitting happens very quickly.
  Strategy 1: instead of aiming for angular resolution, opt for spatial resolution.
  Strategy 2: choose a method robust to noise and stable against noise.

- DTI
  - my two cents: the limitation of single tensor is exaggerated at low spatial resolution.
  - The poor reliability of fractional anisotropy at low SNR is neglected.
  
- GQI/QSDR
  - limited cross fiber resolving power.
  - mathematically, the largest peak at GQI's ODF converges with tensor principle direction.
  - The major strength is providing a robust anisotropy measurement to guide fiber tracking

