# DSI Studio Minimal Preprocessing Pipeline

![image](https://github.com/user-attachments/assets/5102fc0a-ba86-4c61-b165-9c79498e684a)

Preprocessing of diffusion MRI data refers to the steps taken to prepare the data for analysis. Preprocessing typically includes a combination of correction for technical issues and noise reduction techniques.

## Outline

1. MRI Data Acquisitions
  - Recommendations
  
3. Preprocessing DWI data in SRC files
  - motion correction & eddy current distortion correction
  - suscetibility artifact correction

3. Diffusion Models: resolving fibers and quantifying anisotropy
   - DTI/GQI/QSDR

---

## Session 1: Diffusion MRI Acquisitions (15 minutes)

### Recommendation 1: get enough diffusion contrast 

- b-value > 1,000 s/mm^2 for human studies
- no post-acquisition solution

HCP-YA data (b-value=0,1000,2000,3000 s/mm^2, b-vector=0,0,1)

![image](https://github.com/user-attachments/assets/2a47fe2b-7a38-42d3-84c4-b69baae046bc)

  
### Recommendation 2: acquire isotropic resolutions

- slice thickness = inplane resolution
- regrid data to isotropic resolution 

OpenNeuro ds005849 (in-plane = 1.75 mm  slice-thickness = 2.7 mm)

![image](https://github.com/user-attachments/assets/df8847c7-a585-4aa1-88e6-32e8d0e1ba70)

### Recommendation 3: additional reverse-phase b0 

- for correcting suscetibility distortion
- Some tools allows using T1w for correction
- Sequence solution available

(source: [FSL Website](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/topup(2f)TopupUsersGuide.html): )

Before correction (phase encoding: AP,AP,PA,PA)

<img src="https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/attachments/topup(2f)TopupUsersGuide/original_images.png"/>

After correction

<img src="https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/attachments/topup(2f)TopupUsersGuide/hifi_images.png"/>


### Recommendation 4: multiple b-values

- multi-shell (HCP-like): three b-values at 1000 (20 dir),2000 (40 dir),3000 (60 dir)
- grid (DSI-like): 23 b-values from 0 to 4,000 s/mm^2 at 258 directions

---

## Session 2: Diffusion MRI Preprocessing (15 minutes)

- Download [OpenNeuro ds002087](https://openneuro.org/datasets/ds002087): datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI
- Convert NIFTI to SRC files

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

- [FSL's topup](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/topup.html):
  - need reversed phase encoding b0
  - Sucetibility distortion correction: This involves correcting for geometric distortions in the images caused by the MRI's magnetic field.
  
- [FSL's eddy](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/eddy(2f)UsersGuide.html):
  - need enough DWI for each b-value
  - Eddy current + motion correction: This involves correcting for distortions caused by currents induced in the subject by the MRI's magnetic field gradients.

- DSI Studio's motion correction 

- Preprocessing Options:
  1. FSL's topup/eddy
  2. FSL's eddy
  3. DSI Studio's motion correction
  

- Hands-on 1
  1. Download .sz files from Fiber Data Hub's [OpenNeuro][ds002087]
  2. Compare .sz with/without corrections
  3. Compare .fz with/without corrections
  4. Compare arcuate fasciculus with/without corrections
  
- Hands-on 2
  1. Download: [dwi](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.nii.gz), [b0-pa](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/fmap/sub-01_acq-multiband_dir-PA_dwi.nii.gz), [bval](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.bval), [bvec](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.bvec)  
  2. Identify reversed phase encoding b0
  3. Run FSL's topup/eddy

---

## Session 3: Additional Preprocessing Steps (15 minutes)

- B-table correction (animal studies)
- Flip/Swap image axis (animal studies)
- Regrid to isotropic resolution

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

---
## Session 4: GUI-based Batch Processing (15 minutes)

