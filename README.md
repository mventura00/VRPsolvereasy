# VRPsolvereasy  -- Marta Ventura's Journey of getting 'VRPsolvereasy' to run (with the help of Waquar Kaleem!)
This my documentation/ tutorial of how I went about using VRPSolvereasy!!! :-)

**Steps of "How to set up your config file for ROAR Collab"**
1. You have to somewhere open a 'config' file and enter the connection information to connect to ROAR Collab
   To connect, **you need to type:**  ssh mxv176@submit.hpc.psu.edu

   The 'Config' file should look like the following:
   Note, I renamed the 'Host' name to be: ROAR_Collab
   (also make you to never put spaces in whatever you save!!)

   ![image](https://github.com/mventura00/VRPsolvereasy/assets/44207428/130b10af-9342-41bb-87f4-a296f2fc5c54)

**Steps of "How to connect to ROAR Collab"**
1. To connect to ROAR Collab, select the little blue/green button on the lower left hand corner. Looks like this:
   ![image](https://github.com/mventura00/VRPsolvereasy/assets/44207428/9b5d078c-5f0c-44c6-88e1-30cf74bc8933)
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
    source activate vrp
   (note: put 'source' instead of 'conda' as conda may break some inter-active desktops)
10. 




