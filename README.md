# fmriprep_internal
scripts for running fmriprep on Discovery cluster. You can use filter files if you have two or more timepoints.
When getting scans from NUBIC, the T1w will result in 4 separate scans.
1. anatT1_acqmprageNav4e_XX
- Contains images for each individual echo – DO NOT INCLUDE IN ANALYSIS
2. anatT1_acqmprageNav4e_XX
- A Normalized version of “anatT1_acqmprageNav4e_31” – DO NOT INCLUDE IN ANALYSIS
3. anatT1_acqmprageNav4e_RMS_XX
- RMS combination of the 4-echo T1-weighted images – THIS IS WHAT I WOULD USE FOR MY ANALYSIS
4. anatT1_acqmprageNav4e_RMS_XX
- Normalized version of “anatT1_acqmprageNav4e_RMS_33” – You could use this image for your analysis if you want, but since most post-processing pipelines run a Normalization step anyway you run this step twice, which could cause some image quality degradation.

When you rerun fmriprep on the same subject you need to make sure you are deleting all related files, including scratch files. 
When you run more than 1 participant, it may results in errors depending on how you run it because when you sbatch separately, they use the same workflow. 
Use the fmriprep_singularity_run.sh to run in parrell _this may work_
