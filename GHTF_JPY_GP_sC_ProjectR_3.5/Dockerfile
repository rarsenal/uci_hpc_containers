FROM rarsenal/ghtf-jpy-gp-sc-seurat2-3.5

MAINTAINER iychang@uci.edu


#install R packages
RUN Rscript -e 'BiocManager::install("CoGAPS", version = "3.8")'

RUN Rscript -e 'withr::with_makevars(c(PKG_LIBS="-liconv"), install.packages("readxl"), assignment="+=")'
RUN Rscript -e 'withr::with_makevars(c(PKG_LIBS="-liconv"), install.packages("haven"), assignment="+=")'
RUN Rscript -e 'BiocManager::install("SingleCellExperiment", version = "3.8")'

RUN Rscript -e 'devtools::install_github("genesofeve/projectR")'

