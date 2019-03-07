FROM rarsenal/ghtf-jpy-gp-rbase-3.5

MAINTAINER iychang@uci.edu

USER root

#setup R configs
#install libs needed for png 
RUN apt-get update && \
    apt-get -y install --fix-missing libhdf5-dev libtiff5-dev libgmp-dev libpng-dev texinfo texlive texlive-fonts-extra && \
    rm -rf /var/lib/apt/lists/*

RUN ln -s /bin/gzip /usr/bin/gzip && \
    ln -s /bin/tar /bin/gtar

USER $NB_USER 

#install R packages 1/3
RUN Rscript -e 'BiocManager::install("monocle", version = "3.8")'
USER root
RUN apt-get update && \ 
    apt-get -y install --fix-missing libgsl-dev &&\
    rm -rf /var/lib/apt/lists/*

#RUN Rscript -e 'BiocManager::install("zinbwave", version = "3.8")'

#install R packages 2/3
#RUN Rscript -e 'source("http://cf.10xgenomics.com/supp/cell-exp/rkit-install-2.0.0.R")'

#install R packages 3/3
#RUN Rscript -e "devtools::install_github(repo = 'satijalab/seurat', ref = 'release/3.0')"
RUN Rscript -e "install.packages('Seurat', dependencies=TRUE)"
#RUN pip install scanpy

