FROM continuumio/anaconda

RUN conda update -n base -c defaults conda
#RUN /opt/conda/bin/conda install pytorch cudatoolkit=9.0 -c pytorch
RUN /opt/conda/bin/conda install -c anaconda tensorflow-gpu

RUN /opt/conda/bin/conda config --add channels r && \
	/opt/conda/bin/conda config --add channels bioconda && \
	/opt/conda/bin/conda install r && \
	/opt/conda/bin/conda install rstudio && \ 
	/opt/conda/bin/conda clean -tipsy

RUN /opt/conda/bin/conda install -c darts-comp-bio darts_dnn darts_bht && \
	/opt/conda/bin/conda clean -tipsy
