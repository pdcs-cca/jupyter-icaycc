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
bootstrap: docker
from: debian:11

%post 
        MAMBA_PATH=/opt/grads
        export LANG=C.UTF-8 LC_ALL=C.UTF-8 PATH=$MAMBA_PATH/bin:$PATH
        apt update
        apt install -y curl perl-modules git
        cd /opt
        curl -L# https://sourceforge.net/projects/opengrads/files/grads2/2.2.1.oga.1/Linux%20%2864%20Bits%29/opengrads-2.2.1.oga.1-bundle-x86_64-pc-linux-gnu-glibc_2.17.tar.gz/download | tar xzf - 
        mv -v opengrads-2.2.1.oga.1/Contents/* /usr/bin 
        rm -rf opengrads-2.2.1.oga.1
        curl -LO# https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh 
        bash Mambaforge-Linux-x86_64.sh -b -p /opt/grads
        rm Mambaforge-Linux-x86_64.sh
        mamba install --quiet --yes  ipykernel
        pip3 install  git+https://github.com/ykatsu111/jupyter-grads-kernel
        mamba clean --tarballs --index-cache --packages --yes
        find $MAMBA_PATH  -follow -type f -name '*.a' -delete
        find $MAMBA_PATH  -follow -type f -name '*.pyc' -delete
        conda clean --force-pkgs-dirs --all --yes 

%environment
        export LANG=C.UTF-8 LC_ALL=C.UTF-8 MAMBA_PATH=/opt/grads

%runscript
        #!/bin/bash 
        echo "$0($#,\"$@\")"
        source $MAMBA_PATH/etc/profile.d/conda.sh
        conda activate base 
        exec python $*

~~~~


