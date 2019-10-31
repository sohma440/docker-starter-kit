FROM pytorch/pytorch:1.3-cuda10.1-cudnn7-runtime

RUN pip install torchsummary jupyterlab 

RUN conda update -n base -c defaults conda

# jupyter
RUN conda install -c conda-forge jupyterlab nodejs &&\
    jupyter labextension install "@krassowski/jupyterlab-lsp" "@jupyter-widgets/jupyterlab-manager"

# basic tools
RUN conda install -c anaconda pyyaml scikit-learn requests opencv && \
    conda install -c conda-forge flufl.lock scikit-image tensorboard albumentations

# open slide
RUN conda install -c bioconda openslide-python
