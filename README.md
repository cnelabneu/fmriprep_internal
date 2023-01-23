# fmriprep_internal
scripts for running fmriprep on Discovery cluster
This is about how to convert dcm files to bids on discovery cluster

1. load necessary packages for the cluster
srun --pty /bin/bash
module purge
module load discovery
module load anaconda3/2022.05
conda create --prefix=/work/cnelab/code/conda-dcm2bids python=3.9 anaconda
source activate /work/cnelab/conda-dcm2bids
conda install -c conda-forge dcm2bids
conda install -c conda-forge dcm2niix

2. Test if the tools were installed properly
dcm2bids -h
dcm2niix -h

3. Create directory
RAW_DIR=/scratch/ai.me/data
mkdir $RAW_DIR/BIDS

4. Run the dcm2bids helper to get the scanning information, could be a random subject
dcm2bids_helper -d Pilot_1/Pilot_1 -o BIDS/

5. Use the information from step4 to write the BIDS_config.json

Example please see $RAW_DIR/scripts/BIDS_config.json

6. Run dcm2bids

Run run_dcm2bids.sh
Make sure you have a list of participants id 

