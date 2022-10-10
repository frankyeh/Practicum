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

### Longitudinal comparison

1. Download SCA patient's [preprocess SRC files](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EkJeJpW9gkdDsw225T6wcw8Bdfpvr1RBXNPJLWF2yafl8A?e=gLaShw), including the baseline scans and the follow up scans.
2. For each patient, run the following:
  1. Run GQI reconstructions on all SRC files. 
  2. Export FA maps from the follow-up scans.
  3. Open the FIB file of the baseline scan and [Slices][Inser Other Images]=the exported FA maps of the second scan.
  4. Run differential fiber tracking.

```
dsi_studio --action=rec --source=*.src.gz
dsi_studio --action=exp --source=*02_dwi*.fib.gz --export=dti_fa
dsi_studio --action=trk --source=*_ses-01_dwi.src.gz.gqi.1.25.fib.gz --other_slices=*_ses-02_dwi.src.gz.gqi.1.25.fib.gz.dti_fa.nii.gz --dt_metric1=*_ses-02_dwi --dt_metric2=dti_fa --dt_threshold=0.2 --seed_count=10000000 --min_length=30 --output=*.tt.gz
```

### Cross-sectional comparison

1. Download [SCA control subject's connectometry database](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EXhpDe7CdYxGsXySp3OgFI0BoQw5nAFl2wy14VgbuIQ6-w?e=ueMUOs) (dti_fa).
2. For each patient, run the following:
  1. Open the FIB file of the baseline scan and [Slices][Inser Other Images]=sub-control_only.dti_fa.db.fib.gz
  2. Run differential fiber tracking.

### Testing the Results

<img src="https://user-images.githubusercontent.com/275569/170547010-76a8ab42-0463-42eb-acab-4424b150beac.png" width=600>
---

### Practicum assignment: false discovery rate (FDR) estimation for differential tractography

**longitudinal study**
1. run longitudinal differential tractography on all subjects, including controls and patients
2. calculate the averaged volume of findings in the cerebellum from controls --> expected volume of false positives
3. calculate the averaged volume of findings in the cerebellum from patients --> expected volume of true positives+false positives
4. FDR = false positive/(true positive+false positives) = (volume from controls)/(volume from patients)

**cross-sectional study**
1. run cross-sectional differential tractography on SCA2 controls, including controls and patients
2. same as above
3. same as above
4. same as above




