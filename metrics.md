# Diffusion Models and Metrics

## Before practicum on Friday, please complete following:

- Read [[5. Fiber resolving methods]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0020) 
  - 5.1. Model-based methods
  - 5.2. Model-free methods
  - 5.3. Spherical deconvolution
  - 5.4. Comparison

- Watch a video about diffusion tensor imaging

<iframe width="560" height="315" src="https://www.youtube.com/embed/e_xFMpjeZuU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## During practicum on Friday:

### Overview (5 min)

<img src="https://user-images.githubusercontent.com/275569/193154846-4a610eaa-ac9e-4f78-9e0e-c2cc94de3eff.png" width=1000>

### Review Assignment (10 min)

### Diffusion MRI models

- [Diffusion Models](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0020) 
  - Model-based methods (DTI, [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FDT)'s BSM, DKI, NODDI)
  - Model-free methods ([DSI Studio](https://dsi-studio.labsolver.org/)'s GQI)
  - Spherical deconvolution methods ([MRtrix](https://www.mrtrix.org/)'s CSD, MSMT-CSD)

| Model/Method | Full Name | Publications | B-table requirements| Handle Free Water | Quantify Restricted Diffusion | Resolve Multiple Fibers | Metrics |
|-------------|-----|--------|------------|-------------------|------------------------|---------|-------|
| **Model-Based**| | | | | | | |
| [DTI](https://pubmed.ncbi.nlm.nih.gov/8130344/) | Diffusion tensor imaging | [353,000](https://scholar.google.com/scholar?hl=en&q=%22diffusion+tensor+imaging%22) | B0, >= 1 b-value(s) |  No (except for DTI-FWE) |  No | No (except for Multi-Tensor) | fa, ad, rd, md |
| [DKI](https://pubmed.ncbi.nlm.nih.gov/15906300/) | Diffusion kurtosis imaging | [6,400](https://scholar.google.com/scholar?hl=en&q=%22diffusion+kurtosis+imaging%22) | B0, >= 2 b-values   |  No | Yes | No (except for Multi-Tensor) | ak, rk, mk | 
| [NODDI](https://www.sciencedirect.com/science/article/abs/pii/S1053811912003539) | Neurite Orientation Dispersion and Density Imaging | [4,680](https://scholar.google.com/scholar?hl=en&q=noddi) | B0, >= 2 b-values   |  Yes | Yes | No (except for Multi-Fiber NODDI ) | iso, odi, ndi (icvf) | 
| [BSM](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FDT) | Ball & Stick Model | [1,830](https://scholar.google.com/scholar?hl=en&q=ball+stick+fsl) | B0, >= 1 b-value(s)   |  Yes | Yes | Yes | qa, iso, rdi | 
| **Model-Free**| | | | | | | |
| [DSI](https://pubmed.ncbi.nlm.nih.gov/18495497/) | Diffusion Spectrum Imaging | [5,480](https://scholar.google.com/scholar?hl=en&q=%22diffusion+spectrum+imaging%22) | B0, >10 b-values on grid | No | No | Yes | - |
| [QBI](https://onlinelibrary.wiley.com/doi/full/10.1002/mrm.20279) | Q-ball Imaging | [3,460](https://scholar.google.com/scholar?hl=en&q=%22q-ball+imaging%22) | B0, 1 b-value | No | No | Yes | gfa |
| [GQI](https://pubmed.ncbi.nlm.nih.gov/20304721/),[QSDR](https://pubmed.ncbi.nlm.nih.gov/21704171/)  | Generalized Q-sampling Imaging, Q-Space Diffeomorphic Reconstruction | [860](https://scholar.google.com/scholar?hl=en&q=%22generalized+q-sampling+imaging%22), [452](https://scholar.google.com/scholar?hl=en&q=%22q-space+diffeomorphic%22) | B0, >= 1 b-value(s)   |  Yes | Yes | Yes | qa, iso, rdi | 
| **Spherical Deconvolution**| | | | | | | |
| [CSD](https://pubmed.ncbi.nlm.nih.gov/17379540/) | Constrained Spherical Deconvolution | [4,010](https://scholar.google.com/scholar?hl=en&q=%22constrained+spherical+deconvolution%22) | 1 b-value | No | No  | Yes | afd |
| [MSMT-CSD](https://pubmed.ncbi.nlm.nih.gov/25109526/) | Multi-Shell, Multi-Tissue CSD | [229](https://scholar.google.com/scholar?hl=en&q=%22MSMT-CSD%22) | >= 2 b-values | Yes | Yes | Yes | afd |


- Metrics
  - Microscopic: anisotropy, diffusivities, and other voxel-based metrics
  - Macroscopic: [shape metrics](https://www.sciencedirect.com/science/article/pii/S1053811920308156)
  - Graph-based metrics: network measures

![image](https://user-images.githubusercontent.com/275569/169354232-f490be50-627f-4bc1-9aab-97ab86f9eadc.png)

![image](https://user-images.githubusercontent.com/275569/169354388-6fa435d8-5885-47ab-9107-c90d23f48592.png)

  - [Interpretation](https://dsi-studio.labsolver.org/doc/how_to_interpret_dmri.html)
    - Fiber integrtity: 
      - axonal density: fa, qa, afd, odi, ad, SIFT connectivity
      - myelination: fa, rd, qa
    - Cellularity: rdi, ndi, md,
    - Free water: iso, fw

### Hands-on: DTI, GQI, and QSDR Reconstruction

- Download control subject 1 session 1 data from [the SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003)
  - [BVAL](https://openneuro.org/crn/datasets/ds001378/snapshots/00003/files/sub-control01:ses-01:dwi:sub-control01_ses-01_dwi.bval)
  - [BVEC](https://openneuro.org/crn/datasets/ds001378/snapshots/00003/files/sub-control01:ses-01:dwi:sub-control01_ses-01_dwi.bvec)
  - [NIFTI](https://openneuro.org/crn/datasets/ds001378/snapshots/00003/files/sub-control01:ses-01:dwi:sub-control01_ses-01_dwi.nii.gz)

- Reconstruction using DTI, GQI, QSDR
- Check and compare FIB files
- Batch SRC reconstruction

### Hands-on: dMRI analysis 

- Region-based analysis
  - Open a FIB file at Step T3
  - Use [Region][Statistics] to get diffusion metrics from atlases ([Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html)).
- Tract-based analysis 
  - Open a FIB file at Step T3
  - Map a white matter pathway (e.g. use autotrack)
  - Get diffusion and shape metrics at CST using [Tracts][Statistics]
  
  <img src="https://user-images.githubusercontent.com/275569/153015590-a367f769-8694-4dd9-8680-03716c6d5830.png" width="400">
  
  - Use tract cutting (with selection & separate deleted tract) to segment pathways into segments above internal capsule (IC), IC, and below IC sections.
  
  <img src="https://user-images.githubusercontent.com/275569/153015773-27d4d62c-8126-49b2-b125-a7532688c47e.png" width="200">

  - Plot along CST metrics at z-direction or fiber direction. ([Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html))

  <img src="https://user-images.githubusercontent.com/275569/153015872-38da0327-ac4c-4bc5-bc08-4a46ae2c04d5.png" width="400">

- Group-wise region/tract analysis using connectometry database
  - Reconstruct all SRC files using QSDR
  - Construct a database: [samples](https://brain.labsolver.org/hcp_template.html)
  - Region-based analysis
  - Tract-based analysis

---

## Practicum assignment: ROI-based and Track-based analysis comparing SCA2 with controls

1. Download [the SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003)
2. Reconstruct data at [Step T2 Reconstruction] using QSDR
3. Create connectometry databases using [Step C2: Create a connectometry Database], one for `nqa`, and one for `fa`.
4. Open the database at [Step T3: Fiber Tracking]
5. Use region-based analysis to get metrics (nqa, fa) from patients and controls and compare.
6. Use tract-based analysis to get metrics (nqa, fa) from patients and controls and compare.
7. Segment CST into segmentation to get metrics (nqa, fa) and compare them between patients and controls.

