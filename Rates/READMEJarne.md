
1. Find input files. On DAS: file dataset=/HLTPhysics/Run2016H-PromptReco-v3/MINIAOD and copy it localy e.g.: xrdcp root://cms-xrd-global.cern.ch//store/data/Run2016H/HLTPhysics/MINIAOD/PromptReco-v3/000/284/169/00000/70884E5A-A2A1-E611-91FE-FA163E37CD23.root ./
2. Make a .json file with the run number and lumi ranges --> check WBM if all (except CASTOR and ZDC) are green for these lumi ranges: https://cmswbm.cern.ch/cmsdb/servlet/RunSummary --> fill in the run number --> check Lumi Sections
3. cd /user/jdeclerc/OverlapStudy/SteamRatesEdmWorkflow/Rates
4. In config_makeCondorJobsData.py point to the correct directory where you stored the data and point to the correct .json file
4. In Menu_HLT.py select the correct .csv file: out_online3p1_V4.csv (for the files you use for RunG) and out_online_v4p2_V6.csv (for the files you use for RunH) 
5. Prepare the .sh scripts to run by running: python config_makeCondorJobsData.py
6. then run: ./Jobs/Job_0/sub_0.sh (or run all the jobs in this directory in a separate qsub)
7. check the output in: Results/Data/Raw/PathPhysics/output.path.physics.0.csv and Results/Data/Raw/DatasetPhysics/output.dataset.physics.0.csv   
8. You can merge these last files by running  python config_mergeOutputsData.py
9. look at the combined output: Results/Data/output.path.physics.csv and Results/Data/output.dataset.physics.csv. In the first one you will need the totalPhysics rate and in the latter one the sum of all the Physics streams --> the difference is the overlap.

-----------------------------------------------------------------------------------------
