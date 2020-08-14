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
    pip install --upgrade jupyterlab-git nbgitpuller  && \
    wget -O environment.yml https://raw.githubusercontent.com/KennedyClouds/ATSC345_2020/master/ATSC345_2020.yml && \
    conda env update --name und-fall-2020 -f environment.yml && \
    rm environment.yml && \
    conda clean --all -f -y && \
    jupyter lab build -y && \
    jupyter lab clean -y && \
    npm cache clean --force && \
    rm -rf "/home/${NB_USER}/.cache/yarn" && \
    rm -rf "/home/${NB_USER}/.node-gyp" && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

COPY .condarc /

USER $NB_UID
