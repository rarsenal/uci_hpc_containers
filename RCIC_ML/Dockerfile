FROM jupyter/tensorflow-notebook

MAINTAINER iychang@uci.edu

USER root

RUN /opt/conda/bin/conda install pytorch torchvision cudatoolkit=9.0 -c pytorch && \
    /opt/conda/bin/conda install -c anaconda tensorflow-gpu

RUN /opt/conda/bin/conda create -n darts python=2.7

RUN /opt/conda/bin/conda init bash

RUN . /opt/conda/etc/profile.d/conda.sh && \
	conda activate darts && \
	conda install -c darts-comp-bio darts_dnn && \
	conda install pip && \
	pip install ipykernel && \
	python2 -m ipykernel install --user

RUN chown -R jovyan /home/jovyan/.local


USER $NB_USER 

