
---

## 🧠 Fiber Tracking Algorithm

### 🔹 **Input Data**
- **Local fiber orientations** (a.k.a. *fixels*)  
- **Termination criteria** (e.g., anisotropy, angular threshold)

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


 


### Strategy 1 Deterministic fiber tracking: 

<img src="https://github.com/user-attachments/assets/5b81394d-6335-4982-bde7-20b3c338e6df" width="400"/>

  - Always select less turning angle at Step 3
  - Use GQI ODF local maximum to differentiate kissing from crossing
  - At Step 3, always choose the less turning angle -> all resolved fiber orientations are implicitly treated as 'crossing'.

Example:
  - GQI + deterministic fiber tracking 

Cons: False negative results
  - miss sharp crossings or abrupt turning


### Strategy 2 Probablistic fiber tracking:

<img src="https://github.com/user-attachments/assets/5b693fff-a581-42ed-9da3-10ca3ccdb930"/>

   - Use ODF as a distribution to choose kissing or crossing
   - At Step 3, Use probablistic distribtuion to choose fiber continfugration 
   
Example:
  - bedpostx + probtrackx
  - CSD + iFOD2

Cons: False positive results
  - hard to distinguish “crossing” from “kissing” or "turning" fibers  
  - may have false crossing or kissing patterns


## 🧩 Role of Regions in Fiber Tracking

### 🗂️ Region Types

1. **Seed** – Starting region for initiating tracking  
2. **ROI (Region of Interest)** – Tracts **must** pass through; otherwise, they are discarded  
3. **ROA (Region of Avoidance)** – Tracts that **enter** the region are discarded  
4. **Limiting Region** – Tracts that **exit** this region are discarded  
5. **END Region** – Tracts that **do not terminate** within this region are discarded  
6. **NotEND Region** – Tracts that **terminate** within this region are discarded  
7. **Terminating Region** – Tracts are **forced to stop** upon entering this region  

---

### 🔍 Common Use Cases

#### 📌 To find connections of a single region:
- **One ROI + whole brain seeding**  
- **One ROI + dilated tract coordinates** used as **Seed + Limiting**

#### 🔗 To find connections between two regions:
- **Two ROIs + whole brain seeding**  
- **Two ROIs + dilated tract coordinates** as **Seed + Limiting**  
- **One ROI + One END + dilated tract coordinates** as **Seed + Limiting**  
- **Two ROIs + dilated tract coordinates** as **Seed + Limiting**

---

### 💡 Rule of Thumb

- ✅ **Prefer whole brain seeding**, unless you're certain that the tract cannot pass through specific areas (in which case, exclude those from the seed mask)
- ⚠️ **Do not use "END" regions too early** — always define it as an **ROI first** to ensure the tract reliably reaches the target without overshooting


