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

## GRads

~~~bash
LANG=C.UTF-8 LC_ALL=C.UTF-8
apptainer push docker://debian:11
apt update
apt install -y curl perl-modules
cd /opt
curl -L# https://sourceforge.net/projects/opengrads/files/grads2/2.2.1.oga.1/Linux%20%2864%20Bits%29/opengrads-2.2.1.oga.1-bundle-x86_64-pc-linux-gnu-glibc_2.17.tar.gz/download | tar xzvf - 
mv -v opengrads-2.2.1.oga.1/Contents/* /usr/bin 
curl -LO# https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh 
bash Mambaforge-Linux-x86_64.sh -b -p /opt/grads
source /opt/grads/etc/profile.d/conda.sh
conda activate base
mamba install ipykernel
mamba clean --tarballs --index-cache --packages --yes
find $CONDA_PREFIX  -follow -type f -name '*.a' -delete
find $CONDA_PREFIX  -follow -type f -name '*.pyc' -delete
conda clean --force-pkgs-dirs --all --yes 
~~~~


