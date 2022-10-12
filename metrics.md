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

### Overview

<img src="https://user-images.githubusercontent.com/275569/193154846-4a610eaa-ac9e-4f78-9e0e-c2cc94de3eff.png" width=700>

### Review: Diffusion MRI Preprocessing (10 min)

### Diffusion MRI models (10 min)

- [Diffusion Models](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0020) 
  - Model-based methods (DTI, [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FDT)'s BSM, DKI, NODDI)
  - Model-free methods ([DSI Studio](https://dsi-studio.labsolver.org/)'s GQI)
  - Spherical deconvolution methods ([MRtrix](https://www.mrtrix.org/)'s CSD, MSMT-CSD)

| Model/Method | Full Name | Tool |Publications | B-table requirements| Handle Free Water | Quantify Restricted Diffusion | Resolve Multiple Fibers | Metrics |
|-------------|-----|----|----|------------|-------------------|------------------------|---------|-------|
| **Model-Based**| | | | | | | |
| [DTI (Basser, 1994)](https://pubmed.ncbi.nlm.nih.gov/8130344/) | Diffusion tensor imaging | | [353,000](https://scholar.google.com/scholar?hl=en&q=%22diffusion+tensor+imaging%22) | B0, >= 1 b-value(s) |  No (except for DTI-FWE) |  No | No (except for Multi-Tensor) | fa, ad, rd, md |
| [DKI (Jensen, 2005)](https://pubmed.ncbi.nlm.nih.gov/15906300/)| Diffusion kurtosis imaging | [DKE](https://medicine.musc.edu/departments/centers/cbi/dki) | [6,400](https://scholar.google.com/scholar?hl=en&q=%22diffusion+kurtosis+imaging%22) | B0, >= 2 b-values   |  No | Yes | No (except for Multi-Tensor) | ak, rk, mk | 
| [NODDI (Zhang, 2012)](https://www.sciencedirect.com/science/article/abs/pii/S1053811912003539) | Neurite Orientation Dispersion and Density Imaging | [NODDI Matlab Toolbox](http://mig.cs.ucl.ac.uk/index.php?n=Tutorial.NODDImatlab) | [4,680](https://scholar.google.com/scholar?hl=en&q=noddi) | B0, >= 2 b-values   |  Yes | Yes | No (except for Multi-Fiber NODDI ) | iso, odi, ndi (icvf) | 
| [BSM (Behrens,2003)](http://www.ncbi.nlm.nih.gov/pubmed/14587019)| Ball & Stick Model | [BEDPOSTX,FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FDT/UserGuide)  | [1,830](https://scholar.google.com/scholar?hl=en&q=ball+stick+fsl) | B0, >= 1 b-value(s)   |  Yes | Yes | Yes | qa, iso, rdi | 
| **Model-Free (Q-Space Imaging)**| | | | | | | |
| [DSI (Wedeen, 2005)](https://pubmed.ncbi.nlm.nih.gov/16247738/) | Diffusion Spectrum Imaging | [TrackVis](https://www.trackvis.org/) | [5,480](https://scholar.google.com/scholar?hl=en&q=%22diffusion+spectrum+imaging%22) | B0, >10 b-values on grid | No | No | Yes | - |
| [QBI (Tuch,2004)](https://onlinelibrary.wiley.com/doi/full/10.1002/mrm.20279) | Q-ball Imaging | [TrackVis](https://www.trackvis.org/) | [3,460](https://scholar.google.com/scholar?hl=en&q=%22q-ball+imaging%22) | B0, 1 b-value | No | No | Yes | gfa |
| [GQI (Yeh, 2010)](https://pubmed.ncbi.nlm.nih.gov/20304721/),[QSDR (Yeh,2011)](https://pubmed.ncbi.nlm.nih.gov/21704171/) | Generalized Q-sampling Imaging,<br>Q-Space Diffeomorphic Reconstruction | DSI Studio | [860](https://scholar.google.com/scholar?hl=en&q=%22generalized+q-sampling+imaging%22),<br>[452](https://scholar.google.com/scholar?hl=en&q=%22q-space+diffeomorphic%22) | B0, >= 1 b-value(s)   |  Yes | Yes | Yes | qa, iso, rdi | 
| **Spherical Deconvolution**| | | | | | | |
| [CSD (Tournier,2007)](https://pubmed.ncbi.nlm.nih.gov/17379540/) | Constrained Spherical Deconvolution | [MRtrix3](https://www.mrtrix.org/), [DIPY](https://dipy.org/) | [4,010](https://scholar.google.com/scholar?hl=en&q=%22constrained+spherical+deconvolution%22) | 1 b-value | No | No  | Yes | afd |
| [MSMT-CSD (Jeurissen,2014)](https://pubmed.ncbi.nlm.nih.gov/25109526/) | Multi-Shell, Multi-Tissue CSD | [MRtrix3](https://www.mrtrix.org/), [DIPY](https://dipy.org/) |  [229](https://scholar.google.com/scholar?hl=en&q=%22MSMT-CSD%22) | >= 2 b-values | Yes | Yes | Yes | afd |

### Hands-on: DTI, GQI, and QSDR Reconstruction (10 min)

- Download [control subject 1 session 1 data](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EXjaCfVLTaRPgwLZ5t7kxecBnQ2ZY2hmQfHYQbJJ6gYrpA?e=qZUt0G) from [the SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003)
- Reconstruction using DTI, GQI, QSDR
- Check and compare FIB files
- Batch SRC reconstruction

### Metrics (10 min)

<img src="https://user-images.githubusercontent.com/275569/194568269-06a0a704-af29-488e-9723-4139afc1ad4e.png" width=700>

P. Mukherjee, J.I. Berman, S.W. Chung, C.P. Hess and R.G. Henry American Journal of Neuroradiology April 2008, 29 (4) 632-641; DOI: https://doi.org/10.3174/ajnr.A1051

- Microscopic metrics: anisotropy, diffusivities, and other voxel-based metrics
  - Anisotropy: axonal density & myelination
  - Isotropy: free water (not restricted) , cellularity (restricted)
  - [Interpretation](https://dsi-studio.labsolver.org/doc/how_to_interpret_dmri.html)
- Macroscopic metrics: [shape metrics](https://www.sciencedirect.com/science/article/pii/S1053811920308156)

![image](https://user-images.githubusercontent.com/275569/169354232-f490be50-627f-4bc1-9aab-97ab86f9eadc.png)

<img src="https://user-images.githubusercontent.com/275569/169354388-6fa435d8-5885-47ab-9107-c90d23f48592.png" width=700>

- Graph-based metrics: network measures
  
### Hands-on: dMRI analysis  (15 min)

- Region-based analysis
  - Open a FIB file at Step T3
  - Use [Region][Statistics] to get diffusion metrics from atlases ([Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html)).
- Tract-based analysis 
  - Open a FIB file at Step T3 and map a white matter pathway (e.g. use autotrack)
  - Get diffusion and shape metrics at CST using [Tracts][Statistics]   
  - Plot along CST metrics at z-direction or fiber direction. ([Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html))
- Insert other modalities

<img src="https://user-images.githubusercontent.com/275569/153015872-38da0327-ac4c-4bc5-bc08-4a46ae2c04d5.png" width="400">
  
- Group-wise region/tract analysis using connectometry database
  - Reconstruct all SRC files using QSDR
  - Construct a database: [samples](https://brain.labsolver.org/hcp_template.html)
  - Region-based analysis
  - Tract-based analysis

---

## Practicum assignment: ROI-based and Track-based analysis comparing SCA2 with controls

1. [Download SCA2 eddy-processed SRC Files](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EkJeJpW9gkdDsw225T6wcw8Bdfpvr1RBXNPJLWF2yafl8A?e=YF1RlO). Ignore those in the follow-up folder.
2. Reconstruct data at [Step T2 Reconstruction] using QSDR
3. Create connectometry databases using [Step C1: Create a connectometry Database] and select `dti_fa` as the metric. The created database can be checked using [Step C2].
4. Open the database at [Step T3: Fiber Tracking]
5. Use region-based analysis to get fa at pons and compare between patients and controls.
6. Use tract-based analysis to get fa at CST and compare between patients and controls.
7. Cut CST into multiple segments to get metrics (nqa, fa) and compare them between patients and controls.

