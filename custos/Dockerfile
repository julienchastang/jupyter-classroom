from jupyterhub/k8s-hub:0.11.1

# Note this container is *not* for the `singleuser` tag, but for the top-level
# `hub` tag

RUN pip install kubernetes==18.20.0 --ignore-installed PyYAML && \
    pip install jupyterhub-kubespawner==2.0.0 && \
    python3 -m pip install --upgrade jupyterhub==2.1.1 && \
    pip install jupyterhub_idle_culler==1.2.1 && \
    pip install custos-jupyterhub-authenticator
