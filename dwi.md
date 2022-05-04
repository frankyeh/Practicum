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

- [Morozov, Sergey, et al. "Diffusion processes modeling in magnetic resonance imaging." Insights into Imaging 11.1 (2020): 1-9.](https://insightsimaging.springeropen.com/articles/10.1186/s13244-020-00863-w)

  - B-value: Diffusion sensitization
    - Diffusion time
    - Diffusion gradient strength
    - Diffusion gradient duration

  - B-vector: Diffusion encoding directions

  - Hands-on: create SRC files
    - [sub-01_run-1_dwi.nii.gz](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.nii.gz)
    - [sub-01_run-1_dwi.bval](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bval)
    - [sub-01_run-1_dwi.bvec](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-1_dwi.bvec)
    - Create an SRC file

- Sampling schemes
  - Single-shell: one b-value at 30 directions (e.g. DTI, high angular resolution diffusion imaging, a.k.a. HARDI)
  - Multi-shell: 2 or 3 b-values with 90 directions acquired at each b-value
  - Grid: a total of 258 directions acquired by 23 b-values.
  - Hands-on: identify sampling schemes
    - [Single-shell](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EQQ5M77hJWpJlE8w4Byd5-sBIJikasowtgAerUTmQHbL9Q?e=UXLlh3) 
    - [Multi-Shell](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EYW7Ym4EOXNKhV7a_SthyHAB6u1e71zGIwOjb67mUyNT0w?e=2BeFFJ)
    - [Grid](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/ESBC8VHWJNVBpwp6rn68Pu8ByIiwQ8KYPLS0E8wbIZkz8w?e=4YczQ7)

- Quality Checks on dMRI data
  - Hands-on: Quality Control using DSI Studio

  - Correcting motion
    - [sub-01_run-2_dwi.nii.gz](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.nii.gz)
    - [sub-01_run-2_dwi.bval](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bval)
    - [sub-01_run-2_dwi.bvec](https://openneuro.org/crn/datasets/ds002087/snapshots/1.0.0/files/sub-01:dwi:sub-01_run-2_dwi.bvec)
  
  - Correcting eddy current distortion
    

  - Correcting susceptibility distortion and artifacts
    - [sub-01_acq-multiband_dwi.nii.gz](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.nii.gz)
    - [sub-01_acq-multiband_dir-PA_dwi.nii.gz](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:fmap:sub-01_acq-multiband_dir-PA_dwi.nii.gz)
    - [sub-01_acq-multiband_dwi.bval](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bval)
    - [sub-01:dwi:sub-01_acq-multiband_dwi.bvec](https://openneuro.org/crn/datasets/ds003974/snapshots/3.0.0/files/sub-01:dwi:sub-01_acq-multiband_dwi.bvec)

## Assignment :

### Process dMRI data from a real-world study

1. Download data from the [Unilateral Glaucoma 3T dMRI] study(https://openneuro.org/datasets/ds001743/versions/1.0.1) to a folder (e.g. D:/Glaucoma_3T_dMRI)

2. Click [Batch Processing][Step B2a: NIFTI to SRC (BIDS)] and select the folder. Move all constructed SRC files to a new folder (e.g. D:/Glaucoma_3T_dMRI/src)

3. Run [Diffusion MRI Analysis][Step T1a: Quality Control] and select the folder storing the SRC files. Save the report as a text file (e.g. report.txt)

4. Check the report and identify scan with problematic data.

5. Open the problematic SRC file in [Step T2 Reconstruction] and identify the cause. 

6. Apply correction and compare the quality control report with/without correction.

