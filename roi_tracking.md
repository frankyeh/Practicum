# Fiber Tracking

## Before practicum on Friday, please complete following:

- Watch a video about tractography

<iframe width="560" height="315" src="https://www.youtube.com/embed/xIebVWI4WHk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- Read [[2. Challenges in mapping brain pathways]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0002) and [[6. Fiber tracking methods]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0025) of [a review paper](https://www.sciencedirect.com/science/article/pii/S1053811921009241).


## During practicum on Friday:

### Introduction to tractography

- Deterministic fiber tracking
- Probablistic fiber tracking

![image](http://jmahaffy.sdsu.edu/courses/f00/math122/lectures/num_method_diff_equations/images/euler_ani.gif)

source: source: http://jmahaffy.sdsu.edu/courses/f00/math122/lectures/num_method_diff_equations/nummethod_diffeq.html

### Limitations 

  - **false routing and premature termination**:

<img src="https://user-images.githubusercontent.com/275569/166743312-c200c685-c7b7-4510-bb6a-48253ef44c7a.png" width=800>

source: Yeh, Fang-Cheng, et al. "Tractography methods and findings in brain tumors and traumatic brain injury." NeuroImage 245 (2021): 118651.

<img src="https://user-images.githubusercontent.com/275569/166164844-cbc4b071-4ef1-44e1-b407-70921f6b2727.png" width=800>

source: https://www.nature.com/articles/s41467-017-01285-x/figures/7

  - **gyral bias**

<img src="https://user-images.githubusercontent.com/275569/166742047-192c4a92-96b0-412a-9907-f7ddabf6b90c.png" width=800>

source: Wu, Ye, et al. "Mitigating gyral bias in cortical tractography via asymmetric fiber orientation distributions." Medical image analysis 59 (2020): 101543.  


### Using regions to map left arcuate fasciculus

- [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).

- Hands-on
  - Different region types: seed, ROI, ROA, END, terminative
    - Seed: the starting location of fiber tracking
    - ROI: a filtering region that filters IN tracks
    - ROA: a filtering region that filters OUT tracks
    - END: a filtering region that filters IN tracks ending in the region
    - Not-END: a filtering region that filters OUT tracks ending in the region
    - Terminative: cut tracks that enters the region

  - Download [Region Manual](/Materials/Region%20Manual%20v2_0_1_1.pdf) of [Schneider lab](https://www.lrdc.pitt.edu/schneiderlab/), and fib file [100206.src.gz.gqi.1.25.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1).

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

## Assignment: 

### Refine fiber tracking results 

1. Use [AutoTract] to map **left corticospinal tracts** on [100206.src.gz.gqi.1.7.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1)

2. Identify false results and use ROI-based fiber tracking to improve the results.

### Mapping difficult pathways using ROI-based fiber tracking

![image](https://user-images.githubusercontent.com/275569/151996479-7ef66e70-68c6-4f54-812e-98b01249830d.png)

1. Download [HCP1065 1-mm FIB file](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1) 

2. Use region-based fiber tracking, map the orbital connections in nuclei 5.

3. Use region-based fiber tracking, map the temporal connections in nuclei 5.

4. Use region-based fiber tracking, map the occipital connections in nuclei 5.
