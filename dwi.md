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

- Read [[5. Fiber resolving methods]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0020) 
  - 5.1. Model-based methods
  - 5.2. Model-free methods
  - 5.3. Spherical deconvolution
  - 5.4. Comparison

- Watch a video about diffusion tensor imaging

<iframe width="560" height="315" src="https://www.youtube.com/embed/e_xFMpjeZuU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---

## During practicum on Friday:


- [Morozov, Sergey, et al. "Diffusion processes modeling in magnetic resonance imaging." Insights into Imaging 11.1 (2020): 1-9.](https://insightsimaging.springeropen.com/articles/10.1186/s13244-020-00863-w)

  - Diffusion sensitization (a.k.a. b-value)
    - Diffusion time
    - Diffusion gradient strength
    - Diffusion gradient duration

  - Diffusion encoding directions (a.k.a. b-vector)

  - Apparent diffusion coefficient
    - b0 vs DWI

- Sampling schemes
  - [Single-shell](https://zenodo.org/record/6320992/files/20081006_M025Y_DTI_30.src.gz?download=1) 
  - [Multi-Shell] 
  - [Grid](https://zenodo.org/record/6320992/files/20081006_M025Y_DSI_203.src.gz?download=1)

- Reconstruction methods
  - Model-based: diffusion tensor imaging
  - Model-free: q-space imaging
  

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
