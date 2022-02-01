# Week 3 Region-Based Fiber Tracking

Linggang Luo

*January 2022*

Some materials will be shared via our [google drive folder](https://drive.google.com/drive/folders/12XGKtBVUb7i-uW_LSkMERFRhP7S95OrQ?usp=sharing) for confidentiality reasons.


---


## Before practicum on Friday, please complete following:

### Anatomy

- Read through [Overview of White Matter Tracts - Limbic Pathways](https://drive.google.com/file/d/1YJMb8yeKxmFG5b8f7PrA9GQ--H4OnBxE/view?usp=sharing), [Overview of White Matter Tracts - Projection Pathways](https://drive.google.com/file/d/1IUyredH2rEBrBNBDDKgI0_Bm-pXlz5M3/view?usp=sharing) and [Overview of White Matter Tracts - Occipital Visual Pathways](https://drive.google.com/file/d/1IXLd6TMpu6dpzWhcwv7NwlUMTErnMTFO/view?usp=sharing).

- Association pathways include ***Perisylvian***, ***limbic*** and ***occipital visual***, categorized by their functions.
    
    - Perisylvian pathways: Arcuate fasciculus, superior longitudinal fasciculus (SLF), and frontal aslant.
    
    - Limbic pathways: Fornix, cingulum, and uncinate fasciculus.
    
    - Occipital visual pathways: Optic radiations, inferior frontal occipital fasciculus (IFOF), and inferior logitudinal fasciculus (ILF).

---


## During practicum on Friday:

- Dr. Yeh's Q&A.

#### Using regions to map left arcuate fasciculus

- [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).

- Demonstrate function of different region types: seed, ROI, ROA, END, terminative

  - Seed: the starting location of fiber tracking
  - ROI: a filtering region that filters IN tracks
  - ROA: a filtering region that filters OUT tracks
  - END: a filtering region that filters IN tracks ending in the region
  - Not-END: a filtering region that filters OUT tracks ending in the region
  - Terminative: cut tracks that enters the region

- Down load [Region Manual](https://drive.google.com/file/d/1LZTUz2-dybD8LHrZNrnFimXHKWxAG8DK/view?usp=sharing) of [Schneider lab](https://www.lrdc.pitt.edu/schneiderlab/), and fib file [100206.src.gz.gqi.1.25.fib.gz](https://drive.google.com/file/d/1l4Qvyf1FHsLGKQs2axVYqcbBo7Hv2Kox/view?usp=sharing) from shared folder.

- Load the fib file on DSI-Studio by clicking "StepT3: Fiber Tracking & Visualization".

- According to page 17 of the Region Manual, in order to generate raw left arcuate fasciculus, we need to draw regions of interests (ROI) and regions of avoidance (ROA):
    - ROIs: ArcuateCoronal_left and ArcuateAxial_left
    - ROAs: SagittalROA, TemporalCoronal_left, InternalCapsule_left, ExternalCapsule_left, Midbody, InferiorOccipital_left and SFG_left

- To draw region ArcuateCoronal_left, for example, steps include:

1. Look up ***Table of Contents*** in page 2, find ***Regions*** - ***ArcuateCoronal_SIDE (AC)*** - ***page 63***.

2. Turn to page 63, follow the instructions of how to draw ArcuateCoronal_SIDE to identify the region looked for.

3. Remember to define the type of the region drawn, either ROI or ROA in the GUI. In the region window, click ***Type*** and then select ***ROI/ROA***.

4. After creating all the ROIs and ROAs, hit ***Fiber Tracking*** in the ***Tracts*** window.

---

### Practicum task: Mapping unknown pathways using ROI-based fiber tracking

![image](https://user-images.githubusercontent.com/275569/151996479-7ef66e70-68c6-4f54-812e-98b01249830d.png)


1. Download HCP1065 1-mm FIB file from https://brain.labsolver.org/hcp_template.html. 

2. Use region-based fiber tracking, map the orbital connections in nuclei 5.

3. Use region-based fiber tracking, map the temporal connections in nuclei 5.

4. Use region-based fiber tracking, map the occipital connections in nuclei 5.

