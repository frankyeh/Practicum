## 🧭 Workshop Week 3 Outline

1. **Fiber Tracking Algorithm**
   - Best practices and recommendations for diffusion MRI protocol
   
2. **Track Filtering using Regions**
   
4. **Connectome**
   - Region to region connectome
   - Tract to region connectome
    
5. **Tractography in Structural Images**
   - Tractography atlas in subject space

---
## 🧠 Session 1: Fiber Tracking Algorithm

### 🔹 **Input Data**
- **Local fiber orientations** (a.k.a. *fixels*)  
- **Termination criteria** (e.g., anisotropy, angular threshold)

Sample Data: [OpenNeuro][ds004299][sub-103_ses-1_dwi.gqi.fz]

---

### 🔹 **Tracking Steps**

<img src="https://github.com/user-attachments/assets/82b6a925-7334-4af3-8480-6625ea2f6fa5" width="600"/>

1. Select a **starting point** in the seed region and an **initial direction**  
2. Repeat the following steps:  
 2.1 Check **termination conditions** (e.g., low anisotropy, sharp turning angle)  
 2.2 If termination conditions are met, **go to Step 3**  
 2.3 Determine a **new propagation direction** based on local orientations and the previous path  
 2.4 Move **one step forward**  
3. If only one direction has been tracked, **return to Step 1**, reverse the initial direction, and repeat tracking to complete the full trajectory.  
 Otherwise, tracking ends.

### Parameters

- Anisotropy threshold
- Angular threshold
- Step size
- Minimum/Maximum length
- Maximum seed/tract
- Track-to-voxel ratio

## Deterministic vs Probablistic Fiber Tracking

### Deterministic:

<img src="https://github.com/user-attachments/assets/5b81394d-6335-4982-bde7-20b3c338e6df"/>

  - At Step 2.3, always propagate at the less turning angle -> treat all resolved orientations are **crossing** 
  - use GQI ODF's local maximum to resolve fiber orientations.

Example:
  - GQI + deterministic fiber tracking 

Cons: False negative results
  - treat sharp crossings as turning
  - treat abrupt turning as crossing

<img src="https://github.com/user-attachments/assets/d53a9b00-6169-4b4c-85f0-2b9d78090d39"/>


### Probablistic: 

<img src="https://github.com/user-attachments/assets/3ff6d865-a7f2-42b2-a28f-ee7fd44f0c4e"/>

   - At Step 2.3, Use probablistic distribtuion to choose propagation direction
   - Resolve all possible orientations and let probability choose -> determinne fiber configurations by probability
   
Example:
  - bedpostx + probtrackx
  - CSD + iFOD2

Cons: False positive results
  - hard to distinguish “crossing” from “kissing” or "turning" fibers  
  - may have false crossing or kissing patterns

<img src="https://github.com/user-attachments/assets/2ff2ee39-1f0e-46a4-b680-c8378e6dc337"/>

histology reference: [allen brain](https://www.brainspan.org/ish/experiment/dual_view?id=100147602&imageId=153511337&imageType=ihc:parvalbumin&initImage=ihc:parvalbumin&x=28544&y=39296&z=2)

## 🧩 Session 2: Track Filtering using Regions

### 🗂️ Region Types

1. **Seed** – Starting region for initiating tracking  
2. **ROI (Region of Interest)** – Tracts **must** pass through; otherwise, they are discarded  
3. **ROA (Region of Avoidance)** – Tracts that **enter** the region are discarded  
4. **Limiting Region** – Tracts that **exit** this region are discarded  
5. **END Region** – Tracts that **do not terminate** within this region are discarded  
6. **NotEND Region** – Tracts that **terminate** within this region are discarded  
7. **Terminating Region** – Tracts are **forced to stop** upon entering this region  

💡 Rule of Thumb
- ✅ **Prefer whole brain seeding**, unless you're certain that the tract cannot pass through specific areas (in which case, exclude those from the seed mask)
- ⚠️ **Do not use "END" regions too early** — always define it as an **ROI first** to ensure the tract reliably reaches the target without overshooting

---

### 🔍 Common Use Cases

#### 📌 To find connections of a single region:
- **One ROI + whole brain seeding**  
- **One ROI + dilated tract coordinates** used as **Seed + Limiting**

#### 📌 To find connections between two regions:
- **Two ROIs + whole brain seeding**  
- **Two ROIs + dilated tract coordinates** as **Seed + Limiting**  
- **One ROI + One END + dilated tract coordinates** as **Seed + Limiting**  
- **Two ROIs + dilated tract coordinates** as **Seed + Limiting**

#### 📌 AutoTrack: To find a pathway given an possible coverage from atlas
- **Seed and limiting region placed at coverage**  
- **Seed and limiting region placed at coverage** + ROI and/or ROA 

---
## Session 3: AutoTrack

<img src="https://github.com/user-attachments/assets/d1d7f0fe-d4b5-41d1-b4a9-8afbbf53f75d" width=800/>

## Session 3: Connectome

### Region-to-Region (R2R) Connectome
 
<img src="https://github.com/user-attachments/assets/8499ca9b-4ea8-4bd6-9e97-ea1bceae2f30" width=400/><img src="https://github.com/user-attachments/assets/8060a9bd-45af-4692-9b6b-a044eeddb0b6" width=400/>

`Yeh, Fang-Cheng, et al. "Population-averaged atlas of the macroscale human structural connectome and its network topology." Neuroimage 178 (2018): 57-68.`

Steps: 
  - whole brain tractography (> 1mil tracts)
  - choose brain parcellation
  - compute tract count per region pair

Issues:
  - Tract count does not have biological meaning
  - Impossible to get the ground truth due to tract crossing/kissing problems
  - Not sensitive to most brain disease


### Tract-to-Region (T2R) Connectome

<img src="https://github.com/user-attachments/assets/c05d0e70-2941-4c5e-ae25-f3bc65f22f77" width=800/><img src="https://github.com/user-attachments/assets/04bdc869-f3a1-4771-8a6b-5fec26e2aadb" width=400/>

reference: 

Steps: 
  - Map a bundle using autoTrack (good test-retest reliability examined at Yeh, Neuroimage 2020)
  - Choose brain parcellation
  - Calculate end region size between at each tract-region pair 

Pros over R2R:  
  - Has well defined metrics with physical meaning
  - Bypass kissing-crossing problem.


