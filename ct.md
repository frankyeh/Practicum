# Correlational Tractography

## Before practicum on Friday, please complete following:

### Review Paper

- [Connectometry](Materials/paper/connectometry.pdf).

### Correlational tractography tutorial

- [Documentation.](https://dsi-studio.labsolver.org/doc/gui_cx.html)

- Tutorial video:
<iframe width="896" height="504" src="https://www.youtube.com/embed/qC8jx6XZHGI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---

## During practicum on Friday:

### Correlation tractography


|          | Conventional fiber tracking | Differential fiber traacking | Correlational Tractography |
|----------|-----------------------------|------------------------------|----------------------------| 
|seed point| start at any white matter location | start at any white matter location | start at any white matter location |
| propagation | propagate along fiber orientation |  propagate along fiber orientation |  propagate along fiber orientation |
| termination criteria | anisotropy threshold, angular threshold | anisotropy threshold, angular threshold, ***threshold for the anisotropy decrease*** |  anisotropy threshold, angular threshold, ***threshold for the t-statistics*** | 



### Connectometry

<img src="https://user-images.githubusercontent.com/275569/197086945-5eb4bbc9-8a01-4bc6-a59d-84bcbe1f3735.png" width=700>

Connectometry: a statistical method using permutation test and bootstrap resampling to test the significance of correlational tractography.

### Steps
- Calculate t-statistics using Spearman rank-based correlation
  - permuted versus non-permuted, respectively, both after bootstrap resampling
- Fiber tracking based on t-statistics
  - Each fiber tracking from a seed is a statistical test.
  - The test statisticsis the length of track.
  - positive findings: length > L, negative finding: length < L
- FDR calculation at length L
  - #tracts with length > L after permutation   => #false positive
  - #tracts with length > L without permutation => #false positive + #true positive
  - FDR = (#false positive)/(#false positive + #true positive)
- Results
  - Fixed L → report FDR
  - FDR threshold → estimate L* → showing findings satisfying FDR threshold

### Types

- cross-sectional versus longitudinal study
- correlation with a categorical variable (e.g. control v.s. patient) or continuous variable (e.g. age)

| study type | correlation type   | examples of null hypothesis |
|------------|--------------------|-----------------|
| cross-sectional | correlation with a categorical variable | the tractography with decreased metrics in group 1 is the same as those after group permutation. |
| cross-sectional | correlation with a continuous variable | the tractography with decreased metrics correlated with age is the same as those after age permutation. |
| longitudinal | increased of decreased  | the tractography with decreased metrics is the same as those after random-permuting the sign of change. |
| longitudinal | associated with a categorical variable  | the tractography with decreased metrics in group 1 is the same as those after group permutation. |
| longitudinal | associated with a continuous variable  | the tractography with decreased metrics correlated with age is the same as those after age permutation. |

### Hands-on: cross-sectional analysis

data: [SCA2 cross sectional database](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/ETlDr7d6pzFDrSMjX_qGZosBw1i8IGT0E7QqPidQDRuihg?e=9JZddF) and [demographics](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/ETCY96W54wxMvTGjRh0i2iYB5rcuo38NJd1zK3KbKGOLkw?e=qYt5Xj)

- correlational tractography correlated with group 
  - report FDR given a length threshold
  - assign FDR threshold and report findings
  - high t-threshold (more localized) versus low t-threshold (less localized) 
- correlational tractography correlated with group under partial correlation considering age/sex. 
- stratified analysis using cohort selection (e.g. male and female).
- combined ROI/ROA/terminative (wk 3 course)
- post-hoc analysis
  - identifying pathways using manual virtual dissection and recognition (wk 2 course)
  - tract-metric scatter plot using tract-based analysis (week 5 hw).

### Hands-on: longitudinal analysis

data: [SCA2 longitudinal database](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/ET5mwohX9jVPrqsdEkrWOpUBh6cIqElebkLG8wKOTMhyzQ?e=EcoJhf)

- compute longitudinal change using [Step C2][Tools][Longitudinal Scans]
- use connectometry to answer the following question
  - are there significant decrease of FA in the patient group?
  - are there significant decrease of FA in the control group?
  - are decreased FA in the control group significantly correlated with age?
  - are decreased FA in the patient group significantly correlated with age?
  - are there significantly more changes in the patient group than control group?
  - are there significantly more changes in the patient group than control group in the brainstem?


