# Region-Based Fiber Tracking

## Before practicum on Friday, please complete following:

### Anatomy

- Read [**[2. Challenges in mapping brain pathways]**](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0002) and [**[6. Fiber tracking methods]**](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0025). 

- Get familiarized with fiber tracking parameters [[document]](https://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html)

## During practicum on Friday:

### an overview of fiber tracking

- [a review paper](https://www.sciencedirect.com/science/article/pii/S1053811921009241)

### Using regions to map left arcuate fasciculus

- [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).

- Demonstrate function of different region types: seed, ROI, ROA, END, terminative

  - Seed: the starting location of fiber tracking
  - ROI: a filtering region that filters IN tracks
  - ROA: a filtering region that filters OUT tracks
  - END: a filtering region that filters IN tracks ending in the region
  - Not-END: a filtering region that filters OUT tracks ending in the region
  - Terminative: cut tracks that enters the region

- Down load [Region Manual](/Materials/Region%20Manual%20v2_0_1_1.pdf) of [Schneider lab](https://www.lrdc.pitt.edu/schneiderlab/), and fib file [100206.src.gz.gqi.1.25.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1) from shared folder.

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

1. Download [HCP1065 1-mm FIB file](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1) 

2. Use region-based fiber tracking, map the orbital connections in nuclei 5.

3. Use region-based fiber tracking, map the temporal connections in nuclei 5.

4. Use region-based fiber tracking, map the occipital connections in nuclei 5.

