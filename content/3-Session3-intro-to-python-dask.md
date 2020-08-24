---
title: Session3
nav: true
--- 

# Session 3 Tutorial:

# Intro to Distributed Computing on the Ceres HPC System Using Python and Dask

This page contains all the info you need to participate in Session 3 of the SCINet Geospatial Workshop 2020.

After the session we will post a link to the video recording on this page as well.

<br>

**Learning Goals**

- data analysis technique for very large datasets (the tools in this tutorial are most appropriate for analysis of large earth-science-type datasets)
- set up SLURM cluster to compute "in parallel"
- scale clusters for heavy compute
- use adaptive clusters to dynamically scale up and down your computing
- view Dask diagnostics to visualize cluster computations in real time

<br><br>

---

## Contents

[Session Rules](#session-rules)

[How to Run the Tutorial on Ceres](#how-to-run-the-tutorial-on-ceres)

[View the Tutorial Online](#view-the-tutorial-online)

<br><br>

---

## Session Rules

**GREEN LIGHT, RED LIGHT** - Use the Zoom participant feedback indicators to show us if you are following along successfully as well as when you need help. To access participant feed back, click on the "Participants" icon to open the participants pane/window. Click the green "yes" to indicate that you are following along successfully, click the red "no" to indicate when you need help. Ideally, you will have either the red or green indicator displayed for yourself throughout the entire tutorial. We will pause every so often to work through solutions for participants displaying a red light.

**CHAT QUESTIONS/COMMENTS TAKE FIRST PRIORITY** - Chat your questions/comments either to everyone (preferred) or to the chat moderator (Rowan Gaffney) privately to have your question/comment read out loud anonamously. We will address chat questions/comments first and call on people who have written in the chat before we take questions from raised hands.

**SHARE YOUR VIDEO WHEN SPEAKING** - If your internet plan/connectivity allows, please share your video when speaking.

**KEEP YOURSELF ON MUTE** - Please mute yourself unless you are called on.
<br><br>

---

## How to Run the Tutorial on Ceres

1. Login to your SCINet/Ceres account through the JupyterHub web interface
   * Go to [https://jupyterhub.scinet.usda.gov](https://jupyterhub.scinet.usda.gov)
   * Login to the system with your SCINet credentials
   * Submit the Spawning Page with the following information (if not specified below, leave blank):<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Node Type: ```short```<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Number of Cores: ```4```<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Job Duration: ```02:00:00```<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Path to the container image: ```/lustre/project/geospatial_tutorials/wg_2020_ws/ data_science_im_rs_vSCINetGeoWS_2020.sif```<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Container Exec Args: ```--bind /etc/munge --bind /var/log/munge --bind /var/run/munge --bind /usr/bin/squeue --bind /usr/bin/scancel --bind /usr/bin/sbatch --bind /usr/bin/scontrol --bind /usr/bin/sinfo --bind /system/slurm:/etc/slurm --bind /run/munge --bind /usr/lib64/libslurm.so --bind /usr/lib64/libmunge.so.2 --bind /usr/lib64/slurm --bind  /project --bind /lustre```
   
    After a few minutes, a JupyterLab instance running on the Ceres HPC should open in your browser. After several attempts, if the spawner fails and JupyterLab does not open correctly, please contact the SCINet Virtual Research Support Core (VRSC) for assistance at scinet_vrsc@usda.gov.

2. Download the tutorial material from the workshop GitHub repo
   * Open a terminal: File-->New-->terminal (alternatively, click the "+" icon (launcher) on the left and then choose the "terminal" icon on the launcher screen) 
   * Download the tutorials to your home directory
   ```bash
   git clone --single-branch https://github.com/kerriegeil/SCINET-GEOSPATIAL-RESEARCH-WG.git
   ```
   
3. Run a notebook:
   * You should now see a folder (file system extension on the left hand side of JupyterLab) titled *SCINET-GEOSPATIAL-RESEARCH-WG*.
   * Navigate to */SCINET-GEOSPATIAL-RESEARCH-WG/tutorials/*
   * Open session3-intro-to-python-dask-on-ceres.ipynb
   * Select the py_geo kernel (upper right corner in the notebook)
   * Execute blocks of script by clicking the "play" icon in the notebook or typing Shift+Enter 

<br><br>

---

## View the Tutorial Online

If you are not running the tutorial on Ceres during the session you can view a static version of it at [https://kerriegeil.github.io/SCINET-GEOSPATIAL-RESEARCH-WG/html-tutorials/session3-intro-to-python-dask-on-ceres.html](https://kerriegeil.github.io/SCINET-GEOSPATIAL-RESEARCH-WG/html-tutorials/session3-intro-to-python-dask-on-ceres.html)
