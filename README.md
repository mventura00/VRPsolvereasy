# VRPsolvereasy  -- Marta Ventura's Journey of getting 'VRPsolvereasy' to run, which is a Python interface for VRPSolver, a state-of-the-art Branch-Cut-and-Price exact solver for vehicle routing problems
Read more about it here: 
https://pypi.org/project/VRPSolverEasy/

This my documentation/ tutorial of how I went about using VRPSolvereasy!!! :-)

**Steps of "How to set up your config file for ROAR Collab"**
1. You have to somewhere open a 'config' file and enter the connection information to connect to ROAR Collab
   To connect, **you need to type:**  ssh mxv176@submit.hpc.psu.edu

   The 'Config' file should look like the following:
   Note, I renamed the 'Host' name to be: ROAR_Collab
   (also make you to never put spaces in whatever you save!!)
   
![Config file - how I created host name](https://github.com/mventura00/VRPsolvereasy/assets/44207428/d73accc7-72d8-4184-a3bc-da306b12b1c8)

**Steps of "How to connect to ROAR Collab"**
1. To connect to ROAR Collab, select the little blue/green button on the lower left hand corner. Looks like this:
![SSH ROAR_Collab connection button](https://github.com/mventura00/VRPsolvereasy/assets/44207428/6b7ce07d-819a-443e-9106-580da3c71033)

   
2. Then, select "Connect to Host"
3. Select "ROAR_Collab"
4. Select: work
5. Select folder: vrp
6. to double check where you are: Type: pwd
   If it says that you are in the 'work' folder, then you need to do the following.
   Type: cd vrp
   This will get you in side the folder 'vrp'
   Then, type: pwd
   This should then say: that you are in : mxv176/work/vrp 
8. Then, need to make sure 'Anaconda3' is loaded, so type:
   module load anaconda3
9. Then , you need to activate your 'local environment', so make sure to type:
    conda activate vrp

   (Or you can write):
    source activate vrp
   (note: put 'source' instead of 'conda' as conda may break some inter-active desktops)
11. To make sure that 'pip' is there, type:  which pip
    (note: pip is usually already installed)
   If it is not, Type:  python -m pip install --upgrade pip
(these are 1 of 2 commands on VRPSolverEasy website:  https://github.com/inria-UFF/VRPSolverEasy/tree/master  (at the very bottom!!0

12. Then, type:  conda install pip
   (This will install pip within conda)
13. To install the 'VRPSolvereasy' package solver,
    Then, type:  python -m pip install VRPSolverEasy

14. Type: pip list
    (to make sure VRPSolverEasy pkg is there!)
14. Type: conda list
15. which python
    (to make sure python is installed and everything is all set up)
16. I have had it ask me at the bottom, to select a 'Python Interpreter' so make sure to do that too!
17. Now, in order to submit a job, make sure to type:
sbatch submit.sh

    (the 's' in 'sbatch' is because its a SLURN operator, a scheduler)

**Steps of "How to check if ia job is 'Running' (R) or pending (P)"**
1. Type:  squeue -u mxv176

   (and we can see where the file is in the queue!!)

   PD --> if file is in queue, it's pending!
   R --> if file is running! If it is, then it will say something like "on p-sc-2330" which means it is running on the node #2330.
   See screenshot below:
   
 ![To check if task is running or pending](https://github.com/mventura00/VRPsolvereasy/assets/44207428/a552b5f3-bdc7-46ca-8252-409d4bfe0435)


 **Steps of "How to check if if a job DONE running!"** 

 1. Make sure to refresh the screen at the top 'toolbar' area:

![refresh button](https://github.com/mventura00/VRPsolvereasy/assets/44207428/80510aad-139a-47d3-a98a-339721f169a8)

2. Then, check the "Output" file, and see what the output shows

**Steps of "How to set-up your 'Submit.sh' file"**
1. Make sure to set up your 'Submit.sh' file, before you can try to send or submit any jobs.
2. Notice everythign I typed in the screenshot.

![submit sh file - what it contains](https://github.com/mventura00/VRPsolvereasy/assets/44207428/cb020046-5417-4789-ab5a-dc3245fa2cca)


The first 4 lines are the bin/bash scripts. 
#SBATCh --nodes=1
#SBATCh --ntask=1
#SBATCh --mem=16GB
#SBATCh --time= 48:00:00
#SBATCH --partition=open 

Note, the max time allowable to run (for FREE) is 48 hrs. I updated the memory to '16GB'
I **added these extra 3 lines** (that from what is instructed on the PSU ROAR website: https://www.icds.psu.edu/running-batch-jobs-on-roar-collab/
#SBATCH --output=HFVRPoutput.out
#SBATCH --error=HFVRPerror.err
#SBATCH --job-name=HFVRP

So that it puts the 'output' and 'error' in a different script file!

Notice, that I put the pathway of where 'python' is stored/saved... this is the "Python interpretor", so it tells it exactly the path!
The 'HFVRP.py' is the name of the file that yo uwwant to run


node = 1
ntask = 1

**Note:  **
node =1 , uses that it uses 1 server rack, where each 'server rack' has 40 different processors. 
ntask = 1 , means it is using 1 processor, but we can use up to 100 processors per job if we wanted to ...and in order to do that, we would need to 'parallelize our jobs', and python has some sort of 'parallel' package, and he sent me this information. The package to use is called "multiprocessing"...but read  more about it here:
https://docs.python.org/3/library/multiprocessing.html

So, if you'd like to parallelize your script (then you need to change the value of ntasks).

