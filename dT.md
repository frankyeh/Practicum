# Differential Tractography

## Before practicum on Friday, please complete following:

### Review Paper

- Read through [Differential Tractography](https://github.com/frankyeh/Practicum/blob/gh-pages/Materials/paper/dT.pdf).

### Differential tractography tutorial

- [Documentation.](https://dsi-studio.labsolver.org/doc/gui_t3_dt.html)


---

## During practicum on Friday:

### Diffusion MRI analysis methods

![image](https://user-images.githubusercontent.com/275569/195859557-5a9e0b1e-5116-433f-bc4b-3671a5f37bd7.png)

### Conventional versus Differential Tractography

|          | Conventional fiber tracking | Differential fiber traacking |
|----------|-----------------------------|------------------------------| 
|seed point| start at any white matter location | start at any white matter location |
| propagation | propagate along fiber orientation |  propagate along fiber orientation |
| termination criteria | anisotropy threshold, angular threshold | anisotropy threshold, angular threshold, ***threshold for the anisotropy decrease*** | 

<img src="https://user-images.githubusercontent.com/275569/170547111-2def629f-c5b2-4127-93b8-303dfbcf2ae3.png" width=600>

<img src="https://user-images.githubusercontent.com/275569/170546907-eb6763b7-d36c-4b00-9d20-49571dcd874b.png" width=600>

### Differential Tractography

Variants
1. Longitudinal versus cross-sectional analysis
2. native space versus template space

### Type 1: Longitudinal comparison in the native space

summary: comparing patients' baseline scans with follow-up scans in the native space.

data: SCA patient's [preprocess SRC files](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EkJeJpW9gkdDsw225T6wcw8Bdfpvr1RBXNPJLWF2yafl8A?e=gLaShw), including the baseline scans and the follow up scans.

For each patient, run the following:
1. Run GQI reconstructions on all SRC files. 
2. Export FA maps from the follow-up scans.
3. Open the FIB file of the baseline scan and [Slices][Inser Other Images]=the exported FA maps of the second scan.
4. Specify metrics at [Step T3c: Options][Tracking Parameters][Differential Tracking] and run differential fiber tracking.
  
```
dsi_studio --action=rec --source=*.src.gz
dsi_studio --action=exp --source=*02_dwi*.fib.gz --export=dti_fa
dsi_studio --action=trk --source=*_ses-01_dwi.src.gz.gqi.1.25.fib.gz --other_slices=*_ses-02_dwi.src.gz.gqi.1.25.fib.gz.dti_fa.nii.gz --dt_metric1=dti_fa --dt_metric2=*_ses-02_dwi --dt_threshold=0.2 --seed_count=10000000 --min_length=30 --output=*.tt.gz
```

### Type 2: Longitudinal comparison in the template space

summary: comparing patients' baseline scans with follow-up scans in the template space.

- normalization partly handles deformation
- use template as the tracking framework.

For each patient, run the following:
1. Run QSDR reconstructions on all SRC files. 
2. Export FA maps from all scans.
3. Open the template FIB file and [Slices][Inser Other Images]=the exported FA maps of the first and second scan.
4. Specify metrics at [Step T3c: Options][Tracking Parameters][Differential Tracking] and run differential fiber tracking.

```
dsi_studio --action=rec --source=*.src.gz --method=7 --output=*.qsdr.fib.gz
dsi_studio --action=exp --source=*.fib.gz --export=dti_fa
dsi_studio --action=trk --source=0 --other_slices=sub-SCA201_ses-01_dwi.qsdr.fib.gz.dti_fa.nii.gz,sub-SCA201_ses-02_dwi.qsdr.fib.gz.dti_fa.nii.gz --dt_metric1=sub-SCA201_ses-01_dwi --dt_metric2=sub-SCA201_ses-02_dwi --dt_threshold=0.2 --seed_count=10000000 --min_length=30 --output=sub-SCA201.tt.gz

dsi_studio --action=trk --loop=*_ses-01_dwi.qsdr.fib.gz --source=0 --other_slices=*_ses-01_dwi.qsdr.fib.gz.dti_fa.nii.gz,*_ses-02_dwi.qsdr.fib.gz.dti_fa.nii.gz --dt_metric1=*_ses-01_dwi --dt_metric2=*_ses-02_dwi --dt_threshold=0.2 --seed_count=10000000 --min_length=30 --output=*.tt.gz
```

### Type 3: cross-sectional comparison in the native space

summary: compare patients' scans with their **age-sex-matched** scan regressed from the control subjects.

data: [SCA control subject's connectometry database](https://pitt-my.sharepoint.com/:u:/g/personal/yehfc_pitt_edu/EXhpDe7CdYxGsXySp3OgFI0BoQw5nAFl2wy14VgbuIQ6-w?e=ueMUOs) (dti_fa).

for each patient, run the following:
1. Open the FIB file of the baseline scan and [Slices][Inser Other Images]=sub-control_only.dti_fa.db.fib.gz
2. Input [subject's age and sex](https://pitt-my.sharepoint.com/:t:/g/personal/yehfc_pitt_edu/ERmqnTRGs11LhxeloKHUWnoBhtMPQ-YpWB-h4LVeNyKRqg?e=2cha4i) for generating age-sex-matched data. 
3. Specify metrics at [Step T3c: Options][Tracking Parameters][Differential Tracking] and run differential fiber tracking.

```
dsi_studio --action=trk --source=*_ses-01_dwi.src.gz.gqi.1.25.fib.gz --other_slices=sub-control_only.dti_fa.db.fib.gz --dt_metric1=sub-control_only --dt_metric2=dti_fa --subject_demo=patient_age_sex.txt --dt_threshold=0.2 --seed_count=10000000 --min_length=30 --tip_iteration=16 --output=*.cross_sectional.tt.gz
```


### Type 4: cross-sectional comparison in the template space

summary: compare patients' scans with their **age-sex-matched** scan regressed from the control subjects.

for each patient, run the following:
1. Open the QSDR-FIB file of the baseline scan and [Export] dti_fa
2. Open the template FIB file
3. [Slices][Inser Other Images]=the exported FA maps of the baseline scan.
4. [Slices][Inser Other Images]=sub-control_only.dti_fa.db.fib.gz and input [subject's age and sex](https://pitt-my.sharepoint.com/:t:/g/personal/yehfc_pitt_edu/ERmqnTRGs11LhxeloKHUWnoBhtMPQ-YpWB-h4LVeNyKRqg?e=2cha4i) for generating age-sex-matched data. 
5. Specify metrics at [Step T3c: Options][Tracking Parameters][Differential Tracking] and run differential fiber tracking.

```
dsi_studio --action=trk --loop=*_ses-01_dwi.qsdr.fib.gz.dti_fa.nii.gz --source=0 --other_slices=*_ses-01_dwi.qsdr.fib.gz.dti_fa.nii.gz,sub-control_only.dti_fa.db.fib.gz --dt_metric1=sub-control_only --dt_metric2=*_ses-01_dwi --subject_demo=patient_age_sex.txt --dt_threshold=0.2 --seed_count=10000000 --min_length=30 --tip_iteration=16 --output=*.cross_sectional.tt.gz
```


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




