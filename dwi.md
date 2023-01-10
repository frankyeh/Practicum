# Diffusion MRI Basics

Diffusion MRI is a type of magnetic resonance imaging (MRI) that is used to visualize and quantify the movement of water molecules in the body. It is particularly useful for studying the white matter tracts in the brain, which are made up of axons (long, thin fibers) that connect different areas of the brain and facilitate communication between neurons.

In a diffusion MRI scan, the movement of water molecules is measured by applying a magnetic field gradient to the tissue being imaged. The resulting data can be used to calculate various diffusion-related parameters, such as the fractional anisotropy (FA) and mean diffusivity (MD), which can provide information about the structure and function of the brain.

Diffusion MRI is a non-invasive, safe, and widely used technique in the field of neuroscience and has many applications in research and clinical practice. It can be used to study the structural organization of the brain, to identify abnormalities or changes in the white matter tracts that may be associated with various neurological conditions, and to monitor the progression of diseases.

## Before practicum on Friday, please complete following:

### Diffusion MRI basics

Diffusion-weighted images (DWI) are a type of magnetic resonance imaging (MRI) that are sensitive to the movement of water molecules within a sample. They are created by applying a magnetic field gradient to the sample and measuring the resulting diffusion of water molecules. The resulting images are called diffusion-weighted because they are weighted according to the amount of diffusion that has occurred.

The b-value is an important parameter in diffusion MRI, as it determines the sensitivity of the resulting images to the diffusion of water molecules in the tissue. Higher b-values correspond to stronger diffusion weighting and more sensitive images, while lower b-values correspond to weaker diffusion weighting and less sensitive images.

The sammpling scheme of diffusion MRI refers to the specific set of b-value and gradient table used to acquire diffusion weighted images. Commonly-used schemes include single-shell, which acquires one b-value at multiple directions, multishell, which acquires two or three b-values at multiple directions, grid, which acquires multiple b-values at multiple directions.


- Read [[4. Diffusion MRI acquisitions]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0007)
  - 4.1. Scanning time
  - 4.2. B-value
  - 4.3. Sampling scheme

- Watch a video about dMRI

<iframe width="560" height="315" src="https://www.youtube.com/embed/wWcCKHp09QA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

- Read [[4.4 Distortions and artifacts]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0015) 
  - 4.4.1. Eddy current distortion
  - 4.4.2. Susceptibility-induced distortions and artifacts

- Watch a video about distortions and artifacts in dMRI

<iframe width="560" height="315" src="https://www.youtube.com/embed/fXdhCdG4S_E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

## During practicum on Friday:

### Overview (10 min)

<img src="https://user-images.githubusercontent.com/275569/193154846-4a610eaa-ac9e-4f78-9e0e-c2cc94de3eff.png" width=1000>

- Hands-on: create SRC files from NIFTI data
  - [sub-01_run-1_dwi.nii.gz](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.nii.gz)
  - [sub-01_run-1_dwi.bval](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bval)
  - [sub-01_run-1_dwi.bvec](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bvec)
  - source: [Datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI](https://openneuro.org/datasets/ds002087/)
  - Create an SRC file

**CLI for creating SRC**
```
dsi_studio --action=src --source=sub-01_dwi_sub-01_run-1_dwi.nii.gz --bval=sub-01_dwi_sub-01_run-1_dwi.bval --bvec=sub-01_dwi_sub-01_run-1_dwi.bvec --output=sub-01_dwi_sub-01_run-1_dwi.src.gz
```

### Diffusion MRI sequence diagram (10 min)

<img src="https://user-images.githubusercontent.com/275569/168139630-595e86c8-440e-4e3e-8ba4-bf4a608201c5.png" width=500>

source: [Morozov, Sergey, et al. "Diffusion processes modeling in magnetic resonance imaging." Insights into Imaging 11.1 (2020): 1-9.](https://insightsimaging.springeropen.com/articles/10.1186/s13244-020-00863-w)

<img src="https://user-images.githubusercontent.com/275569/168139693-32751d64-985b-4651-9040-8da96541552a.png" width=500>

source: [Morozov, Sergey, et al. "Diffusion processes modeling in magnetic resonance imaging." Insights into Imaging 11.1 (2020): 1-9.](https://insightsimaging.springeropen.com/articles/10.1186/s13244-020-00863-w)

- diffusion MRI = MRI acquisition (mostly spin-echo) + additional diffusion sensitization
- diffusion contrast created by signal attenuation

### Diffusion sensitization (5 min)

- B-value: a product of variables affecting the sensitivity to diffusion
  - Diffusion time (Δ): the "explosure time"
  - Diffusion gradient strength (g) and duration (δ): the "ISO"
    
  ![image](https://user-images.githubusercontent.com/275569/168140200-5ffde8c7-18b3-477a-a527-36da7fe3c332.png)
    
  (γ: gyromagnetic ratio)
       
- B-vector: Diffusion encoding directions

### Sampling schemes of the b-table (5 min)

- Single-shell: one b-value at 30 directions (e.g. DTI, high angular resolution diffusion imaging, a.k.a. HARDI)
- Multi-shell: 2 or 3 b-values with 90 directions acquired at each b-value
- Grid: a total of 258 directions acquired by 23 b-values.
 
![image](https://user-images.githubusercontent.com/275569/168138897-e96f3fd6-e690-4b2d-a72f-5036437a6612.png)
 
- Hands-on: identify sampling schemes
  - [Single-shell](https://zenodo.org/record/6320992/files/20081006_M025Y_HARDI.src.gz?download=1) 
  - [Multi-Shell](https://zenodo.org/record/6315871/files/mgh_1001.src.gz?download=1)
  - [Grid](https://zenodo.org/record/6320992/files/20081006_M025Y_DSI_203.src.gz?download=1)

### Quality Checks on dMRI data 
    
- Hands-on
  - [sub-01_run-2_dwi.nii.gz](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.nii.gz)
  - [sub-01_run-2_dwi.bval](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bval)
  - [sub-01_run-2_dwi.bvec](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bvec)
  - source: [Datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI](https://openneuro.org/datasets/ds002087/)
  - Identify motion induced signals issues
  - QC in DSI Studio
  
- Motion artifacts (5 min)
  - Check sagittal slices
  - Check slice signal dropout
  - Correction using [FSL's eddy](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)
      
- Eddy distortion (10 min)     


<img src="https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy?action=AttachFile&do=get&target=before_after_s2v.gif" width=500>

(source: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)
        
<img src="https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy?action=AttachFile&do=get&target=before_after_hcp_v4.gif" width=250>

(source: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)

  - Linear distortion
  - Larger at higher b-value
  - Correction using [FSL's eddy](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)
  - Bipolar-pulse to cancel eddy currents

**CLI for EDDY**
```
dsi_studio --action=rec --source=sub-01_dwi_sub-01_run-1_dwi.nii.gz.src.gz --cmd="[Step T2][Corrections][EDDY]" --save_src=preproc.src.gz
```

    
- Susceptibility distortion and artifact (10 min)    
  
<img src="https://user-images.githubusercontent.com/275569/167231465-26a3d2b7-d3ad-42d6-abb7-7720330aac14.png" width=500>
      
(source: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/topup/TopupUsersGuide)
  
- Hands-on
  - [sub-01_acq-multiband_dwi.nii.gz](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
  - [sub-01_acq-multiband_dir-PA_dwi.nii.gz](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
  - [sub-01_acq-multiband_dwi.bval](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
  - [sub-01_acq-multiband_dwi.bvec](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)
  - Correct susceptibility artifact and distortion using [FSL's topup](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/topup)   

**CLI for TOPUP+EDDY**
```
dsi_studio --action=rec --source=sub-01_dwi_sub-01_acq-multiband_dwi.nii.gz.src.gz --rev_pe=sub-01_fmap_sub-01_acq-multiband_dir-PA_dwi.nii.gz --save_src=preproc.src.gz
```

- Recommended steps: TOPUP (handles susceptibility) + EDDY (handles eddy distortion and motion displacement)
  - DWI without reverse PE
    - create SRC from DWI
    - apply eddy: [Step T2][Correction][EDDY]
  - DWI with reverse PE(b0)
    - create SRC from DWI
    - create NIFTI from reversed PE b0
    - apply topup + eddy: [Step T2][Correction][TOPUP/EDDY] or specify --rev_pe=rev_b0.nii.gz
  - DWI with reverse-PE(full DWI)
    - create SRC from DWI
    - create SRC from reversed-PE DWI
    - apply topup + eddy: [Step T2][Correction][TOPUP/EDDY] or specify --rev_pe=rev_dwi.rsrc.gz


## Assignment :

### Process dMRI data on real-world studies

1. Download data from the [SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003) to a folder (e.g. D:/SCA2) study

2. Click [Batch Processing][Step B2a: NIFTI to SRC (BIDS)] and select the folder. DSI Studio will ask to specify another folder to output the SRC files (e.g. D:/src).

3. Run [Diffusion MRI Analysis][Step T1a: Quality Control] and select the folder storing the SRC files. Save the report as a text file (e.g. report.txt)

4. Check the report and identify scan with problematic data.

5. Open the problematic SRC file in [Step T2 Reconstruction] and identify the cause. 

6. Apply eddy correction and compare the quality control report with/without correction.
