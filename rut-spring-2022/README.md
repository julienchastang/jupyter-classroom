The following Dask gateway is built on top of Andrea Zonca's work on [how to build and run a Dask cluster on Jetstream](https://zonca.dev/2022/01/dask-gateway-jupyterhub.html).

After you build the `Dockerfile` image in this directory and push it to dockerhub,  it should be referenced in `secrets.yaml`. See the `image` tag. It should also be referenced in `dask/config_jupyterhub.yaml`.

After you build the `Dockerfile` image in the `dask` and push it to dockerhub,  it should be referenced in in the `dask/config_dask-gateway.yaml` file in the `c.Backend.cluster_options`section.

The `wrf.ipynb` file is a Jupyter notebook that demonstrates analysis and visualization of WRF data from the NCAR RDA employing a Dask cluster.
