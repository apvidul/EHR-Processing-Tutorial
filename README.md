# Resources for BMIF204

## MIMIC-IV Setup Scripts
```bash
wget https://raw.githubusercontent.com/apvidul/setup-scripts/refs/heads/main/setup_ehr_tutorial_mimic4_codi_nlp.sh
```

## Tools for Downstream Analysis

1. [ONCE](https://shiny.parse-health.org/ONCE/): A feature generation app that identifies related NLP and codified features based on an input or target disease. For example: PheCodes and CUIs.

2. [KESER Network](https://shiny.parse-health.org/kesernetwork-linkage/): A tool to identify and visualize codified concepts relevant to diseases, medications, and procedures (e.g., PheCodes, RxNorm).

3. [NILE](https://celehs.hms.harvard.edu/software/NILE.html): An NLP tool for fast and efficient processing of clinical notes to UMLS CUIs. Note: You will need a UMLS License to use this tool.

4. [PETEHR](https://pypi.org/project/petehr/): Python toolkit for EHR processing developed specifically for this tutorial. It is designed to process MIMIC-IV data and generate research-ready datasets. 


&nbsp;


## Accessing Jupyter Notebook on O2 from your local machine

Follow the steps below to set up and access a Jupyter Notebook running on the o2 server from your local machine.


### 1. Prerequisites
Ensure that X11 forwarding is active on your system:
- **Mac**: Install and run [XQuartz](https://www.xquartz.org/).
- **Windows**: Install [MobaXterm](https://mobaxterm.mobatek.net/).

### 2. Set Up Local Port Forwarding
On your **local machine**, run the following command to log in to the `o2` server and set up port forwarding:
```bash
ssh -Y -L 50001:127.0.0.1:50001 username@o2.hms.harvard.edu
```

### 3. Request an Interactive Session
After logging into o2, request an interactive compute node enabling X11 forwarding and setting up a network tunnelby running:
```bash
srun -t 0-00:40 --pty -p interactive --mem=12G --x11 --tunnel 50001:50001 /bin/bash
```

### 4. Navigate to Your Workspace and Activate Conda
```bash
cd /n/scratch/users/v/va67/EHR_TUTORIAL_WORKSPACE
source activate ehr_tutorial
```

### 5. Start the Jupyter Notebook Server on O2
```bash
jupyter notebook --port=50001 --browser="none"
```

### 6. Access the Jupyter Notebook on your Local Machine
Open a browser and go to
http://localhost:50001/tree

### 7. Shut Down the Jupyter Server
To stop the Jupyter Notebook server, go to the terminal where the session is running and do Ctrl+C
