## 🧭 Workshop Week 3 Outline

1. **Fiber Tracking Algorithm**  
   - Principles and implementation of deterministic and probabilistic tracking  
   - Tracking parameters and termination criteria  

2. **Track Filtering Using Regions**  
   - Role of ROI, ROA, END, and other region types in shaping tractography results  

3. **AutoTrack**

4. **Connectomics**  
   - Region-to-region connectome  
   - Tract-to-region connectome as a workaround for crossing/kissing ambiguity  

---

## 🧠 Session 1: Fiber Tracking Algorithm

### 🔹 **Input Requirements**
- **Local fiber orientations** (also known as *fixels*)  
- **Anisotropy** 

**Sample Dataset:** [OpenNeuro][ds004299][sub-103_ses-1_dwi.gqi.fz]


### 🔹 **Tracking Steps**

<img src="https://github.com/user-attachments/assets/82b6a925-7334-4af3-8480-6625ea2f6fa5" width="800"/>

1. Select a **starting point** in the seed region and an **initial direction**  
2. Repeat the following loop:  
 2.1 Check **termination conditions** (e.g., low anisotropy, sharp turning angle)  
 2.2 If conditions are met, **proceed to Step 3**  
 2.3 Determine a **new propagation direction** based on local fiber orientation and prior path  
 2.4 Move **one step forward**  
3. If only one direction has been tracked, **return to Step 1**, reverse the initial direction, and repeat tracking to generate the full streamline.  
 Otherwise, tracking ends.

---

### ⚙️ Tracking Parameters

- **Anisotropy threshold** – stops tracking in low-contrast regions  
- **Angular threshold** – stop at sharp turns  
- **Step size** – distance advanced per iteration  
- **Minimum/Maximum length** – defines acceptable tract lengths  
- **Maximum seeds/tracts** – limits total output  
- **Track-to-voxel ratio**

## Key Challenge in Tractography: Crossing vs Kissing Configuration

<img src="https://github.com/user-attachments/assets/5b81394d-6335-4982-bde7-20b3c338e6df" width="800"/>

---

## 🎯 Deterministic vs. Probabilistic Fiber Tracking

### 🔵 **Deterministic Tracking**

![image](https://github.com/user-attachments/assets/1d832a3f-24e4-4f87-b288-85a7ec0b3731)

- At **Step 2.3**, always follows the direction with the **smallest turning angle**  
- Assumes all resolved orientations represent **crossing fibers**  
- Direction is chosen from **local maxima** of the GQI ODF  

📌 **Example:**  
- GQI + deterministic tracking  

⚠️ **Limitations (False Negatives):**  
- May **misinterpret large turns as crossings** → early termination  
- May **misinterpret sharp crossings as turns** → incorrect continuation  

<img src="https://github.com/user-attachments/assets/d53a9b00-6169-4b4c-85f0-2b9d78090d39" width="800"/>

---

### 🔴 **Probabilistic Tracking**

<img src="https://github.com/user-attachments/assets/3ff6d865-a7f2-42b2-a28f-ee7fd44f0c4e" width="800"/>

- At **Step 2.3**, selects propagation direction based on a **probability distribution**  
- Resolves **multiple orientations** due to crossing or turning
- Fiber configuration is inferred from **accumulated probability over many iterations**

📌 **Examples:**  
- **bedpostx + probtrackx**  
- **CSD + iFOD2**

⚠️ **Limitations (False Positives):**  
- May produce **spurious pathways** due to false configurations

<img src="https://github.com/user-attachments/assets/2ff2ee39-1f0e-46a4-b680-c8378e6dc337" width="800"/>

🧬 **Histology Reference:**  
[Allen Brain Atlas – Parvalbumin Stain](https://www.brainspan.org/ish/experiment/dual_view?id=100147602&imageId=153511337&imageType=ihc:parvalbumin&initImage=ihc:parvalbumin&x=28544&y=39296&z=2)

---

## 🧩 Session 2: Track Filtering Using Regions

### 🗂️ Region Types

1. **Seed** – Region where tracking starts  
2. **ROI (Region of Interest)** – Tracts **must** pass through; otherwise, they are discarded  
3. **ROA (Region of Avoidance)** – Tracts that **enter** this region are discarded  
4. **Limiting** – Tracts that **exit** this region are discarded  
5. **END** – Tracts that **do not terminate** within this region are discarded  
6. **NotEND** – Tracts that **terminate** within this region are discarded  
7. **Terminating** – Tracts are **forced to stop** upon entering this region  

---

💡 **Rule of Thumb**
- ✅ Prefer **whole brain seeding** unless you are confident certain regions should be excluded from the tract  
- ⚠️ Avoid using **END** regions too early — test with **ROI** first to make sure the tract reaches the target without premature termination

---

### 🔍 Common Use Cases

#### 📌 **To find connections of a single region:**
- One **ROI** + whole brain seeding  
- One **ROI** + **dilated tract coordinates** used as Seed + Limiting  

#### 📌 **To find connections between two regions:**
- Two **ROIs** + whole brain seeding  
- Two **ROIs** + **dilated tract coordinates** as Seed + Limiting  
- One **ROI** + one **END** + **dilated tract coordinates** as Seed + Limiting  
- Two **ROIs** + **dilated tract coordinates** as Seed + Limiting  

#### 📌 **AutoTrack: To find pathways using atlas coverage**
- **Seed + Limiting regions** placed at tract coverage  
- Add **ROI** and/or **ROA** to refine filtering

---
## Session 3: AutoTrack

Sample Data: [Other major studies][penthera]
   - [sub-PT001_ses-1_dwi.gqi.fz]
   - [sub-PT001_ses-2_dwi.gqi.fz]
   - [sub-PT001_ses-3_dwi.gqi.fz]

<img src="https://github.com/user-attachments/assets/d1d7f0fe-d4b5-41d1-b4a9-8afbbf53f75d" width=800/>

---

## 🧠 Session 4: Connectome

### 🔗 Region-to-Region (R2R) Connectome

<img src="https://github.com/user-attachments/assets/8499ca9b-4ea8-4bd6-9e97-ea1bceae2f30" width="400"/> <img src="https://github.com/user-attachments/assets/8060a9bd-45af-4692-9b6b-a044eeddb0b6" width="400"/>

📄 *Yeh, Fang-Cheng, et al. NeuroImage, 2018*

**Workflow:**
- Run **whole-brain tractography** (e.g., >1 million streamlines)  
- Apply a **brain parcellation** scheme  
- Count the number of tracts connecting each pair of regions

**Limitations:**
- Tract count lacks **biological specificity**  
- Ground truth is unattainable due to **crossing/kissing ambiguities**  
- Limited **sensitivity to brain disorders**

---

### 🧬 Tract-to-Region (T2R) Connectome

<img src="https://github.com/user-attachments/assets/c05d0e70-2941-4c5e-ae25-f3bc65f22f77" width="800"/>  
<img src="https://github.com/user-attachments/assets/04bdc869-f3a1-4771-8a6b-5fec26e2aadb" width="400"/>

📄 *Yeh, NeuroImage, 2020*

**Workflow:**
- Use **autoTrack** to extract individual tract bundles (**test-retest validated**)  
- Apply a **brain parcellation**  
- Compute the **volume fraction of each region** that is traversed by the tract → defines T2R connectivity

**Advantages over R2R:**
- Produces **physically interpretable metrics** (e.g., % of region volume)  
- Reduces uncertainty from **crossing/kissing ambiguities** by evaluating bundles individually  

---

### Assignment: Plot T2R connectome on HCP-MMP parcellation

 - select a baby in the BCP study (scanned at 3 months, 6 months, and 2 years), a child from OpenNeuro (ds003604; scanned at 5, 7, and 9 years), and a teenager from the ABCD study (scanned at 10, 12, and 14 years)
 - compute their t2r connectome of the arcuate fasciculus and HCP-MMP parcellation
 - visualize the t2r connectome using region rendering
