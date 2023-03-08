# Descargar e instalar mambaforge
~~~bash
curl -LO https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh   
bash Mambaforge-Linux-x86_64.sh -b -p /opt/software/apps/python/mambaforge/diplomado2023 
~~~

# Cargar entorno 

~~~bash
source /opt/software/apps/python/mambaforge/diplomado2023/etc/profile.d/conda.sh
mamba env list
# conda environments:
#
base                     /opt/software/apps/python/mambaforge/diplomado2023

conda activate base

mamba install jupyterlab-system-monitor \
jupyterlab-unfold jupyterlab-autosave-on-focus-change \
jupyterlab-github nb_conda_kernels jupyterhub 
~~~

~~~bash
mamba env export --from-history
name: base
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.10
  - mamba==1.1.0
  - conda==22.11.1
  - pip
  - setuptools=65
  - jupyterlab-system-monitor
  - jupyterlab-unfold
  - jupyterlab-autosave-on-focus-change
  - jupyterlab-github
  - ca-certificates
  - certifi
  - openssl
  - nb_conda_kernels
  - jupyterhub
prefix: /opt/software/apps/python/mambaforge/diplomado2023

~~~
