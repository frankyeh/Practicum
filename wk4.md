# Week 4 Region-Based & Tract-Based Analysis (Tractometry) 

## Before practicum on Friday, please complete following:

### Review Paper

- [Abhinav, Kumar, et al. "Advanced diffusion MRI fiber tracking in neurosurgical and neurodegenerative disorders and neuroanatomical studies: a review." Biochimica et Biophysica Acta (BBA)-Molecular Basis of Disease 1842.11 (2014): 2286-2297.](Materials/paper/review2.pdf) SECTION 3.4 analytical approaches.


## During practicum on Friday:

#### Region-based analysis 

- [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).

- Demonstrate using corticospinal tract (CST) ROI to get diffusion metrics.

<img src="https://user-images.githubusercontent.com/275569/153015590-a367f769-8694-4dd9-8680-03716c6d5830.png" width="600">


#### Tract-based analysis 

- [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).

- Demonstrate CST fiber tracking to get diffusion metrics at CST.

- Use tract cutting (with selection & separate deleted tract) to segment CST into segments above internal capsule (IC), IC, and below IC sections.

<img src="https://user-images.githubusercontent.com/275569/153015773-27d4d62c-8126-49b2-b125-a7532688c47e.png" width="300">

#### Tract profile

- [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).

- Plot along tract metrics at z-direction or fiber direction.

<img src="https://user-images.githubusercontent.com/275569/153015872-38da0327-ac4c-4bc5-bc08-4a46ae2c04d5.png" width="600">

---

### Practicum task: ROI-based and Track-based analysis comparing ALS with controls


1. Download subject FIB files at [ALS](https://drive.google.com/drive/folders/1q7YdmjaR-8w-pBUYe0nENnm3fiGnP1Md?usp=sharing).

2. Use region-based analysis to get metrics (nqa, fa) from patients and controls and compare.

3. Use tract-based analysis to get metrics (nqa, fa) from patients and controls and compare.
 
3. Segment CST into segmentation to get metrics (nqa, fa) and compare them between patients and controls.

4. Get tract profile of metrics (nqa, fa) and average within patients and controls groups, respectively. Comparison.

