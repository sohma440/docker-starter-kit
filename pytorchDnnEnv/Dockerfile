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


# polynote
RUN apt update -y && \
    apt install -y wget
RUN wget -q https://github.com/polynote/polynote/releases/download/$POLYNOTE_VERSION/polynote-dist.tar.gz && \
    tar xfzp polynote-dist.tar.gz && \
    rm polynote-dist.tar.gz && \
    sed -e "20,22 s/^#//" -e "s/127.0.0.1/0.0.0.0/" polynote/config-template.yml | tee polynote/config.yml
RUN wget -q https://www-us.apache.org/dist/spark/spark-2.4.4/spark-2.4.4-bin-hadoop2.7.tgz && \
    tar xfz spark-2.4.4-bin-hadoop2.7.tgz && \
    rm spark-2.4.4-bin-hadoop2.7.tgz


EXPOSE 8192

CMD ["./polynote/polynote.py"]