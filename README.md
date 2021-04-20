# EGMObjectDumper
This package dumps electron and photon related variables into a flat tree. The package runs on CMS MINIAOD data/MC. Also it will be updated soon to run on AOD data/MC.

How to Install?

cmsrel CMSSW_11_1_0_pre8

cd CMSSW_11_1_0_pre8/src

cmsenv

git clone https://github.com/akapoorcern/EGMObjectDumper.git

scram b -j8

cmsRun EGMObjectDumper/egmNtuplizer/test/Run3_ConfFile_cfg.py

#This will make a first tree for the following sample:
#/store/mc/Run3Summer19MiniAOD/GJet_Pt-40toInf_DoubleEMEnriched_MGG-80toInf_TuneCP5_14TeV_Pythia8/MINIAODSIM/2021Scenario_106X_mcRun3_2021_re\
alistic_v3-v2/130000/00DF0005-F507-2C4B-BF8B-C46342D7194E.root
#You will need grid proxy setup for this

###################################################################################

### Check the branches in egmTree.root

See if you have the following branches 
```
 pt
 eta
 hadTowOverEmValid
 hadTowOverEm
 trkSumPtHollowConeDR03
 ecalRecHitSumEtConeDR03
 hcalTowerSumEtConeDR03
 sigmaIetaIeta
 trkSumPtSolidConeDR03
```

How to check if the branches were added in the code:
example, look for this line in egmNtuplizer/plugins/egmNtuplizer_photons.cc
```
phoHoverE_          .push_back(iPho->hadTowOverEm());
```
This is how you add hadTowOverEm 

Also see how many times phoHoverE_ has been written in egmNtuplizer/plugins/egmNtuplizer_photons.cc

In one place it is declared

In one place it is filled

In one place is added in the tree

In one place it is cleared

All the steps have to done for any variable

if any of the branches we need is not added in egmNtuplizer/plugins/egmNtuplizer_photons.cc, we will have to add ourselves