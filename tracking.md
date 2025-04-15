
---

## 💡 Crossing vs Kissing/Turning Configuration Issue

If a voxel's diffusion signals shows two fiber orientations, there can be three possible conditions:
  - Crossing fibers: two straight fiber populations crossing each other
  - Kissing fibers: two turning fiber populations touch each other back-to-back.
  - Turning fiber: one fiber making a large turn.
  - Any combination of above

<img src="https://user-images.githubusercontent.com/275569/167182297-129fb316-60a5-40b1-8c77-f3d0f3ed1122.png"/> → <img src="https://github.com/user-attachments/assets/8be66885-248f-42d6-ac73-47db336119b7" width="200" /> → Different Connectivity Matrices

🧠 *It is impossible to distinguish “crossing” from “kissing” or "turning" fibers*  
→ Even with perfect angular resolution, DWI still cannot resolve this ambiguity.

Consequences on connectivity matrices

The same fiber patterns can have different connectivity pattern

## 🧠 Fiber Tracking Algorithm

### 🔹 **Input Data**
- **Local fiber orientations** (a.k.a. *fixels*)  
- **Termination criteria** (e.g., anisotropy, angular threshold)

---

### 🔹 **Tracking Steps**
1. Select a **starting point** in the seed region and an **initial direction**  
2. Check **termination conditions** (e.g., low anisotropy, sharp turning angle)  
   → If conditions are met, **stop tracking**  
3. Determine a **new propagation direction** based on local orientations and prior path 
4. Move **one step forward**  
5. Repeat steps **2–4**  
6. Return to the starting point, **reverse direction**, and repeat steps **2–4**

---

### 🔹 **Output**
- A fiber is represented as a sequence of **3D coordinates** forming a streamline

### 

Strategy 1 Deterministic fiber tracking:
  - Always select less turning at Step 3
  - Determine 'kissing' or 'turning' in GQI due to their single local maximum in ODF -> resolve only one fiber orientation. 
  - Resolve 'crossing' as separate fiber orientations in GQI due to multiple local maximums in ODF -> resolve each fiber orientation.
  - At Step 3, always choose the less turning angle -> all resolved fiber orientations are implicitly treated as 'crossing'.

Example:
  - GQI + deterministic fiber tracking 

Cons: False negative results
  - miss sharp crossings

Strategy 2 Probablistic fiber tracking:
   - Resolve all possible orientations, including crossing, kissing, turning.
   - At Step 3, Use probablistic distribtuion to choose fiber continfugration 
   
Example:
  - bedpostx + probtrackx
  - CSD + iFOD2

Cons: False positive results
  - may have false crossing patterns


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


