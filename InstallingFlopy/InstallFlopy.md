## Installing Flopy with Conda

Installing Flopy using conda is fairly straightforward.  However, it can take a bit of time.

### Step 1:
Intall Conda/miniconda/anaconda.  I use miniconda, but the full flown Anaconda installation could be your jam.  
You need at the very least - conda.

*Linux* 
 - use your package manager, they'll have a conda package.  

 - On CentOS:

     yum install conda

*MacOS, Windows* - there are package installers at the Anaconda website: 
      https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html 

 - Run the installer.

### Step 2:
- Create and activate a conda environment for flopy. 

 * FloPy is a python library with capabilites for producing the required input files to run MODFLOW, along with the ability to read modflow output into python arrays for post processing and vizualiation.
 * This environment should have decent, basic science capabilities as well as flopy. I have added a file which creates a starting environment for you.  The file is named:
    flopy_forge_environment.yml

- Run the following command to create the environment with the above requested packages:

    conda env create --file flopy_forge_environment.yml

- This command will create the new conda environment flopy_forge. Its going to take awhile.  Go get a coffee.

- Once conda has finished creating the environment we now need to activate it:
     
    conda activate flopy_forge

### Step 3:
- Install pymake for max/linux.

  - Pymake is utility for downloading and building modflow programs on your local machine. Pymake requires a fortran compiler.  I use gcc/gfortran which is available on all package managers. I think pymake only works easily for \*nix computers.  Windows users usually have to download pre-made binaries.

- With flopy_forge environment active:    


- There scripts to make every USGS groundwater code.  This is a bit over kill, but ensure you are always able to get the most up to date version of the build scripts.  Clone the git respository some where you like.  For me I keep all downloaded software in a folder under $Home/soft, where $Home is your user home prefix.  To download this repository I would then:

    cd $Home/soft
    git clone https://github.com/modflowpy/pymake.git

- To update:
  
    cd $Home/soft/pymake
    git pull

-Install pymake
    python setup.py install

### Step 4:
- Install modflow2005 using pymake, (with flopy-forge active):

 -  Change to the examples directory

    cd pymake/examples
    python ./make_mf2005.py

- This script will download the source code for the internet and compile it using your system compiler, so it requires an internet connection. After it completes you will have an exectuable named mf6, which is the modflow 2005 program.  This program is what will be needed to run modflow simulations. the exectuable needs to be in the system PATH.  In other words, it either needs to be in a location the sytem knows to search (e.g. /usr/local/bin) or needs to be copied into any directory you trying to run model in, or you can add the current location to your PATH. The examples directory has scripts to download and build almost any USGS software.  Its pretty rad.  

- We are now ready to begin simulating and analyzing groundwater flow problems. 

### Getting started with FLOPY
I have written a tutorial which uses Flopy and MODFLOW 2005 to simulate the results of Toth 1962.  You can get the entire repository by navigating to a directory where you like the repostiroy to reside, and then clone with git using:

git clone https://github.com/boatmorrow/FlopyTothDemo
