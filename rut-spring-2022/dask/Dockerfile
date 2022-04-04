ARG BASE_CONTAINER=daskgateway/dask-gateway:latest
FROM $BASE_CONTAINER

LABEL maintainer="Unidata <support-gateway@unidata.ucar.edu>"

RUN conda install -c conda-forge --quiet --yes \
    'xarray' \
    'netcdf4' \
    'h5netcdf'
