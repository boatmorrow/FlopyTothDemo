## Installing PYSGFLOW in a virtual environment in VSCODE
These notes are for installing [PYSGFLOW](https://github.com/pygsflow/pygsflow) using a project specific .conda environement managed by VSCODE.  The changes for a general environment are small, and basically include creating your own named environement using conda, and updating that environment rather than the .conda local environment.

### Install conda and VSCODE
You need at least [miniconda](https://docs.conda.io/projects/miniconda/en/latest/) (my favorite).  [VSCODE](https://code.visualstudio.com/) is downloadable for free on all OS's as far as I can tell.

### Create a project folder
This folder will contain your .conda env and should also house all your other files for the project.  Everything we do for the .conda env can be easily modified for a real user environment, which might be the better move as some point.

### Now Build the ENV
Here we'll build the env using a file named flopy_forge.yml, created by me 1/22/24.  First we should modify our .condarc to make sure conda-forge is the default channel.  This should probably give you better results for most scientific software packages anyways.

* Open (create if necessary) the file ~/.condarc , where ~ is your home directory.
* Add the following lines:

        channels:
          - conda-forge
          - defaults

* Create new conda environment using vscode.
    - command shift P on mac (something similiar on windows...) -> Python: Create Environment
    - now there a new conda envrionment with no name and path /path/to/project/folder/.conda

* Add the packages 
    - open a terminal in vscode.  The commands listed here are for a "nix" type terminal.  I'm pretty sure the conda commands should be the same for a windows machine, using the correct paths (i.e. C:\path\to\your\folder).
        - make sure the (.conda) environment is the active one in your terminal, should be, but make sure.

      conda env update -p /path/to/project/folder/.conda --file flopy_forge.yml

    - this should add all the needed packages except gsflow, which we'll add next.

### Now Install GSFLOW
We'll install the dev version of GSFLOW, so we will need to clone the gsflow repository.  So, you need to have git installed.  [Installation Instructions for most OS's.](https://github.com/git-guides/install-git).

#### Clone the repo
* Make or cd to a directory where we'll download the repository to.
    - So, I have a directory ~/soft where I download all open source scientific software.  That makes it easy for me to find software I have added, and centralizes things.  I'd suggest something along these lines.  
    - If you already have something like this, change to that directory:

            cd /path/to/software/directory
        or
            dir C:\path\to\software\directory
    
    - If you don't have one make it:

            mkdir -p /path/to/software/directory
            cd /path/to/software/directory
        or
            
            dir C:\path\to\software\directory
        - the -p flag probably doesn't work on windows, so we'll have to figure that one out on the fly.
* Clone the pysflow git repository:
    - Make sure you are in your software directory.

            git clone https://github.com/pygsflow/pygsflow
    
    - You should now have a directory pygsflow in your software directory.

#### Install pysgsflow:
 - Make sure your desired conda environment is active!
 - Change into the pysgflow directory:

        cd pygsflow

    or 

        dir pygsflow

 - Install the dev version using pip:
            
            pip install .

* Check to make sure everything installed correctly:
    - change back your project folder:

            cd /path/to/project/folder
    
    - check for pygsflow:

            conda list | grep pygsflow
        
        - this command is nix specific, not sure how to do this in windows, but I think you use Select-String instead of grep. You can also* Check to make sure everything installed correctly:
    - change back your project folder:

            cd /path/to/project/folder
    
    - check for pygsflow:

            conda list | grep pygsflow
        
        - this command is nix specific, not sure how to do this in windows, but I think you use Select-String instead of grep. You can also just use "conda list", and look for pygsflow in the output.