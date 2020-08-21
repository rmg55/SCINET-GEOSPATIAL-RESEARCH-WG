---
title: Session2
#nav: true
--- 

# Session 2 Tutorial

# Introduction to the Ceres High-Performance Computing System Environment 

[Session Rules](#session-rules)

[The SCINet Website](#the-scinet-website)

[High-Performance Computing (HPC) System Basics](#high-performance-computing-hpc-system-basics)
  - [What is an HPC system?](#what-is-an-hpc-system)
  - [Why use an HPC system?](#why-use-an-hpc-system)
  - [HPC terminology](#hpc-terminology)

[USDA-ARS HPC System Details](#usda-ars-hpc-system-details)
  - [The Ceres HPC System](#the-ceres-hpc-system)
  - [Other SCINet HPC Systems](#other-scinet-hpc-systems)

[Ceres HPC Login with Secure Shell (SSH)](#ceres-hpc-login-with-secure-shell)

[Ceres HPC Login with JupyterHub](#ceres-hpc-login-with-jupyterhub)
  - [Tour of JupyterLab](#tour-of-jupyterlab)
  - [Jupyter Notebook Basics](#jupyter-notebook-basics)

[Basic Linux Commands](#basic-linux-commands)

[Interactive Computing vs Batch Computing](#interactive-computing-vs-batch-computing)
  -[Interactive Computing on Ceres](#interactive-computing-on-ceres)
  -[Batch Computing on Ceres](#batch-computing-on-ceres)

[Submitting a Compute Job with a SLURM Batch Script](#submitting-a-compute-job-with-a-slurm-batch-script)


## Session Rules

**GREEN LIGHT, RED LIGHT** - Use the Zoom participant feedback indicators to show us if you are following along successfully as well as when you need help. To access participant feed back, click on the "Participants" icon to open the participants pane/window. Click the green "yes" to indicate that you are following along successfully, click the red "no" to indicate when you need help. Ideally, you will have either the red or green indicator displayed for yourself throughout the entire tutorial. We will pause every so often to work through solutions for participants displaying a red light.

**CHAT QUESTIONS/COMMENTS TAKE FIRST PRIORITY** - Burning questions or comments should go in the chat. Chat your question either to everyone (preferred) or to the chat moderator () privately to have your question/comment read out loud anonamously. We will answer chat questions first before we take questions from raised hands.

**RAISED HANDS TAKE SECOND PRIORITY** - After we go through chat questions/comments, we'll call on participants with raised hands. Select "raise hand" from within the participants pane/window (same location as green "yes", red "no").

**SHARE YOUR VIDEO WHEN SPEAKING** - If your internet plan/connectivity allows, please share your video when speaking.

**KEEP YOURSELF ON MUTE** - Please mute yourself unless you are called on.


## The SCINet Website

The [SCINet Website](https://scinet.usda.gov/) is the source of much of the material presented in this tutorial. Use the SCINet website to request SCINet accounts, access SCINet/HPC user guides, get computing help or other support, and find out about upcoming and previous computational training events. 


## High-Performance Computing (HPC) System Basics

### What is an HPC System? 


### Why use an HPC System?


### HPC Terminology

SSH

login node, compute node

core/logical core

batch/interactive computing

SLURM/job scheduler


## USDA-ARS HPC System Details

The [Computer Systems](https://scinet.usda.gov/about/compute) page of the SCINet website gives a brief summary of the USDA-ARS HPC systems.

### The Ceres HPC System

The [Ceres User Manual](https://scinet.usda.gov/guide/ceres/) and [Ceres Quick Start Guide](https://scinet.usda.gov/guide/quickstart) contain most of the information you could want to know about the Ceres HPC.

The operating system running on Ceres is CentOS and the job scheduler is SLURM. LINK

Nodes
You SSH into Ceres on the login node. The login node should be used for navigating your directories, organizing your files, and running minor scripts. All computing on Ceres should be done on compute nodes. DON'T RUN YOUR COMPUTE SCRIPTS OR INSTALL SOFTWARE ON THE LOGIN NODE AS IT SLOWS THE NODE DOWN FOR EVERYONE. 

When you use JupyterHub to login to Ceres you are placed on a compute node, not a login node

The [Technical Overview of the Ceres User Manual](https://scinet.usda.gov/guide/ceres/#technical-overview) describes the 5000 compute cores (10000 logical cores), 65 TB of total RAM, 250TB of total local storage, and 4.7 PB of shared storage available on the Ceres HPC.

Partitions/Queues - Community and priority, short is the default

Directory structure and data storage - home, project, keep, /project/shared_files/, shared library, common data library, backups

User quotas

Compute limitations - nodes per user, time per partition

Software on Ceres - module system, software page, user installed software

Getting data on/off

User support from the Virtual Research Support Core

Requesting storage, software, cloud compute (AWS)

Best Practices
nothing serious on the login node
use /scratch space for faster i/o with large datasets
for heavy compute short jobs (less than 2hrs) go for brief-low (more cores per node and more memory)
acknowledge SCINet in your pubs!
WHAT ELSE????


### Other SCINet HPC Systems
There are two other HPC Systems coming to SCINet soon. Summaries of the systems will be posted to the SCINet website [computing systems page](https://scinet.usda.gov/about/compute).


## Ceres HPC Login with Secure Shell (SSH)

First, let's login to our SCINet (Ceres) accounts with SSH. You should have already successfully logged in this way at least once before today by following the instructions sent to you when your SCINet account was approved. The [Quick Start Guide](https://scinet.usda.gov/guide/quickstart#accessing-scinet) has instructions for SSH'ing to Ceres from Windows, Mac, and Linux Machines.

If you haven't yet set up a config file for SSH'ing to Ceres (we won't cover it but instructions are at the Quick Start Guide link above) then:
```bash
ssh -o TCPKeepAlive=yes -o ServerAliveInterval=20 -o ServerAliveCountMax=30 user.name@ceres.scinet.usda.gov
```

The keep alives are especially important for rural/satellite internet connections so that instantaneous breaks in service won't terminate your connection to the HPC.

If you've set up your config file you can simply:
```bash
ssh whatever-you-named-the-host-in-your-config
```

If you are not on an ARS VPN, you will be asked for a 6-digit Google Authenticator code. See the [multi-factor authentication guide](https://scinet.usda.gov/guide/multifactor/) for help. After entering the Google code, you will be asked to enter your password.

If you are on an ARS VPN, you will skip the Google authentication and be asked only for your password.

After a successful login you will see a list of all your quotas and used space.

If you can't successfully login to your account, contact scinet_vrsc@usda.gov for assistance.

To sign out of Ceres just close your terminal or type exit.


## Ceres HPC Login with JupyterHub

In summer 2020, a new way of accessing Ceres was set up with JupyterHub. JupyterHub allows access to Ceres through a web browser and spawns an instance of JupyterLab on a compute node.

Let's walk through how to login to Ceres using JupyterHub with the [Jupyter Guide](https://scinet.usda.gov/guide/jupyter).

### Tour of JupyterLab

The Launcher:
Click the plus sign on the left or go to File > New Launcher to see the launcher screen. From here you can open a Jupyter Notebook, a terminal, a textfile, a markdown file, and more.

Accessing your files:
Clicking on the folder icon on the far left will show you the files and folders in your home directory or the directory you listed in the JupyterLab spawner during the login process.

Access to software modules:
Clicking on the hexagon icon on the far left will show you all the software modules available on the Ceres HPC. Clicking load on any of the modules is equivalent to typing ```module load name-of-software``` (as described in the [Quick Start Guide](https://scinet.usda.gov/guide/quickstart#using-the-software-applications-on-ceres)). Note: there aren't a ton of software modules on Ceres that are relevant to the geospatial research community, so you likely won't need to use this feature often.

### Jupyter Notebook Basics

**Step 1: Open a Jupyter Notebook**

Click the launcher and launch a Python 3 notebook- notice the .ipynb file extension. 

Notice how it says "Python 3" at the top right of the notebook. You are working in a Python 3 environment or "kernel". You could change this by clicking on "Python 3" and selecting a different kernel from the dropdown list in the pop-up box. Don't choose a different kernel for now, but note that this is where you could select a Conda environment that you have created. We will cover this in the Session 4 Tutorial on computational reproducibility. 

**Step 2: Add a Raw Text Cell**

At the top of the notebook click "Code" and change it to "Raw". Click on the cell and type the following:
```bash
author: your name
date: today's date
description: my first jupyter notebook hello world
```

To execute the cell type Shift+Enter or click the run button at the top of the notebook (looks like "play").

**Step 3: Add a Markdown Cell**

Click inside the new cell that has appeared in your notebook, then at the top of the notebook click again on "Code" and change it to "Markdown". Click inside the Markdown cell and type:
```bash
# Make Notes in Your Codes Prettier Using Markdown
## add a subtitle

Write some pretty text.
```

Execute the Markdown cell. 

Learn more about JupyterHub markdown syntax [here](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html) or [here](https://www.ibm.com/support/knowledgecenter/en/SSGNPV_2.0.0/dsx/markd-jupyter.html). A quick Google search on "JupyterHub markdown cheat sheet" will reveal tons of helpful sites. 

**Step 4: Add a Code Cell**

If you executed the previous cell, a new code cell should have automagically appeared. Type:
```bash
print('Hello, Jupyter world!')
```

and execute the cell.

Notice how the output appears right in the Jupyter notebook. You can also print tables and plot figures right in the Jupyter notebook... all your code, comments, and outputs will be in one place- inside the .ipynb file!


**Step 5: Delete a Cell**

Right click on the cell and choose "Delete Cells" or place your cursor in the cell and then click on the scissors icon at the top of the notebook.

**Step 6: Insert a Cell**

Insert a cell under the markdown cell by clicking on the markdown cell and then clicking the plus button at the top of the notebook (next to the scissors). Type:
```bash
print('How awesome is this?!')
```

and execute the cell.

**Step 7: Clear all Outputs**

At the top of JupyterLab click Kernel > Restart Kernel and Clear All Outputs, the click Restart in the pop-up window. All you outputs are now cleared.

**Step 8: Re-run all Cells**

At the top of JupyterLab click Run > Run All Cells

**Step 9: Save Your Work**

Actually, JupyterLab is autosaving your notebook as you work, but you'll want to name your file.

Right click on "Untitled.ipynb" either on the notebook tab or in the file browser on the left, then choose "Rename". In the pop-up window, name your file and click "Rename". 



## Basic Linux Commands

Now we'll work through a bit of the [Unix Basics Tutorial from the bioinformatics workbook](https://bioinformaticsworkbook.org/Appendix/Unix/unix-basics-1.html#gsc.tab=0) created by Andrew Severin of Iowa State University/SCINet VRSC.

We'll also look at some [useful SLURM commands from the bioinformatics workbook](https://bioinformaticsworkbook.org/Appendix/Unix/01_slurm-basics.html#gsc.tab=0).



## Interactive Computing vs Batch Computing

Many geospatial researchers spend much of their time writing and debugging new scripts for each project they work on. This differs from other research communities who may be able to re-use a single script frequently for multiple projects or who can use a standard analysis process/workflow on many different input datasets.

A geospatial researcher may write and debug their scripts using small to medium size data until the script is functional and then modify the script to process big data only once. For this reason, geospatial researchers may more often use interactive computing sessions on an HPC.

### Interactive Computing on Ceres

Interactive computing essentially means that you are working directly on a compute node as opposed to using the SLURM job scheduler to submit compute jobs in batches. JupyterHub allows us easy access to interactive computing on the Ceres HPC. Just login to Ceres through JupyerHub and start coding in a Jupyter notebook- you will automatically be placed in an interactive compute session.

But let's learn how to open an interactive computing session from the command line. This is important when you log in with SSH or if you've logged in with JupyterHub but want to compute or install software on a different node than where your JupyterLab session is running. 

**Step 1: Open a terminal on Ceres**

Since we are already in JupyterLab, use the launcher to open a terminal. We could also use Windows Powershell or Mac/Linux Terminal to SSH onto the Ceres login node instead.

**Step 2: Start an Interactive Compute Session**
The simplest way to start an interactive session is:
```bash
salloc
```
Issuing this command requests the SLURM job scheduler to allocate you a single hyper-threaded core (2 logical cores) with 6200 MB of allocated memory on one of the compute nodes. The session will last for 2 days, but will timeout after 1.5 hours of inactivity.

View your runnning compute sessions/jobs with:
```bash
squeue -u user.name
````

To exit the interactive session:
```bash
exit
```

For more control over your interactive session you can use the ```srun``` command instead of ```salloc``` using the format:
```srun --pty -p queuename -t hh:mm:ss -n cores -N nodes /bin/bash -l```

```bash
srun --pty -p short -t 03:00:00 -n 4 -N 1 /bin/bash -l
```

will request the SLURM job scheduler to allocate you two hyper-threaded cores (4 logical cores) with 3100x4 MB of allocated memory on one of the compute nodes in the short partition. The session will last for 3 hours, but will also timeout due to inactivity after 1.5 hours.

### Batch Computing on Ceres

Batch computing involves writing and executing a batch script that the SLURM job scheduler will manage. This mode of computing is good for "set it and forget it" compute jobs such as running a climate model, executing a single script multiple times in a row, or executing a more complicated but fully functional workflow that you know you don't have to debug. We'll cover how to write and execute a batch script next.



## Submitting a Compute Job with a SLURM Batch Script

Let's practice by submitting a batch script.

First create simple python program:
```bash
cat > hello-world.py
print('Hello, world!')
```
then type Ctl-d to exit.

View the file you just created:
```bash
cat hello-world.py
```

Now create your batch script with nano or other text editor:
```bash
nano my-first-batch-script.sbatch
```

In the nano editor type:
```
#!/bin/bash
#SBATCH --job-name=HelloWorld 
#SBATCH -p short              #name of the partition (queue) you are submitting to
#SBATCH -N 1                  #number of nodes in this job
#SBATCH -n 2                  #number of cores/tasks in this job, you get all 20 physical cores with 2 threads per core with hyper-threading
#SBATCH -t 00:00:30           #time allocated for this job hours:mins:seconds
#SBATCH -o "stdout.%j.%N"     # standard output, %j adds job number to output file name and %N adds the node name
#SBATCH -e "stderr.%j.%N"     #optional, prints our standard error

module load python_3
echo "you are running python" 
python3 --version

python3 hello-world.py
```

Exit the nano editor with Ctl+O, enter, Ctl+X.

Submit your batch script with:
```bash
sbatch my-first-batch-script.sbatch
```

Check out the output of your compute job. It's in the stdout file:
```bash
ls
cat stdout.######.ceres##-compute-##
```

Note: there are a ton of other SBATCH options you could add to your script. For example, you could receive an email when your job has completed ([see the Ceres User Manual](https://scinet.usda.gov/guide/ceres/#batch-mode)) and lots more ([see the SLURM sbatch doc](https://slurm.schedmd.com/sbatch.html)).

Also Note: **this is a serial job**, meaning that it will run on a single compute core. The compute likely won't be any faster than if you ran this type of job on your laptop. To run your hello-world code in parallel from a batch script (multiple times simulataneously on different cores) you would use openMP or MPI (see the [Ceres User Manual](https://scinet.usda.gov/guide/ceres/#running-a-simple-openmp-job)) and your code would have to be in C or Fortran (not Python). For Python coders, there are much easier ways to run in parallel (using interactive mode as opposed to batch scripting), which we will cover in Session 3: Intro to Python and Dask.
