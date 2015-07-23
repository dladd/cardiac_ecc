cardiac_ecc
===========

A set of codes to simulate excitation-contraction coupling in cardiac cells using FE methods. 
The code uses the OpenCMISS libraries (www.opencmiss.org) to set up the simulation framework. The geometric model -half-sarcomere of a rat left-ventricular myocyte- was generated by integrating electron tomography data of myofibrils and mitochondria and confocal microscopy data of RyR clusters using the RyRSimulator software: https://github.com/vraj004/RyR-simulator . The model currently simulates calcium release and diffusion from clusters of ryanodine receptors.


**required Applications/Packages**
----------------------------------
openCMISS and associated libraries - www.opencmiss.org



**BRANCH INFORMAITON**
----------------------
master:
 - contains the base codes for simulating Ca2+ release and diffusion in the half-sarcomere model. The simulation uses a prescribed equation to model the Ca2+ release profile from the RyR clusters. 
 
 cicr_v2:
 - contains the same codes as master branch, except that the simulation uses a set of biophysical equations describing calcium-induced-calcium release (based on Sobie et al, Biophys J, 2002)

**FOLDER INFORMATION**
----------------------
cube_spark/:
 - directory containing codes to simulate release from a single release site inside a cube of 5 micrometer size.
 
 src/:
 - directory containing the fortran 90 program routine that uses opencmiss libraries to simulate calcium release and diffusion in the half-sarcomere geometric model.
 
 meshinputs/:
  - directory containing all the necessary inputs related to the geometry that are required for the simulations
  
  - filenames containing .1.node/ele/face : tetgen generated half-sarcomere mesh files of an electron-tomogram derived rat ventricular myocyte

  - filename containing .1.bdnode : node numbers of the mesh around the outer surface at which some boundary conditions are assigned. 

  - filenames containing _N123_simPP3_tausim2 : text file containing spatially varying fields representing density of ryr clusters (total number determined by the number after "N") and the ryr-cluster associated lag in triggering of calcium release; the fields are defined at the mesh nodes. The number after simPP determines the version of the RyR cluster simulation results being used and the number after tausim identifies the version of the time release lag sampling that is being used.


RUNNING THE PROGRAM
-------------------
1. Interested users need to install compiled versions of the opencmiss libraries. Instructions and support are available at www.opencmiss.org. 
2. Once installed, the Makefile must be edited in order to compile the main program in src/ against the opencmiss libraries.
3. File 'inputs.txt' contains default settings to run a simulation. Comments (prefixed by #) explain the different input variables. 
 


