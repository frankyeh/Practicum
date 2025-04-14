---


## Fiber Tracking Algorithm

- Input Data:
  - local fiber orientation (a.k.a. fixel)
  - termination metrics (e.g., anisotropy)
  
- Steps:
  1. Choose a starting point within the seed region and an incoming direction
  2. Check termination criteria (anisotropy threshold,angular threshold, and others), if stop goto 6.
  3. Decide a propagation direction from the incoming direction
  4. Move a step
  5. Repeat 2 - 4
  6. Back to the starting point, but reverse the initial direction. Repeat 2 - 4 until stop.
  
- Output: sequences of 3D coordinates

## Role of regions

  1. Seed: the starting region of the tracking
  2. ROI: if the tract does not enter the region, it will be deleted.
  3. ROA: if the tract enters the region, it will be deleted.
  4. Limiting: if the tract exists the region, it will be deleted.
  5. END: if the tract does not stop within the region, it will be deleted.
  5. NotEND: if the tract stops within the region, it will be deleted.
  6. Terminative: the tract will stop if it enter the region

Commonly used combinations:

Find connections of a region:
  - One ROI + whole brain seeding 
  - One ROI + Dilated tract coordinates as seed and limiting

Find connections between two regions:
  - Two ROIs + whole brain seeding 
  - Two ROIs + Dilated tract coordinates as seed and limiting
  - One ROI + One End + Dilated tract coordinates as seed and limiting
  - Two ROI + Dilated tract coordinates as seed and limiting

Rule of thumb
- Always use whole brain seeding unless unless you know the tract definitely won't exist at certain region (thus you can exclude them from whole brain seed).
- Do not use the "end" region before you specify it as "ROI" first to confirm there is no overshooting.


## 💡 Angular Resolution Issue

<img src="https://user-images.githubusercontent.com/275569/167182297-129fb316-60a5-40b1-8c77-f3d0f3ed1122.png"/> → <img src="https://github.com/user-attachments/assets/8be66885-248f-42d6-ac73-47db336119b7" width="200" /> → Different Connectivity Matrices

🧠 *It is impossible to distinguish “kissing” vs. “crossing” fibers*  
→ Even with perfect angular resolution, DWI still cannot resolve this ambiguity.

Consequences on connectivity matrices

The same fiber patterns can have different connectivity pattern
