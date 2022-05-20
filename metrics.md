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

### Diffusion MRI models

- [Diffusion Models](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0020) 
  - Model-based methods (DTI, [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FDT)'s BSM, DKI, NODDI)
  - Model-free methods ([DSI Studio](https://dsi-studio.labsolver.org/)'s GQI)
  - Spherical deconvolution methods ([MRtrix](https://www.mrtrix.org/)'s CSD, MSMT-CSD)

| Model/Method| B-table requirements| Handle Free Water | Quantify Restricted Diffusion | Resolve Multiple Fibers | Metrics |
| ------------|---------------------|-------------------|------------------------|---------|-------|
| DTI         | B0, >= 1 b-value(s) |  No (except for DTI-FWE) |  No | No (except for Multi-Tensor) | fa, ad, rd, md |
| DKI         | B0, >= 2 b-values   |  Yes | Yes | No (except for Multi-Tensor) | ak, rk, mk | 
| NODDI       | B0, >= 2 b-values   |  Yes | Yes | No (except for Multi-Fiber NODDI ) | iso, odi, ndi (icvf) | 
| GQI         | B0, >= 1 b-value(s)   |  Yes | Yes | Yes | qa, iso, rdi | 
| CSD         | 1 b-value | No | No | Yes | afd |
| CSD-MSMT    | >= 2 b-values | Yes | Yes | Yes | afd |

- Metrics
  - Voxel-based metrics
  - Fiber-based metrics
  - Tractography-based metrics: SIFT connectivity, network measures, [(shape metrics)](https://www.sciencedirect.com/science/article/pii/S1053811920308156)

![image](https://user-images.githubusercontent.com/275569/169354232-f490be50-627f-4bc1-9aab-97ab86f9eadc.png)

![image](https://user-images.githubusercontent.com/275569/169354388-6fa435d8-5885-47ab-9107-c90d23f48592.png)

  - [Interpretation](https://dsi-studio.labsolver.org/doc/how_to_interpret_dmri.html)
    - Fiber integrtity: 
      - axonal density: fa, qa, afd, odi, ad, SIFT connectivity
      - myelination: fa, rd, qa
    - Cellularity: rdi, ndi, md,
    - Free water: iso, fw

### Hands-on: Region-based analysis 

- Download [FIB files from the SCA2 Diffusion Tensor Imaging study](https://github.com/frankyeh/DSI-Studio-Cloud/releases/download/ds001378/ds001378_fib.zip)

- Use [Region][Statistics] to get diffusion metrics from atlases ([Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html)).


### Hands-on: Tract-based analysis 

- Map corticospinal tracts

- Get diffusion metrics at CST using [Tracts][Statistics]

<img src="https://user-images.githubusercontent.com/275569/153015590-a367f769-8694-4dd9-8680-03716c6d5830.png" width="400">

- Use tract cutting (with selection & separate deleted tract) to segment CST into segments above internal capsule (IC), IC, and below IC sections.

<img src="https://user-images.githubusercontent.com/275569/153015773-27d4d62c-8126-49b2-b125-a7532688c47e.png" width="200">

### Hands-on: Tract profile

- Plot along CST metrics at z-direction or fiber direction. ([Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html))

<img src="https://user-images.githubusercontent.com/275569/153015872-38da0327-ac4c-4bc5-bc08-4a46ae2c04d5.png" width="400">

---

## Practicum assignment: ROI-based and Track-based analysis comparing ALS with controls


1. Download [FIB files from the SCA2 Diffusion Tensor Imaging study](https://github.com/frankyeh/DSI-Studio-Cloud/releases/download/ds001378/ds001378_fib.zip)

2. Use region-based analysis to get metrics (nqa, fa) from patients and controls and compare.

3. Use tract-based analysis to get metrics (nqa, fa) from patients and controls and compare.
 
3. Segment CST into segmentation to get metrics (nqa, fa) and compare them between patients and controls.

4. Get tract profile of metrics (nqa, fa) and average within patients and controls groups, respectively. Comparison.

