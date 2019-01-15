FROM rarsenal/ghtf-jp-sc-gp

MAINTAINER iychang@uci.edu

USER root

COPY cellranger-3.0.0.tar.gz /opt/

RUN cd /opt && \
    tar -xzvf cellranger-3.0.0.tar.gz

ENV PATH="/opt/cellranger-3.0.0:${PATH}"

USER $NB_USER 

ENV PATH="/opt/cellranger-3.0.0:${PATH}"
