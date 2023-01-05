# Instlación mamba
https://github.com/conda-forge/miniforge#mambaforge

curl -LO https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-pypy3-Linux-x86_64.sh

bash Mambaforge-Linux-x86_64.sh -b -p /opt/mambaforge/22.9.0-2/
source /opt/mambaforge/22.9.0-2/etc/profile.d/conda.sh 
conda activate base
mamba install jupyterlab jupyterhub jupyterlab-system-monitor nb_conda_kernels
