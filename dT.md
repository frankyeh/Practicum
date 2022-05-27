# Differential Tractography

## Before practicum on Friday, please complete following:

### Review Paper

- Read through [Differential Tractography](https://github.com/frankyeh/Practicum/blob/gh-pages/Materials/paper/dT.pdf).

### Differential tractography tutorial

- [Documentation.](https://dsi-studio.labsolver.org/doc/gui_t3_dt.html)

- Tutorial video:
<iframe width="600" height="300" src="https://www.youtube.com/embed/EWOGQ3QTrnw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---


## During practicum on Friday:

### Diffusion MRI analysis methods

![image](https://user-images.githubusercontent.com/275569/170546285-d395bf1c-2eaf-4840-81b7-bd81c4aa53bb.png)


### Differential tractography demonstration

<img src="https://user-images.githubusercontent.com/275569/170547111-2def629f-c5b2-4127-93b8-303dfbcf2ae3.png" width=600>

### Flowchart

<img src="https://user-images.githubusercontent.com/275569/170546907-eb6763b7-d36c-4b00-9d20-49571dcd874b.png" width=600>

### Hands-On: Patients with spinocerebellar ataxia

**Longitudinal comparison**

1. Download two scan session data of sub-SCA202 at [the SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003)
2. Create two SRC files
3. Construct FIB files
4. Export NQA from the follow-up scan
5. Open the FIB file of the baseline and load the NQA with registration.
6. Differential fiber tracking to show the change.

### Testing the Results

<img src="https://user-images.githubusercontent.com/275569/170547010-76a8ab42-0463-42eb-acab-4424b150beac.png" width=600>
---

### Practicum assignment: Cross-sectional comparison using Differential tractography

1. Create a connectometry database using control data at [the SCA2 Diffusion Tensor Imaging study](https://openneuro.org/datasets/ds001378/versions/00003)
2. Generate a subject-matched NQA map at [Step C2a: Modify a Connectometry Database]
  - [Documentation](https://dsi-studio.labsolver.org/doc/gui_t3_dt.html)
  - Subjects demographics:  participants.tsv (need to be modified to keep only values)
3. Open the baseline FIB file of the patient #2 and load the subject-matched NQA using [Slice][Insert MNI image]
4. Differential fiber tracking to show the change.

