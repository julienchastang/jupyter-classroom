# Heavily borrowed from docker-stacks/scipy-notebook/
# https://github.com/jupyter/docker-stacks/blob/master/scipy-notebook/Dockerfile

ARG BASE_CONTAINER=jupyter/scipy-notebook:latest
FROM $BASE_CONTAINER

LABEL maintainer="Unidata <support-gateway@unidata.ucar.edu>"

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends ffmpeg vim curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    wget https://ramadda.scigw.unidata.ucar.edu/repository/entry/get/python-novice-gapminder-data.zip?entryid=b355c304-0993-4bc4-ad5d-d6faba006197 \
    -O /python-novice-gapminder-data.zip && \
    unzip /python-novice-gapminder-data.zip -d /

RUN conda install --quiet --yes \
    'conda-forge::nb_conda_kernels'  && \
    pip install --upgrade jupyterlab-git jupyterlab_sql nbgitpuller && \
    wget https://raw.githubusercontent.com/Unidata/python-training/master/environment.yml && \
    conda env update --name und2-spring-2020 -f environment.yml && \
    conda clean --all -f -y && \
    jupyter lab build -y && \
    jupyter lab clean -y && \
    npm cache clean --force && \
    rm -rf "/home/${NB_USER}/.cache/yarn" && \
    rm -rf "/home/${NB_USER}/.node-gyp" && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

USER $NB_UID
