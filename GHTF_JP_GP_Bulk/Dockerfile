FROM rarsenal/ghtf-jp-rbase-gp

MAINTAINER iychang@uci.edu

RUN Rscript -e 'source("http://bioconductor.org/biocLite.R")' \
	-e 'biocLite("DESeq2")' \
	-e 'biocLite("edgeR")' \
	-e 'biocLite("limma")'
