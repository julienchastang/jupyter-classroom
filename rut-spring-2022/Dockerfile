# Heavily borrowed from docker-stacks/scipy-notebook/
# https://github.com/jupyter/docker-stacks/blob/master/scipy-notebook/Dockerfile

# python 3.8.6
ARG BASE_CONTAINER=pangeo/base-notebook:18b3f15
FROM $BASE_CONTAINER

LABEL maintainer="Unidata <support-gateway@unidata.ucar.edu>"

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends vim curl wget csh && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN . /srv/conda/etc/profile.d/conda.sh && conda activate notebook && \
    conda install 'pip'  && \
    pip install 'cloudpickle==1.6.0' && \
    pip install 'distributed==2.30.1' && \
    pip install 'numpy==1.19.2' && \
    pip install 'toolz==0.11.1' && \
    pip install 'tornado==6.1' && \
    pip install 'dask==2.30.0'  && \
    pip install 'xarray'  && \
    pip install 'ipywidgets'  && \
    pip install 'matplotlib'  && \
    pip install 'netcdf4'  && \
    pip install 'h5netcdf'  && \
    pip install 'pydap'  && \
    pip install 'scipy'  && \
    pip install 'nodejs'  && \
    pip install 'dask-gateway==0.9.0'

RUN . /srv/conda/etc/profile.d/conda.sh && conda activate notebook && \
    jupyter labextension install @jupyter-widgets/jupyterlab-manager && \
    jupyter lab build -y && \
    jupyter lab clean -y && \
    npm cache clean --force && \
    rm -rf "/home/${NB_USER}/.cache/yarn" && \
    rm -rf "/home/${NB_USER}/.node-gyp"

COPY wrf.ipynb /

USER $NB_UID
