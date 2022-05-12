# Diffusion MRI Basics

## Before practicum on Friday, please complete following:

### Diffusion MRI basics

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

- Diffusion MRI 

<img source="https://media.springernature.com/full/springer-static/image/art%3A10.1186%2Fs13244-020-00863-w/MediaObjects/13244_2020_863_Fig1_HTML.png?as=webp" width=500>

<img source="https://media.springernature.com/full/springer-static/image/art%3A10.1186%2Fs13244-020-00863-w/MediaObjects/13244_2020_863_Fig3_HTML.png?as=webp" width=500>

source: [Morozov, Sergey, et al. "Diffusion processes modeling in magnetic resonance imaging." Insights into Imaging 11.1 (2020): 1-9.](https://insightsimaging.springeropen.com/articles/10.1186/s13244-020-00863-w)

  - B-value: Diffusion sensitization
    - Diffusion time
    - Diffusion gradient strength
    - Diffusion gradient duration
  - B-vector: Diffusion encoding directions

- Hands-on: create SRC files from NIFTI data
  - [sub-01_run-1_dwi.nii.gz](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.nii.gz)
  - [sub-01_run-1_dwi.bval](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bval)
  - [sub-01_run-1_dwi.bvec](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bvec)
  - Create an SRC file

- Sampling schemes of the b-table
 
![image](https://user-images.githubusercontent.com/275569/168138897-e96f3fd6-e690-4b2d-a72f-5036437a6612.png)

  - Single-shell: one b-value at 30 directions (e.g. DTI, high angular resolution diffusion imaging, a.k.a. HARDI)
  - Multi-shell: 2 or 3 b-values with 90 directions acquired at each b-value
  - Grid: a total of 258 directions acquired by 23 b-values.
 
- Hands-on: identify sampling schemes
  - [Single-shell](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EQQ5M77hJWpJlE8w4Byd5-sBIJikasowtgAerUTmQHbL9Q?e=UXLlh3) 
  - [Multi-Shell](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EYW7Ym4EOXNKhV7a_SthyHAB6u1e71zGIwOjb67mUyNT0w?e=2BeFFJ)
  - [Grid](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/ESBC8VHWJNVBpwp6rn68Pu8ByIiwQ8KYPLS0E8wbIZkz8w?e=4YczQ7)


- Quality Checks on dMRI data
    
  1. Motion artifacts and eddy distortion 
    - Hands-on
      - [Datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI](https://openneuro.org/datasets/ds002087/)
      - [sub-01_run-2_dwi.nii.gz](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.nii.gz)
      - [sub-01_run-2_dwi.bval](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bval)
      - [sub-01_run-2_dwi.bvec](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bvec)
      - Identify motion induced signals issues

    - Motion artifacts
      - often has slice signal dropout
      <img src="https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy?action=AttachFile&do=get&target=before_after_s2v.gif" width=500>

      (source: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)

      - Correction using [FSL's eddy](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)
        
    - Eddy current distortion
      - Larger with higher b-value
      - Can be corrected in the MRI sequence to cancel eddy currents
        
      <img src="https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy?action=AttachFile&do=get&target=before_after_hcp_v4.gif" width=500>

      (source: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/eddy)
    
  2. Suscetibility distortion and artifact     
    - Hands-on: 
    - Identify and correct susceptibility distortion/artifacts
      - [FSL's topup](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/topup)
      - [sub-01_acq-multiband_dwi.nii.gz](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
      - [sub-01_acq-multiband_dir-PA_dwi.nii.gz](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
      - [sub-01_acq-multiband_dwi.bval](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
      - [sub-01:dwi:sub-01_acq-multiband_dwi.bvec](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)

      <img src="https://user-images.githubusercontent.com/275569/167231465-26a3d2b7-d3ad-42d6-abb7-7720330aac14.png" width=500>
      
      (source: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/topup/TopupUsersGuide)

  3. Inconsistent parameters (TE, TR, b-table, resolution...etc.)     
    - Quality check on SRC files

## Assignment :

### Process dMRI data on real-world studies

1. Download data from the [SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003) to a folder (e.g. D:/SCA2) study

2. Click [Batch Processing][Step B2a: NIFTI to SRC (BIDS)] and select the folder. Move all constructed SRC files to a new folder (e.g. D:/SCA2)

3. Run [Diffusion MRI Analysis][Step T1a: Quality Control] and select the folder storing the SRC files. Save the report as a text file (e.g. report.txt)

4. Check the report and identify scan with problematic data.

5. Open the problematic SRC file in [Step T2 Reconstruction] and identify the cause. 

6. Apply correction and compare the quality control report with/without correction.
