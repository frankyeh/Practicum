# Fiber Tracking

## Before practicum on Friday, please complete following:

- Watch a video about tractography

<iframe width="560" height="315" src="https://www.youtube.com/embed/xIebVWI4WHk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- Read [[2. Challenges in mapping brain pathways]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0002) and [[6. Fiber tracking methods]](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0025) of [a review paper](https://www.sciencedirect.com/science/article/pii/S1053811921009241).


## During practicum on Friday:

### 1.Introduction to tractography

- [Fiber tracking method](https://www.sciencedirect.com/science/article/pii/S1053811921009241#sec0025)
  - Input: local fiber orientations (a.k.a. fixel)
  - Output: sequences of 3D coordinates
  - Deterministic vs probablistic

![image](https://user-images.githubusercontent.com/275569/167182297-129fb316-60a5-40b1-8c77-f3d0f3ed1122.png)

Local fiber orientations derived from dMRI

![image](http://jmahaffy.sdsu.edu/courses/f00/math122/lectures/num_method_diff_equations/images/euler_ani.gif)

source: source: http://jmahaffy.sdsu.edu/courses/f00/math122/lectures/num_method_diff_equations/nummethod_diffeq.html

- Hands-on: [tracking parameters](https://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html)
  - [100206.src.gz.gqi.1.7.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1) 
  - Parameters
    - Anisotropy threshold
    - Angular threshold
    - Step size
    - Minimum and maximum length

### 2.Limitations 

  - **false routing and premature termination**:

<img src="https://user-images.githubusercontent.com/275569/166743312-c200c685-c7b7-4510-bb6a-48253ef44c7a.png" width=800>

source: Yeh, Fang-Cheng, et al. "Tractography methods and findings in brain tumors and traumatic brain injury." NeuroImage 245 (2021): 118651.

<img src="https://user-images.githubusercontent.com/275569/166164844-cbc4b071-4ef1-44e1-b407-70921f6b2727.png" width=800>

source: https://www.nature.com/articles/s41467-017-01285-x/figures/7

  - **gyral bias**

<img src="https://user-images.githubusercontent.com/275569/166742047-192c4a92-96b0-412a-9907-f7ddabf6b90c.png" width=800>

source: Wu, Ye, et al. "Mitigating gyral bias in cortical tractography via asymmetric fiber orientation distributions." Medical image analysis 59 (2020): 101543.  


### 3.Region types used in fiber tracking

- Hands-on: [region-based fiber tracking](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html)
  - Load [HCP1065.1mm.fib.gz](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1)
  - Demonstrate Region types: seed, ROI, ROA, END, terminative
    - Seed: the starting location of fiber tracking
    - ROI: a filtering region that filters IN tracks
    - ROA: a filtering region that filters OUT tracks
    - END: a filtering region that filters IN tracks ending in the region
    - Not-END: a filtering region that filters OUT tracks ending in the region
    - Terminative: cut tracks that enters the region

### 4.Fiber tracking protocols

- [Region Manual](/Materials/Region%20Manual%20v2_0_1_1.pdf)(source: [Schneider lab](https://www.lrdc.pitt.edu/schneiderlab/))
- [TractEM](https://my.vanderbilt.edu/tractem/)
- Hands-on: mapping left arcuate fasciculus
  - Load [HCP1065.1mm.fib.gz](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1) by clicking "StepT3: Fiber Tracking & Visualization".
  - According to page 17 of the Region Manual, in order to generate raw left arcuate fasciculus, we need:
    - ROIs: ArcuateCoronal_left, ArcuateAxial_left
    - ROAs: SagittalROA, ExternalCapsule_left
  - To draw region ArcuateCoronal_left, for example, steps include:

    1. Look up ***Table of Contents*** in page 2, find ***Regions*** - ***ArcuateCoronal_SIDE (AC)*** - ***page 63***.
    2. Turn to page 63, follow the instructions of how to draw ArcuateCoronal_SIDE to identify the region looked for.
    3. Remember to define the type of the region drawn, either ROI or ROA in the GUI. In the region window, click ***Type*** and then select ***ROI/ROA***.
    4. After creating all the ROIs and ROAs, hit ***Fiber Tracking*** in the ***Tracts*** window.
   
  - Save regions using [Regions][Save Checked Regions in Multiple Files]
  - Repeat the mapping on [100206.src.gz.gqi.1.7.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1) by loading the saved regions from [Regions Misc][Open MNI Regions]


---

## Assignment: 

### 1. Combine automatic fiber tracking and region-based fiber tracking

1. Use [AutoTract] to map **left corticospinal tracts** on [100206.src.gz.gqi.1.7.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1)

2. Identify false results and use ROI-based fiber tracking to improve the results.

3. [Optional] write a script to map CST in [multiple FIB files](https://zenodo.org/record/6307812)(Download 3~5 FIB files)
  - rename the regions files to include "mni" in the file name, and DSI Studio will load it as MNI regions
  - [examples](https://dsi-studio.labsolver.org/doc/cli_t3.html) 

### 2. Mapping difficult pathways using region-based fiber tracking

![image](https://user-images.githubusercontent.com/275569/151996479-7ef66e70-68c6-4f54-812e-98b01249830d.png)

1. Download [HCP1065 1-mm FIB file](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1) 

2. Use region-based fiber tracking, map the orbital connections in nuclei 5.

3. Use region-based fiber tracking, map the temporal connections in nuclei 5.

4. Use region-based fiber tracking, map the occipital connections in nuclei 5.

