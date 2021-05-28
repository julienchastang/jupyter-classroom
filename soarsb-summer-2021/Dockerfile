ARG BASE_CONTAINER=jupyter/scipy-notebook:latest
FROM $BASE_CONTAINER

LABEL maintainer="Unidata <support-gateway@unidata.ucar.edu>"

USER root

# ffmpeg for matplotlib anim & dvipng for latex labels
RUN apt-get update && \
    apt-get install -y --no-install-recommends openssh-client && \
    rm -rf /var/lib/apt/lists/*

RUN conda install --quiet --yes \
    'conda-forge::nb_conda_kernels'  && \
    wget https://raw.githubusercontent.com/Unidata/python-training/master/environment.yml && \
    conda env update --name soarsb-summer-2021 -f environment.yml && \
    rm environment.yml && \
    conda clean --all -f -y && \
    conda clean --all -f -y && \
    npm cache clean --force && \
    jupyter lab clean && \
    rm -rf /home/$NB_USER/.cache/yarn && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

USER $NB_UID
