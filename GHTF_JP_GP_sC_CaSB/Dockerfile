FROM rarsenal/ghtf-jp-sc-gp

MAINTAINER iychang@uci.edu

USER root 

#install R packages
RUN Rscript -e "source('https://bioconductor.org/biocLite.R')" \
	-e "biocLite('CoGAPS')"

#RUN Rscript -e 'install.packages("dplyr")'

RUN ln -s /bin/tar /bin/gtar

#RUN Rscript -e "source('https://bioconductor.org/biocLite.R')" \
#	-e "biocLite('genesofeve/projectR', dependencies = TRUE, build_vignettes = TRUE)"

RUN Rscript -e 'install.packages("devtools", dependencies = TRUE)'


RUn Rscript -e 'library(devtools)' \ 
	-e 'install_github("drisso/SingleCellExperiment")'

RUn Rscript -e 'library(devtools)' \ 
	-e 'install_github("genesofeve/projectR")'

USER $NB_USER
