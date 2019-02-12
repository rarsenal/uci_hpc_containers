FROM rarsenal/ghtf-jp-rbase-gp

MAINTAINER iychang@uci.edu

USER root

#setup R configs
#install libs needed for png 
RUN apt-get update && \
    apt-get -y install --fix-missing libhdf5-dev libtiff5-dev libgmp-dev libpng-dev texinfo texlive texlive-fonts-extra && \
    rm -rf /var/lib/apt/lists/*

USER $NB_USER 

#install R packages 1/3
RUN Rscript -e "source('https://bioconductor.org/biocLite.R')" \
	-e "biocLite('monocle')" \
	-e "biocLite('zinbwave')"

#install R packages 2/3
RUN Rscript -e 'source("http://cf.10xgenomics.com/supp/cell-exp/rkit-install-2.0.0.R")'

#install R packages 3/3
RUN Rscript -e "install.packages('Seurat', dependencies=TRUE)"

RUN pip install scanpy

