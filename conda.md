# Conda

## Overview

### [Official description](https://docs.conda.io/en/latest/):
> Package, dependency and environment management for any language — **Python**, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, FORTRAN
> Conda:
>  * runs on Windows, macOS and Linux. 
>  * installs, runs and updates packages and their dependencies
>  * creates, saves, loads and switches between environments on your local computer

### Environment definition
> A conda environment is a directory that contains a specific collection of conda packages that you have installed (and their dependencies). 
> If you change one environment, your other environments are not affected. 

### Use cases
 * Use/develop a python package **which works** with a known set of python libraries (can simply export environment)
 * Develop a python package and test it in different environments (i.e. different version of libraries)
 * Create lightweight environments per project (only install required dependencies)
 * Python package working only with a specific version of python (Python 2 and not Python 3)
 * Etc.

### Distribution
 * Anaconda is a full distribution of the central software in the PyData ecosystem, and includes Python itself along with binaries for several hundred third-party open-source projects.
 * Miniconda is essentially an installer for an empty conda environment, containing only Conda and its dependencies, so that you can install what you need from scratch.
 
## Installation
### Example for Ubuntu OS with bash as default shell
```bash
mkdir -p ~/tmp/conda_install
cd ~/tmp/conda_install
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh

# Optional: create a custom path for miniconda
mkdir ~/pyutils 
# During installation:
# - accept default path or use custom path defined above
# - Agree to update $PATH in bashrc
bash Miniconda3-latest-Linux-x86_64.sh
# Update bash environment
source ~/.bashrc

# Optional: create custom path for python environments
mkdir ~/python_envs

### If custom paths used (miniconda and/or python envs), 
### update .condarc accordingly
echo "envs_dirs:" >> ~/.condarc
echo "- ${HOME}/python_envs" >> ~/.condarc
echo "- ${HOME}/pyutils/miniconda3/envs" >> ~/.condarc

### Add conda-forge channel (popular community channel)
conda config --add channels conda-forge
# If you prefer default channel to have priority,
# edit ~/.condarc to have conda-forge channel AFTER defaults
```

## Creating environments
### Example of python 2.7 environment
```bash
conda create python=2.7 -p ~/python_envs/sci27
# Or conda create python=2.7 -n sci27 if no custom env directory
### Activate environment and install packages
conda activate sci27
# Note the ipykernel package for integration of conda with jupyter (cf next section)
conda install numpy cython ipython scipy scikit-learn pandas xlrd matplotlib ipykernel
# Install package not available in known conda channels, with pip
pip install fury
# Install package hosted on github not available in conda or pip, but with a setup.py available
git clone http://github.com/demianw/tract_querier.git
cd tract_querier
python setup.py install
# Install package hosted on github not available in conda or pip, and without setup.py
pip install git+git://github.com/jkbr/httpie.git
```

### Example of python 3.7 environment
```bash
Create python 3.7 env
conda create python=3.7 -p ~/python_envs/sci37
source activate sci37
conda install numpy cython ipython scipy scikit-learn pandas xlrd matplotlib ipykernel
```

The next installation commands assume you would like to use Jupyter Notebooks with conda.
```bash
#Install Jupyter in base environment
conda activate base
conda install jupyter nb_conda_kernels
```
