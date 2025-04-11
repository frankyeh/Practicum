## 🧭 Workshop Week 2 Outline

1. **MRI Data Acquisition**
   - Best practices and recommendations for diffusion MRI protocol
   
2. **Preprocessing DWI Data (SRC Files)**
   - Motion correction & eddy current distortion correction  
   - Susceptibility artifact correction  

3. **Diffusion Modeling: Resolving Fibers and Measuring Anisotropy**
   - Overview of DTI, GQI, and QSDR models  

---

## 🧭 Session 1: DSI Studio Pipeline (10 minutes)

<img src="https://github.com/user-attachments/assets/9afac513-ccbd-419c-9d79-4b7dd9458294" width="800"/>


## 🖐️ Hands-On Practice

### NIFTI/bids [OpenNeuro ds002087](https://openneuro.org/datasets/ds002087): datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI
   1. Convert NIFTI to SRC
   2. SRC to FIB
      
### DICOM: [An MRI DICOM data set of the head of a normal male human aged 52](https://zenodo.org/records/16956/files/DICOM.zip?download=1)
   1. Rename & Sort DICOM files
   2. Convert DICOM to NIFTI

---

## 🧭 Session 2: Diffusion MRI Protocol (10 minutes)


### ✅ Protocol Checklist 1: Sufficient Diffusion Sensitivity

- Use **b-value > 1,000 s/mm²** for human studies
- ⚠️ No post-processing can recover low diffusion sensitivity  

📌 *Example: HCP-YA dataset*  
b-values: **0, 1000, 2000, 3000 s/mm²**  
b-vector: **(0, 0, 1)**

<img src="https://github.com/user-attachments/assets/2a47fe2b-7a38-42d3-84c4-b69baae046bc" width="800"/>

---

### ✅ Protocol Checklist 2: Isotropic Resolution

- Ensure **slice thickness ≈ in-plane resolution**  
- If anisotropic, consider **regridding to isotropic** before analysis  

📌 *Example: OpenNeuro ds005849*  
In-plane: **1.75 mm**  
Slice thickness: **2.7 mm** → ⚠️ Not isotropic

<img src="https://github.com/user-attachments/assets/df8847c7-a585-4aa1-88e6-32e8d0e1ba70" width="400"/>

---

### ✅ Protocol Checklist 3: Reverse-Phase b0 Image

- Used to **correct susceptibility distortions**, especially in frontal and temporal lobes  
- Some tools allow T1w-based correction, but **b0 pairs are preferred**  
- **Sequence-based** corrections (e.g., readout segmentation) are also available  

📌 *Source: [FSL Topup User Guide](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/topup(2f)TopupUsersGuide.html)*

**Before Correction**  
(Phase encoding: AP, AP, PA, PA)  
<img src="https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/attachments/topup(2f)TopupUsersGuide/original_images.png" width="800"/>

**After Correction**  
<img src="https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/attachments/topup(2f)TopupUsersGuide/hifi_images.png" width="800"/>

---

### ✅ Protocol Checklist 4: Multiple b-values

**Multi-shell scheme (HCP-like)**

3 b-values: **1000 (20 directions), 2000 (40 directions), 3000 (60 directions)**

Enables robust modeling across a range of diffusion strengths

**Grid scheme (DSI-like)**

23 b-values from 0 to 4000 s/mm², distributed across 258 directions

Optimized for q-space sampling and advanced reconstruction (e.g., DSI, GQI)

---

## 🧭 Session 3: Diffusion MRI Preprocessing (15 minutes)

### Quality Issues in Diffusion MRI

| Artifact | Cause | Consequence | Solution |
|----------|-------|-------------|----------|
| **motion artifacts** | subject moves during the scan | signal dropout and between-dwi misalignment  → hairball-like tractography | (1) discard the scan if motion is severe<br>(2) apply motion correction to realign images |
| **eddy current artifacts** | gradient-induced eddy currents distort the readout | between-dwi misalignment → hairball-like tractography  | (1) use current-canceling gradient designs (e.g., bipolar, twice-refocused)<br>(2) apply affine image registration |
| **susceptibility artifacts** | magnetic field distortion near air-tissue interfaces | signal dropout and geometric distortion along the phase-encoding direction | (1) use sequence-based corrections (e.g., segmented EPI)<br>(2) combine reversed-phase b0 images to correct distortion |
| **flipped b-table** |  common in animal scans | urchin-like tractography | automatic b-table checking | 
| **rotated/flipped image volume**  | common in animal scans | cannot use atlas or autotract functions | flip or swap axis in pair |
| **thick slices**  | old DWI sequence | poor fiber tracking result | regrid images |

other corrections (less important): noise reduction, bias field correction, gibbs ringing correction
---

## 🖐️ Hands-On Practice

### Identify issues on [OpenNeuro ds002087] and correct it

---

## 🛠️ Tools for Corrections

**Popular Tools:**  ✅ FSL • ✅ MRtrix3 • ✅ QSIPrep • ✅ DIPY • ✅ DSI Studio

#### [FSL's topup](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/topup.html)
- Corrects **nonlinear distortion** caused by susceptibility  
- Requires **reversed phase-encoding b0 images**

#### [FSL's eddy](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/eddy(2f)UsersGuide.html)
- Corrects **linear distortion** from eddy currents & subject motion  
- Works best with **multiple DWIs per b-value**

#### DSI Studio: Motion Correction
- Corrects for **eddy current and motion artifacts**  
- Lightweight and integrated into `.src` workflow

---

### 🧩 Preprocessing Options

1. **FSL's `topup + eddy`** → most comprehensive  
2. **FSL's `eddy` only** → for datasets lacking reverse-phase b0  
3. **DSI Studio motion correction** → quick fix when others are unavailable  

---

## 🖐️ Hands-On Practice

### Compare correction results using Quality Control

1. Download `.sz` files from [Fiber Data Hub – ds002087][ds002087]  
2. Use QC routine to compare `.sz` and `.fz` with/without correction
3. Check "diffusion contrast" and "Neighboring DWI correlation"

### Identify reversed phase encoding b0 for TOPUP

1. Download data:  
   - [dwi](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.nii.gz)  
   - [pa b0](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/fmap/sub-01_acq-multiband_dir-PA_dwi.nii.gz)  
   - [bval](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.bval), [bvec](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.bvec)  
2. Identify reversed-phase b0  

---

## 🧭 Session 4: Diffusion Modeling Methods (15 minutes)

---

<img src="https://github.com/user-attachments/assets/6f182387-1275-4070-b003-83828212894f" width="400" />

<img src="https://github.com/user-attachments/assets/4603498e-a769-432b-87fc-7d5145397105" width="400" />

---

## 🖐️ Hands-On Practice

### Reconstruct DTI and GQI data and compare FA and QA

---

### 🧰 DTI: 

- ⚠️ *single tensor model cannot handle crossing fibers*  
- ⚠️ FA maps are unreliable at **low SNR**, yet often used in fiber tracking.  
- ✅ still effective when paired with sufficient spatial resolution and smoothing

---

### 🧰 GQI / QSDR: 

- ⚠️ *Limited power for resolving complex crossing fibers*
- ⚠️ sensitive to *b1 inhomogniety*  
- ✅ main advantage: Provides a **robust anisotropy index** (QA) to guide fiber tracking

---

### Trade-off between sensitivity and sepcificity

<img src="https://github.com/user-attachments/assets/f496b44e-75d7-4edc-8dd1-a4fa1b6e17cd" width="400" />

<img src="https://github.com/user-attachments/assets/56de9cf1-dfcb-439f-9609-ef11bd623d20" width="400" />


source: Yeh, Fang-Cheng, et al. "Tractography methods and findings in brain tumors and traumatic brain injury." Neuroimage 245 (2021): 118651.

<img src="https://github.com/user-attachments/assets/21e7476f-c6d0-4465-a737-d88ac7e0c4fd" width="400" />

source: Kjer, Hans Martin, et al. "Bridging the 3D geometrical organisation of white matter pathways across anatomical length scales and species." Elife 13 (2025): RP94917.

---

## 🧭 Session 5: GUI-based Batch Processing (10 minutes)   
   
- NIFTI/bids [OpenNeuro ds001378 (SCA2)](https://openneuro.org/datasets/ds001378/)

   1. run [NIFTI Quality Control]
   2. run [Step B2a: NIFTI to SRC (BIDS)]
   3. run [SRC Quality Control]
   4. SRC to FIB 
   5. FIB to tractography

---

## Assignment 1: Explore Correction Effects on Tractography

1. Download `.sz` files from [Fiber Data Hub][Open Neuro][ds002087]  
2. Visualize **arcuate fasciculus** with/without corrections and with/without head motion


